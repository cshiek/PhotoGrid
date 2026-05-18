# PhotoGrid

A browser-based photo grid editor for arranging images in a configurable grid layout with per-image pan and zoom.

## Features

- **Configurable grid** — Set any number of rows and columns (1–20)
- **Upload & place** — Upload photos and click empty cells to place them
- **Drag & drop** — Drag photos between cells to reorder; drag from anywhere on the page to upload
- **Per-image pan & zoom** — Scroll wheel to zoom, Shift+drag to pan each image independently
- **Cover / Contain toggle** — Switch all images between "cover" (fills cell, cropped edges) and "contain" (full image visible with letterbox bars)
- **Double-click** — Reset an image to its default zoom and center position
- **Save / Load** — Export the grid state to a JSON file for backup or transfer
- **Print** — Print-friendly layout optimized for A4 paper
- **TIFF support** — TIFF files are automatically decoded and converted to JPEG
- **Persistent state** — Grid layout and image positions are saved to localStorage automatically
- **Dark theme** — Clean dark UI that's easy on the eyes

## Dependencies

No build tools or frameworks. Only three JavaScript libraries:

| Library | Purpose |
|---|---|
| `utif.js` | TIFF file decoding |
| `pako.min.js` | DEFLATE decompression (required by UTIF.js for compressed TIFF data) |
| `tiff.min.js` | Additional TIFF utilities (optional) |

## Installation

1. Download or clone this repository
2. Ensure the three library files (`utif.js`, `pako.min.js`, `tiff.min.js`) are in the same directory as `index.html`
3. Open `index.html` directly in any modern browser (Chrome, Firefox, Edge, Safari) — no server required

Alternatively, serve locally:

```bash
python3 -m http.server 8080
```

Then navigate to `http://localhost:8080`.

## Browser Support

Works in all modern browsers. Requires:

- ES6+ JavaScript support
- Canvas API (for image compression)
- LocalStorage (for state persistence)
- Web Audio API is **not** required

TIFF support requires `utif.js` and `pako.min.js` to be present.

## Usage

1. **Upload** — Click "Upload Photos" or drag image files onto the page
2. **Place** — Click an empty cell to place the first queued photo
3. **Zoom** — Scroll the mouse wheel while hovering an image (1x–10x)
4. **Cover / Contain** — Click "Cover" or "Contain" in the topbar to toggle between cropped (fills cell) and full-image (letterboxed) views for all photos
5. **Pan** — Hold Shift and drag on an image to reveal hidden areas
6. **Reorder** — Drag an image to a different cell to move it; drag to an occupied cell to swap
7. **Reset** — Double-click any image to reset its zoom and position
8. **Delete** — Hover an image and click the × button in the top-right corner
9. **Save** — Click "Save" to download the grid configuration as a JSON file
10. **Load** — Click "Load" to restore a previously saved grid configuration
11. **Print** — Click "Print Grid" to generate a print-ready layout

## Keyboard Shortcuts

| Shortcut | Action |
|---|---|
| Shift + drag | Pan an image (reveals cropped areas) |
| Double-click | Reset zoom and center an image |

## Storage

Grid state (images, layout, zoom, pan positions) is saved to the browser's `localStorage` under the key `photogrid_state`. Each image is stored as a compressed JPEG data URL. Clearing browser data will erase all saved grids.
