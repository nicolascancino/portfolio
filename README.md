# nicolascancino.dev

Personal site / portfolio. Astro + Tailwind, deployed on Cloudflare Pages.

## Stack

- [Astro 6](https://astro.build) — content-first SSG with optional islands
- [Tailwind CSS v4](https://tailwindcss.com) via `@tailwindcss/vite`
- [Newsreader](https://fonts.google.com/specimen/Newsreader) (serif headings) + [Inter](https://rsms.me/inter/) (body) + [JetBrains Mono](https://www.jetbrains.com/lp/mono/) (code) — bundled via `@fontsource`

## Develop

Requires Node ≥ 22.12.

```bash
npm install
npm run dev      # local dev server on :4321
npm run build    # static build to ./dist
npm run preview  # serve the built site
```

## Deploy

- Production: Cloudflare Pages, auto-deploys on push to `main`.
- Custom domain: configured in CF Pages → Custom domains.

## Structure

```
src/
├── layouts/Layout.astro       HTML shell, fonts, meta
├── components/
│   ├── Section.astro          page section wrapper (label + title + slot)
│   └── WorkCard.astro         project case-study card
├── pages/index.astro          single-page site
└── styles/global.css          Tailwind + @theme tokens

public/favicon.svg             monogram favicon
```

## Editorial light theme

Off-white `#FAFAF9` background, near-black `#0A0A0A` text, electric blue
`#2563EB` accent. Serif (Newsreader) for headings, sans (Inter) for body,
mono (JetBrains Mono) for code and section labels.
