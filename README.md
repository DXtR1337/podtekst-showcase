<p align="center">
  <img src="podtekst_logo.svg" alt="PodTeksT" width="380" />
</p>

<p align="center">
  <b>odkryj to, co kryje się między wierszami</b><br/>
  <sub>discover what hides between the lines</sub>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Next.js-16-black?style=for-the-badge&logo=next.js" alt="Next.js 16" />
  <img src="https://img.shields.io/badge/React-19-61DAFB?style=for-the-badge&logo=react" alt="React 19" />
  <img src="https://img.shields.io/badge/TypeScript-strict-blue?style=for-the-badge&logo=typescript" alt="TypeScript strict" />
  <img src="https://img.shields.io/badge/Rust-WASM-b7410e?style=for-the-badge&logo=rust" alt="Rust compiled to WASM" />
  <img src="https://img.shields.io/badge/SQLite-OPFS-003B57?style=for-the-badge&logo=sqlite" alt="SQLite on OPFS" />
</p>

<p align="center">
  <a href="https://podtekst.app"><img src="https://img.shields.io/badge/podtekst.app-10b981?style=for-the-badge" alt="podtekst.app" /></a>
</p>

> **Status: pre-launch.** The landing page, articles, psychometric questionnaires and the research pages are public at [podtekst.app](https://podtekst.app). The analysis app sits behind a login and registration is closed for now.
>
> **About this repository:** the code here is a stripped snapshot from March 2026, kept for reference. It does not build, and [NOTICE.md](NOTICE.md) lists what was left out. This README describes the private codebase as of November 2026, which has moved well past the snapshot.

## What is PodTeksT?

PodTeksT reads chat exports and shows what a conversation says about a relationship. Metrics are computed in the browser by ordinary code, with no model involved. An optional multi-pass AI analysis then writes the interpretation on top of them, and the results are packaged as playful modes people can share.

It is built for Polish first: morphology, diacritics, declension of names, chat slang and the way people actually text. The name is a wordplay on *podtekst*, the Polish word for subtext.

## Scale

Counted on the development branch on 2026-11-05.

| | |
|---|---|
| TypeScript and TSX, without tests | about 1.2 million lines |
| Rust | about 160,000 lines in 17 crates |
| Automated test cases (Vitest) | about 22,000 in 2,160 files |
| Pages and API routes | 157 and 70 |
| Web Workers | 16 |
| Psychometric questionnaires | 70+ |
| Articles | 50+ |

In development since February 2026 by one person working with AI coding agents.

## Architecture

```
Browser
  Upload       TypeScript preflight, then the Rust/WASM parser
  Kernel       Rust/WASM: metrics, sentiment, event graph
  Storage      SQLite on OPFS, in the user's browser
  Embeddings   PolDense 512D, on WebGPU or WASM
  Search       worker: dense + BM25 + SPLADE, RRF fusion
     |
     |  sampled messages, names swapped (details under Privacy)
     v
Server: Next.js API routes, streaming over SSE
  Analysis     multi-pass AI with schema validation and resumable jobs
  Models       Gemini Flash for analysis, Claude on Bedrock for the book mode
  Services     Supabase Auth, Sentry
```

### Rust kernel

Parsing and the quantitative engine live in `podtekst-core`, compiled to WebAssembly and used by the browser as the single source of truth. A second family of crates, `podtekst-search-*`, holds the search engine. A Tauri desktop app under development shares the same Rust code.

### Supported exports

Messenger, Instagram, WhatsApp, Telegram and Claude. Facebook's broken text encoding is repaired on import, including end-to-end encrypted threads, and a new export can be appended to a conversation already in the library.

### Semantic search

| Layer | Technology |
|---|---|
| Dense | PolDense-68M-FT, a fine-tuned Polish model, 512 dimensions, run locally |
| Lexical | BM25 with Polish morphology (PoliMorf, CLARIN-PL) |
| Sparse | SPLADE |
| Fusion | Reciprocal Rank Fusion, k = 60 |
| Rerank | Optional model rerank in the paid tier |

### AI analysis

The kernel selects a sample of the conversation, a reconnaissance pass finds what deserves a closer look, and later passes build on the earlier ones. Claims carry evidence tags (direct quote, behavioral pattern, statistic, inference), output is validated against schemas, and an interrupted run resumes instead of starting over.

## Privacy

What the product does, without rounding up:

- **Stays in the browser:** the uploaded export, parsing, metrics, the conversation library and local embeddings.
- **Sent for AI features:** a sample of messages, with participant names swapped for invented ones before it leaves. This is pseudonymization, not anonymization: nicknames, names of other people and other identifiers can still pass through.
- **Sent without name swapping:** text for server-side embeddings, only after explicit consent; sparse search queries; image analysis; and search requests when the user turns name swapping off.
- **Logging:** chat content is kept out of server logs.

## What users get

| Surface | What it is |
|---|---|
| **Metrics boards** | Full-window boards for rhythm, response times, sentiment and language |
| **Roast and Stand-up** | Comedy written about the conversation |
| **Dating profile** | A profile based on how someone actually texts |
| **Credibility board** | Declarations compared with what happened later |
| **Delusion quiz** | A game show about how well you know your own chat, also playable on two phones |
| **Animals, Emotions, Memories, Map** | Themed views of the same conversation |
| **Investigator** | An agent that reads the archive and reports back |
| **Diary** | A book written from the conversation |
| **Paragon** | Relationship receipts as a series of drawn street scenes |
| **Share cards and tickets** | Exportable cards, and links that carry a saved result with the key in the URL fragment |

### Psychometric questionnaires

More than 70 self-report questionnaires with scoring and result summaries at [podtekst.app/testy](https://podtekst.app/testy). **A test result comes only from the answers given in the questionnaire, never from chat data.** These are not diagnostic tools, some are our own translations without Polish norms, and instruments with an explicit ban on app use are excluded.

### Design

Every mode is a drawn scene rather than a page of cards: dark backgrounds, spot lighting and a metaphor that carries the data, like a receipt printer or a game show studio. Animation is budgeted by device, with heavier layers pausing off screen and a lighter version for weak hardware.

## Research

- Preprint on synthetic Polish personas: [DOI 10.5281/zenodo.21406223](https://doi.org/10.5281/zenodo.21406223)
- Data and code: [30synthetic-polish-personas](https://github.com/DXtR1337/30synthetic-polish-personas)
- Overview: [podtekst.app/persony](https://podtekst.app/persony)

## Tech stack

| Layer | Technology |
|---|---|
| App | Next.js 16 (App Router), React 19, TypeScript strict with tsgo |
| Core | Rust compiled to WebAssembly |
| Storage | SQLite on OPFS |
| Local ML | ONNX Runtime Web, transformers.js, WebGPU with WASM fallback |
| AI | Gemini Flash, Claude on Amazon Bedrock |
| Styling and motion | Tailwind CSS v4, custom CSS, Motion, Spline |
| Auth and payments | Supabase Auth; Stripe integration, not live yet |
| Infrastructure | Google Cloud Run, Cloudflare, Sentry |
| Desktop | Tauri, in development |
| Testing | Vitest, Playwright, Rust tests |

---

<p align="center">
  <a href="https://podtekst.app"><b>podtekst.app</b></a><br/>
  <sub>Michał Wiencek (DXTR), Kraków</sub>
</p>
