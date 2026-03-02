# Byte Wave

**AI-powered physics learning platform.** Ask any physics question → get a Manim animation, an interactive Matter.js simulation, AI feedback, and a structured skill map.

## Project layout

```
├── frontend/        React + Vite app (main UI)
├── backend/         FastAPI server — LLM pipeline, Manim renderer, RAG
│   └── rag/         ChromaDB knowledge base for physics accuracy
├── media_output/    Auto-generated Manim videos (created at runtime)
│   ├── clips/       Pre-rendered clip library
│   └── media/       Manim render cache (SVG, video frames)
├── .env             Environment variables (copy from .env.example)
└── run.sh           One-command startup script
```

## Quick start

### 1. Environment

```bash
cp .env.example .env
# Edit .env and add your DEEPSEEK_API_KEY
```

### 2. Backend dependencies

```bash
pip install -r backend/requirements.txt
```

For Manim video rendering (optional but recommended):

```bash
# macOS
brew install cairo pkg-config ffmpeg
pip install -r backend/requirements-manim.txt

# Linux (Ubuntu/Debian)
sudo apt install libcairo2-dev pkg-config ffmpeg
pip install -r backend/requirements-manim.txt
```

### 3. Frontend dependencies

```bash
cd frontend && npm install
```

### 4. Run everything

```bash
./run.sh
```

- **Frontend** → http://localhost:5173
- **Backend API** → http://localhost:8000

Or start them separately:

```bash
# Terminal 1 — API server
python -m uvicorn backend.main:app --reload --port 8000

# Terminal 2 — Frontend dev server
cd frontend && npm run dev
```

## Key features

| Feature | Stack |
|---|---|
| AI Physics Chat + Manim animations | DeepSeek V3 → Manim |
| Interactive physics simulations | Matter.js |
| Physics accuracy layer | RAG (ChromaDB) |
| Skill map + spaced repetition | React + SM-2 algorithm |
| Community forum | FastAPI in-memory store |
| Auth + onboarding | localStorage (Supabase-ready) |
| Analytics | PostHog |
