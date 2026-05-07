# Francesco Aiena — Portfolio

Personal portfolio site for Francesco Aiena, a video editor working across AI video, VFX and motion design. The site presents selected projects with case-study detail pages and a contact form.

Live: https://shotbywhosfra.com

---

## Tech stack

- HTML5
- CSS3 (CSS custom properties, Grid, Flexbox, container queries)
- Vanilla JavaScript (ES2020+, no transpiler)
- Canvas 2D API for the ambient particle field
- History API for client-side routing and deep links
- Google Fonts: Syne (display), DM Serif Display (italic accents), Inter (body)
- Formspree for contact-form submissions

No framework. No build step. No npm dependencies.

---

## Project structure

```
.
├── index.html      All HTML, CSS and JavaScript in a single file
├── media/          Images, posters and video assets
│   ├── VFX/
│   ├── VIDEOS/
│   └── AI/
└── README.md
```

The site is intentionally a single file. This keeps deployment trivial and avoids a build pipeline for a portfolio that updates infrequently.

---

## Features

- Five top-level views: Home, Video, AI, VFX, About
- Per-project case-study pages built from a modular renderer (hero, stats strip, lyrics block, split-feature, director's note, credits, pull-quote, contact-sheet, pipeline)
- Client-side routing with hash-based deep links (`#/vfx/aftermovie`, `#/ai/01`, `#/video/push-it`)
- Light / dark theme toggle with system-preference detection and `localStorage` persistence
- Custom cursor with hover affordance on interactive elements
- Ambient particle field with mouse repulsion and constellation lines (inner pages only)
- Mobile drawer navigation with focus trap and swipe-to-close
- Background video on the home page with poster fallback
- Contact form with Formspree integration, honeypot anti-spam, and reply-to wiring

---

## Local development

Serve the directory with any static file server. The site uses ES modules and the History API, both of which require an HTTP origin (not `file://`).

```bash
# Python
python3 -m http.server 8000

# Node
npx serve .

# PHP
php -S localhost:8000
```

Then open `http://localhost:8000`.

---

## Deployment

Static hosting on any provider. The site has been tested on:

- GitHub Pages — push to `main`, enable Pages from `Settings → Pages → Deploy from branch`
- Netlify, Vercel, Cloudflare Pages — drop the folder, no build command needed

Video assets currently live on GitHub raw URLs. For production traffic, move them to a dedicated CDN (Cloudflare R2, Bunny.net, Mux) — GitHub raw is rate-limited and lacks reliable byte-range support for streaming.

---

## Browser support

Tested and working on:

- Chrome / Edge / Brave 120+
- Firefox 121+
- Safari 17+ (macOS), Safari iOS 17+

The site uses `backdrop-filter`, `color-mix()` and `dvh` units. Older browsers will render the site without these effects but with no broken layout.

---

## Updating content

All content lives in `index.html`. The relevant data structures:

- `videoData` — Video page grid items
- `aiProjects` and `aiDetails` — AI page rows and case-study detail
- `vfxData` — VFX page projects and case-study detail
- `<section class="ab-...">` blocks — About page content (statement, numbers, capabilities, selected)

The contact form `action` URL is the Formspree endpoint, set inline on the `<form>` element.

---

## License

All rights reserved. © Francesco Aiena.
