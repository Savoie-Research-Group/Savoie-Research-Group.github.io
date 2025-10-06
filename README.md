# Savoie Research Group Website

Static website for the Savoie Research Group. Built with plain HTML/CSS and light client-side JS for dynamic publications. Uses Notre Dame branding colors and (optionally) legacy styles from the previous site for layout.

## Contents
- `index.html` – Home page (ND branding + optional legacy layout)
- `research.html` – Research overview
- `people.html` – Current team (photos and bios)
- `publications.html` – Auto-loads latest publications (Crossref)
- `contact.html` – Contact info
- `data+code.html` – Links to datasets and code (placeholder if empty)
- `styles.css` – Site styles (ND palette, components)
- `downloaded/` – Assets/CSS pulled from the old site
  - `downloaded/main.css` – Legacy stylesheet (linked before `styles.css`)
- `images/` – Site images (e.g., `images/people/*`)

## Local development
Just open any `.html` file in a browser. For a simple local server (recommended for CORS-friendly behavior):

```bash
# Python 3
python -m http.server 8000
# then open http://localhost:8000/
```

## Notre Dame colors
Primary colors are set in `styles.css`:
- ND Blue `#0c2340`
- ND Metallic Gold `#ae9142`
- Light backgrounds use ND sky blues.

## Legacy styling
The old site’s stylesheet is included for layout/visual parity:
```html
<link rel="stylesheet" href="downloaded/main.css">
<link rel="stylesheet" href="styles.css">
```
`styles.css` loads after and overrides where needed. Remove the legacy link if you want a pure ND-branded look.

## People page – photos and bios
- Place photos in `images/people/`.
- Filenames should match slugs referenced in `people.html` (e.g., `bryan-piguave.jpg`, `zhao-li.png`).
- Missing images automatically fall back to `images/people/_placeholder.jpg` if present.
- Bios are sourced from the current People page; Alumni intentionally have no photos.

## Publications – Crossref loader
`publications.html` fetches the latest 5 items from Crossref on page load. It prefers University of Notre Dame affiliation and falls back to author-only results. Client-side filters ensure results correspond to Brett M. Savoie.

To adjust filtering or query:
- Update the URLs and filters near the bottom `<script>` in `publications.html`.

Optional (Google Scholar): requires a small serverless proxy (e.g., Cloudflare Worker + SerpAPI). Not enabled by default.

## Banners and images
- Research page supports a banner image in `images/AA_CG.png`.
- Styles for banners are in `styles.css` (can enable/disable overlay as needed).

## Consistent head sections
All pages include:
```html
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<link rel="stylesheet" href="downloaded/main.css">
<link rel="stylesheet" href="styles.css">
```

## Deployment
This is a static site. Host via GitHub Pages or any static host.

GitHub Pages quick start:
1. Push to `main`.
2. In repo settings → Pages → Deploy from branch → `main` → `/root`.
3. Wait for build; visit the published URL.

## Maintenance checklist
- Update team in `people.html` (and add/remove photos in `images/people/`).
- Check publication rendering on `publications.html` loads 5 recent items.
- Keep ND branding consistent in `styles.css`.
- Remove/reduce legacy `downloaded/main.css` if you move fully to the new design.