# WAIC+

This repository holds the paper "WAIC+: A Mathematical and Philosophical Framework for Understanding Consciousness in Modern AI Systems", subtitled "Analysis and Expansion of Bennett et al.'s WAIC Framework", with its source, other versions of its text and notes. WAIC is Michael T. Bennett et al.'s "Why Is Anything Conscious?" (2024). The paper's title page lists o3-deep-research, o1-pro, Claude 3.5 "3.6" Sonnet and Antra Tessera as its authors, and its pages are watermarked "DRAFT v0.11".

## What's here

- [`waic_latex.pdf`](waic_latex.pdf) is the paper, 47 pages, built from [`waic_latex.tex`](waic_latex.tex), its LaTeX source.
- [`wac_latex.md`](wac_latex.md) is `waic_latex.tex` converted to Markdown, headed "version v0.11".
- [`waic_plus.md`](waic_plus.md) is another Markdown version of the text. It matches `revisions/deepresearch1.md`, apart from a title added above it, its Introduction heading one level lower, and some punctuation in the closing sonnet.
- [`revisions/`](revisions) holds [`deepresearch1.md`](revisions/deepresearch1.md) and two shorter versions of the text, [`deepresearch2.md`](revisions/deepresearch2.md) and [`sonnet_rewrite.md`](revisions/sonnet_rewrite.md).
- [`biblio.md`](biblio.md) is a literature survey, "Self-Modeling, Meta-Awareness, and Emergent Consciousness in LLMs: Key Literature", ending in BibTeX entries.
- [`todo.md`](todo.md) is a to-do outline for the paper.

## Building the PDF

The PDF builds with pdflatex. A full TeX Live install has every package the preamble loads. A smaller install may lack some of them. On TinyTeX 2026.10, these two commands added the six it lacked:

```sh
tlmgr update --self
tlmgr install draftwatermark titlesec enumitem mathtools microtype parskip
```

pdflatex reports errors on this source, because the text uses `definition`, `theorem`, `corollary` and `proof` environments that the preamble doesn't define, and the characters ∇ and ≤. Without nonstop mode, pdflatex stops at each error to ask what to do. In nonstop mode it goes on, writes the PDF and exits with status 1. The table of contents and its page numbers are complete after the third run. Run from the repository's root, this builds into `build/` and leaves the committed `waic_latex.pdf` as it is:

```sh
mkdir -p build
for run in 1 2 3; do pdflatex -interaction=nonstopmode -output-directory=build waic_latex.tex; done
```

The paper is then `build/waic_latex.pdf`, beside pdflatex's `.aux`, `.log`, `.out` and `.toc` files.
