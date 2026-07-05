# GlowAI + Kane

A frontend-only integration demo: [GlowAI](https://github.com/808cadger/GlowAI)'s existing PWA UI with [Kane](https://github.com/808cadger/kane-avatar) — a real-time 3D AI companion avatar — embedded via a single script tag.

This is **not** the production GlowAI app (no backend, no mobile wrappers) — it's a snapshot of GlowAI's `www/` frontend used to prove Kane can be dropped into a real, already-built app without touching its source. See `vendor/kane.js` (Kane's self-mounting embed bundle) and the script tag near the bottom of `index.html`.

Integration notes:
- Kane mounts in `corner` mode, positioned `bottom-left` to avoid overlapping GlowAI's own chat panel.
- `index.html`'s CSP `connect-src` is extended to allow Kane's backend origin (`http://127.0.0.1:8787` for local dev) — without this, Kane's chat silently fails with no visible error.
- `kane-avatar.glb` is Kane's current avatar model (Avaturn T2 export — full ARKit blendshapes for blink/lip-sync, gaze-tracking eye bones).
- Kane's backend (chat/persona/memory) is a separate process — see the `kane-avatar` repo's own README for running it locally.
