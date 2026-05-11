# AI Research — GitHub Pages Site

## Files in this package

```
index.html          ← Main website (edit article text inside)
sitemap.xml         ← Google sitemap (update your username/URL)
robots.txt          ← Allows Google to index PDFs
README.md           ← This file
```

## Setup Instructions

### 1. Create your GitHub Pages repo
- Create a repo named `yourusername.github.io` (replace with your GitHub username)
- Go to Settings → Pages → Source: Deploy from branch → `main` / `root`

### 2. Add your PDFs
- Create a folder called `pdfs/` in the repo
- Upload your 3 PDF files with these exact names:
  - `pdfs/warfare.pdf`
  - `pdfs/neural-networks.pdf`
  - `pdfs/synthetic-data.pdf`

### 3. Add your article text
- Open `index.html`
- Search for the 3 placeholder comments:
  - `<!-- PASTE YOUR WARFARE ARTICLE TEXT BELOW -->`
  - `<!-- PASTE YOUR NEURAL NETWORKS ARTICLE TEXT BELOW -->`
  - `<!-- PASTE YOUR SYNTHETIC DATA ARTICLE TEXT BELOW -->`
- Replace the placeholder `<p>` tags with your real article content
- Use `<h2>` for section headings, `<h3>` for sub-labels, `<p>` for paragraphs
- Use `<blockquote><p>` for pull quotes

### 4. Update your URL everywhere
Replace `yourusername.github.io` with your actual GitHub Pages URL in:
- `index.html` → the `<link rel="canonical">` and `og:url` tags
- `sitemap.xml` → all `<loc>` entries
- `robots.txt` → the `Sitemap:` line

### 5. Submit to Google Search Console
- Go to https://search.google.com/search-console
- Add your site property
- Submit `https://yourusername.github.io/sitemap.xml`
- This tells Google to index your HTML page AND your 3 PDFs

## PDF Google Indexing Tips
- PDFs must be text-based (not scanned images) for Google to read them
- The `robots.txt` already allows crawling of `/pdfs/`
- The `sitemap.xml` lists each PDF as its own URL
- Google typically indexes PDFs within 1–4 weeks of submission

## Customization
- Your name/brand: find `AI/Research` in the nav and footer, replace with yours
- Article titles: find `AI & the Future of Warfare` etc. and update
- Colors: edit `:root` CSS variables at the top of `index.html`
  - `--accent: #00e5c0` — the cyan highlight color
  - `--bg: #080a0c` — the background
