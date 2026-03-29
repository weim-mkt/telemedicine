---
paths:
  - "overleaf-telemedicine/**/*.tex"
  - "overleaf-telemedicine/**/*.bib"
---

# Manuscript Compilation Protocol

## Local Compilation (pdflatex + bibtex, 3-pass)

### Main manuscript
```bash
cd overleaf-telemedicine && pdflatex -interaction=nonstopmode Main.tex && bibtex Main && pdflatex -interaction=nonstopmode Main.tex && pdflatex -interaction=nonstopmode Main.tex
```

### MSOM abstract
```bash
cd overleaf-telemedicine && pdflatex -interaction=nonstopmode Abstract_MSOM.tex && bibtex Abstract_MSOM && pdflatex -interaction=nonstopmode Abstract_MSOM.tex && pdflatex -interaction=nonstopmode Abstract_MSOM.tex
```

## Verification After Compilation

Check for:
1. No undefined references (`grep "undefined" Main.log`)
2. No missing citations (`grep "Citation.*undefined" Main.log`)
3. Overfull hbox warnings (`grep "Overfull" Main.log`) -- flag any > 10pt
4. Missing bibliography entries (`grep "empty.*thebibliography" Main.blg`)

## When to Compile

- After any .tex content edit (to verify no broken references)
- After .bib edits (full 3-pass needed to update citations)
- Before committing changes
