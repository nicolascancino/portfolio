# nicolascancino.dev

Personal site / portfolio. Astro + Tailwind, deployed on Cloudflare Pages.

**Live**: https://nicolascancino-portfolio.pages.dev — will move to `https://nicolascancino.dev` once the domain is purchased and connected.

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

Two paths to deploy:

### Option A — Manual deploy from local (current state)

```bash
npm run build
npx wrangler pages deploy dist --project-name=nicolascancino-portfolio --branch=main
```

Requires `wrangler login` once.

### Option B — Auto-deploy from GitHub Actions (recommended)

The workflow at `.github/workflows/deploy.yml` builds + deploys on every push to `main`. To enable it:

1. Repo **Settings → Environments** → create environment `production`.
2. Add Environment secrets:
   - `CLOUDFLARE_API_TOKEN` — same token used by ambrocito/danig (Workers Scripts: Edit + Pages: Edit + Account: Read).
   - `CLOUDFLARE_ACCOUNT_ID` — `1a48112162681bc58a10371b716bfcde`.
3. Push any commit to `main` → workflow runs → deploys.

The `nicolascancino-portfolio` Pages project already exists (created via `wrangler pages project create`). The workflow only needs the secrets to authenticate.

## Custom domain (when ready)

After purchasing `nicolascancino.dev`:

1. Cloudflare Dashboard → Pages → `nicolascancino-portfolio` → **Custom domains** → Add → enter the domain.
2. CF auto-provisions DNS + SSL.
3. Update `astro.config.mjs` `site:` field to the custom URL so canonical/OG links match.

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
.github/workflows/deploy.yml   CF Pages auto-deploy
```

## Editorial light theme

Off-white `#FAFAF9` background, near-black `#0A0A0A` text, electric blue `#2563EB` accent. Serif (Newsreader) for headings, sans (Inter) for body, mono (JetBrains Mono) for code and section labels.
