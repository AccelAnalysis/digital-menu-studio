```markdown
# Digital Menu Studio

**A zero-backend, static-web digital menu board platform for restaurants**

Design beautiful, on-brand menu boards in any browser.  
Deploy lightweight, offline-capable players to TVs, tablets, or signage devices — even on completely isolated networks.

No server. No database. No monthly fees. Just files and a CDN (or a USB stick).

```
digital-menu-studio/
├─ editor/          # Full design studio (admin tool)
└─ player/          # Minimal runtime for screens (guest view)
```

## Features

- WYSIWYG drag-and-drop editor with snap-to-grid, image library, themes, and live preview
- Multiple menu groups (Breakfast, Lunch, Happy Hour, Seasonal, etc.)
- Rich tile types: items with prices & badges, hero promos, split layouts, QR codes, video
- One-click export:
  - Single-file `menu-player.html` (truly offline)
  - Folder bundle (`index.html` + `menu.json`)
- Live Remote Editing – direct “Save & Publish” to the same URL the TVs read from
- Undo/Redo + automatic version history (20 snapshots)
- Conflict detection modal (last-write-wins with warning)
- Player is a full Progressive Web App (PWA) – installable on tablets, works offline, auto-refreshes
- Themes: default, fast-casual, fine-dining + easy custom branding
- 100 % static – host on S3, Cloudflare Pages, GitHub Pages, Netlify, or copy from USB

## Quick Start (5 minutes)

```bash
git clone https://github.com/yourorg/digital-menu-studio.git
cd digital-menu-studio
```

### Option A – Open locally (no install needed)
1. Open `editor/index.html` in Chrome/Edge/Firefox  
2. Start designing immediately – everything saves to your browser automatically  
3. Export → “Self-contained Player” → copy the generated file to your signage device

### Option B – Host centrally (recommended for chains)
1. Push the entire repo to any static host (Netlify, Vercel, Cloudflare Pages – free tiers work great)
2. Editor URL: `https://yourdomain.com/editor/`
3. Player URL example: `https://yourdomain.com/player/?config=https://cdn.yourchain.com/locations/main-street/menu.json`

## Live Remote Editing Setup (the “magic” part)

1. Store your `menu.json` on any CDN that supports pre-signed URLs (AWS S3, Cloudflare R2, Google Cloud Storage).
2. HQ generates a pre-signed PUT URL (valid 1–24 hours) and sends it to the manager.
3. In the Editor → Export tab → “Live Remote” panel → paste the URL + token → enable.
4. From now on “Save & Publish” updates the live menu instantly.  
   All Players auto-refresh within 3 minutes (or instantly on reload).

No backend required – just a signed URL.

## Player Deployment Options

| Scenario                  | How to deploy                                                                                  | Update method                     |
|---------------------------|------------------------------------------------------------------------------------------------|------------------------------------|
| Internet-connected TVs    | Point browser to `https://yourdomain.com/player/?config=https://…/menu.json`                  | Auto-refresh (3 min) or manual) |
| Air-gapped / no internet  | Copy exported `menu-player.html` (single file) to USB → open on device                         | Replace file on USB                |
| Tablets / kiosks          | Install as PWA (“Add to Home Screen”) → full-screen, auto-start                               | Auto-refresh when online           |

## Folder Overview

```
editor/              → Design studio (open index.html)
player/              → Runtime for screens
   ├─ manifest.json
   └─ service-worker.js
shared/              → validator.js + version info (used by both apps)
export-kits/         → Generated bundles appear here
docs/                → Guides (live remote, PWA install, conflict handling)
```

## Tech Stack (tiny & modern)

- Vanilla JS + HTML5 + CSS Grid/Flexbox
- Zustand (~3 KB) for state + undo/redo
- idb-keyval (~1 KB) for Player offline cache
- No framework, no build step required (optional Vite config included for dev convenience)

Total size (gzipped):  
Editor ≈ 140 KB | Player ≈ 60 KB → loads instantly even on slow connections.

## Contributing

Pull requests welcome! Please open an issue first for major changes.

## Copyright

© 2025 Accel Analysis, LLC. All rights reserved.

---

Made with ❤️ for restaurants that want beautiful menus without the headache.
```
