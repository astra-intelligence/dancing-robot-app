# Beep Boop Disco Bot

A hilarious animated SVG dancing robot with CSS keyframe dances.

## Run it

Three ways to serve the project, plus the GitHub Pages deployment.

### 1. Dev server (Vite)

```bash
npm install
npm run dev
```

Vite dev server with HMR on **port 3000** (`--host`, so it's reachable from other devices on your LAN).

### 2. Build + SSR server (production)

```bash
npm install
npm run build     # type-check + emit dist/ (server.mjs imports ./dist/server/server.js)
node server.mjs   # or: npm start
```

Serves the built app from `dist/` (static hits are short-circuited, everything else goes through the TanStack Start handler). Listens on **port 3000** by default; override with `PORT` and `HOST` (default `0.0.0.0`):

```bash
PORT=8080 HOST=127.0.0.1 node server.mjs
```

### 3. No-JS static fallback (zero-dependency)

No build, no dependencies at all — just open a file in a browser:

- `index.html` — the full standalone demo (vanilla JS, same dance modes)
- `public/demo.html` — the same page with **no React** at all, served as the fallback when the app's assets fail to load

Both carry the full Open Graph / Twitter card meta block, so either one previews with the 1200×630 `og-image.png` when shared in chat.

### Deploy (GitHub Pages)

The repo deploys to a project page:

```
https://billyx86.github.io/dancing-robot-app/
```

(The absolute URLs in the `og:`/`twitter:` meta tags point at this same base path.)

## Features

- Full SVG robot: googly eyes, wobbling antenna, LED panel, dancing limbs
- Four modes: Groove, Robot, Breakdance, Panic
- **Dance mode is remembered** — the last chosen mode persists across reloads via `localStorage` (falls back to Groove for missing/corrupt values)
- Cycling funny captions
- Disco floor, music notes, sparkles
- `prefers-reduced-motion` freezes to a static pose
- Dark playful aesthetic with electric lime accent
- Social meta (Open Graph + Twitter card) and a 1200×630 `og-image.png` for chat link previews
- Branded `404` page and an SVG/favicon icon
- `scripts/check-modes.mjs` CI guard keeps the React app's `MODES` list and the vanilla fallback's `modes` array in sync, and asserts both `index.html` and `public/demo.html` carry the full Open Graph block

Live standalone page: open `index.html`.
