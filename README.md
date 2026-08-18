# Finger Garden 🌱

Pinch your thumb against any of your other eight fingers and a seed drops into the air.
It falls, sprouts, grows a stem and leaves, blooms — then the wind carries it away.
Every finger has its own flower and its own note. Fill the screen with 30 plants and
five butterflies come out to tell you what you already suspected: you have magic.

Built with vanilla HTML/CSS/JS, [Three.js](https://threejs.org) for rendering and
[MediaPipe Hands](https://developers.google.com/mediapipe) for hand tracking.
No build step — one `index.html`.

## Play

Open the live site, allow camera access, and pinch.

Works on desktop, iPad and phones, in portrait or landscape. The interface is
available in English and 中文 (toggle in the top-right corner).

> **The camera only works over HTTPS.** `github.io` and `localhost` are fine;
> a plain `http://192.168.x.x` LAN address is not — browsers block camera
> access outside a secure context.

## Controls

| | |
|---|---|
| Thumb + index / middle / ring / pinky | Sow a seed — 8 fingers, 8 flowers, 8 notes |
| Left hand | 🌷 🌻 🌸 🌼 · C4 D4 E4 F4 |
| Right hand | 🌹 🪷 🌺 🪻 · G4 A4 B4 C5 |

Plants take 3–5 s to bloom, linger 5–8 s, then blow away. Sizes are randomised.

## Run locally

```bash
python3 -m http.server 5173
```

Then open <http://localhost:5173>.

To test on a real phone or tablet you need an HTTPS URL — the quickest way is a
tunnel:

```bash
npx --yes localtunnel --port 5173
```

## Notes

- MediaPipe is loaded through a plain `<script>` tag and read off the global
  `window.Hands`; Three.js is loaded as an ES module via an import map.
- First load pulls ~10 MB of MediaPipe model and WASM from jsDelivr.
- The camera feed keeps its native aspect ratio (letterboxed, never stretched);
  the WebGL canvas is matched pixel-for-pixel to that rectangle so fingertips
  and flowers line up exactly.
