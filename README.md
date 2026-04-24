# personal-site-2

This repository is the active Astro-based version of my personal site.

## Tech Stack

- [Astro](https://astro.build/)
- plain CSS in [`src/styles/global.css`](/Users/rsteilberg/Developer/Repositories/personal-site-2/src/styles/global.css)
- Vercel Analytics and Speed Insights in [`src/layouts/SiteLayout.astro`](/Users/rsteilberg/Developer/Repositories/personal-site-2/src/layouts/SiteLayout.astro)

## Commands

Install dependencies:

```bash
npm install
```

Start local development:

```bash
npm run dev
```

Run Astro's checks:

```bash
npm run check
```

Create a production build:

```bash
npm run build
```

Preview the production build:

```bash
npm run preview
```

## Background Images

The site picks a random background image on each page load.

To change the set of backgrounds:

1. Add or replace files in [`public/assets`](/Users/rsteilberg/Developer/Repositories/personal-site-2/public/assets)
2. Update the `backgroundImagePaths` array in [`src/layouts/SiteLayout.astro`](/Users/rsteilberg/Developer/Repositories/personal-site-2/src/layouts/SiteLayout.astro)

## Flight Ribbon

The homepage includes a live flight ribbon implemented in [`src/components/FlightRibbon.astro`](/Users/rsteilberg/Developer/Repositories/personal-site-2/src/components/FlightRibbon.astro).

Set these environment variables to connect it to the live feed:

- `PUBLIC_SERVE1090_URL`
- `PUBLIC_SERVE1090_TOKEN`

See [.env.template](/Users/rsteilberg/Developer/Repositories/personal-site-2/.env.template).

If the environment variables are missing or the feed is offline, the ribbon should still render safely and fall back to the empty state.

## Notes

- Background images are optimized `.webp` files for performance.
- Future agent guidance lives in [AGENTS.md](/Users/rsteilberg/Developer/Repositories/personal-site-2/AGENTS.md).
