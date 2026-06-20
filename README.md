# 🤖 Persona AI / Lumi

**A private, self-hosted personal AI assistant that runs on your own hardware.**
Memory, voice, RAG, and tool-calling — with no user data leaving your machines.

This is the **project hub**. Persona AI spans four repositories:

| Repo | Role | Stack |
|------|------|-------|
| 🧠 **[persona-ai](https://github.com/ZarbieK-9/persona-ai)** | Backend — server + GPU laptop | Python, FastAPI, PostgreSQL + pgvector, Redis, Ollama |
| 🌐 **[persona-ai-web](https://github.com/ZarbieK-9/persona-ai-web)** | Web client (chat) | Vite, React, TypeScript |
| 📱 **[persona-ai-android](https://github.com/ZarbieK-9/persona-ai-android)** | Native Android client | Kotlin (chat, voice, on-device wake-word) |
| ✨ **[persona-ai-marketing](https://github.com/ZarbieK-9/persona-ai-marketing)** | Marketing site | Astro, React, Framer Motion, GSAP → Cloudflare Pages |

## Architecture

```
   🌐 web   📱 android        ✨ marketing site (Cloudflare Pages)
      │         │
      └────┬────┘  HTTPS over a private tunnel
           ▼
   ┌─────────────────────────────────────────────┐
   │  SERVER (always-on)                          │
   │  FastAPI · Postgres + pgvector (RAG) · Redis  │
   │  memory · files · audit log · tool-calling    │
   └───────────────────┬─────────────────────────┘
                       │  Tailnet
                       ▼
   ┌─────────────────────────────────────────────┐
   │  LAPTOP (on-demand GPU)                       │
   │  Ollama — Qwen 2.5 / 2.5-VL / nomic-embed     │
   │  + agent orchestrator                         │
   └─────────────────────────────────────────────┘
```

## Highlights

- **AI integration**: OpenAI / Anthropic APIs **and** self-hosted models via **Ollama**.
- **RAG** over PostgreSQL + **pgvector**; **tool-calling / agent orchestration**.
- **Privacy-first**: user-visible, deletable memory; nothing leaves your hardware by default.

Grouped under the **[`persona-ai`](https://github.com/ZarbieK-9?tab=repositories&q=topic%3Apersona-ai)** topic.
Live marketing site: **[lumi-marketing.pages.dev](https://lumi-marketing.pages.dev)**.

---
*Built by [Bishwas Khanal](https://bishwaskhanal.com.np).*
