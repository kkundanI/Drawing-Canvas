# Drawboard

A minimal, zero-dependency browser-based drawing app. Open the HTML file and draw — no install, no build step, no server.

![drawboard v4](https://img.shields.io/badge/version-4.0-c8f04a?style=flat-square&labelColor=18181b) ![license](https://img.shields.io/badge/license-MIT-60a5fa?style=flat-square&labelColor=18181b) ![html only](https://img.shields.io/badge/stack-HTML%20%2B%20Canvas-f0f0f0?style=flat-square&labelColor=18181b)

---

## Features

### Drawing tools
- **Pen** — clean, precise strokes
- **Marker** — semi-transparent, wide strokes
- **Brush** — tapered, pressure-sensitive feel
- **Pencil** — light, textured strokes
- **Chalk** — rough, scattered effect
- **Spray** — airbrush-style spray paint
- **Text** *(v4)* — click anywhere on the canvas to place text with font and size controls

### Shapes
- Rectangle, Ellipse, Triangle, Line, Arrow
- Star, Diamond, Hexagon
- Fill modes: **None**, **Solid**, or **Canvas BG** *(v4)*

### Stroke & fill controls
- **Stroke size** slider (1–60px)
- **Opacity** slider (5–100%)
- **20 stroke color swatches** + custom color picker
- **Separate fill color** palette with 10 swatches + custom picker *(v4)*

### Text tool *(v4)*
- Click to place text anywhere on the canvas
- Choose from **Default**, **Dave Mergens** (handwriting), **Serif**, or **Monospace** fonts
- Adjustable text size (8–144px) via the font dropdown in the topbar
- Font scope — apply font to new text only, the whole canvas, or a selection

### Stabilization & smoothing
- **Smooth lines** — Bézier curve smoothing on freehand strokes
- **Pressure simulation** — stroke width varies naturally with drawing speed
- **Stabilizer** — lag-based stabilizer with adjustable smoothness (0.01–0.99)

### Canvas management
- **Resize canvas** — preset sizes (HD, Full HD, 4K, Square, A4, Story) or custom dimensions with aspect ratio lock and anchor point control
- **Crop canvas** — drag to select and crop any region
- **Select & move** — marquee select any region, move it around the canvas
- **Undo / Redo** — up to 60 steps (Ctrl+Z / Ctrl+Y)

### Export & utility
- **Export PNG** — downloads the canvas as a PNG
- **Clear canvas** — wipe and start fresh
- **Eraser** — toggle with `E` key or topbar button
- **Live cursor dot** — scales with brush size, switches style for eraser and select modes

### Keyboard shortcuts
| Key | Action |
|-----|--------|
| `T` | Text tool |
| `E` | Toggle eraser |
| `Ctrl+Z` | Undo |
| `Ctrl+Y` / `Ctrl+Shift+Z` | Redo |
| `Ctrl+A` | Select all |
| `Delete` / `Backspace` | Delete selection |
| `Escape` | Cancel selection, crop, or text input |

---

## Files

| File | Description |
|------|-------------|
| `drawboard-v4.html` | **Latest** — adds text tool, font picker, separate fill color palette, fill modes |
| `drawboard-v3.html` | Previous version — shapes, crop, select, resize modal |
| `canvas-draw-stabilized.html` | Stabilizer-focused build |
| `canvas-draw.html` | Earlier build — core drawing tools |
| `canvas-draw__1_.html` | Alternate early build |

Start with `drawboard-v4.html`.

---

## Usage

1. Download or clone the repo
2. Open `drawboard-v4.html` in any modern browser
3. Draw

No dependencies. No npm. No build. Just open and go.

---

## Tech stack

- Vanilla HTML, CSS, JavaScript
- HTML5 Canvas API — four layered canvases: background, drawing, overlay, crop
- Google Fonts — [Syne](https://fonts.google.com/specimen/Syne) + [DM Mono](https://fonts.google.com/specimen/DM+Mono)
- Custom font — Dave Mergens (handwriting, loaded via CDN)

---

## How it works

The app uses four stacked `<canvas>` elements. The main drawing canvas stores committed strokes. An overlay canvas handles live previews — shape outlines as you drag, selection marquees, crop regions — committed to the main canvas on mouse up. A background canvas provides the neutral white drawing surface. A fourth canvas handles the crop interaction overlay.

Stroke stabilization uses a lag algorithm: instead of following the cursor directly, the brush follows a point that moves toward the cursor at a configurable speed, producing smooth, wobble-free lines.

Pressure simulation infers pen pressure from drawing speed — fast strokes produce thinner lines, slow strokes produce thicker ones — mimicking the feel of physical media without requiring a pressure-sensitive input device.

The text tool renders typed input directly onto the drawing canvas using the Canvas 2D `fillText` API, with font family and size controlled through the topbar dropdown.

---

## Changelog

### v4
- Added **Text tool** — click to place, choose font, adjust size
- Added **separate fill color palette** with its own swatches and custom picker
- Added **Canvas BG fill mode** for shapes
- Font dropdown in topbar with scope control (new strokes / all canvas / selection)
- Undo history expanded to 60 steps
- UI tightened and refined throughout

### v3
- Added shapes (Rect, Ellipse, Triangle, Line, Arrow, Star, Diamond, Hexagon)
- Added canvas resize modal with presets, aspect ratio lock, anchor control
- Added crop tool
- Added select & move

### v2 / early builds
- Core freehand drawing tools
- Stroke stabilizer
- Pressure simulation

---

## License

MIT — Have fun with it.
