Got it. I'll use these **OpenChat project rules** going forward:

* **Frontend**: Node 24, Next.js 16, React 19, Tailwind CSS 4, shadcn/ui — port `3000`
* **Backend:** FastAPI, Python 3.13, `uv`, Ruff, pytest — port `8000`
* **Local AI:** Ollama at `localhost:11434`, using `llama3.1b`
* **Cloud AI:** OpenAI or Anthropic
* **Frontend:** `npm install` → `npm run dev`
* **Backend:** `uv sync` → `uv run fastapi dev`
* **Add backend packages:** `uv add <package>`
* **Tests:** `cd backend && pytest`

### Development rules I'll follow

1. **Explain changes simply**, assuming you're a beginner.
2. **Run tests after every change** and tell you whether they passed.
3. **Never commit `.env` files or API keys.**
4. Prefer **small, understandable changes** rather than unnecessarily complex architecture.
5. When debugging, I'll first identify the actual error before suggesting changes.
6. I'll keep the existing stack intact unless there's a good reason to change it.
7. For AI features, I'll distinguish clearly between **Ollama/local AI** and **OpenAI/Anthropic/cloud AI**.