<p align="center">
  <img src="podtekst_logo.svg" alt="PodTeksT" width="380" />
</p>

<p align="center">
  <b>odkryj to, co kryje się między wierszami</b><br/>
  <sub>discover what hides between the lines</sub>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Next.js-16+-black?style=for-the-badge&logo=next.js" />
  <img src="https://img.shields.io/badge/TypeScript-5-blue?style=for-the-badge&logo=typescript" />
  <img src="https://img.shields.io/badge/Tailwind-v4-06B6D4?style=for-the-badge&logo=tailwindcss" />
  <img src="https://img.shields.io/badge/Gemini_AI-3_Flash-8E75B2?style=for-the-badge&logo=google" />
  <img src="https://img.shields.io/badge/Discord_Bot-15_cmds-5865F2?style=for-the-badge&logo=discord" />
</p>

<p align="center">
  <a href="https://podtekst.app"><img src="https://img.shields.io/badge/Live_App-podtekst.app-10b981?style=for-the-badge" /></a>
</p>

---

> **This is a public showcase** of the PodTeksT codebase. AI prompt engineering, proprietary scoring formulas, server-side API routes, and deployment infrastructure have been intentionally excluded. See [NOTICE.md](NOTICE.md) for details.

---

## What is PodTeksT?

PodTeksT is an AI-powered conversation analyzer that reveals the psychology behind your chats. Upload a chat export from **Messenger, WhatsApp, Instagram, Telegram, or Discord** and get:

- **150+ quantitative metrics** computed entirely client-side (your messages never leave your device)
- **Multi-pass AI psychological analysis** powered by Gemini API with a 3-phase intelligent sampling pipeline
- **12 interactive AI modules** — from personality profiling to comedy roasts
- **30+ shareable cards** for social media
- **Discord bot** with 15 slash commands for server analytics

The name is a Polish wordplay: *pod-tekst* = subtext, *eks* = ex (former partner), *między wierszami* = between the lines.

---

## Key Features

### Quantitative Engine (150+ Metrics, No AI)

All computed client-side using published academic methodology:

| Category | Highlights |
|---|---|
| **Per-Person Stats** | Messages, words, emoji, reactions, catchphrases, media breakdown |
| **Timing** | Response times (median/avg/fastest), initiations, double-text rate, burst detection |
| **Engagement** | Weighted engagement score, consistency, 7x24 heatmap, monthly trends |
| **Sentiment** | AFINN-165 + 6-layer Polish dictionary (~7000 words), negation handling |
| **Linguistics** | MTLD, LSM (Ireland & Pennebaker), pronoun analysis, CNI (Derber), cognitive complexity |
| **Dynamics** | Conflict detection, intimacy progression, pursuit-withdrawal cycles, reciprocity index |
| **Chronobiology** | Behavioral chronotype (Roy et al. 2021), compatibility score, weekday-weekend shift |
| **Scores** | Compatibility, Interest, Ghost Risk, Investment Asymmetry (Stanley et al. 2017) |
| **Assessment** | Gottman Four Horsemen, bid-response ratio, communication grade (A-F), repair potential |
| **Rankings** | Heuristic percentile rankings + 15 achievement badges |

<details>
<summary>Full metric list (click to expand)</summary>

**Per-Person:** Total messages, words, avg words/message, longest/shortest messages, questions asked, media count (photos, video, GIF, stickers, audio, files), reactions sent/received, deleted/edited messages, active days, top emoji/words/phrases, catchphrase detection

**Timing:** Median/average/fastest/slowest response time, conversation initiations, longest silence, double-text rate, response time distribution (8 bins), IQR outlier filtering

**Engagement:** Engagement score (0-100), consistency score, session count (6h gap), late night ratio, weekend ratio, 7x24 heatmap, 24h activity chart, monthly trends, year milestones

**Sentiment & Dynamics:** AFINN-165 + Polish 6-layer dictionary, conflict escalation/resolution patterns, intimacy progression, pursuit-withdrawal cycles, reciprocity index (0-1), burst detection (3x rolling average)

**Linguistics:** MTLD (McCarthy & Jarvis 2010), Language Style Matching (Ireland & Pennebaker 2010), pronoun I/We/You rates with Polish declension, Conversational Narcissism Index (Derber 1979), emotion vocabulary diversity (12-category Plutchik), cognitive complexity (Suedfeld & Tetlock 1977), temporal focus, conversational repair patterns (Schegloff et al. 1977)

**Advanced:** Behavioral chronotype, chronotype compatibility, Gottman Four Horsemen, bid-response ratio (Driver & Gottman 2004), Active-Constructive Responding (Gable et al. 2004), Moral Foundations (Haidt & Graham 2007), 4 dynamic indicators, communication strain index, threat meters, damage report
</details>

---

### AI Analysis (4-Pass Pipeline)

Three-phase intelligent sampling with Gemini 3 Flash:

```
Phase 1: Recon          500 stratified msgs → AI identifies critical moments
Phase 2: Deep Recon     targeted extraction → AI refines narrative
Phase 3: Deep Analysis  ~1500 msgs total → 4 structured passes
```

| Pass | Focus | Output |
|---|---|---|
| **1** | Relationship Overview | Tone, style, relationship type, themes |
| **2** | Dynamics Deep Dive | Power balance, conflict, intimacy, red/green flags |
| **3** | Individual Profiles | Big Five, MBTI, attachment style, love languages |
| **4** | Final Synthesis | Health Score (0-100), predictions with confidence% |

---

### Interactive AI Modules (12)

| Module | What it does |
|---|---|
| **Enhanced Roast** | Psychological roast with full analysis context |
| **Stand-Up Comedy** | 7-act comedy show about your chat (PDF export) |
| **CPS Screener** | 63-question Communication Pattern Screening |
| **Subtext Decoder** | What did they *really* mean? (30+ message windows) |
| **Court Trial** | AI courtroom — charges, prosecution, defense, verdict + mugshots |
| **Dating Profile** | Honest dating profile based on texting behavior |
| **Reply Simulator** | Type a message, get a response in your partner's voice |
| **Delusion Quiz** | Self-awareness test (Delusion Index 0-100) |
| **Capitalization** | Active-Constructive Responding (Gable et al. 2004) |
| **Moral Foundations** | Haidt's 6 foundations — radar chart + conflict analysis |
| **Emotion Causes** | SemEval-2024 format — who triggered what emotion |
| **Argument Simulator** | AI generates a realistic argument scenario |

---

### Tryb Eks — Relationship Autopsy

A cinematic scrollytelling experience for analyzing ended relationships.

**16 scenes** from *Intro* to *Epitaph*, each with unique CSS themes, ambient audio, and particle effects.

| Feature | Implementation |
|---|---|
| Navigation | IntersectionObserver with per-scene CSS themes |
| Particles | Canvas2D noise-based drift (embers, ash, dust) |
| Audio | Web Audio API — 9 mood groups with crossfade |
| Export | 6-page crimson A4 PDF ("Akt Zgonu") |
| Sharing | 11 card types + anonymized links (LZ compression) |
| Safety | Entry gate, emergency exit, crisis hotline (116 123) |
| Revisit | Archives previous result, shows delta on re-run |

3-phase AI pipeline: Recon (temp 0.3) → Deep Autopsy (temp 0.4) → Verdict (temp 0.6)

---

### Multi-Relationship Comparison Hub

Compare yourself across N relationships in a 9-tab system:

**Dynamika** (AI trait sliders) · **Statystyki** (80+ metrics) · **Wariancje** (self-trait variance) · **Odkrycia** (auto-generated insights) · **Ranking** (sortable table) · **Radar** (overlay charts) · **Profil** (aggregate profile) · **Zdrowie** (health dashboard) · **Trendy** (temporal overlays)

Auto-detects common user across analyses.

---

### Discord Bot (15 Commands)

HTTP interactions bot with Ed25519 verification and in-memory LRU cache.

| Command | Type | Description |
|---|---|---|
| `/stats` `/versus` `/whosimps` `/ghostcheck` | Instant | Channel analytics |
| `/besttime` `/catchphrase` `/emoji` `/nightowl` | Instant | User behavior |
| `/ranking` `/search` `/analyze` | Instant | Rankings & search |
| `/roast` `/megaroast` `/personality` `/przegryw` | AI | AI-powered analysis |

AI commands use **Drama Keyword Search** — scanning full channel history for the most dramatic moments.

---

### Share Cards (30+ Types)

Exportable PNG cards for social media, including:

**Analysis:** Stats, Personality, Personality Passport, Receipt, Versus, Compatibility, Red Flag, Ghost Forecast, Health Score, MBTI, Badges, Flags, Scores

**Modules:** Subtext, Mugshot, Dating Profile, Delusion, Simulator

**Tryb Eks:** Nekrolog, Akt Zgonu, Paragon Czasu, Autopsy, Forecast, Decay Phases, Tombstone, Golden Age, Unsaid, Death Certificate, Death Line

---

### Story Mode (Wrapped)

12-scene animated presentation in Spotify Wrapped style. Auto-play with Framer Motion transitions.

---

### Server View (5+ Participants)

Automatically activates for group chats: Person Navigator (20-color palette), Server Leaderboard, Pairwise 1v1 Comparison, Server Overview dashboard.

---

## Architecture

```
Client (Browser)                          Server (Next.js API Routes)
┌─────────────────────────┐               ┌──────────────────────────┐
│  Upload & Parse          │               │  /api/analyze (SSE)      │
│  ├─ Auto-detect platform │               │  ├─ Phase 1: Recon       │
│  ├─ Normalize to unified │               │  ├─ Phase 2: Deep Recon  │
│  │  ParsedConversation   │               │  └─ Phase 3: Pass 1-4    │
│  │                       │               │                          │
│  Quantitative Engine     │  sampled msgs │  12 AI Module Endpoints  │
│  ├─ 150+ metrics         │──────────────>│  ├─ Roast, Stand-Up, CPS │
│  ├─ Sentiment (PL+EN)    │               │  ├─ Court, Dating, Eks   │
│  ├─ LSM, Chronotype      │    SSE stream │  └─ Simulator, Subtext   │
│  └─ Gottman, Bid-Response│<──────────────│                          │
│                       │               │  Gemini 3 Flash Preview  │
│  Visualization           │               │  ├─ Structured JSON out   │
│  ├─ Recharts + custom SVG│               │  └─ Evidence-based citing │
│  ├─ 30+ Share Cards      │               └──────────────────────────┘
│  ├─ PDF Export (jsPDF)   │
│  └─ Story Mode (Framer)  │
│                          │
│  Storage                 │
│  ├─ IndexedDB            │
│  └─ localStorage         │
└─────────────────────────┘
```

**Privacy:** Raw messages are processed client-side and never uploaded. Only 200-500 sampled messages are sent to Gemini per AI pass. All data stored locally.

---

## Supported Platforms

| Platform | Format | Import |
|---|---|---|
| Facebook Messenger | JSON export | File upload |
| WhatsApp | TXT export | File upload |
| Instagram DM | JSON export | File upload |
| Telegram | JSON export | File upload |
| Discord | API | Bot integration |

Auto-detection identifies the platform from file structure.

---

## Scientific Foundation

All quantitative metrics audited against published research:

| Metric | Reference |
|---|---|
| MTLD | McCarthy & Jarvis (2010) *Behavior Research Methods* |
| Language Style Matching | Ireland & Pennebaker (2010) *JPSP* |
| Pronoun Analysis | Karan, Rosenthal & Robbins (2019) — meta-analysis |
| Sentiment (AFINN-165) | Nielsen (2011) *arXiv:1103.2903* |
| Behavioral Chronotype | Roy et al. (2021) *Scientific Reports* |
| Bid-Response Ratio | Driver & Gottman (2004) *Family Process* |
| Conversational Repair | Schegloff, Jefferson & Sacks (1977) *Language* |
| Pursuit-Withdrawal | Christensen & Heavey (1990) *JPSP* |
| Investment Asymmetry | Stanley et al. (2017) *PMC* |
| Capitalization (ACR) | Gable et al. (2004) |
| Moral Foundations | Haidt & Graham (2007), Rathje et al. (2024) *PNAS* |

Methodology documentation: 57 algorithms documented at [podtekst.app/metodologia](https://podtekst.app/metodologia)

---

## Tech Stack

| Layer | Technology |
|---|---|
| Framework | Next.js 16+ (App Router), React 19 |
| Language | TypeScript 5 (strict mode) |
| Styling | Tailwind CSS v4 |
| AI | Gemini 3 Flash Preview |
| Development AI | Claude Opus 4.6 |
| Streaming | Server-Sent Events (SSE) |
| 3D | Spline |
| Animations | Framer Motion, CSS keyframes, Canvas2D particles |
| Charts | Recharts, custom SVG/Canvas |
| Export | jsPDF, html-to-image |
| Storage | IndexedDB, localStorage |
| Bot | Discord HTTP Interactions (Ed25519) |
| Auth | Supabase Auth (prepared) |
| Deployment | Google Cloud Run (Docker) |
| Package Manager | pnpm |

---

## Project Scale

| Metric | Count |
|---|---|
| Quantitative metrics | 150+ |
| AI analysis passes | 4 (+ 3-phase recon) |
| Interactive AI modules | 12 |
| Share card types | 30+ |
| Discord bot commands | 15 |
| Tryb Eks scenes | 16 |
| Comparison Hub tabs | 9 |
| Documented algorithms | 57 |
| Supported platforms | 5 |
| Achievement badges | 15 |

---

<p align="center">
  <a href="https://podtekst.app"><b>podtekst.app</b></a> — upload your chat export and see the magic.
  <br/>
  No registration needed. Your messages stay on your device.
</p>

<p align="center">
  <sub>Built with Claude Opus 4.6 + Human collaboration</sub>
</p>
