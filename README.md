# Pretext Again

An interactive, audio-reactive text visualization built with [@chenglou/pretext](https://github.com/chenglou/pretext) — a pure JS text measurement library that avoids DOM reflow.

**Live site deployed on Vercel.**

## What It Does

Pretext Again captures audio from a YouTube video (via screen share) and turns it into a real-time waveform made entirely of flowing text. Frequency bands drive the height of vertical text columns across the canvas — bass frequencies at the center, treble at the edges. The text content is a house music monologue (Jack & House, spoken word samples, astronaut dialogue).

### Features

- **Audio-reactive text columns** — FFT analysis maps frequency bins to column heights, with smooth interpolation
- **Interactive void** — mouse cursor carves a circular cutout (48px radius) with a green (#24BD20) outline ring in all states
- **Play/pause cursor** — cursor shows ⏸ when playing, ▶ when paused; reverts to default over UI elements (video panel, social handle)
- **Logo push effect** — each word in the logo is individually displaced by the void rather than clipped
- **Floating YouTube player** — hide/show and 1x/2x size toggle, with native progress bar for scrubbing
- **Keyboard controls** — Space (play/pause), Escape (toggle panel), 1/2 (open video at 1x/2x size)

### States

| State | Cursor | Audio |
|---|---|---|
| Unsupported browser | Default | None |
| Pre-connect | Default + void | None, iframe not loaded |
| Audio connected, playing | ⏸ + void + green ring | Playing, reactive waveform |
| Audio connected, paused | ▶ + void + green ring | Paused |
| Over UI elements | Default | Unchanged |

## Built With

- **[@chenglou/pretext](https://github.com/chenglou/pretext)** — text measurement and layout without DOM reflow. Uses `prepareWithSegments()` and manual line layout to render Unicode-aware text into Canvas columns efficiently
- **Web Audio API** — `AnalyserNode` with 2048-bin FFT, 0.75 smoothing constant
- **Canvas 2D** — full-viewport rendering with devicePixelRatio scaling
- **Vite** — dev server and production bundler
- **Vercel** — hosting

## Getting Started

```bash
npm install
npm run dev        # starts dev server (localhost:5173)
npm run build      # production build to dist/
```

### Usage

1. Open in Chrome/Edge (required for screen share audio capture)
2. Click **"connect audio"**
3. Share a browser tab playing audio
4. Move your mouse around the waveform

Safari is not supported — a fallback message is shown.

## Project Structure

```
src/fred.ts        # all application code (~26KB)
index.html         # entry point, loads src/fred.ts as ES module
public/og.png      # Open Graph image
dist/              # production build output
```

## Origin

Forked from / inspired by [chenglou/pretext](https://github.com/chenglou/pretext) — Cheng Lou's pure-JS text measurement library that enables fast text layout without triggering browser reflow. This project uses pretext's segmented layout API to render text into canvas columns driven by audio data.
# pretext-again
