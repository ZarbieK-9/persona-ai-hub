# 🤖 Persona AI

**A private, self-hosted personal AI assistant that runs on your own hardware.**
Memory, voice, RAG, and tool-calling — designed so no user data leaves your machines.

> Persona AI is its own project (distinct from [lifeOS](https://github.com/ZarbieK-9/lifeOS),
> my life-management app). It's a real AI assistant: retrieval-augmented generation,
> agent/tool-calling, and a mix of hosted + self-hosted models.

## Repositories

| Repo | Role | Stack | |
|------|------|-------|---|
| ✨ **[persona-ai-marketing](https://github.com/ZarbieK-9/persona-ai-marketing)** | Marketing site → [live](https://lumi-marketing.pages.dev) | Astro, React, Framer Motion, GSAP → Cloudflare Pages | 🌐 public |
| 🌐 **[persona-ai-web](https://github.com/ZarbieK-9/persona-ai-web)** | Web chat client | Vite, React, TypeScript | 🌐 public |
| 🧠 persona-ai | Backend — server + GPU laptop | Python, FastAPI, Postgres + pgvector, Redis, Ollama | 🔒 private |
| 📱 persona-ai-android | Native Android client | Kotlin — chat, voice, on-device wake-word | 🔒 private |

*(The backend and Android client are private; the web client and marketing site are open.)*

## Architecture

```
   🌐 web        ✨ marketing (Cloudflare Pages)
      │
      │  HTTPS over a private tunnel (Tailscale)
      ▼
   ┌─────────────────────────────────────────────┐
   │  SERVER (always-on)                          │
   │  FastAPI · Postgres + pgvector (RAG) · Redis  │
   │  memory · file upload/retrieval · audit log   │
   │  tool-calling / agent orchestration           │
   └───────────────────┬─────────────────────────┘
                       │  Tailnet
                       ▼
   ┌─────────────────────────────────────────────┐
   │  LAPTOP (on-demand GPU)                       │
   │  Ollama — Qwen 2.5 / 2.5-VL / nomic-embed     │
   └─────────────────────────────────────────────┘
```

## Highlights

- **AI integration**: OpenAI / Anthropic APIs **and** self-hosted models via **Ollama**.
- **RAG** over PostgreSQL + **pgvector**; **tool-calling / agent orchestration**.
- **Privacy-first**: user-visible, deletable memory; nothing leaves your hardware by default.

Grouped under the **[`persona-ai`](https://github.com/ZarbieK-9?tab=repositories&q=topic%3Apersona-ai)** topic.

---
*Built by [Bishwas Khanal](https://bishwaskhanal.com.np).*
