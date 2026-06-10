# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is the **Wecoden** marketing website (wecoden.com) — a static HTML/CSS/JS site originally designed and exported from **Webflow**. It is served via **GitHub Pages** (CNAME points to wecoden.com). There is no build system, package manager, or backend.

## Local Development

The site runs under **MAMP** at `/Applications/MAMP/htdocs/wecoden2`. Open MAMP and start the servers to serve it locally. No build step is required — open any `.html` file directly in a browser or via MAMP's local server.

## Deployment

Push to the `main` branch on the remote `wecoden-site` (GitHub) to deploy. GitHub Pages serves the root of the repo automatically.

```bash
git push wecoden-site main
```

## Site Structure

| Path | Description |
|------|-------------|
| `index.html` | Home page |
| `about-us.html` | About Us page |
| `services.html` | Services overview page |
| `contact-us.html` | Contact page |
| `services-posts/*.html` | 10 individual service detail pages |
| `css/` | Single shared Webflow stylesheet |
| `js/` | Webflow runtime chunks, GSAP, jQuery, Lottie JSON |
| `images/` | Locally hosted images (some assets load from Webflow CDN) |

## Architecture Notes

**Webflow origin:** HTML files are Webflow exports (annotated `<!-- Handled by Exflow.site -->`). Structural/layout changes should ideally be made in the Webflow designer and re-exported. Manual HTML edits are fine for content, links, and meta tags.

**Navigation is duplicated:** The navbar (including the full dropdown with all service links) is copy-pasted into every `.html` file. When adding or changing navigation links, update all pages.

**Asset paths in service posts:** Files under `services-posts/` use relative paths (`../css/`, `../js/`) for stylesheets and scripts, while root-level pages use `css/` and `js/` directly. Keep this distinction when copying page templates.

**JS libraries loaded locally:**
- `gsap.min.js`, `splittext.min.js`, `scrolltrigger.min.js` — GSAP animation suite
- `jquery.js` — jQuery
- `webflow-script.js` (and numbered variants) — minified Webflow interaction/animation bundles (do not edit by hand)
- `webflow.schunk.*.js` — Webflow runtime chunks (do not edit)
- `lottieflow-menu-nav-06-000000-easey-20-1-.json` — Lottie animation for the hamburger menu icon

**Images:** Static images live in `images/`. Many images (logos, hero graphics) are served from `cdn.prod.website-files.com` (Webflow CDN) and are not stored in this repo.

**Font:** JetBrains Mono loaded via Google Fonts WebFont loader on every page.
