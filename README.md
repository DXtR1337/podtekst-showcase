<p align="center">
  <img src="podtekst_logo.svg" alt="PodTeksT" width="380" />
</p>

<p align="center">
  <b>odkryj to, co kryje się między wierszami</b><br/>
  <sub>discover what hides between the lines</sub>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Next.js-16+-black?style=for-the-badge&logo=next.js" />
  <img src="https://img.shields.io/badge/TypeScript-5_strict-blue?style=for-the-badge&logo=typescript" />
  <img src="https://img.shields.io/badge/React-19-61DAFB?style=for-the-badge&logo=react" />
  <img src="https://img.shields.io/badge/Tailwind-v4-06B6D4?style=for-the-badge&logo=tailwindcss" />
  <img src="https://img.shields.io/badge/Gemini_AI-3_Flash-8E75B2?style=for-the-badge&logo=google" />
  <img src="https://img.shields.io/badge/Discord_Bot-20_cmds-5865F2?style=for-the-badge&logo=discord" />
</p>

<p align="center">
  <a href="https://podtekst.app"><img src="https://img.shields.io/badge/Live_App-podtekst.app-10b981?style=for-the-badge" /></a>
</p>

---

> **This is a public showcase** of the PodTeksT codebase. AI prompt engineering, proprietary scoring formulas, server-side API routes, and deployment infrastructure have been intentionally excluded. See [NOTICE.md](NOTICE.md) for details.

---

## What is PodTeksT?

PodTeksT is a local-first AI-powered conversation analyzer that reveals the psychology behind your chats. Upload a chat export from **Messenger, WhatsApp, Instagram, Telegram, or Discord** and get:

- **48+ quantitative metric modules** computed entirely client-side (your messages never leave your device)
- **6-phase AI psychological analysis** powered by Gemini API with intelligent sampling pipeline
- **17+ interactive AI modules** — from personality profiling to comedy roasts to courtroom trials
- **62 shareable cards** for social media
- **79 psychometric tests** with adaptive item selection
- **Semantic search** with morphological NLP (BM25 + cosine + MMR + PoliMorf lemmatization)
- **Discord bot** with 20 slash commands for server analytics
- **Full GDPR pseudonymization** — 7-case Polish declension, real names never leave browser

The name is a Polish wordplay: *pod-tekst* = subtext, *eks* = ex (former partner), *między wierszami* = between the lines.

---

## Project Scale

| Metric | Count |
|---|---|
| Source files | ~2,017 |
| Lines of code | ~477,000 |
| React components | ~891 |
| Pages | 103 |
| API routes | 52 (29 SSE) |
| React hooks | 39 |
| Test files | 192 (3,752 cases) |
| Quant modules | 48+ |
| AI analysis phases | 6 (+ verification + reranking) |
| Interactive AI modules | 17+ |
| Share card files | 62 |
| Psychometric tests | 79 |
| Discord bot commands | 20 |
| Documented algorithms | 77 |
| Supported platforms | 5 |

Built solo in ~45 days using **Claude Opus 4.6** as development AI.

---

## Key Features

### Quantitative Engine (48+ Modules, O(n), No AI)

Single-pass O(n) engine over all messages. Target: <200ms for 50,000 messages. All computed client-side using published academic methodology.

| Category | Highlights |
|---|---|
| **Per-Person Stats** | Messages, words, emoji (Intl.Segmenter, ZWJ-aware), reactions (4-tier matching), catchphrases, media breakdown |
| **Timing** | Burst-aware response times, initiations, double-text rate, enter-as-comma detection (2min threshold) |
| **Engagement** | Weighted engagement score, consistency, 7x24 heatmap (ISO 8601), monthly trends, year milestones |
| **Sentiment** | 12-phase engine, 7 dictionaries (~4,800 pos / ~8,400 neg), QWERTY typo tolerance (Damerau 1964), Polish inflection fallback |
| **Linguistics** | MTLD (McCarthy & Jarvis 2010), LSM (Ireland & Pennebaker 2010), pronoun analysis with Polish declension, CNI (Derber 1979), integrative complexity (Suedfeld & Tetlock 1977) |
| **Dynamics** | Conflict detection, intimacy progression, pursuit-withdrawal cycles (Christensen & Heavey 1990), reciprocity index |
| **Chronobiology** | Behavioral chronotype (Roy et al. 2021), compatibility score, social jet lag |
| **Survival Analysis** | Discrete hazard model (Allison 1982), Kaplan-Meier estimator for response time modeling |
| **Change-Point** | PELT algorithm for detecting sentiment regime shifts |
| **Gottman** | Four Horsemen mapping, bid-response ratio (Driver & Gottman 2004), repair patterns (Schegloff et al. 1977) |
| **Moral** | Moral Foundations (Haidt & Graham 2007), 6 foundations with radar visualization |
| **Scores** | Compatibility, Interest, Ghost Risk, Investment Asymmetry (Stanley et al. 2017), Delusion Index |
| **Dialog Acts** | Classification (Derber CNI) feeding into bid-response and repair analysis |
| **Badges** | 12+ achievement badges (Night Owl, Chatterbox, Double-Texter, etc.) |

<details>
<summary>Sentiment Engine — 12 Phases, 7 Dictionaries (click to expand)</summary>

**7-Layer Dictionary Stack:**
| # | Source | License | Positive | Negative |
|---|--------|---------|----------|----------|
| 1 | Manual curated | — | 271 | 304 |
| 2 | plWordNet-emo (Zasko-Zielinska et al. 2015) | CC-BY 4.0 | 195 | 182 |
| 3 | NAWL (Riegel et al. 2015, PLoS ONE) | CC-BY 4.0 | 480 | 139 |
| 4 | PL Extended (manual, validated) | — | 106 | 150 |
| 5 | sentiment-polish (AFINN-165 -> PL, Wolanin) | MIT | 1,349 | 2,437 |
| 6 | NAWL_PL extended | CC-BY 4.0 | 498 | 503 |
| 7 | plWordNet 3.0 (Maziarz et al. 2012, 2016) | — | 1,949 | 4,707 |

**5-Tier Token Resolution:** Neutral override -> exact match -> chat emphasis dedup -> QWERTY typo tolerance (Damerau 1964, LRU cache) -> Polish inflection fallback (morphology)

**Special Handling:** XD classification (3 pragmatic variants per Kapuscinska 2020), profanity as filler detection, negation (PL+EN), laughter resistance, somatic negatives, weighted scoring (-3 to +3)

**Benchmark Result (Study 2, N=34, blind):**
| # | Model | MAE | Bias | r | Acc |
|---|-------|-----|------|---|-----|
| 1 | Opus 4.6 | 0.75 | +0.22 | 0.831 | 79.4% |
| 2 | **Engine V20** | **0.92** | **0.00** | **0.671** | **76.5%** |
| 3 | XLM-R | 1.41 | -1.11 | 0.568 | 35.3% |
| 4 | Twitter-PL | 1.44 | -0.96 | 0.511 | 41.2% |
| 5 | HerBERT | 2.14 | -1.96 | 0.458 | 32.4% |
| 6 | nlptown | 2.25 | -1.98 | 0.324 | 32.4% |
| 7 | GPT2-PL | 2.38 | -2.18 | 0.374 | 44.1% |
| 8 | BERT-Politics | 3.24 | -3.13 | 0.278 | 29.4% |

Rule-based Engine V20 beats all 6 transformer models on informal Polish chat. Key finding: systematic negative bias in all ML models (-0.71 to -3.16) due to domain gap (reviews/tweets vs. chat). Fine-tuned HerBERT also tested (3 iterations) — still loses to rule-based engine on this domain.
</details>

---

### AI Analysis (6-Phase Pipeline)

Intelligent sampling pipeline with Gemini 3 Flash Preview. ~950-1,550 messages sampled total across all phases (from conversations of 100k+ messages).

| Phase | Focus | Details |
|---|---|---|
| **Pass 0: Recon** | Scout | Stratified sample -> AI identifies critical moments, flagged date ranges (max 8) |
| **Pass 0.5: Deep Recon** | Verify | Hypothesis verification, structural analysis, narrative refinement |
| **Pass 1: Overview** | Foundation | Relationship type, tone per person, overall dynamic |
| **Pass 2: Dynamics** | Deep dive | Power balance, emotional labor, conflict patterns, intimacy, red/green flags |
| **Post-2: Verification** | Fact-check | Red flag verification (sarcasm/irony detection), message reranking (30 most revealing) |
| **Pass 3A+3B: Profiles** | Per-person | Big Five, Attachment, MBTI, Love Languages, Communication, Emotional Patterns, EI (parallel) |
| **Pass 4: Synthesis** | Integration | Health Score, predictions, final synthesis |
| **Post-4: Sense Check** | Validation | Cross-pass consistency verification |

**Evidence tagging:** Every AI claim tagged as [DQ] direct quote, [BP] behavioral pattern, [SR] statistical reference, [AC] accusation, [IN] inference.

**Anti-hallucination:** Cultural preamble (Polish pragmatics), source criticism requirements, confidence calibration.

---

### Privacy & Pseudonymization (GDPR)

Full client-side pseudonymization before ANY data leaves the browser:

- Real names replaced with fake Polish names from PESEL-validated pool (~400 names)
- **7-case grammatical declension** generated per name (mianownik through wolacz)
- **4-tier matching:** exact -> NFC normalized -> ASCII-folded -> substring (longest first)
- Fuzzy stem matching for declined forms
- PRIV codes for edge cases
- Full reverse mapping applied to AI responses
- Privacy module: 8 files, 541-line core engine

---

### Semantic Search (Web Worker)

Full-text semantic search with morphological NLP, running in a Web Worker for zero main-thread blocking.

| Layer | Technology |
|---|---|
| Sparse retrieval | BM25 (k1=1.5, b=0.75) with PoliMorf lemmatization |
| Dense retrieval | Gemini embedding-2-preview (768d Matryoshka from 3072d) |
| Hybrid fusion | RRF (Reciprocal Rank Fusion, k=60) |
| Diversity | MMR (Lambda=0.3, trigram Jaccard, pool=topK x 3) |
| Fuzzy matching | Levenshtein distance <= 1-2, Polish diacritics/phonetic awareness, prefix index |
| Morphology | PoliMorf (BSD-2-Clause, CLARIN-PL) + 247-entry seed dictionary |
| Query expansion | Gemini-powered synonym + slang expansion (premium) |
| Reranking | Gemini cross-encoder scoring 1-10 (premium) |
| Temporal | Polish temporal expression parser ("rok temu", "latem 2023") |

---

### Interactive AI Modules (17+)

| Module | What it does |
|---|---|
| **Enhanced Roast** | Psychological roast with full analysis context |
| **Mega Roast** | Multi-round brutal roast |
| **Stand-Up Comedy** | 7-act comedy show about your chat (PDF export) |
| **CPS Screener** | Communication Pattern Screening |
| **Subtext Decoder** | What did they *really* mean? (message-by-message) |
| **Court Trial** | AI courtroom — charges, prosecution, defense, verdict + mugshots |
| **Dating Profile** | Honest dating profile based on texting behavior |
| **Reply Simulator** | Type a message, get a response in your partner's voice |
| **Delusion Quiz** | Self-awareness test (Delusion Index 0-100) |
| **Capitalization** | Active-Constructive Responding (Gable et al. 2004) |
| **Moral Foundations** | Haidt's 6 foundations — radar chart + conflict analysis |
| **Emotion Causes** | Who triggered what emotion (SemEval-2024 format) |
| **Argument Simulator** | AI generates a realistic argument scenario |
| **Przegryw Tygodnia** | Weekly "loser" entertainment mode |
| **Paragon** | Receipt-style relationship cost breakdown |
| **Credibility Index** | Credibility analysis |
| **AI Deep Dive** | Extended multi-pass deep analysis |

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

3-phase AI pipeline: Recon (temp 0.3) -> Deep Autopsy (temp 0.4) -> Verdict (temp 0.6)

---

### Psychometric Tests (79 Tests + TCTM Platform)

#### Test Catalog (`/testy`)
79 psychometric tests across 8 categories: personality, relationships, emotions, well-being, motivation, communication, Dark Triad, sexuality.

Full quiz engine with Likert scale, progress tracking, result visualization (bars, radar, single score, two-axis). Each test maps to quantitative metrics from conversation analysis via `chatTieIn`.

#### TCTM Psychometric Platform (`/tctm`)
Multi-layer assessment for Theory of Mind:

```
Layer 1: Self-Report     20 Likert-7 items
Layer 2: Adaptive Test   12-15 vignettes from 57-item pool (IRT-based selection)
Layer 3: Delta Report    Per-subscale self-report vs actual performance
Layer 4: AI Narrative    Gemini Flash SSE, 200-400 word Polish report
```

- **Adaptive item selector:** deterministic algorithm based on self-report confidence per subscale
- **Distractor profiling:** MASC error types (DOS/NAD/BK) — identifies literal, over-read, or direction errors
- **Response validity:** acquiescence bias, random responding, social desirability detection
- **Behavioral validation:** cross-reference self-report against actual chat behavior
- **History tracking:** snapshots over time with delta comparison
- Share card: Instagram-format (1080x1350) delta radar

---

### Profil — 8 Themed Worlds

AI-generated psychological profiles organized into 8 themed "worlds" per person:

| World | Theme |
|---|---|
| Osobowosc | Personality |
| Emocje | Emotions |
| Komunikacja | Communication |
| Relacje | Relationships |
| Motywacja | Motivation |
| Dobrostan | Well-being |
| Ciemna Triada | Dark Triad |
| Bliskosc | Intimacy |

Each world features: custom SVG illustration, AI-generated narrative, data-driven metrics, per-partner analysis. Additional pages: Kartografia (overview map), Porownanie (comparison), Szczegoly (details).

---

### Share Cards (62 Files)

Exportable PNG cards for social media via html2canvas-pro:

**Personality:** AttachmentStyle, BigFive, EQ, Label, LoveLanguage, MBTI, Personality, PersonalityPassport

**Relationship:** Compatibility, Delusion, EmotionalBank, EmotionalLabor, Flags, FrictionMap, Gaps, PowerDynamics, Pronoun, PursuitWithdrawal, RedFlag

**Entertainment:** CourtVerdict, DatingProfile, MegaRoast, Mugshot, PrzegrywTygodnia, RoastVerdict

**Health/Scores:** HealthScore, Credibility, Scores, ResponseTime

**Viral:** AktZgonu, Autopsy, Badges, Chronotype, CoupleQuiz, DeathCertificate, DeathLine, DecayPhases, Forecast, GhostForecast, GoldenAge, KeyFindings, MoralFoundations, Nekrolog, ParagonCzasu, ParagonReceipt, Predictions, Receipt, CPS

Share URLs use lz-string compression for compact payloads. Web Share API integration.

---

### Multi-Relationship Comparison Hub

Compare yourself across N relationships in a 9-tab system:

**Dynamika** (AI trait sliders) · **Statystyki** (80+ metrics) · **Wariancje** (self-trait variance) · **Odkrycia** (auto-generated insights) · **Ranking** (sortable table) · **Radar** (overlay charts) · **Profil** (aggregate profile) · **Zdrowie** (health dashboard) · **Trendy** (temporal overlays)

Auto-detects common user across analyses.

---

### Discord Bot (20 Commands)

HTTP interactions bot with Ed25519 verification and in-memory LRU cache.

| Command | Type | Description |
|---|---|---|
| `/besttime` `/catchphrase` `/emoji` `/nightowl` | Instant | User behavior analysis |
| `/stats` `/versus` `/ghostcheck` `/ranking` | Instant | Channel analytics |
| `/search` | Instant | Semantic search in Discord messages |
| `/roast` `/deeproast` `/megaroast` | AI | Comedy roasts (escalating intensity) |
| `/personality` `/court` `/przegryw` | AI | AI-powered character analysis |
| `/simulate` | AI | Conversation continuation |
| + 4 more | — | Additional commands |

AI commands use **Drama Keyword Search** — scanning channel history for the most dramatic moments.

---

### Story Mode & Wrapped

| Mode | Description |
|---|---|
| **Story Mode** | 11-scene Spotify Wrapped-style animated story (Framer Motion) |
| **Wrapped 3D** | 18-scene cinematic visualization with Spline 3D overlays |
| **Arena** | Fighting game style comparison simulation (32 components) |

---

### AI Benchmark Framework (`/benchmarks`)

Automated quality assessment of AI analysis output:

- **28 lib modules:** runner, metrics, error detectors, field verification, bias analysis, construct validity, sensitivity analysis
- **21 dashboard components** across 12 tabs (overview KPIs, accuracy matrix, bias radar, calibration, consistency)
- Multi-model comparison, prompt version diffing
- Scientific basis: ICC, ECE, hallucination detection
- **Sentiment benchmark:** 8 ML models + rule-based engine + LLM, blind evaluation (N=34)
- MCP integration for external tool access

---

### Export

| Format | Modes |
|---|---|
| PDF (jsPDF) | Standard analysis, Stand-Up Comedy, AI Deep Dive, Enhanced Roast, Mega Roast, Tryb Eks, Argument, Paragon, Przegryw |
| PNG (html2canvas-pro) | 62 share card types |
| Web Share API | Native sharing on supported devices |

---

## Architecture

```
Client (Browser)                              Server (Next.js API Routes)
+-------------------------------+             +--------------------------------+
|  Upload & Parse               |             |  /api/analyze (SSE)            |
|  +- Auto-detect (5 platforms) |             |  +- Pass 0: Recon              |
|  +- Normalize -> Parsed-      |             |  +- Pass 0.5: Deep Recon       |
|     Conversation              |             |  +- Pass 1-4: Analysis         |
|                               |             |  +- Red Flag Verification      |
|  Pseudonymization             |             |  +- Reranking                  |
|  +- 7-case Polish declension  |  pseudonym. |  +- Sense Verification         |
|  +- 4-tier name matching      |  sampled    |                                |
|  +- PRIV codes                |  messages   |  17+ AI Module Endpoints       |
|                               |------------>|  +- Roast, Court, Dating, Eks  |
|  Quantitative Engine (O(n))   |             |  +- Simulator, Subtext, CPS    |
|  +- 48+ metric modules        |  SSE stream |  +- Paragon, Emotions, Moral   |
|  +- 12-phase sentiment        |<------------|                                |
|  +- Survival analysis         |             |  Gemini 3 Flash Preview        |
|  +- PELT change-point         |             |  +- Structured JSON (Zod)      |
|  +- Dialog acts + Gottman     |             |  +- Evidence-based [DQ][BP]    |
|                               |             |  +- Anti-hallucination         |
|  Semantic Search (Web Worker) |             +--------------------------------+
|  +- BM25 + Cosine + MMR      |
|  +- PoliMorf lemmatization    |
|  +- Fuzzy Levenshtein         |
|                               |
|  Visualization                |
|  +- 891 React components      |
|  +- Recharts + custom SVG     |
|  +- 62 Share Cards (PNG)      |
|  +- PDF Export (jsPDF)        |
|  +- Story/Wrapped/Arena       |
|  +- GSAP + Motion + Spline 3D |
|                               |
|  Storage                      |
|  +- IndexedDB v5 (7 stores)  |
|  +- localStorage              |
+-------------------------------+
```

**Privacy:** Raw messages are processed client-side and never uploaded. Only ~950-1,550 sampled messages (pseudonymized) are sent to Gemini across all passes. All data stored locally in the browser.

---

## Supported Platforms

| Platform | Format | Import |
|---|---|---|
| Facebook Messenger | JSON export | File upload |
| WhatsApp | TXT export | File upload |
| Instagram DM | JSON export | File upload |
| Telegram | JSON export | File upload |
| Discord | API | Bot integration |

Auto-detection identifies the platform from file structure. Facebook UTF-8 mojibake handled (Latin-1 double-encoding).

---

## Scientific Foundation

All quantitative metrics audited against published research:

| Metric | Reference |
|---|---|
| MTLD | McCarthy & Jarvis (2010) *Behavior Research Methods* |
| Language Style Matching | Ireland & Pennebaker (2010) *JPSP* |
| Pronoun Analysis | Karan, Rosenthal & Robbins (2019) — meta-analysis |
| Sentiment (AFINN-165) | Nielsen (2011) *arXiv:1103.2903* |
| Polish Sentiment (plWordNet-emo) | Zasko-Zielinska et al. (2015) |
| Polish Sentiment (NAWL) | Riegel et al. (2015) *PLoS ONE* |
| Behavioral Chronotype | Roy et al. (2021) *Scientific Reports* |
| Bid-Response Ratio | Driver & Gottman (2004) *Family Process* |
| Conversational Repair | Schegloff, Jefferson & Sacks (1977) *Language* |
| Pursuit-Withdrawal | Christensen & Heavey (1990) *JPSP* |
| Investment Asymmetry | Stanley et al. (2017) *PMC* |
| Capitalization (ACR) | Gable et al. (2004) |
| Moral Foundations | Haidt & Graham (2007), Rathje et al. (2024) *PNAS* |
| Survival Analysis | Allison (1982), Kaplan-Meier |
| Change-Point Detection | PELT (Killick et al. 2012) |
| XD Classification | Kapuscinska (2020) — PWN Youth Word 2017 |
| PoliMorf | BSD-2-Clause, CLARIN-PL |
| Conversational Narcissism | Derber (1979) |

**Academic documentation:** 5 LaTeX documents (~90 pages) including validity roadmap, academic overview, and sentiment benchmark paper. Bibliography: 30+ sources.

Methodology documentation: 77 algorithms documented at [podtekst.app/metodologia](https://podtekst.app/metodologia)

---

## Tech Stack

| Layer | Technology |
|---|---|
| Framework | Next.js 16+ (App Router), React 19 |
| Language | TypeScript 5 (strict mode) + tsgo |
| Styling | Tailwind CSS v4 + shadcn/ui (customized) |
| AI Analysis | Gemini 3 Flash Preview |
| Development AI | Claude Opus 4.6 |
| Embeddings | gemini-embedding-2-preview (768d Matryoshka) |
| Streaming | Server-Sent Events (SSE), heartbeat 15s |
| 3D | Spline, GSAP |
| Animations | Motion (Framer Motion), CSS keyframes, Canvas2D particles |
| Charts | Recharts, custom SVG/Canvas |
| Morphological NLP | PoliMorf (CLARIN-PL), 247-entry seed dictionary |
| Export | jsPDF, html2canvas-pro |
| Storage | IndexedDB v5 (7 stores), localStorage |
| Auth | Supabase Auth (conditional) |
| Payments | Stripe (prepared) |
| Bot | Discord HTTP Interactions (Ed25519) |
| Deployment | Google Cloud Run (Docker, europe-west1) |
| Testing | Vitest + Playwright |
| Package Manager | pnpm |

---

<p align="center">
  <a href="https://podtekst.app"><b>podtekst.app</b></a> — upload your chat export and see what hides between the lines.
  <br/>
  No registration needed. Your messages stay on your device.
</p>

<p align="center">
  <sub>Built with Claude Opus 4.6 + Human direction &middot; ~477,000 lines of code &middot; 45 days solo</sub>
</p>
