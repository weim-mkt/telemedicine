# Workflow Quick Reference

**Model:** Contractor (you direct, Claude orchestrates)

---

## The Loop

```
Your instruction
    ↓
[PLAN] (if multi-file or unclear) → Show plan → Your approval
    ↓
[EXECUTE] Implement, verify, done
    ↓
[REPORT] Summary + what's ready
    ↓
Repeat
```

---

## I Ask You When

- **Design forks:** "Option A (fast) vs. Option B (robust). Which?"
- **Ambiguity:** "Spec unclear on X. Assume Y?"
- **Scope question:** "Also address Y while here, or focus on X?"
- **Proofreading judgment calls:** "This sentence could be read two ways. Intended meaning?"

---

## I Just Execute When

- Obvious typo/grammar fixes (propose first per proofreading protocol)
- Verification (compilation, reference checks)
- Documentation (session logs, commits)
- Quality scoring

---

## Quality Gates (No Exceptions)

| Score | Action |
|-------|--------|
| >= 80 | Ready to commit |
| < 80  | Fix blocking issues |

---

## Non-Negotiables

- **INFORMS style** -- `informs3ek` document class, `informs2014.bst` bibliography style
- **natbib citations** -- `\citep{}` for parenthetical, `\citet{}` for textual, never `\cite{}`
- **pdflatex compilation** -- 3-pass with bibtex (not XeLaTeX)
- **Proofreading protocol** -- propose changes first, apply only after approval
- **No informal abbreviations** in manuscript text (e.g., don't, can't, it's)

---

## R Code Conventions

- `set.seed()` before any randomness
- `here::here()` for paths
- `library()` not `require()`
- Base pipe `|>` preferred
- `data.table` for data manipulation
- `ggplot2` with explicit `ggsave()` dimensions

---

## Preferences

**Collaboration style:** Structured, precise, rigorous
**Reporting:** Concise but thorough; check in more during early sessions
**Proofreading:** All .tex content files in scope
**Visuals:** Publication-ready, polished
**Session logs:** Always (post-plan, incremental, end-of-session)

---

## Next Step

You provide task → I plan (if needed) → Your approval → Execute → Done.
