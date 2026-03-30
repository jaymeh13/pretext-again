# Pretext again..

Audio-reactive text visualization built with [@chenglou/pretext](https://github.com/chenglou/pretext).

**[pretextagain.vercel.app](https://pretextagain.vercel.app/)**

By [Jayme Hoffman](https://twitter.com/jaymehoffman)

## What It Does

Captures audio from a YouTube video via screen share and renders a real-time waveform made of flowing text. Frequency bands drive vertical text column heights — bass at center, treble at edges.

### Features

- **Audio-reactive columns** — FFT maps frequency bins to column heights
- **Void** — circular cutout (48px) follows cursor with green (#24BD20) ring
- **Play/pause cursor** — ⏸ when playing, ▶ when paused; default over UI elements
- **Logo push** — each word displaced individually by the void
- **YouTube player** — hide/show, 1x/2x size, native progress bar
- **Keyboard** — Space (play/pause), Escape (toggle panel), 1/2 (video size)

### States

| State | Cursor | Audio |
|---|---|---|
| Unsupported browser | Default | None |
| Pre-connect | Default + void | None |
| Playing | ⏸ + void + ring | Reactive waveform |
| Paused | ▶ + void + ring | Paused |
| Over UI | Default | Unchanged |

## Built With

- **[@chenglou/pretext](https://github.com/chenglou/pretext)** — text layout without DOM reflow
- **Web Audio API** — AnalyserNode, 2048-bin FFT
- **Canvas 2D** — full-viewport, devicePixelRatio scaling
- **Vite** / **Vercel**

## Getting Started

```bash
npm install
npm run dev        # localhost:5173
npm run build      # dist/
```

### Usage

1. Open in Chrome/Edge
2. Click "connect audio"
3. Share a browser tab
4. Move your mouse around

## Project Structure

```
src/fred.ts        # all application code
index.html         # entry point
public/og.png      # Open Graph image
dist/              # build output
```

## Origin

Built on [chenglou/pretext](https://github.com/chenglou/pretext) — pure-JS text measurement without browser reflow.
