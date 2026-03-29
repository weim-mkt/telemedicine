---
paths:
  - "overleaf-telemedicine/**/*.tex"
  - "quality_reports/**"
---

# Manuscript Proofreading Protocol

**Scope:** All .tex content files in `overleaf-telemedicine/` (excluding .cls, .bst, MainPackages.tex, LinksAndMetadata.tex)

**CRITICAL: Propose changes first. Never apply edits without approval.**

## What to Check

1. **Grammar** -- subject-verb agreement, missing articles, wrong prepositions
2. **Typos** -- misspellings, duplicated words, search-and-replace corruption
3. **Consistency** -- terminology (telemedicine vs telehealth vs virtual care), notation, abbreviation usage
4. **Citations** -- `\citep` vs `\citet` usage, missing citations, broken references
5. **Academic quality** -- no informal contractions, clear sentence structure, precise language
6. **INFORMS formatting** -- proper use of document class features, theorem/hypothesis environments
7. **LaTeX hygiene** -- overfull/underfull boxes, missing `~` before `\citep`, proper use of `\textit` for Latin (e.g., e.g., i.e.)

## Three-Phase Workflow

### Phase 1: Review & Propose (NO EDITS)
- Read entire file
- Produce report with: location, current text, proposed fix, category
- Save to `quality_reports/[filename]_report.md`
- Do NOT modify source files

### Phase 2: Review & Approve
- User reviews proposed changes
- Accepts all, selectively, or requests modifications

### Phase 3: Apply Fixes
- Apply only approved changes via Edit tool
- Verify each edit succeeded
- Report completion summary

## Terminology Consistency Guide

Track and enforce consistent usage across all files:
- "telemedicine" (preferred) vs "telehealth" (only when citing others who use it)
- "in-person" (hyphenated as adjective) vs "in person" (as adverb)
- "service time" (the paper's key DV)
- "parity law" (not "parity legislation" unless context requires)
