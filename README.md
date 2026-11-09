# frasalvi.github.io

> **Living document** — current state only. No history, decision-rationale, or which-subtask-did-what notes; keep it current.

Source for [frasalvi.github.io](https://frasalvi.github.io), Francesco Salvi's personal website. Built with Jekyll on the [al-folio](https://github.com/alshedivat/al-folio) theme (MIT, see `LICENSE`).

## Deploy

Pushes to `master` trigger the `deploy` GitHub Actions workflow, which builds the site, runs PurgeCSS on `assets/css`, and pushes `_site` to the `gh-pages` branch that GitHub Pages serves. Pull requests run the same build without deploying. There is no local build setup.

## Where things live

- `_pages/`: top-level pages (about, publications, media, projects, CV redirect).
- `_bibliography/papers.bib`: publications list.
- `_media/`: press coverage entries shown on the media page.
- `_projects/`: past project cards.
- `assets/`: images, PDFs, CSS, and JS. ImageMagick generates responsive `.webp` copies of images in `assets/img/` at build time.
