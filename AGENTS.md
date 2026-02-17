# Repository Guidelines

## Project Structure & Module Organization
- `content/` stores site pages and posts (`content/posts/*.md`, `content/about.md`).
- `layouts/` contains Hugo templates for page shells and content rendering (`_default/baseof.html`, `index.html`, `404.html`).
- `assets/` holds pipeline assets, currently `assets/css/main.css`.
- `static/` contains files served as-is (favicons, social images, optional `CNAME`).
- `archetypes/default.md` defines default front matter for new content.
- `public/` is generated build output and should not be committed.
- `.github/workflows/hugo.yml` defines PR build checks and Pages deployment.

## Build, Test, and Development Commands
- `hugo server -D` runs the local dev server and includes draft content.
- `hugo --gc --minify` creates a production build in `public/`.
- `hugo new content posts/my-new-post.md` scaffolds a new post from the archetype.
- `hugo --gc --minify --baseURL "https://<user>.github.io/<repo>/"` mirrors CI build behavior when validating GitHub Pages paths.

## Coding Style & Naming Conventions
- Use Markdown with TOML front matter: `title`, `date`, `draft`, `description`, `tags`.
- Name post files in kebab-case (example: `writing-workflow.md`), with short, URL-friendly slugs.
- Keep template and config indentation consistent with existing files (2 spaces for nested TOML/YAML blocks).
- Keep CSS class names lowercase and hyphenated; prefer reusable variables in `:root` over hardcoded colors.

## Testing Guidelines
- There is no formal test suite yet; treat a production build as the baseline check.
- Before opening a PR, run `hugo --gc --minify` and verify no build errors.
- Smoke test locally with `hugo server -D`: home page, post page, about page, and `404` route.
- For publish-ready posts, confirm `draft = false` and correct date metadata.

## Commit & Pull Request Guidelines
- Follow the existing commit style: concise, imperative summaries (example: `Add RSS link to header`).
- Keep commits focused to one logical change (content, layout, styling, or config).
- PRs should include: purpose summary, related issue (if any), and screenshots for visible UI changes.
- Ensure GitHub Actions completes successfully on the PR before merge.

## Deployment & Configuration Notes
- `hugo.toml` keeps a placeholder `baseURL`; GitHub Actions sets the effective Pages URL during CI.
- For custom domains, add `static/CNAME` and update `baseURL` accordingly.
