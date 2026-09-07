# BmRadio Landing Page

This is a static, no-build website. The simplest and most reliable hosting setup is
GitHub Pages deployed directly from the `main` branch.

## Recommended GitHub Pages setup

1. Push the complete repository to `main`. Keep `index.html`, `.nojekyll`, the legal
   pages, `terms.html`, `404.html`, and all PNG assets in the repository root.
2. Open **Settings → Pages** in GitHub.
3. Set **Source** to **Deploy from a branch**.
4. Select branch `main` and folder `/ (root)`, then click **Save**.
5. GitHub will publish the site at
   `https://izyaboi.github.io/bmradio-landing/`.

This approach is preferable here to a build workflow because there is no framework,
dependency installation, or compilation step. Every push to `main` is published as-is.

## Custom domain

For a custom domain, add a root-level `CNAME` file containing only the domain name,
then configure the domain's DNS records as GitHub describes in **Settings → Pages**.
Enable **Enforce HTTPS** after DNS verification completes.

## Deployment checklist

- `index.html` is lowercase and at the repository root.
- `404.html` provides a branded fallback for unknown routes.
- `terms.html` provides the bilingual Terms of Use page.
- `.nojekyll` is committed; it prevents Jekyll from interpreting the embedded script.
- `impressum.html`, `privacy.html`, `bmradio-logo.png`, `bmradio-texture.png`, and
  `bmradio-hero.png` are committed alongside the homepage.
- Replace the bracketed provider and contact details in `impressum.html` before launch.
- Test the published homepage and both legal-page links after the first deployment.

## Why `.nojekyll` matters

The bundled `index.html` contains `{{` inside an embedded script. Jekyll treats that
sequence as Liquid syntax, so the empty `.nojekyll` file ensures GitHub serves the
static files directly.
