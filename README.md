# ai-encyclopedia

> Live site: [nathanreitinger.github.io/ai-encyclopedia](https://nathanreitinger.github.io/ai-encyclopedia/)

---

## Table of Contents

- [Overview](#overview)
- [Site Architecture](#site-architecture)
- [Design System](#design-system)
- [File Structure](#file-structure)
- [Deployment](#deployment)
- [The Book](#the-book)
- [Author](#author)

---

## Overview

This repository hosts a single-page web application that presents three pre-publication draft chapters in the *Elgar Concise Encyclopedia of Artificial Intelligence and Law*. The chapters cover three of the most consequential intersections of AI and law: How neural networks work at a foundational level; how autonomous weapons systems are governed under international law; and how synthetic data navigates the tension between machine learning utility and privacy protection.

---
## Site Architecture

The entire site is a single HTML file with no external JavaScript dependencies and no build pipeline. All three article pages and the home/index page live inside this one document, with visibility toggled via a small inline script.

**Navigation model:** JavaScript functions (`showArticle(id)` and `showHome()`) set `display: none` and `display: block` on four top-level `<div>` containers — `#home`, `#article-neural`, `#article-warfare`, and `#article-synthetic` — and scroll the window to the top on each transition. An `IntersectionObserver` drives staggered fade-in animations on `.fade-in` elements.

**No routing:** There are no URL changes on navigation. All state is in the DOM. Refreshing the page always returns to the home view.

**No dependencies:** The only external resources loaded at runtime are three Google Fonts families (Cormorant Garamond, Instrument Sans, JetBrains Mono), a single Amazon SVG icon from jsDelivr, and the PDF files hosted in the `pdfs/` directory.

---

## Design System

The visual language is deliberately editorial — modeled on literary magazines and high-end longform journalism rather than documentation sites or developer portfolios. All design tokens are defined as CSS custom properties on `:root`.

**Color palette (dark mode only):**

| Token | Value | Role |
|---|---|---|
| `--ink` | `#e8e2d9` | Primary text |
| `--ink-muted` | `#8a8278` | Secondary text, excerpts |
| `--ink-dim` | `#4a4640` | Tertiary, metadata |
| `--paper` | `#0d0c0b` | Base background |
| `--paper-2` | `#141311` | Slightly elevated surfaces |
| `--paper-3` | `#1a1916` | Cards, notices |
| `--accent` | `#c9a96e` | Gold — primary accent, links, drop caps |
| `--accent-2` | `#8fb8a0` | Sage green — secondary topic labels |

**Typography:**

- `Cormorant Garamond` (serif) — body text, headlines, drop caps. Weights 300, 400, 500, 600; italic variants.
- `Instrument Sans` (sans-serif) — navigation, labels, metadata, UI chrome. Weights 400, 500.
- `JetBrains Mono` (monospace) — wordmark, topic tags, issue numbers, date strings.

**Layout:** CSS Grid throughout. The home page uses a `1.4fr 1fr` asymmetric grid for the featured/secondary article split. Article headers use a `1fr 1fr` two-column layout. A `--max: 760px` variable governs article body width; `--wide: 1100px` governs full-bleed container width. The masthead is `position: sticky` with a backdrop blur.

**Article typography details:** First paragraphs use a CSS `::first-letter` drop cap rendered at 5.5rem in the accent gold. Pull quotes use a 2px left border in the accent color. Sections use a centered ornament character with wide letter-spacing.

**Responsive breakpoint:** A single `@media (max-width: 768px)` rule collapses all grids to single-column, hides the masthead navigation, and reduces padding. The Amazon link notice also reflows to a stacked column layout.

---

## File Structure

```
ai-encyclopedia/
├── .github/
│   └── workflows/          # GitHub Actions (Pages deployment)
├── pdfs/
│   ├── neural-networks.pdf
│   ├── warfare.pdf
│   └── synthetic-data.pdf
├── google4cbf193f52acb771.html   # Google Search Console verification
├── index.html                    # Entire site — all pages, all styles, all JS
├── neural-networks.pdf           # Root-level copy (legacy or direct link)
├── robots.txt                    # Crawl directives
└── sitemap.xml                   # XML sitemap for search engines
```

The `pdfs/` directory holds the downloadable versions of each chapter, linked from both the article cards on the home page and the individual article headers. A root-level `neural-networks.pdf` also exists, likely a direct-link copy predating the `pdfs/` subdirectory.

The `robots.txt` and `sitemap.xml` are present for standard search engine discoverability. The Google Search Console verification file (`google4cbf193f52acb771.html`) confirms domain ownership for Google's indexing tools.

---

## Deployment

The site is deployed automatically via GitHub Actions to GitHub Pages from the `main` branch. The workflow file lives in `.github/workflows/`. No build step is required — the output is the source. GitHub Pages serves `index.html` directly at the repository's Pages URL.

To run locally, no tooling is required beyond a web browser:

```bash
git clone https://github.com/nathanReitinger/ai-encyclopedia.git
cd ai-encyclopedia
open index.html   # or python3 -m http.server for local font loading
```

Google Fonts will not load over `file://` in some browsers due to CORS restrictions. Serving via a local HTTP server resolves this.

---

## The Book

These chapters are pre-publication drafts. The final, peer-reviewed versions appear in:

**Elgar Concise Encyclopedia of Artificial Intelligence and Law**
Publisher: Edward Elgar Publishing
ISBN: 978-1035336890

The encyclopedia is a comprehensive reference work covering the legal dimensions of artificial intelligence across dozens of entries. 

The volume is available for purchase [on Amazon](https://www.amazon.com/Elgar-Concise-Encyclopedia-Artificial-Intelligence/dp/1035336898).

---

## Author

**Nathan Reitinger** is the Empirical Fellow in Law and Computer Science at Northwestern Pritzker School of Law. His research integrates empirical and technical methods to study privacy, artificial intelligence, and the regulation of digital technologies.

Faculty profile: [law.northwestern.edu/faculty/profiles/nathanreitinger](https://www.law.northwestern.edu/faculty/profiles/nathanreitinger/)
