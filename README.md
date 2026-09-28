# Texas Light Crew — Eleventy Static Site

This website is built with [Eleventy](https://www.11ty.dev/). Render.com monitors the Github repository and updates the website at https://txlightcrew.onrender.com/ when updates are pushed to the main branch. 

## Quick Start

```bash
npm install
npm start        # dev server at http://localhost:8080
npm run build    # production build → _site/
```

## Project Structure

```
txlightcrew-11ty/
├── src/
│   ├── _includes/       # Partials (header, footer, quote-modal)
│   ├── _layouts/        # Page layouts (base.njk)
│   ├── css/
│   │   └── main.css     # Full stylesheet (loaded deferred)
│   ├── js/
│   │   └── main.js      # Lightweight vanilla JS (deferred)
│   ├── images/          # Local image assets
│   │   └── icons/       # SVG stat icons
│   └── index.njk        # Homepage
├── .eleventy.js         # Eleventy config
├── package.json
└── _site/               # Build output (gitignored)
```

## Deploying to Render Static Web Hosting

To update the website, update the code. Commit the changes and push this repo to GitHub: `https://github.com/tlcoperations/txlightcrew`. Every push to the `main` branch auto-deploys.

Render.com settings:

| Setting | Value |
|---------|-------|
| Build command | `npm install; npm run build` |
| Build directory | `_site` |


## Performance Notes

- **Critical CSS** is inlined in `<head>` (above-the-fold styles only)
- **Full CSS** is loaded with `rel="preload"` + `onload` swap (zero render-blocking)
- **JS** is deferred — never blocks parsing
- **Hero image** uses `fetchpriority="high"` for LCP optimization
- **Below-fold images** use `loading="lazy" decoding="async"`
- **No external CDN resources** (all CSS/JS/fonts are local)
- **Animations respect** `prefers-reduced-motion`

## WCAG 2.1 AA Compliance

- Skip-to-content link
- All images have descriptive `alt` text (decorative images use `alt=""`)
- Color contrast meets AA ratios (navy/white, gold on navy)
- All interactive elements have visible focus indicators
- Modal has focus trap and `aria-labelledby`/`aria-describedby`
- Navigation uses proper ARIA roles (`aria-expanded`, `aria-haspopup`, `aria-label`)
- Stats section uses `<dl>/<dt>/<dd>` for semantic data
