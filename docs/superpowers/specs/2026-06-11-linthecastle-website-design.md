# L in the Castle — One-Page Website Design

**Date:** 2026-06-11
**Domain:** linthecastle.com
**Purpose:** A professional one-page marketing site for L in the Castle LLC, a software company that builds apps. Primary near-term goal: serve as the verifiable company website for Apple Developer Program enrollment.

## Goals

- Present L in the Castle LLC as a legitimate, established software company.
- Clearly state what the company does (software & mobile apps).
- Provide a clear contact method and company location (Apple verification expects both).
- Load instantly, look polished on desktop and mobile, no build step.

## Non-Goals (YAGNI)

- No blog, portfolio, CMS, analytics, or contact form backend.
- No JavaScript framework, no build pipeline, no external runtime dependencies.
- No multi-page navigation.

## Tech Approach

A single self-contained `index.html` with embedded CSS (and minimal inline SVG for the favicon/logo mark). No external CSS/JS/font dependencies — uses a system font stack so it renders identically offline and everywhere. Portable to any static host (Netlify, Vercel, GitHub Pages, Cloudflare Pages, registrar hosting) by uploading one file.

## Visual Style — "Clean Minimal"

- **Background:** white (`#ffffff`), light section tint (`#f9fafb`) where needed for contrast.
- **Text:** near-black (`#111827`), secondary gray (`#4b5563` / `#6b7280`).
- **Accent:** indigo `#4f46e5` (buttons, links, highlights).
- **Type:** system sans-serif stack; large confident headings, comfortable line-height.
- **Spacing:** generous whitespace, max content width ~1080px, subtle 1px borders and soft shadows on cards.
- **Footer:** dark slate (`#111827`) band with light text.

## Page Structure (single scrolling page)

1. **Nav (sticky)** — "L in the Castle" wordmark (with small SVG mark) on the left; anchor links Services · About · Contact and a "Get in touch" button on the right. Collapses gracefully on mobile.
2. **Hero** — Headline: *"Software & mobile apps, built with craft."* (final copy may be lightly refined). Supporting tagline sentence. Primary CTA button → scrolls to Contact.
3. **Services** — three cards:
   - **App Development** — native and cross-platform iOS & Android apps.
   - **Web & Cloud** — web apps and cloud-backed services.
   - **Product Design** — UX/UI design from idea to shipped product.
4. **About** — short paragraph: L in the Castle LLC is a software company that designs and builds applications; based in Prishtina, Kosovo. Conveys craft, reliability, partnership.
5. **Contact** — heading, one supporting line, large email button linking `mailto:info@linthecastle.com`, and a location line "Prishtina, Kosovo".
6. **Footer** — © 2026 L in the Castle LLC.

## Concrete Content / Data

- **Company name:** L in the Castle LLC
- **Contact email:** info@linthecastle.com
- **Location:** Prishtina, Kosovo
- **Copyright year:** 2026

## Technical Details

- Responsive via CSS (flexbox/grid + a mobile breakpoint around 720px).
- Smooth-scroll anchor navigation (`scroll-behavior: smooth`).
- Semantic, accessible HTML: landmark elements (`header`, `nav`, `main`, `section`, `footer`), descriptive `alt`/`aria` where relevant, sufficient color contrast, focus-visible styles.
- `<head>` metadata for legitimacy/SEO: `<title>`, meta description, viewport, theme-color, Open Graph (og:title, og:description, og:url, og:type=website) and Twitter card tags.
- Inline SVG favicon (a small castle / "L" mark) via `<link rel="icon" href="data:image/svg+xml,...">`.

## Deliverables

- `index.html` at the repo root — the complete site.
- `README.md` — one-paragraph description plus deploy instructions (how to publish to a static host / point linthecastle.com at it).

## Success Criteria

- Opening `index.html` in a browser renders the full page correctly on desktop and mobile widths.
- All anchor links and the email button work.
- Page clearly communicates company name, what it does, contact email, and location.
- No console errors; no external network requests required to render.
