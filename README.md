# Lyrics Studio (v1)

A production-ready AI songwriting studio (lyrics + AI assistant + voice/TTS) with a professional dark UI, strict language enforcement (RU/AZ/DE/MIX), and project library.

## Monorepo
- `client/` – React + TypeScript + Tailwind
- `server/` – Express + TypeScript + SQLite
- `shared/` – shared types

## Requirements
- Node.js 18+
- An OpenAI API key (server-side only)

## Setup
```bash
cd lyrics-studio
npm install
```

### Configure server env
Create `server/.env`:
```bash
OPENAI_API_KEY=your_key
# optional
OPENAI_MODEL=gpt-4o-mini
OPENAI_TTS_MODEL=gpt-4o-mini-tts
PORT=8787
SQLITE_PATH=./data.sqlite
```

## Run locally
```bash
npm run dev
```
- Client: http://localhost:5173
- Server: http://localhost:8787

## Build
```bash
npm run build
npm run start
```

## Key guarantees
- No API keys in client
- Language enforced inside server `buildSystemPrompt(settings)`
- Assistant uses same language constraints + current lyrics context

