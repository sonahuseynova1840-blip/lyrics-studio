# Implementation Notes

## Language enforcement
- Single source of truth: `SongSettings.language`
- Enforced in **server** only: `server/src/ai/prompt.ts -> buildSystemPrompt(settings)`
- Client only sends `settings` and does not hardcode language rules.

## Lyrics generation
- Endpoint: `POST /api/projects/:id/lyrics/generate`
- Uses OpenAI Chat Completions with JSON schema response format.
- 3 versions (A/B/C) with strict section names.
- Quality gate (heuristic): lexical diversity + cliché blacklist; regenerates once if low.

## Assistant
- Endpoint: `POST /api/projects/:id/messages`
- Uses same system prompt + contextual lyrics (version A) when present.

## Voice / TTS
- Endpoint: `POST /api/projects/:id/audio/generate`
- Generates mp3 via OpenAI TTS, stores under `server/storage/`, served at `/storage/*`.

## Persistence
- SQLite (better-sqlite3) with WAL.
- Tables: `projects`, `messages`, `audio`.

