# BmRadio Landing Page

Static single-file landing page. No build step.

## GitHub Pages

1. Create a repo (or use an existing one) and copy `index.html` + `.nojekyll` into its **root**.
2. Commit and push to `main`.
3. Repo → **Settings → Pages** → Source: **Deploy from a branch**, Branch: `main`, Folder: `/ (root)` → Save.
4. Wait ~1 min. URL: `https://<user>.github.io/<repo>/`

### Why builds were failing
`index.html` contains `{{` inside an inlined script. GitHub Pages runs Jekyll by default and its Liquid
templating treats `{{ }}` as a tag, which aborts the build. The empty `.nojekyll` file at the repo root
disables Jekyll entirely and serves the files as-is. **It must be committed** — check with
`git status --ignored` if it seems missing (dotfiles are easy to skip when copying).

### Other things that break Pages
- Pages source never set (Settings → Pages).
- File committed as `Index.html` or nested in a subfolder that isn't the selected Pages folder.
- Private repo on a free plan — Pages requires public (or Pro).
- Landing page dropped into the Kotlin app repo root: fine, but keep `.nojekyll` there too.

## Alternative: Actions workflow
If you prefer a workflow over branch deploys, use `.github/workflows/pages.yml` from this folder.
