# Solutions Log

## 2026-03-04 - Create Katherine Howe GitHub Pages Migration Pilot

### Problem
- The current Katherine Howe site is hosted on Wix, and the goal is to test migration patterns without doing a full cutover yet.
- A pilot site is needed with the same core structure as the Louis Hyman migration approach (books, talks/media, events, contact) and stable static hosting.

### Solution
- Built a new standalone static site project (`katherinehowe-site`) for GitHub Pages.
- Added route structure for a migration pilot:
  - `/`
  - `/books/`
  - `/talks/`
  - `/media/` (alias page)
  - `/events/`
  - `/contact/`
  - pilot book routes (`/vanderbilt/`, `/astor/`, `/physickbook/`, `/conversion/`, `/the-house-of-velvet-and-glass/`, `/annievansinderen/`).
- Localized cover/hero images from live Wix assets into `assets/images/` for stable static rendering.
- Added GitHub Pages deployment workflow, `.nojekyll`, `robots.txt`, and `sitemap.xml`.
- Included `MIGRATION_CHECKLIST.md` to carry migration lessons into this repo.

### Outcome
- A working migration-test site is ready to publish on GitHub Pages without touching the live Wix domain.
- The pilot verifies route strategy, styling approach, and deployment flow before full migration.

## 2026-03-04 - Fix First-Run Pages Permission Failure

### Problem
- The first GitHub Actions deploy failed at `configure-pages` because the workflow attempted auto-enablement without sufficient integration permissions.

### Solution
- Created the Pages site once via GitHub API.
- Switched repository Pages `build_type` to `workflow`.
- Removed `enablement: true` from `.github/workflows/deploy-pages.yml` so future runs use the existing Pages configuration.

### Outcome
- The deployment workflow now runs against an already configured Pages site and avoids the first-run permission error.

## 2026-03-04 - Refresh Katherine Test Site to Match Live Structure and Content

### Problem
- The test build still looked like a migration pilot and did not reflect the live site's structure or tone.
- Navigation and content sections were incomplete for current needs (social links, media mentions, podcasts, and recent reviews).
- Events content from the live scrape was historical, and needed a future-only presentation.
- Several links needed validation before publishing.

### Solution
- Reworked the core pages (`/`, `/books/`, `/talks/`, `/media/`, `/events/`, `/contact/`) to match the live-site information architecture and visual direction.
- Replaced pilot messaging with production-style copy and added a new local route for `/atrueaccount/`.
- Added all requested social links: Instagram, X, Facebook, Pinterest, Substack, Goodreads, and LinkedIn.
- Added curated recent review and media links (AP, Kirkus, Publishers Weekly, Historical Novel Society, WBUR, CNN, Shelf Awareness) and recent podcast links (Apple Podcasts and Best of Women's Fiction).
- Switched the events page to future-only behavior by removing past listings and showing a "no current public events" state.
- Ran internal and external link checks to remove or avoid broken URLs.

### Outcome
- The GitHub Pages test site now presents as a clean, real-site-style static build rather than a migration scaffold.
- Core content sections and social/media coverage are in place with verified links.
- Past events are no longer surfaced.
