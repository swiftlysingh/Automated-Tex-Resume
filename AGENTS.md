# AGENTS.md

## Cursor Cloud specific instructions

This repo is a LaTeX resume with two variants. `resume.tex` is the iOS resume
(compiles to `resume.pdf`). `resume-fde.tex` is the forward deployed engineer
variant (compiles to `resume-fde.pdf`). There is no lint or test suite.

### Build / run (dev)
- Compile iOS: `latexmk -xelatex -interaction=nonstopmode resume.tex`
- Compile FDE: `latexmk -xelatex -interaction=nonstopmode resume-fde.tex`
- Continuous preview while editing: `latexmk -xelatex -pvc resume.tex`
- Outputs are `resume.pdf` and `resume-fde.pdf` (git-ignored). To preview
  headlessly, render a PNG with
  `pdftoppm -png -r 150 -singlefile resume-fde.pdf preview` (poppler-utils).

### Non-obvious gotchas
- Must use **XeLaTeX**, not `pdflatex`. `fonts.cls` uses `fontspec` with the bundled
  fonts under `fonts/lato` and `fonts/raleway`, so `pdflatex` will fail.
- `\documentclass{fonts}` refers to the local `fonts.cls` in the repo root, not a
  CTAN package.
- A harmless "Some font shapes were not available, defaults substituted" warning is
  expected (no bold Raleway shape); the PDF still builds fine.
- `resume.xdv` is checked into git (an intermediate build artifact). Any rebuild
  rewrites it, so `git checkout -- resume.xdv` before committing to avoid noise.
  Do not add `resume-fde.xdv`. `resume.pdf`, `resume-fde.pdf`, and other
  `.aux/.log/.fls` intermediates are git-ignored.
- CI (`.github/workflows/build.yml`) compiles both `resume.tex` and
  `resume-fde.tex` via `xu-cheng/latex-action` with `latexmk_use_xelatex: true`
  and publishes both PDFs. GitHub Pages serves `Pushpinder_Resume.pdf` and
  `Pushpinder_Resume_FDE.pdf`.
