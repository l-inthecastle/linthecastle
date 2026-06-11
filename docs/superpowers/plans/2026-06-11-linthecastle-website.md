# L in the Castle Website Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Build a polished, dependency-free one-page marketing website for L in the Castle LLC as `index.html`, suitable as the verifiable company site for Apple Developer Program enrollment.

**Architecture:** A single self-contained `index.html` with embedded CSS and an inline SVG favicon. No build step, no external CSS/JS/font requests. A short `README.md` documents deployment. Verification is visual/behavioral in a browser, since there is no application logic to unit-test.

**Tech Stack:** HTML5, embedded CSS (flexbox/grid, system font stack), inline SVG. No frameworks, no dependencies.

**Reference spec:** `docs/superpowers/specs/2026-06-11-linthecastle-website-design.md`

---

## File Structure

- Create: `index.html` — the complete single-page site (head metadata, embedded CSS, all sections, inline SVG favicon).
- Create: `README.md` — project description + deploy instructions.

---

### Task 1: Build `index.html` document skeleton, head metadata, and embedded CSS base

**Files:**
- Create: `index.html`

- [ ] **Step 1: Create the document skeleton with full `<head>` metadata**

Create `index.html` with `<!DOCTYPE html>`, `<html lang="en">`, and a `<head>` containing:
- `<meta charset="utf-8">`
- `<meta name="viewport" content="width=device-width, initial-scale=1">`
- `<meta name="theme-color" content="#4f46e5">`
- `<title>L in the Castle — Software & Mobile Apps</title>`
- `<meta name="description" content="L in the Castle LLC is a software company designing and building web and mobile apps. Based in Prishtina, Kosovo.">`
- Open Graph tags: `og:title`, `og:description`, `og:type` = `website`, `og:url` = `https://linthecastle.com`
- Twitter card: `twitter:card` = `summary`, `twitter:title`, `twitter:description`
- Inline SVG favicon via `<link rel="icon" href="data:image/svg+xml,...">` — a simple castle/"L" mark in indigo. Use URL-encoded SVG, e.g. a rounded square with crenellations and an "L".

- [ ] **Step 2: Add embedded CSS design tokens and base styles in a `<style>` block**

Inside `<head>`, add a `<style>` block defining:
- `:root` custom properties: `--bg:#ffffff; --bg-tint:#f9fafb; --text:#111827; --muted:#4b5563; --muted-2:#6b7280; --accent:#4f46e5; --accent-dark:#4338ca; --border:#e5e7eb; --max:1080px;`
- A modern CSS reset: `*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}`
- `html{scroll-behavior:smooth}`
- `body{font-family:-apple-system,BlinkMacSystemFont,"Segoe UI",Roboto,Helvetica,Arial,sans-serif;color:var(--text);background:var(--bg);line-height:1.6;-webkit-font-smoothing:antialiased}`
- A `.container{max-width:var(--max);margin:0 auto;padding:0 24px}` helper.
- `:focus-visible{outline:2px solid var(--accent);outline-offset:2px}` for accessibility.
- A reusable `.btn` style (indigo background, white text, rounded `10px`, padding `12px 22px`, `font-weight:600`, hover → `--accent-dark`) and `.btn--ghost` variant (transparent bg, accent text/border).

- [ ] **Step 3: Verify the document opens and is valid so far**

Run: `open index.html` (macOS) — or open the file in a browser.
Expected: A blank white page with the correct tab title "L in the Castle — Software & Mobile Apps" and the castle favicon. No console errors.

- [ ] **Step 4: Commit**

```bash
git add index.html
git commit -m "feat: add index.html skeleton, head metadata, and base CSS"
```

---

### Task 2: Sticky nav and hero section

**Files:**
- Modify: `index.html`

- [ ] **Step 1: Add the sticky nav inside `<body>`**

Add a `<header>` with a `.container` holding:
- Left: a brand link `<a href="#top">` with the inline SVG mark + wordmark text "L in the Castle".
- Right: a `<nav>` with anchor links `Services` (`#services`), `About` (`#about`), `Contact` (`#contact`), and a `.btn` "Get in touch" linking to `#contact`.

CSS: header is `position:sticky;top:0;z-index:10;background:rgba(255,255,255,.85);backdrop-filter:blur(8px);border-bottom:1px solid var(--border)`. Nav is flex, items gap ~24px. Brand uses `font-weight:700;font-size:18px;` with the SVG mark sized ~22px and `display:flex;align-items:center;gap:10px;text-decoration:none;color:var(--text)`.

- [ ] **Step 2: Add the hero `<section id="top">`**

Inside `<main>`, add a hero section with a `.container`:
- `<h1>` "Software & mobile apps, built with craft."
- A `<p class="lead">` tagline: "L in the Castle is a software studio designing and building reliable web and mobile apps — from first idea to App Store."
- A primary `.btn` "Get in touch" → `#contact` and a secondary `.btn--ghost` "See what we do" → `#services".

CSS: hero padding ~`96px 0`, `h1` large and tight (`font-size:clamp(2.2rem,5vw,3.4rem);line-height:1.1;letter-spacing:-0.02em;font-weight:800;max-width:18ch`), `.lead{font-size:1.15rem;color:var(--muted);max-width:60ch;margin:20px 0 32px}`, button row uses flex with gap and wraps on mobile.

- [ ] **Step 3: Verify nav and hero render and anchors work**

Run: reload `index.html` in the browser.
Expected: Sticky frosted nav at top; clicking "Get in touch" smooth-scrolls toward the (not-yet-built) contact anchor without error; hero shows headline, tagline, and two buttons. Looks clean on a narrow (mobile) window.

- [ ] **Step 4: Commit**

```bash
git add index.html
git commit -m "feat: add sticky nav and hero section"
```

---

### Task 3: Services section (3 cards)

**Files:**
- Modify: `index.html`

- [ ] **Step 1: Add the services section**

Add `<section id="services" class="section">` with a `.container`:
- A small `.eyebrow` label "WHAT WE DO" and an `<h2>` "Services".
- A `.cards` grid of three `<article class="card">` items, each with an inline SVG icon, an `<h3>`, and a `<p>`:
  - **App Development** — "Native and cross-platform iOS & Android apps, built to feel fast and reliable."
  - **Web & Cloud** — "Modern web apps and cloud-backed services that scale with your business."
  - **Product Design** — "Thoughtful UX and UI design that turns ideas into products people love to use."

- [ ] **Step 2: Style the section and cards**

CSS:
- `.section{padding:80px 0;border-top:1px solid var(--border)}`
- `.eyebrow{text-transform:uppercase;letter-spacing:.08em;font-size:.8rem;font-weight:700;color:var(--accent)}`
- `h2{font-size:clamp(1.8rem,3vw,2.4rem);font-weight:800;letter-spacing:-0.01em;margin:8px 0 8px}`
- `.cards{display:grid;grid-template-columns:repeat(3,1fr);gap:20px;margin-top:32px}`
- `.card{background:var(--bg-tint);border:1px solid var(--border);border-radius:14px;padding:26px}` with `.card h3{margin:14px 0 8px;font-size:1.15rem}` and `.card p{color:var(--muted)}`.
- Card icon: indigo SVG ~28px.
- Mobile breakpoint `@media (max-width:720px){.cards{grid-template-columns:1fr}}`.

- [ ] **Step 3: Verify services render responsively**

Run: reload `index.html`; resize the window narrow and wide.
Expected: Three cards in a row on desktop, stacked single-column under ~720px. "See what we do" / `Services` nav link scrolls here.

- [ ] **Step 4: Commit**

```bash
git add index.html
git commit -m "feat: add services section with three cards"
```

---

### Task 4: About and Contact sections

**Files:**
- Modify: `index.html`

- [ ] **Step 1: Add the about section**

Add `<section id="about" class="section">` with a `.container`:
- `.eyebrow` "ABOUT" and `<h2>` "Built in Prishtina, made for everywhere".
- One or two `<p class="prose">` paragraphs: "L in the Castle LLC is a software company that designs and builds applications for web and mobile. We partner closely with founders and teams to ship products that are well-crafted, dependable, and a pleasure to use." + "Based in Prishtina, Kosovo, we work with clients wherever they are."

CSS: `.prose{max-width:65ch;color:var(--muted);font-size:1.08rem}` with `.prose p + p{margin-top:16px}`.

- [ ] **Step 2: Add the contact section**

Add `<section id="contact" class="section contact">` with a `.container`, centered:
- `.eyebrow` "CONTACT", `<h2>` "Let's build something.", a `<p>` "Tell us about your project — we'd love to hear from you."
- A large `.btn` email button: `<a class="btn" href="mailto:info@linthecastle.com">info@linthecastle.com</a>`.
- A `<p class="muted-line">` "Prishtina, Kosovo".

CSS: `.contact{text-align:center}` , `.contact .btn{font-size:1.05rem;margin-top:24px}`, `.muted-line{color:var(--muted-2);margin-top:16px}`. Optionally give the contact section `background:var(--bg-tint)`.

- [ ] **Step 3: Verify about and contact**

Run: reload `index.html`.
Expected: About text reads well at a comfortable width; Contact is centered with a working email button (clicking opens the mail client to info@linthecastle.com) and shows "Prishtina, Kosovo". The nav "Get in touch" now lands here.

- [ ] **Step 4: Commit**

```bash
git add index.html
git commit -m "feat: add about and contact sections"
```

---

### Task 5: Footer, final polish, and full verification

**Files:**
- Modify: `index.html`

- [ ] **Step 1: Add the footer**

Add `<footer>` (outside `<main>`) with a `.container`: left side "L in the Castle LLC", right side "© 2026 L in the Castle LLC". CSS: `footer{background:#111827;color:#cbd5e1;padding:28px 0;font-size:.9rem}` with a flex `.container` that wraps and gaps on mobile.

- [ ] **Step 2: Accessibility and polish pass**

- Ensure exactly one `<h1>` (the hero).
- Confirm color contrast: body text `#4b5563` on white passes AA for body copy; footer text `#cbd5e1` on `#111827` passes.
- Confirm every interactive element is a real `<a>`/`<button>` and reachable by Tab with a visible focus ring.
- Confirm no external network requests in DevTools Network tab (everything inline).

- [ ] **Step 3: Full-page verification against the spec**

Run: open `index.html`, then in DevTools toggle a mobile device width.
Expected, all true:
- Tab title and favicon correct; meta description present (check `<head>`).
- All five sections present in order: hero, services, about, contact, footer.
- Company name, "software & mobile apps" messaging, `info@linthecastle.com`, and "Prishtina, Kosovo" all visible.
- All nav anchors smooth-scroll to the right sections.
- Layout is clean and unbroken at 375px, 768px, and 1280px widths.
- No console errors, no failed network requests.

- [ ] **Step 4: Commit**

```bash
git add index.html
git commit -m "feat: add footer and finalize accessibility polish"
```

---

### Task 6: README with deploy instructions

**Files:**
- Create: `README.md`

- [ ] **Step 1: Write `README.md`**

Create `README.md` containing:
- Title "L in the Castle" and one-line description (software company site for linthecastle.com).
- "Local preview" section: `open index.html` (or just double-click it).
- "Deploy" section explaining it is a single static file and can be hosted by dragging `index.html` onto Netlify Drop, or via Cloudflare Pages / GitHub Pages / Vercel, then pointing the `linthecastle.com` DNS at the host. Note there is no build step.

- [ ] **Step 2: Verify README renders**

Run: view `README.md` (e.g. preview in editor or `cat README.md`).
Expected: Clear, accurate instructions; no placeholders.

- [ ] **Step 3: Commit**

```bash
git add README.md
git commit -m "docs: add README with deploy instructions"
```

---

## Self-Review Notes

- **Spec coverage:** head metadata/OG/favicon (Task 1), nav + hero (Task 2), 3 services cards (Task 3), about + contact with email & location (Task 4), footer + accessibility + responsive verification (Task 5), README deliverable (Task 6). All spec sections mapped.
- **No placeholders:** every step names exact content, selectors, and concrete copy.
- **Consistency:** CSS custom property names, class names (`.btn`, `.card`, `.section`, `.eyebrow`, `.container`, `.contact`), and section IDs (`#top`, `#services`, `#about`, `#contact`) are used consistently across tasks.
