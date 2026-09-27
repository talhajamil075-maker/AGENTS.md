# 🤖 AI Assistant - Full Stack AI Application

A high-performance, production-ready AI chat application. This project integrates **Local AI** (via Ollama) and **Cloud AI** (via Anthropic, OpenAI, Gemini, Grok, Llama) into a seamless full-stack experience.

## 🚀 Project Architecture

The application is split into two main components:

- **Backend (`/api`):** Built with **FastAPI (Python 3.13)**. It manages AI providers, handles streaming responses via SSE (Server-Sent Events), and implements a smart fallback system.
- **Frontend (`/web`):** Built with **Next.js 16**, **React 19**, and **Tailwind CSS 4**. It provides a modern, responsive chat interface using **shadcn/ui**.

```text
ai-assistant/
├── api/   # FastAPI · Python 3.13 · uv · ruff · pytest
├── web/   # Next.js 16 · React 19 · TypeScript 7 · Tailwind CSS 4
└── README.md
```

## 🛠️ Getting Started

### Prerequisites
- **Python 3.13** with [uv](https://docs.astral.sh/uv/)
- **Node.js 24+**
- **Ollama** (Optional, for local AI)

### Installation & Setup

#### 1. Local AI (Optional)
Pull a model to use it locally:
```bash
ollama pull llama3.2
```

#### 2. Backend Setup
```bash
cd api
uv sync
cp .env.example .env  # Add your cloud API keys here (OpenAI, Anthropic, etc.)
uv run fastapi dev app/main.py
```
The API will be available at `http://localhost:8000`. You can view the interactive docs at `http://localhost:8000/docs`.

#### 3. Frontend Setup
```bash
cd web
npm install
cp .env.example .env.local
npm run dev
```
The web interface will be available at `http://localhost:3000`.

---

## 🧠 AI Model Logic & Fallbacks

The application features a sophisticated model management system:

### Model Selection
- **Auto (Default):** Tries the first available Ollama model. If none exist, it falls back to cloud providers based on the `CLOUD_PRIORITY` setting.
- **Local · Ollama:** Direct selection of any model currently pulled into your Ollama instance.
- **Cloud Providers:** Live lists of models from providers whose API keys are configured in `.env`.

### Smart Fallback
If a chosen model fails (e.g., Ollama is offline, or a cloud key is out of quota), the system automatically attempts the next best candidate in the priority list. The user is notified via a small notice in the UI about which model actually processed the request.

## 🧪 Quality Assurance

To ensure the project remains stable, use the following quality gates:

**Backend:**
```bash
cd api
uv run ruff check .           # Linting
uv run ruff format --check .  # Formatting
uv run pytest                 # Run 20+ tests
```

**Frontend:**
```bash
cd web
npm run typecheck             # TypeScript verification
npm run build                 # Production build check
```

## 🚢 Production Readiness

Before deploying to a live environment:
1. **Security:** Set `ENVIRONMENT=production` in `.env` to hide the `/docs` endpoint.
2. **CORS:** Configure `CORS_ORIGINS` to only allow your trusted domain.
3. **HTTPS:** Use a reverse proxy (like Nginx or Caddy) to provide SSL. Ensure response buffering is disabled for `/api/chat` to maintain streaming.
4. **Auth:** The current version stores chat history in the browser's local storage. Implement a database and authentication for persistent user accounts.
