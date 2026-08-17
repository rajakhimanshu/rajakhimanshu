<h1 align="center">Himanshu Rajak</h1>
<h3 align="center">AI × FinTech × Systems — real products, real users, real commit history.</h3>

<p align="center">
  <a href="https://github.com/rajakhimanshu"><img src="https://img.shields.io/badge/github-rajakhimanshu-000000?style=for-the-badge&logo=github&logoColor=white" /></a>
  <a href="https://www.himanshurajak.in"><img src="https://img.shields.io/badge/site-himanshurajak.in-000000?style=for-the-badge&logo=vercel&logoColor=white" /></a>
  <a href="https://www.linkedin.com/in/rajakhimanshu/"><img src="https://img.shields.io/badge/linkedin-connect-000000?style=for-the-badge&logo=linkedin&logoColor=white" /></a>
  <a href="https://www.instagram.com/himanshu_rajak22/"><img src="https://img.shields.io/badge/instagram-follow-000000?style=for-the-badge&logo=instagram&logoColor=white" /></a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/3-Live_Products-1a1a1a?style=flat-square" />
  <img src="https://img.shields.io/badge/8%2B-EAs_Built_%26_Tested-1a1a1a?style=flat-square" />
</p>

---

### `whoami`

B.Tech CSE (AI/ML), TIT Bhopal. Here's the ledger, pulled straight from commit history and production logs:

- **Founding engineer, GrowEdge Capital** — a live investment-operations platform supporting portfolio, KYC, payout, and withdrawal workflows. First commit 1 May 2026, still shipping .
- **Founder, Kapsee** — Hinglish AI captioning SaaS, live at `kapsee.in`, building since June 2026. `api.kapsee.in/health` and `www.kapsee.in` both verified 200 OK. 9 test modules, EC2 + Vercel + Caddy in production.
- **8+ Expert Advisors** designed and forward-tested on MT5 accounts across 2025–2026 (Aureon, Rapid Bullet, EA Elite v8.10, HFT prototypes), plus an independent multi-year private indicator (`Dr.D / DX`) ported across MQL5, Pine Script, and Python.
- **Costed, holdout-tested quant research** — not just backtests. My most recent trading code compares strategies net of costs on a 30% holdout set, the kind of rigor that separates a real edge from a curve-fit one.
- **Built Astro.AI** — a Vedic astrology reasoning engine with 40+ backend modules covering ephemeris calculation, dashas, transits, yogas, shadbala, and a RAG pipeline over classical texts.
- **A confidential cross-platform enforcement system** — built on modern .NET, with a single source of truth for session and rule state synchronized live across a Windows desktop core, a browser extension, and a mobile companion. Full architecture below.

I don't chase polish. I chase things that run, get tested, and get used.

---

### Live in production

#### 🏦 GrowEdge Capital — *Live · Founding Engineer*

Full investment-ops platform: KYC (6-stage), portfolios, FIFO withdrawal accounting, automated monthly payouts, referrals, ops/finance consoles. Not a CRUD app — a real financial engine.

- `UnifiedFinancialEngine` replaced **8 duplicate financial engines** after a formal internal audit
- FIFO lot-based withdrawal logic (`withdrawal_engine.py`) with dedicated test coverage
- Signup-abuse honeypot, fake-KYC image rejection, generated-email risk scoring
- JWT + session revocation, staff geo-alerts, rate limiting, bandit/flake8 pre-commit hooks
- 66+ backend pytest modules, Playwright E2E, GitHub Actions CI, 45 Alembic migrations
- **Stack:** React 19 · FastAPI · SQLAlchemy async · PostgreSQL · Celery/Redis · Docker · Railway
- **Live:** [growedgecapital.com](https://www.growedgecapital.com)

#### 🎬 Kapsee — *Live · Founder*

Hinglish caption generation for Indian short-form creators — upload → dual ASR (Groq + Sarvam) → LLM polish → in-browser editor → burned-in export.

- VFR→CFR video normalization pipeline so captions don't drift on Instagram/YouTube exports
- Dual-provider ASR with independent rate limiters for graceful failover
- Device-UUID free-trial abuse capping, login lockout, password policy enforcement, JWT deny-list
- Production-hardened middleware stack: security headers, global rate limiting, body-size limits
- Staff control portal with separately-scoped auth
- **Stack:** Next.js · FastAPI · SQLAlchemy async · PostgreSQL · Celery/Redis · Razorpay · EC2 + Caddy
- **Live:** [kapsee.in](https://kapsee.in)

---

### 🔒 In development — confidential

A full-grade system currently in active build. Product name and exact mechanics stay private, but the architecture is worth showing:

**Cross-platform enforcement system** — one source of truth for session and rule state, synchronized live across a Windows desktop core, a browser extension, and a mobile companion, on modern .NET.

- **Windows desktop core** — WPF (.NET), running with elevated privileges. A C# rule engine evaluates session state continuously, not just at session boundaries. OS integration through Win32 API / P-Invoke.
- **Browser layer** — Chrome/Edge extension on **Manifest V3** (TypeScript), enforcing the same rules at tab/URL level, synced live from the shared state rather than a static local blocklist.
- **Mobile companion** — **.NET MAUI**, sharing the same C# business logic as the desktop core rather than a second, separately-maintained implementation.
- **Data layer** — local **SQLite** per device for low-latency reads, backed by a cloud sync layer (PostgreSQL/Supabase) so desktop, mobile, and browser all agree on current state without depending on any one surface being reachable.
- **Integrations** — Google Calendar API, OAuth-scoped third-party integrations, tokenized payment-provider APIs — no raw credentials stored anywhere.

The hard engineering problem isn't any one surface — it's keeping shared rule logic and session state consistent, in real time, across a native process, a browser extension, and a mobile app.

---

**🌍 EarthRanker**
Calculates statistical rarity of your traits against 8.28B people using real demographic data and a logarithmic scoring model, with server-side AI story generation to keep the API key off the client.
`React` `Firebase` `Groq` `Vercel` — [earthranker.himanshurajak.in](https://earthranker.himanshurajak.in)

**🔮 Astro.AI**
Vedic astrology reasoning engine — 40+ backend modules for ephemeris, dashas, transits, yogas, shadbala, and a RAG pipeline over classical texts (BPHS, Phaladeepika, Brihat Jataka).
`Python` `FastAPI` `Next.js` `RAG` `ChromaDB`

**🔧 FORGE**
Local multi-agent startup validator — idea in, research + feasibility verdict + technical architecture + sprint blueprint out. Kept its own self-audit report scoring its output honestly rather than hiding the gaps.
`LangGraph` `Ollama` `Tavily` `ChromaDB`

**📅 ForexSync**
Forex Factory economic events → Google Calendar + Telegram alerts, with an SSE-driven live ticker and 15-second market refresh.
`React` `FastAPI` `PostgreSQL` `Selenium` — [forex-sync-in-frontend.vercel.app](https://forex-sync-in-frontend.vercel.app/)

**🗓️ Internal utility tools**
Self-built systems for running my own operation — automated task scheduling into Google Calendar, work-tracking utilities, and a Forex-calendar scraper precursor. Built to run my work, not to ship.
`Python` `Google Calendar API` `Automation`

---

### Markets & quant research

Most of my earlier work was broad systems and AI engineering — fintech ops, creator SaaS, agentic pipelines. I'm now deliberately narrowing that into quantitative research and systematic trading, which is why the projects below exist together rather than as scattered side work:

- **8+ Expert Advisors** built and forward-tested on MT5 — Aureon, Rapid Bullet, EA Elite (v8.10, session-filtered, ADX/DX-gated, trailing stops), and HFT prototypes.
- **A private multi-year indicator thesis (`Dr.D / DX`)** — implemented independently in MQL5, Pine Script, and Python, reused across every EA generation rather than rebuilt from scratch each time.
- **Costed, holdout-validated strategy comparison** — my most recent research (`honest_two_strategy_test.py`) benchmarks Rapid Bullet against an ATR-momentum strategy net of trading costs on a 30% holdout split. That's the difference between a backtest and a curve-fit story.
- **A full portable Python port of an MT5 EA** (ATR Momentum v1.11) with its own parameter optimizer — turning MQL5 logic into something testable outside the terminal.
- **Independent EMA200 touch-rejection study** across XAUUSD and 7 major forex pairs on 3 years of M30 data, with session-tagged signal windows and a reproducible YAML-configured pipeline.
- **218+ documented discretionary trades**, including an early account blowup that fundamentally changed how I approach position sizing and risk.

**Current focus:** DSA & problem-solving · probability & statistics · time-series methods · production-grade Python research tooling.

**Target:** quant programmer / quant developer roles at systematic trading firms — off-campus applications as the primary path.

---

### Stack

| Area | Tools |
|---|---|
| **Languages** | Python, TypeScript, JavaScript, MQL5, SQL, C# |
| **Backend** | FastAPI, SQLAlchemy (async), PostgreSQL, Redis, Celery, Alembic |
| **Frontend** | React, Next.js, Tailwind, Vite |
| **AI / ML** | Groq, LangGraph, RAG, ChromaDB, Ollama, faster-whisper |
| **Infra** | AWS/EC2, Cloudflare R2, Vercel, Railway, Docker, Caddy, GitHub Actions |
| **Markets** | MetaTrader 5, MQL5, Selenium, pandas/numpy backtesting, Razorpay |

---

### Selected metrics from commit history and production checks — Aug 2026

| | |
|---|---|
| 🚀 Live products, checked directly | GrowEdge Capital · Kapsee · EarthRanker |
| 🧪 Backend test modules — GrowEdge | 66+ pytest, Playwright E2E, GitHub Actions CI |
| 🧪 Backend test modules — Kapsee | 9 pytest, CI on EC2 deploy |
| 📐 Database migrations — GrowEdge | 45 Alembic versions |
| 🤖 Expert Advisors built & forward-tested | 8+, multi-year |
| 📊 Documented discretionary trades | 218+ |
| 🕯️ Backtest data processed | 3 years, 8 instruments, M30 |
| 📦 Total tracked codebases | 15+ across production, research, and hackathons |

---

<p align="center">
<a href="https://github.com/rajakhimanshu">GitHub</a> ·
<a href="https://www.himanshurajak.in">Portfolio</a> ·
<a href="https://www.linkedin.com/in/rajakhimanshu/">LinkedIn</a> ·
<a href="https://www.instagram.com/himanshu_rajak22/">Instagram</a>
</p>
