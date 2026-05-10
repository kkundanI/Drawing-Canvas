# drawboard

A minimal, zero-dependency browser-based drawing app. Open the HTML file and draw — no install, no build step, no server.

![drawboard v3](https://img.shields.io/badge/version-3.0-c8f04a?style=flat-square&labelColor=18181b) ![license](https://img.shields.io/badge/license-MIT-60a5fa?style=flat-square&labelColor=18181b) ![html only](https://img.shields.io/badge/stack-HTML%20%2B%20Canvas-f0f0f0?style=flat-square&labelColor=18181b)

---

## Features

### Drawing tools
- **Pen** — clean, precise strokes
- **Marker** — semi-transparent, wide strokes
- **Brush** — tapered, pressure-sensitive feel
- **Pencil** — light, textured strokes
- **Chalk** — rough, scattered effect
- **Spray** — airbrush-style spray paint

### Shapes
- Rectangle, Ellipse, Triangle, Line, Arrow
- Star, Diamond, Hexagon
- Toggle between **outline** and **solid fill** for all shapes

### Stroke controls
- **Stroke size** slider (1–60px)
- **Opacity** slider (5–100%)
- **20 color swatches** + custom color picker

### Stabilization & smoothing
- **Smooth lines** — Bézier curve smoothing on freehand strokes
- **Pressure simulation** — stroke width varies naturally with drawing speed
- **Stabilizer** — lag-based stabilizer with adjustable smoothness (0.01–0.99) for clean, controlled lines

### Canvas management
- **Resize canvas** — preset sizes (HD, Full HD, 4K, Square, A4, Story) or custom dimensions with aspect ratio lock and anchor point control
- **Crop canvas** — drag to select and crop any region
- **Select & move** — marquee select any region, move it around the canvas
- **Undo / Redo** — full history (Ctrl+Z / Ctrl+Y)

### Export & utility
- **Export PNG** — downloads the canvas as a transparent-background PNG
- **Clear canvas** — wipe and start fresh
- **Eraser** — toggle with `E` key or sidebar button
- **Snap indicator** — visual cursor dot that scales with brush size

### Keyboard shortcuts
| Key | Action |
|-----|--------|
| `E` | Toggle eraser |
| `Ctrl+Z` | Undo |
| `Ctrl+Y` / `Ctrl+Shift+Z` | Redo |
| `Ctrl+A` | Select all |
| `Delete` / `Backspace` | Delete selection |
| `Escape` | Cancel selection or crop |

---

## Files

| File | Description |
|------|-------------|
| `drawboard-v3.html` | Latest version — full feature set including shapes, crop, select, resize modal |
| `canvas-draw-stabilized.html` | Stabilizer-focused build — clean implementation of lag-based stroke stabilization |
| `canvas-draw.html` | Earlier build — core drawing tools without advanced canvas management |
| `canvas-draw__1_.html` | Alternate early build |

Start with `drawboard-v3.html`.

---

## Usage

1. Download or clone the repo
2. Open `drawboard-v3.html` in any modern browser
3. Draw

No dependencies. No npm. No build. Just open and go.

---

## Tech stack

- Vanilla HTML, CSS, JavaScript
- HTML5 Canvas API (two layered canvases — drawing layer + overlay layer)
- Google Fonts — [Syne](https://fonts.google.com/specimen/Syne) + [DM Mono](https://fonts.google.com/specimen/DM+Mono)

---

## How it works

The app uses two stacked `<canvas>` elements. The main drawing canvas stores committed strokes. An overlay canvas handles live previews — shape outlines as you drag, selection marquees, crop regions — which are then committed to the main canvas on mouse up. A third background canvas provides the neutral drawing surface.

Stroke stabilization uses a lag algorithm: instead of following the cursor directly, the brush follows a point that moves toward the cursor at a configurable speed, producing smooth, wobble-free lines even when drawing quickly.

Pressure simulation infers pen pressure from drawing speed — fast strokes produce thinner lines, slow strokes produce thicker ones — mimicking the feel of physical media without requiring a pressure-sensitive input device.

---

## License

MIT — do whatever you want with it.
