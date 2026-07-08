# MetaBrainz Internship — Engineering Case Study

A single-page engineering case study documenting the **Cross-Page User Onboarding System** built during Om Mukherjee's Software Engineering Internship at MetaBrainz Foundation (Summer 2026).

## Live site

> TODO: Add GitHub Pages URL after deployment

## Tech stack

- **[Astro](https://astro.build/)** — static site generator
- **[TailwindCSS v4](https://tailwindcss.com/)** — utility-first CSS via `@tailwindcss/vite`
- **[Shiki](https://shiki.style/)** — syntax highlighting (built into Astro)
- **[Mermaid.js](https://mermaid.js.org/)** — architecture and flow diagrams (CDN)

## Project structure

```
src/
├── pages/
│   └── index.astro         ← All content lives here (edit this to update the page)
├── layouts/
│   └── BaseLayout.astro    ← HTML shell, fonts, theme toggle, Mermaid init
├── components/
│   ├── TableOfContents.astro
│   ├── Callout.astro
│   ├── MermaidDiagram.astro
│   └── PRCard.astro
├── data/
│   └── prs.json            ← Add new PRs here
└── styles/
    └── global.css          ← Design tokens and all styles
```

## Development

```bash
npm install
npm run dev        # Start dev server at localhost:4321
npm run build      # Build static output to dist/
npm run preview    # Preview the built site
```

## Deployment

The site deploys automatically to GitHub Pages on every push to `main` via `.github/workflows/deploy.yml`.

**Setup steps (one-time):**

1. Go to your repository → **Settings** → **Pages**
2. Set **Source** to `GitHub Actions`
3. Update `site` and `base` in `astro.config.mjs`:
   ```js
   site: 'https://YOUR_USERNAME.github.io',
   base: '/YOUR_REPO_NAME',
   ```
4. Push to `main` — the workflow handles the rest.

## How to update content

### Adding a new PR

Edit `src/data/prs.json` and append a new object:

```json
{
  "number": 7,
  "title": "feat: Add Art Creator Tour",
  "description": "Implements the Art Creator Tour ...",
  "status": "merged",
  "issue": 1234,
  "merged_at": "2026-08-01",
  "url": "https://github.com/metabrainz/listenbrainz-server/pull/XXXX",
  "files": ["ArtCreatorTourManager.tsx"],
  "details": "...",
  "lessons": "..."
}
```

### Updating page content

All page content (sections, code blocks, diagrams, tables) is in `src/pages/index.astro`.
Each section is clearly delimited with HTML comments like `<!-- OVERVIEW -->`.

### Adding screenshots

1. Place images in `public/images/`
2. Add them in the Screenshots section of `src/pages/index.astro`:

```html
<img src="/YOUR_REPO_NAME/images/screenshot.png" alt="Description" style="width:100%; border-radius:8px; border: 1px solid var(--color-border);" />
```

### Adding a video embed

Replace a `video-placeholder` div with a real embed:

```html
<iframe
  src="https://www.youtube.com/embed/VIDEO_ID"
  width="100%" height="400"
  frameborder="0" allowfullscreen
  style="border-radius:8px; border: 1px solid var(--color-border);">
</iframe>
```
