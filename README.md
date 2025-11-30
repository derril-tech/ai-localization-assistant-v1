# AI Localization Assistant (CrewAI + DeepL)

**Live app:** `https://ai-localization-assistant.vercel.app/`

**AI-powered localization playground for product and marketing teams.** Paste source copy once, pick locales and tone, and let a CrewAI of Translator, Context Reviewer, and Proofreader agents turn it into high‑quality, on‑brand translations.

---

## ✨ What this app does

### 🎯 Core Localization Flow
- **Multi‑locale runs**: Paste source text (e.g. English) and get translations for multiple target locales in a single run.
- **CrewAI agents**:
  - **Translator** – uses DeepL for accurate baseline translations.
  - **Context Reviewer** – adjusts tone, brand voice, and product context.
  - **Proofreader** – polishes grammar, fluency, and microcopy.
- **Per‑locale cards**: Clean, card‑based layout for each locale with copy‑to‑clipboard.

### 🧠 AI Enhancements
- **Real‑time translation preview** – debounced DeepL preview while typing in `/playground`.
- **Baseline vs. refined comparison** – side‑by‑side diff view that highlights what the crew changed.
- **Batch mode** – run line‑by‑line batch translations with progress and results grid.
- **Quality scores** – 0–100 overall and per‑metric (fluency, accuracy, tone match, cultural fit) using `gpt-4.1-mini`.
- **Agent insights timeline** – see what each agent did at each step of the pipeline.
- **Alternatives per locale** – 2–3 alternative translations per locale, selectable per card.
- **Interactive chat** – ask questions like “Why did you choose this German phrasing?” and get context‑aware answers.

### 🌐 Collaboration & Export
- **Shareable links** – one click to copy a public, read‑only URL for a specific job (`/share/{jobId}`).
- **Export** – download translations as JSON, CSV, PO, or XLIFF directly from the browser.
- **Dashboard** – `/dashboard` shows recent jobs from Supabase with locales, tone, and translation snippets.

### 🎨 UX and Design
- **Modern 2025 UI** – video hero, gradients, and micro‑animations, all theme‑safe.
- **Light / dark mode** – full theme support via CSS variables and `ThemeProvider`.
- **Mobile‑first** – responsive layouts for `/`, `/dashboard`, `/playground`, and `/share/[id]`.
- **Accessible** – labeled controls, focus-visible outlines, and keyboard-friendly nav.

---

## 🏗️ Tech Stack

### Backend (FastAPI, CrewAI, DeepL)
- **FastAPI** (`/api`) – Python 3.11+ backend on Railway.
- **CrewAI** – orchestrates Translator, Context Reviewer, Proofreader agents.
- **LLM** – `gpt-4.1-mini` via `langchain-openai`:
  - Localization crew reasoning.
  - Quality scoring (fluency/accuracy/tone/cultural fit).
  - Translation alternatives.
  - Interactive chat.
- **DeepL API** – baseline translations per locale.
- **Supabase** – Postgres schema `locassistant` for:
  - `profiles`, `projects`, `messages`, `jobs`.
- **Upstash Redis** – job state + rate limiting (key prefix `locassistant`).

### Frontend (Next.js 15, React 19)
- **Next.js 15 (App Router)** – `/web` package.
- **React 19.2** – client/server components.
- **Tailwind CSS** – theme tokens for light/dark.
- **shadcn/ui** – cards, buttons, inputs, etc.
- **lucide-react** – icons.



## Demo

<!-- TODO: Add live demo URL and screenshot -->
- **Live Demo**: [Coming soon]
- **Screenshot**: ![Localization Assistant Playground](./docs/screenshot.png)

## Overview

**Localization Assistant** orchestrates a crew of three specialized AI agents:

- **Translator**: Uses DeepL API to generate accurate baseline translations
- **Context Reviewer**: Adjusts translations for tone, brand voice, and product context
- **Proofreader**: Finalizes translations for grammar, fluency, and microcopy polish

Together, they produce production-ready localized content that maintains brand consistency across multiple languages.

## Features

- 🌍 **Multi-language Translation**: Paste source copy and get localized variants for multiple target locales in one run
- 🎯 **Tone Customization**: Specify tone and high-level guidelines to ensure localized copy stays on-brand
- 🤖 **AI-Powered Review**: See per-locale output plus notes from Translator, Context Reviewer, and Proofreader agents
- 📊 **Job History**: Inspect past localization jobs and re-run specific strings when requirements change
- 💾 **Export Ready**: Final translations available as locale-keyed JSON to plug directly into your frontend
- 🔄 **Real-time Status**: Poll job status and view results as they complete

## Tech Stack

### Frontend
- **Next.js 15** (React 19.2, App Router)
- **TypeScript**
- **Tailwind CSS** + **shadcn/ui** components
- **npm** package manager

### Backend
- **FastAPI** (Python 3.11+)
- **CrewAI** for multi-agent orchestration
- **DeepL API** for baseline translations
- **Supabase** (PostgreSQL) for persistence
- **Upstash Redis** for caching and job state (optional)

### Infrastructure
- **Railway** for deployment
- **Supabase** for database
- **Upstash** for Redis (optional)



## Support

For issues and questions, please open an issue on GitHub.

## Additional Resources

- [Deployment Guide](./DEPLOYMENT.md) - Detailed Railway deployment instructions
- [Architecture Documentation](./ARCH.md) - System architecture details
- [Project Plan](./PLAN.md) - Development milestones

---

Built with ❤️ using CrewAI, DeepL, and Next.js.

