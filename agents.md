# AGENTS.md

## Project Architecture

This is a minimal static site deployment — no framework, no build step.

### Key Files

- `index.html` — the entire application; a self-contained HTML file containing the IGCSE Maths 0607 question bank UI, styles, and logic
- `images/` — question and mark-scheme PNGs, referenced from the app's Google Sheet data source via relative `/images/<QuestionID>_q.png` / `_ms.png` paths
- No `netlify.toml`-style build config is required by Cloudflare Pages beyond an empty build command and `/` as the output directory

### Conventions

- All code lives in `index.html`. There is no separate JS or CSS file.
- No build pipeline. Cloudflare Pages serves the static files directly.
- To add questions or modify the UI, edit `index.html` directly.
- Question/mark-scheme image URLs live in the published Google Sheet (the app's data source), not in this repo — this repo only hosts the image files themselves.

### Non-obvious Decisions

- Images were migrated here from ImgBB (2026) because ImgBB's free tier had a cold-cache penalty causing 15-20s+ load times on rarely-viewed images. Cloudflare Pages serves static assets with no bandwidth billing at all.
