# Notes for AI agents

<!-- github-actions-disabled-note -->
## GitHub Actions is disabled in this repository

GitHub Actions is turned off for this repo in its settings (since 2026-10-21, on purpose). Nothing in `.github/workflows/` will run: no CI, tests, scheduled jobs, deploys, Dependabot or Copilot runs. Do not add or edit workflows expecting them to run, and do not re-enable Actions unless the repo owner explicitly asks.

**GitHub Pages must be deployed from a branch, never via GitHub Actions.**

- The Pages source must be **"Deploy from a branch"** (usually `gh-pages` at `/`, or `main` at `/` or `/docs`), never "GitHub Actions".
- Build the site locally (e.g. `npm run build`, `quarto render`, `mkdocs build`), then commit the built static files to the publishing branch/folder and push. Helpers such as `quarto publish gh-pages`, `mkdocs gh-deploy` or `npx gh-pages -d <dist>` do this.
- The published folder **must contain an empty `.nojekyll` file** at its root. With Actions disabled, GitHub only deploys a branch that has `.nojekyll` (Jekyll builds need Actions); without it, the site silently stops updating.
- Run builds, tests and checks locally before pushing — nothing runs on GitHub's side.

**This repo:** no GitHub Pages site is configured. If one is needed, set it up as "Deploy from a branch" as described above.
