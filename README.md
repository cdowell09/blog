# Lean Hugo Blog

Minimal static blog setup using Hugo + GitHub Pages.

## Requirements

- Hugo Extended (`>= 0.155.3` tested)

## Run locally

```bash
hugo server -D
```

Open `http://localhost:1313`.

## Build production output

```bash
hugo --gc --minify
```

Generated files are written to `public/`.

## Writing posts

Create a new post:

```bash
hugo new content posts/my-new-post.md
```

Set `draft = false` in front matter when ready to publish.

## GitHub Pages deployment

This repo includes `.github/workflows/hugo.yml` that:

- Builds on pull requests (validation)
- Builds and deploys on push to `main` or `master`
- Uses `actions/configure-pages` so `baseURL` is set correctly for:
  - User/org repos: `https://<user>.github.io/`
  - Project repos: `https://<user>.github.io/<repo>/`

In GitHub repo settings:

1. Go to **Settings > Pages**.
2. Set **Source** to **GitHub Actions**.

## `baseURL` and custom domain

- `hugo.toml` keeps a placeholder `baseURL` for local/default builds.
- CI overrides `baseURL` automatically with the correct Pages URL.
- For a custom domain, set your DNS and update `baseURL` in `hugo.toml` to your domain (for example, `https://blog.example.com/`).
- If using a custom domain on GitHub Pages, add `static/CNAME` with your domain name.
