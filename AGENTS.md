# AGENTS.md

## Project Overview

This is a single-file static HTML web app: `mesibathaor3 (1).html` — a Hebrew RTL interactive game ("מסיבת האור של נועה" / "Noa's Light Party"). All CSS and JavaScript are inline; there is no build step, no backend, and no external API dependencies (only an optional Google Fonts import).

## Running the App

The app is served by nginx via `docker-compose.base44.yml`:

```
docker compose -f docker-compose.base44.yml up -d
```

- The web entry point is on **host port 3000**.
- nginx serves the HTML file directly from the bind-mounted repo (read-only).
- The repo directory has restrictive permissions (700), so nginx runs as `root` (configured in `nginx.base44.conf`).
- No secrets or environment variables are required.

## Editing

Edits to the HTML file are immediately served on browser refresh (static file, no build). Use `reload_preview` after edits to force the preview iframe to refresh.

## Verification

- `curl -s -o /dev/null -w "%{http_code}" http://localhost:3000/` should return `200`.
- The page title should be `מסיבת האור של נועה`.
