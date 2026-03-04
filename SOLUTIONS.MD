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
