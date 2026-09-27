# 💬 OpenChat

OpenChat is a full-stack AI orchestration project designed to provide a seamless interface between local AI models and powerful cloud LLMs. 

## 🚀 Project Overview

This repository serves as the primary hub for the OpenChat ecosystem, featuring a high-performance chat application that prioritizes local execution while maintaining cloud-grade reliability.

### Core Stack
- **Frontend:** Next.js 16, React 19, Tailwind CSS 4, shadcn/ui
- **Backend:** FastAPI (Python 3.13), `uv` for package management
- **AI Integration:** Ollama (Local) + Anthropic/OpenAI/Gemini/Grok (Cloud)

## 📂 Repository Structure

```text
openchat/
├── ai-assistant/     # The full-stack AI application (API + Web)
│   ├── api/          # FastAPI backend
│   └── web/          # Next.js frontend
├── AGENTS.md         # Project rules and development guidelines
└── README.md         # Project entry point
```

## 🛠️ Quick Start

To get the main AI assistant running:

1. **Clone and Enter the Assistant Directory:**
   ```bash
   cd ai-assistant
   ```

2. **Start the Backend:**
   ```bash
   cd api
   uv sync
   uv run fastapi dev app/main.py
   ```

3. **Start the Frontend:**
   ```bash
   cd ../web
   npm install
   npm run dev
   ```

4. **Access the App:**
   Open [http://localhost:3000](http://localhost:3000) in your browser.

## ⚙️ Development Guidelines

This project follows strict development rules to ensure maintainability and quality:
- **Small Changes:** Prefer incremental, understandable updates over complex architecture.
- **Testing First:** Run `pytest` after every backend change.
- **AI Distinction:** Clearly distinguish between Local (Ollama) and Cloud (API-based) AI features.
- **Linting:** All Python code must pass `ruff` checks.

For detailed development rules, refer to the `AGENTS.md` file.

## 🤖 AI Capabilities

OpenChat implements a "Local-First" AI strategy:
- **Local Priority:** If an Ollama model is available, the app uses it first to ensure privacy and zero cost.
- **Cloud Fallback:** If local models are missing or fail, the system automatically falls back to the highest priority cloud provider (configured in `.env`).
- **Live Probing:** The system probes available models in real-time, meaning new models added to Ollama or Cloud providers appear automatically without restarts.

---
*Developed with Claude Code.*
