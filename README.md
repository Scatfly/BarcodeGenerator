# CodeForge (PWA)

An installable, offline-capable barcode/QR generator. Pure static files — no build step.

## Files
- `index.html` — the app
- `manifest.webmanifest` — makes it installable (name, icons, colors)
- `sw.js` — service worker (offline caching)
- `icon-180.png`, `icon-192.png`, `icon-512.png` — home-screen icons

All paths are relative (`./`), so it works in a repo subfolder or at the root.

## Deploy to GitHub Pages
1. Put these files in a repo (root, or a folder like `/codeforge`).
2. Commit and push.
3. Repo → **Settings → Pages** → Source: your branch (e.g. `main`), root.
4. Open the published `https://scatfly.github.io/<repo>/` URL.

GitHub Pages serves over HTTPS, which a PWA requires — so install works automatically.

## Install on your phone
- **iPhone (Safari):** open the URL → Share → **Add to Home Screen**.
- **Android (Chrome):** open the URL → menu (⋮) → **Install app** / **Add to Home screen**, or tap the install prompt.

Launch it from the home-screen icon and it runs full-screen with no browser bar. After the first load it works offline.

## Updating the app
When you change `index.html`, bump the cache name in `sw.js`
(`const CACHE = "codeforge-v2"`) so phones fetch the new version instead of the
cached one.

## Local testing
A service worker needs http(s), not `file://`. From this folder:

```
python3 -m http.server 8000
```

then open `http://localhost:8000`.
