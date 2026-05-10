# Vicki Liang — Studio Portfolio

Static HTML/CSS/JS portfolio site. No build step, no framework. Open `index.html` directly or serve with `npx serve`.

## Structure

| File | Purpose |
|------|---------|
| `index.html` | Portfolio index — tabular list of all projects |
| `info.html` | About / bio page with editorial 4-column grid |
| `*.html` | Individual project gallery pages (e.g. `fondazione-prada.html`) |
| `style.css` | Single shared stylesheet for all pages |

## Design system

- **Font**: Inter (Google Fonts), 14px base, weight 400
- **Background**: `#f0efec` — warm light gray (all pages)
- **Text**: `#1C191A` — near-black
- **Accent**: `#EA3F25` — used for row hover fill, transition overlay %, gallery box bg
- **Accent text**: `#EAD091` — warm yellow, used on red accent backgrounds

## Index page layout

4-column flex row (`.portfolio-row`):

| Class | Width | Notes |
|-------|-------|-------|
| `.col-title` | 180px | Project name |
| `.col-city` | 120px | Location |
| `.col-count` | 50px | Image count, right-aligned |
| `.col-tags` | flex-grow | Discipline / campaign type |

Rows have `0.0625rem 2rem` padding (1px vertical, 32px horizontal). Hover turns row `#EA3F25` bg with `#EAD091` text.

A `.portfolio-spacer` (2rem height) separates commercial work from the personal "Innenwelt" project at the bottom.

## Inline gallery drawer (index page)

Clicking a row with images opens an accordion drawer beneath it — no page navigation.

- **Active row**: gets `.active` class → same `#EA3F25` / `#EAD091` styling as hover
- **Drawer**: `.gallery-drawer` — `max-height` animates `0 → 280px` (0.38s ease)
- **Track**: `.gallery-drawer-track` — horizontal flex, 260px tall, `overflow-x: auto`, drag-to-scroll via `mousedown/mousemove`
- **Images**: full color (no grayscale), `height: 100%`, `width: auto`
- **Toggle**: clicking the active row closes it; clicking a different row swaps instantly
- **Image data**: stored as `data-images='[…]'` JSON on each `.portfolio-row`
- Rows with `href="#"` (no images yet) are inert on click

## Gallery pages (individual `.html` files)

Kept as standalone pages. Horizontal drag-to-scroll carousel (`gallery-carousel`). Images are grayscale (`filter: grayscale(1) brightness(0.95)`). Footer shows slide counter.

## Animations

- **Page entry**: `pageFadeIn` 0.4s on `body`
- **Row stagger**: JS sets `animationDelay` at 0.04s × row index; `rowFadeIn` 0.4s per row

## Dev server

`.claude/launch.json` is configured — run via:

```
npx serve -l 3000
```

Or use Claude Code's preview tool (`static-site` config).
