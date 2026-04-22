# Astro Rewrite

This directory contains a standalone Astro rebuild of the current personal site. It mirrors the visible Gatsby site as it exists today:

- full-screen background image
- translucent top navigation
- portrait/profile card
- matching `404` page
- no active flight tracker

## Commands

1. Install dependencies:

   ```bash
   npm install
   ```

   Modern Astro expects a newer Node runtime than the root Gatsby app currently pins. If you are still using the root Volta toolchain, switch to Node 18+ before installing.

2. Start local development:

   ```bash
   npm run dev
   ```

3. Build for production:

   ```bash
   npm run build
   ```

4. Run Astro's project checks:

   ```bash
   npm run check
   ```

## Background Image

The background image is intentionally easy to swap.

- Default file: [`public/assets/site-background.jpg`](/Users/rsteilberg/Developer/Repositories/personal-site/astro/public/assets/site-background.jpg)
- Layout reference: [`src/layouts/SiteLayout.astro`](/Users/rsteilberg/Developer/Repositories/personal-site/astro/src/layouts/SiteLayout.astro)

To replace it, either:

1. overwrite `public/assets/site-background.jpg` with a new image using the same filename, or
2. update the `backgroundImagePath` constant in `SiteLayout.astro`

The current CSS keeps the image right-aligned on smaller screens and centered on wider screens to match the Gatsby site.

## Assets

- Avatar: [`public/assets/avatar.jpg`](/Users/rsteilberg/Developer/Repositories/personal-site/astro/public/assets/avatar.jpg)
- Favicon: [`public/assets/favicon.png`](/Users/rsteilberg/Developer/Repositories/personal-site/astro/public/assets/favicon.png)
- Resume PDF: [`public/assets/resume.pdf`](/Users/rsteilberg/Developer/Repositories/personal-site/astro/public/assets/resume.pdf)

## Notes

- Fonts are loaded from Google Fonts to match the existing Gatsby look.
- This Astro app is intentionally simple and mostly static so it is easy to maintain or extend later.
