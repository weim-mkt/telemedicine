# CLAUDE.MD -- Telemedicine Manuscript Project

**Project:** Does Virtual Take Longer? Service Time in Telemental Health
**Institution:** University College London (UCL), School of Management
**Authors:** Yupu Sun, Ersin Korpeoglu, Wei Miao
**Target journals:** OPRE (main manuscript), MSOM (extended abstract)
**Branch:** main

---

## Core Principles

- **Plan first** -- enter plan mode before non-trivial tasks; save plans to `quality_reports/plans/`
- **Verify after** -- compile and confirm output at the end of every task
- **Single source of truth** -- `overleaf-telemedicine/Main.tex` is the authoritative manuscript
- **Quality gates** -- nothing ships below 80/100
- **[LEARN] tags** -- when corrected, save `[LEARN:category] wrong -> right` to MEMORY.md

---

## Folder Structure

```
telemedicine/
├── CLAUDE.md                       # This file
├── MEMORY.md                       # Persistent learnings
├── .claude/                        # Rules, settings, workflow config
│   ├── settings.json
│   ├── WORKFLOW_QUICK_REF.md
│   └── rules/                      # Project-specific rules
├── overleaf-telemedicine/          # LaTeX manuscript (Overleaf sync)
│   ├── Main.tex                    # Main manuscript body
│   ├── Appendices.tex              # Appendices
│   ├── supplementary.tex           # Supplementary materials
│   ├── parity laws.tex             # Parity laws analysis
│   ├── copy.tex                    # Working copy
│   ├── upgrade.tex                 # Revision/upgrade draft
│   ├── Abstract_MSOM.tex           # MSOM extended abstract
│   ├── telemedicine.bib            # Bibliography
│   ├── MainPackages.tex            # Package configuration
│   ├── LinksAndMetadata.tex        # Hyperref setup
│   ├── figures/                    # Figures and images
│   ├── informs3ek.cls              # INFORMS document class
│   ├── informs2014.bst             # Bibliography style
│   └── ormsv080.bst                # Alt bibliography style
├── quality_reports/                # Plans, session logs, specs
└── readme.md
```

---

## Commands

```bash
# LaTeX compilation (3-pass, pdflatex + bibtex)
cd overleaf-telemedicine && pdflatex -interaction=nonstopmode Main.tex
bibtex Main
pdflatex -interaction=nonstopmode Main.tex
pdflatex -interaction=nonstopmode Main.tex

# MSOM abstract compilation
cd overleaf-telemedicine && pdflatex -interaction=nonstopmode Abstract_MSOM.tex
bibtex Abstract_MSOM
pdflatex -interaction=nonstopmode Abstract_MSOM.tex
pdflatex -interaction=nonstopmode Abstract_MSOM.tex
```

---

## Quality Thresholds

| Score | Gate | Meaning |
|-------|------|---------|
| 80 | Commit | Good enough to save |
| 90 | PR | Ready for submission review |
| 95 | Excellence | Submission-ready |

---

## Skills Quick Reference

| Command | What It Does |
|---------|-------------|
| `/proofread [file]` | Grammar/typo/consistency review |
| `/review-paper [file]` | Full manuscript review (structure, methods, citations) |
| `/validate-bib` | Cross-reference citations vs bibliography |
| `/compile-latex [file]` | 3-pass pdflatex + bibtex |
| `/review-r [file]` | R code quality review |
| `/data-analysis [dataset]` | End-to-end R analysis pipeline |
| `/lit-review [topic]` | Literature search + synthesis |
| `/research-ideation [topic]` | Research questions + strategies |
| `/interview-me [topic]` | Interactive research interview |
| `/commit [msg]` | Stage, commit, PR, merge |
| `/learn [skill-name]` | Extract discovery into persistent skill |
| `/context-status` | Show session health + context usage |
| `/deep-audit` | Repository-wide consistency audit |

---

## Citation Conventions

- **Author-year style** via `natbib` package
- Use `\citep{key}` for parenthetical citations: (Author, Year)
- Use `\citet{key}` for textual citations: Author (Year)
- Use `\citep[e.g.][]{key}` for citations with prefixes
- Bibliography style: `informs2014` (main) or `ormsv080` (alt)

---

## Manuscript File Inventory

| File | Purpose | Status |
|------|---------|--------|
| `Main.tex` | Full OPRE manuscript | Active |
| `Appendices.tex` | Appendices and robustness checks | Active |
| `supplementary.tex` | Supplementary materials | Active |
| `parity laws.tex` | Parity laws analysis section | Active |
| `copy.tex` | Working copy/draft | Working |
| `upgrade.tex` | Revision draft | Working |
| `Abstract_MSOM.tex` | MSOM extended abstract | Active |
