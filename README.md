# L in the Castle — Website

The official one-page website for **L in the Castle LLC**, a software studio in Prishtina, Kosovo that designs and builds web and mobile apps (iOS & Android). Lives at [linthecastle.com](https://linthecastle.com).

The entire site is a single self-contained `index.html` — embedded CSS, inline SVG icons and favicon, no build step, and **no external network requests** (no CDNs, web fonts, or third-party scripts).

## Local preview

```sh
open index.html
```

Or just double-click `index.html` in your file browser.

## Deploy

The site is one static file, so any static host works and **no build step is required**:

- **Netlify Drop** — drag the project folder onto <https://app.netlify.com/drop>.
- **Cloudflare Pages** — create a project from this repo; framework preset *None*, no build command, output directory `/`.
- **GitHub Pages** — enable Pages on the repo and serve from the branch root.
- **Vercel** — import the repo; framework preset *Other*, no build command.

After deploying, point the **linthecastle.com** DNS at your host (per that host's custom-domain instructions — typically an `A`/`ALIAS` record for the apex and a `CNAME` for `www`).

## Contact

- Email: info@linthecastle.com
- Location: Prishtina, Kosovo

© 2026 L in the Castle LLC
