# Night Ventures — marketing site

A single-page marketing site for Night Ventures (venture studio). Static, self-contained, no build step.

## Run it locally

It's plain HTML/CSS/JS — open `index.html` in a browser, or serve it:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

(A local server is recommended over double-clicking, so the relative image paths resolve consistently.)

## Structure

```
index.html               # the entire site — markup, CSS, and JS in one file
nv-mark.png              # NV monogram logo, transparent (used in hero, nav, diagram)
kylie.png, jay-hunter.jpg, k5-logo.png,
  maryruths-logo.jpg, house-logo.svg, k2o.png   # case-study photos + logos
quad-chart-archive.html  # ARCHIVED talent-led/CPG 2x2 chart (removed from the live site; kept for reference)
nv-mark.jpg / nv-logo.jpg # source/originals for the placeholder logo (not referenced at runtime)
```

> Note: assets are kept flat in the repo root for simplicity — feel free to reorganize into an `img/` or `assets/` folder (just update the `src`/`href` paths in `index.html`).

## How it's built

- Vanilla HTML/CSS/JS, no dependencies or framework.
- Five full-screen **scroll-snap** sections: Header → Why/How (diagram + case study) → Companies → Operators & Co-investors → CTA/Footer.
- A sticky top nav (NV mark) appears after section 1; a back-to-top button appears past it.
- The section-1 line "We combine world-class operators…" **morphs/enlarges** into the section-2 heading on scroll (a scroll-linked fixed element; see the `#flyer` / `#slotA` / `#slotB` logic in the JS).
- Theme is driven by two CSS variables at the top of `index.html`:
  - `--green` → currently holds **cerulean `#0C4A6E`** (this is a color trial; the variable name is legacy). Change this one value to recolor the whole site.
  - `--cream` → `#F8F3F0` (type + logo).

## Known placeholders / TODO

- **Logo:** `nv-mark.png` is a placeholder monogram — swap for final brand files when ready.
- **Links:** the CTA "Get in touch" and footer "Fund One" / "LinkedIn" point to `#`. Wire to real URLs.
- **Case study images:** real assets are in place; person photos are cropped to 2:1 via `object-position` (tweak per image if framing needs adjusting).
- **Color:** cerulean is a trial — easy to revert/try alternates via `--green`.

## Deploy

Any static host works (no build):

- **GitHub Pages:** push this repo, then Settings → Pages → deploy from the default branch (root).
- **Netlify / Vercel / Cloudflare Pages:** connect the repo (build command: none; publish directory: repo root) or drag-and-drop the folder.
