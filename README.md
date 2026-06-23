# OBI - Ontological Bayesian Intelligence

OBI means Ontological Bayesian Intelligence. It is an ontological and Bayesian reasoning infrastructure for uncertainty-aware robotic and humanitarian systems.

The repository contains a static documentation toolchain that converts plain text, Markdown, LaTeX, and BibTeX source material into consistent HTML pages, a client-side search index, bibliography outputs, and static publishing artifacts.

## What OBI Is Not

OBI should not be described as conscious AI. It is not a claim of machine consciousness, sentience, or personhood. The project language should stay focused on reasoning infrastructure, uncertainty modeling, ontologies, Bayesian inference, semantic graphs, robotics interfaces, and humanitarian real-world assistance systems.

## Repository Layout

```text
.
├── .circleci/
├── .github/workflows/
├── docs/
│   ├── archive/
│   ├── public/
│   └── source/
├── nw/
├── obi/
├── scripts/
├── package.json
├── pyproject.toml
└── README.md
```

Source documents live under `docs/source`. Generated static output is written to `docs/public`. Research ZIP bundles are preserved under `docs/archive`.

## Install

Node.js is used for the documentation build. Python remains available for future research tooling and the package is still installable.

```powershell
npm install
pip install -e .
```

The Node build currently has no external runtime dependencies, so it is easy to run from PowerShell and CI.

## Documentation Commands

```powershell
npm run clean
npm run docs:build
npm run docs:validate
npm run docs:serve
npm run publish:check
```

`npm run docs:build` generates:

- `docs/public/index.html`
- `docs/public/papers.html`
- `docs/public/bibliography.html`
- `docs/public/search.json`
- `docs/public/sitemap.xml`
- `docs/public/robots.txt`
- `docs/public/manifest.json`
- `docs/public/assets/obi.css`
- `docs/public/assets/obi.js`

## Source Formats

Place source files in these folders:

- `.tex` in `docs/source/tex`
- `.bib` in `docs/source/bib`
- `.md` in `docs/source/md`
- `.txt` in `docs/source/txt`
- images and diagrams in `docs/source/assets`

The build converts source pages into static HTML under `docs/public/sources`.

## LaTeX and MiKTeX Notes

The HTML build does not require MiKTeX. The Node converter handles common LaTeX structures directly, including titles, authors, abstracts, sections, lists, citations, labels, references, and TeX math blocks.

Math syntax is preserved and rendered in HTML with MathJax. If a local TeX toolchain such as MiKTeX, `pdflatex`, `xelatex`, or `bibtex` is installed, it can be added later as an optional PDF build path without blocking the static HTML pipeline.

## BibTeX Notes

BibTeX files belong in `docs/source/bib`. The build generates `docs/public/bibliography.html` and `docs/public/bibliography.json`.

LaTeX citations are linked when the citation key exists in the loaded BibTeX entries. Missing keys are shown as unresolved citations but do not fail the build.

## NW.js / Node-Webkit Notes

The desktop wrapper lives in `nw/package.json` and points at `../docs/public/index.html`.

```powershell
npm run docs:build
npm run nw:start
```

The user-facing phrase may be node-webkit, but the implementation uses modern NW.js naming.

## CircleCI

CircleCI installs Node.js dependencies, cleans generated docs, builds the static site, validates required outputs, and stores `docs/public` as an artifact.

## GitHub Pages Publishing

The GitHub Actions workflow in `.github/workflows/publish.yml` runs on pushes to `main`, builds the documentation, validates it, uploads `docs/public` as a Pages artifact, and deploys it to GitHub Pages.
