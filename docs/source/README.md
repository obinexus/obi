# OBI Source Documentation

This folder contains source material for the OBI documentation build. Generated files are written to `docs/public`; do not edit generated HTML by hand.

## Where Files Go

- Put LaTeX papers in `docs/source/tex`.
- Put BibTeX files in `docs/source/bib`.
- Put Markdown notes in `docs/source/md`.
- Put plain text transcripts or notes in `docs/source/txt`.
- Put images, diagrams, and other web assets in `docs/source/assets`.
- Put older research ZIP bundles in `docs/archive`.

## Build

```powershell
npm run docs:build
```

The build creates static HTML, `search.json`, `bibliography.html`, `bibliography.json`, `sitemap.xml`, `robots.txt`, `manifest.json`, and the shared CSS/JavaScript assets.

## Serve Locally

```powershell
npm run docs:serve
```

The local server starts at `http://127.0.0.1:4173/` by default and automatically tries the next available port if needed.

## Add a New Paper

1. Add the `.tex` file to `docs/source/tex`.
2. Add references to a `.bib` file in `docs/source/bib`.
3. Put any images in `docs/source/assets`.
4. Run `npm run docs:build`.
5. Run `npm run docs:validate`.

## Citations

The LaTeX converter resolves `\cite{}`, `\citep{}`, and `\citet{}` keys against BibTeX entries found in `docs/source/bib`. Resolved citations link to `bibliography.html`. Missing keys are shown as unresolved but do not fail the build.

## MathJax

Inline math written as `\( ... \)` and display math written as `\[ ... \]`, `equation`, or `align` environments is preserved as TeX and rendered in HTML through MathJax.

## Source Preservation

The build reads from `docs/source` and `docs/archive`. It cleans only generated files under `docs/public`, so original source material remains preserved.
