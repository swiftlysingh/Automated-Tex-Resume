# AGENTS.md

## Cursor Cloud specific instructions

This repo is a single-file LaTeX resume. The "application" is `resume.tex`, which
compiles to `resume.pdf`. There is no lint or test suite.

### Build / run (dev)
- Compile: `latexmk -xelatex -interaction=nonstopmode resume.tex`
- Continuous preview while editing: `latexmk -xelatex -pvc resume.tex`
- Output is `resume.pdf` (git-ignored). To preview headlessly, render a PNG with
  `pdftoppm -png -r 150 -singlefile resume.pdf preview` (poppler-utils).

### Non-obvious gotchas
- Must use **XeLaTeX**, not `pdflatex`. `fonts.cls` uses `fontspec` with the bundled
  fonts under `fonts/lato` and `fonts/raleway`, so `pdflatex` will fail.
- `\documentclass{fonts}` refers to the local `fonts.cls` in the repo root, not a
  CTAN package.
- A harmless "Some font shapes were not available, defaults substituted" warning is
  expected (no bold Raleway shape); the PDF still builds fine.
- `resume.xdv` is checked into git (an intermediate build artifact). Any rebuild
  rewrites it, so `git checkout -- resume.xdv` before committing to avoid noise.
  `resume.pdf` and other `.aux/.log/.fls` intermediates are git-ignored.
- CI (`.github/workflows/build.yml`) compiles the same file via
  `xu-cheng/latex-action` with `latexmk_use_xelatex: true` and publishes the PDF.
