# Parsa Amini — Personal Site

Hugo site for [parsaamini.github.io](https://ParsaAminpour.github.io). Single-page React app served from a Hugo shell, dark theme, dock-style floating navbar.

## Local dev

```bash
hugo server
# → http://localhost:1313
```

## Deploy

Push to `main` — GitHub Actions builds with Hugo `0.128.0` and deploys to GitHub Pages automatically.

## File map

```
hugo.toml                          # Hugo config — no theme
content/_index.md                  # Homepage stub (triggers layouts/index.html)
archetypes/default.md              # Default front matter for new content
layouts/
  index.html                       # The entire homepage — React app inline
static/
  images/
    avatar.jpg                     # Profile avatar
    logo-skatefi.png               # Work experience logos
    logo-prc.png
    logo-allinhype.png
    logo-accelerate.png
.github/workflows/hugo.yml         # Auto-deploy on push to main
```

## How to migrate from the old hugo-coder setup

1. **Replace your existing repo contents** with this folder's contents — keep the `.git/` folder.
2. Remove the `.gitmodules` file and the `themes/` submodule (no longer used).
3. Delete `resources/`, `public/`, `.hugo_build.lock` if present (build artifacts).
4. Commit and push.

```bash
# In your existing repo:
git rm --cached -r themes/
git rm .gitmodules
rm -rf themes/ resources/ public/ .hugo_build.lock

# Then copy the new files in and commit
git add .
git commit -m "Redesign: dark theme with floating dock nav"
git push origin main
```

GitHub Pages will rebuild in ~1 minute.

## Editing content

Most copy lives directly in `layouts/index.html` as JSX strings — the `experience`, `skills`, `projects`, `posts`, and `repos` arrays. Edit and push.

To make work cards data-driven from Hugo content (e.g. one markdown file per company), let me know and I'll wire it up.
