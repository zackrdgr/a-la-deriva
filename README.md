# A la Deriva — installable offline web app

This folder is a ready-to-host version of the cruise guide. Host the **whole folder**
(with `index.html` at the root) on any HTTPS static host, then each person installs it.

## Contents
- `index.html` — the guide (self-contained), with manifest + service worker wired in
- `sw.js` — service worker; caches the page so it works with NO internet
- `manifest.webmanifest` — app name, icon, standalone display
- `icon-180/192/512.png` — app icons

## Host it (pick one, all give HTTPS automatically)
- **Netlify Drop** — https://app.netlify.com/drop → drag this folder in. Instant URL.
- **Cloudflare Pages** — create a project → upload this folder.
- **GitHub Pages / Vercel** — also fine.

> Must be **HTTPS**. Service workers (the offline part) do NOT work over plain `http://`
> or from a `file://` double-click. That's why opening the file directly never offered
> "save as a web app."

## Install on iPhone (each person)
1. Open the hosted URL in **Safari** while you still have internet.
2. Let the page finish loading once (this caches it for offline).
3. Share button → **Add to Home Screen** → Add.
4. Launch it from the home-screen icon. It now opens full-screen and works offline.

## Install on Mac
Open the URL in Safari → **File ▸ Add to Dock**.

## IMPORTANT for the ship (no wifi on board)
- Everyone should open the app **once while online shortly before sailing** so the latest
  copy is cached.
- iOS may clear an unused web app's cache after about a week. Opening it within a few days
  of the cruise (and using it on board) keeps it cached, so this isn't an issue for the trip.

## If you change the guide later
Re-copy the updated `Tres Amigos.html` over `index.html` here (keep the manifest/SW
`<link>`/`<script>` lines near the top and bottom — see the originals), bump `aladeriva-v1`
to `-v2` in `sw.js` so devices fetch the new version, then re-upload.
