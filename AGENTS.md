# AGENTS.md

## Project Snapshot

- This is the active Astro-based replacement for the old Gatsby personal site.
- The site is intentionally small and mostly static:
  - homepage at [`src/pages/index.astro`](/Users/rsteilberg/Developer/Repositories/personal-site-2/src/pages/index.astro)
  - custom 404 at [`src/pages/404.astro`](/Users/rsteilberg/Developer/Repositories/personal-site-2/src/pages/404.astro)
- The visible homepage currently has three main sections:
  - top nav
  - profile card
  - live flight ribbon

## Tooling And Runtime

- Framework: Astro 6
- Package manager: `npm`
- Runtime declared in [`package.json`](/Users/rsteilberg/Developer/Repositories/personal-site-2/package.json):
  - Node `^24.15.0`
- Preferred local toolchain is also pinned via Volta in [`package.json`](/Users/rsteilberg/Developer/Repositories/personal-site-2/package.json):
  - Node `24.15.0`
  - npm `11.12.1`
- Useful scripts:
  - `npm run dev`
  - `npm run build`
  - `npm run preview`
  - `npm run check`

## Important Structure

- [`src/layouts/SiteLayout.astro`](/Users/rsteilberg/Developer/Repositories/personal-site-2/src/layouts/SiteLayout.astro)
  - global page wrapper
  - SEO/meta tags
  - Vercel Analytics and Speed Insights
  - random background-image selection logic
- [`src/styles/global.css`](/Users/rsteilberg/Developer/Repositories/personal-site-2/src/styles/global.css)
  - almost all visual styling lives here
  - includes nav, profile card, 404, and flight ribbon styles
- [`src/components/Header.astro`](/Users/rsteilberg/Developer/Repositories/personal-site-2/src/components/Header.astro)
  - top navigation links
- [`src/components/ProfileCard.astro`](/Users/rsteilberg/Developer/Repositories/personal-site-2/src/components/ProfileCard.astro)
  - avatar and text block
- [`src/components/FlightRibbon.astro`](/Users/rsteilberg/Developer/Repositories/personal-site-2/src/components/FlightRibbon.astro)
  - client-side WebSocket-driven aircraft ribbon
- [`public/assets`](/Users/rsteilberg/Developer/Repositories/personal-site-2/public/assets)
  - avatar, favicon, resume, and background images

## Background Images

- Backgrounds are selected randomly on each page load in [`src/layouts/SiteLayout.astro`](/Users/rsteilberg/Developer/Repositories/personal-site-2/src/layouts/SiteLayout.astro).
- Current active background pool:
  - `site-background-1.webp`
  - `site-background-2.webp`
  - `site-background-3.webp`
  - `site-background-4.webp`
  - `site-background-5.webp`
  - `site-background-6.webp`
- The layout sets a fallback `--site-background-image` on `<body>`, then overrides it after `.site-shell` exists.
- If changing the randomizer, be careful about timing:
  - setting the CSS variable from a `<head>` script was previously too early
  - the working version updates `.site-shell` after it is present in the DOM
- The live asset set in [`public/assets`](/Users/rsteilberg/Developer/Repositories/personal-site-2/public/assets) currently uses only the `.webp` background variants.

## Images

- Avatar:
  - [`public/assets/avatar.jpg`](/Users/rsteilberg/Developer/Repositories/personal-site-2/public/assets/avatar.jpg)
  - intentionally resized to `512x512`
- Background images:
  - optimized full-screen assets in `public/assets`
  - current `.webp` files are the ones used by the site
- If changing image assets, preserve the current visual feel unless the task is explicitly a redesign.
- If adding new randomized backgrounds, update the `backgroundImagePaths` array in [`src/layouts/SiteLayout.astro`](/Users/rsteilberg/Developer/Repositories/personal-site-2/src/layouts/SiteLayout.astro).

## Flight Ribbon

- The flight ribbon is intentionally client-side and tolerant of the feed being offline.
- Environment variables:
  - `PUBLIC_SERVE1090_URL`
  - `PUBLIC_SERVE1090_TOKEN`
- There is also fallback support for legacy names:
  - `GATSBY_SERVE1090_URL`
  - `GATSBY_SERVE1090_TOKEN`
- Behavior expectations:
  - if env vars are missing, the ribbon should still render safely
  - if the socket fails, the ribbon should reset to the empty state and retry
  - the empty state is `none in range`
- If editing [`src/components/FlightRibbon.astro`](/Users/rsteilberg/Developer/Repositories/personal-site-2/src/components/FlightRibbon.astro), be careful with:
  - browser-only APIs
  - reconnect cleanup
  - direct `innerHTML` rendering of aircraft links

## Styling Notes

- This repo does not use Tailwind. Styling is plain CSS in [`src/styles/global.css`](/Users/rsteilberg/Developer/Repositories/personal-site-2/src/styles/global.css).
- The current design intentionally mirrors the old site:
  - serif typography
  - white text
  - translucent header and ribbon bars
  - full-screen photographic background
- Small spacing and typography shifts are visually noticeable here. Prefer careful, minimal changes.

## Verification

- Standard verification:
  - `npm run build`
- Additional useful check:
  - `npm run check`
- For visual changes, manually review:
  - homepage
  - 404 page
  - random background behavior across reloads
  - flight ribbon with and without env vars configured

## Known Gotchas

- Do not assume background randomization is purely server-side; it currently happens client-side after load.
- The repo includes Vercel analytics integrations in the layout. Preserve them unless asked to remove them.
- If tightening `engines.node`, remember the local machine may still be on a different installed Node version and npm will warn accordingly.
- README and AGENTS should stay aligned on:
  - Node version expectations
  - current background pool
  - flight ribbon env vars
