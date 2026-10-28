# Bulldog Silicon Website

## Local preview

```bash
python -m venv .venv
source .venv/bin/activate  # macOS/Linux; on Windows use .venv\\Scripts\\activate
pip install -r requirements.txt
mkdocs serve
```

Open http://127.0.0.1:8000/.

## Publish

1. Create the GitHub organization and public repository `bulldog-silicon.github.io` (if available).
2. Upload all files, including the hidden `.github/workflows/deploy.yml` directory, to the repository's `main` branch. Keep directory structure intact.
3. Go to repository Settings → Pages → Build and deployment → Source: GitHub Actions.
4. Push a commit to `main` (or run the deploy workflow manually in Actions).
5. View site at https://bulldog-silicon.github.io/ (if using that organization and repository).

The website URL in `mkdocs.yml` assumes that precise organization/repository name. Change `site_url` if yours differs.

## Customize

Edit Markdown files in `docs/` to update pages, and `mkdocs.yml` for navigation. All changes pushed to `main` trigger a rebuild.

This is a starter scaffold. Meeting location, link to enrollment form, PDK/toolchain and detailed labs are placeholders until confirmed.
