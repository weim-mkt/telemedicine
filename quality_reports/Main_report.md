# Proofreading Report: Main.tex

**File:** `overleaf-telemedicine/Main.tex`
**Date:** 2026-03-30
**Scope:** Active content only (skipping `\iffalse` blocks and commented-out lines)
**Total issues found:** 30

---

## CRITICAL Issues (2)

### 1. Hypothesis references swapped (H3a/H3b)
- **Line:** 469
- **Current:** "The evidence therefore supports Hypothesis \ref{hyp:PerVisita} and rejects the alternative prediction in Hypothesis \ref{hyp:PerVisitb} that telemedicine would shorten individual visits."
- **Proposed:** "The evidence therefore supports Hypothesis \ref{hyp:PerVisitb} and rejects the alternative prediction in Hypothesis \ref{hyp:PerVisita} that telemedicine would shorten individual visits."
- **Category:** ACADEMIC
- **Explanation:** H3a states telemedicine *decreases* per-visit time; H3b states it *increases*. The finding is an increase, so H3b is supported and H3a is rejected. The current text has them reversed.

### 2. CPT code mapping error (90838 listed under both 30 and 60 minutes)
- **Line:** 200
- **Current:** "Each code defines a reference duration: 90832 and 90838 for 30 minutes, 90834 and 90836 for 45 minutes, and 90837 and 90838 for 60 minutes."
- **Proposed:** "Each code defines a reference duration: 90832 and 90833 for 30 minutes, 90834 and 90836 for 45 minutes, and 90837 and 90838 for 60 minutes."
- **Category:** ACADEMIC
- **Note:** Code 90838 is a 60-minute add-on code and cannot be both 30 and 60 minutes. The 30-minute add-on code is 90833. The same error appears in the footnote on the same line ("90832 and 90838 for 16-37 minutes" should be "90832 and 90833 for 16-37 minutes").

---

## MAJOR Issues (11)

### 3. Typo "envolving" -> "evolving"
- **Line:** 196
- **Current:** "the envolving impact of COVID-19 pandemic"
- **Proposed:** "the evolving impact of the COVID-19 pandemic"

### 4. Typo "Rolleout" -> "Rollout" in subsection title
- **Line:** 693
- **Current:** `\subsection{An Alternative IV: Staggered Rolleout of Payment Parity Law}`
- **Proposed:** `\subsection{An Alternative IV: Staggered Rollout of Payment Parity Law}`

### 5. Typo "parient's" -> "patient's"
- **Line:** 697
- **Current:** "the proportion of a parient's tele-visits"
- **Proposed:** "the proportion of a patient's tele-visits"

### 6. Typo "imporant" -> "important"
- **Line:** 1018
- **Current:** "an increasingly imporant mode of care delivery"
- **Proposed:** "an increasingly important mode of care delivery"

### 7. Typo "spliting" -> "splitting"
- **Line:** 482
- **Current:** "by spliting Medicare patients"
- **Proposed:** "by splitting Medicare patients"

### 8. Typo "discrepency" -> "discrepancy"
- **Line:** 484
- **Current:** "The discrepency between"
- **Proposed:** "The discrepancy between"

### 9. Typo "heterogenity" -> "heterogeneity"
- **Line:** 587
- **Current:** "the baseline heterogenity"
- **Proposed:** "the baseline heterogeneity"

### 10. Typo "Pennylvania" -> "Pennsylvania"
- **Line:** 866 (footnote)
- **Current:** "Oregon, Pennylvania, South Carolina"
- **Proposed:** "Oregon, Pennsylvania, South Carolina"

### 11. Typo "assessed" -> "accessed"
- **Line:** 940
- **Current:** "some of these patients assessed virtual services"
- **Proposed:** "some of these patients accessed virtual services"

### 12. Typo "Commerical" -> "Commercial"
- **Line:** 209 (footnote)
- **Current:** "The Commerical database"
- **Proposed:** "The Commercial database"

### 13. Wrong verb "rise" -> "raise"
- **Line:** 1022
- **Current:** "which may rise both patient time costs"
- **Proposed:** "which may raise both patient time costs"

### 14. Subject-verb agreement "Column presents" -> "Columns present"
- **Line:** 469
- **Current:** "Column (2) and (4) presents the second stage estimations"
- **Proposed:** "Columns (2) and (4) present the second stage estimations"

### 15. Subject-verb agreement "use increase" -> "use increases"
- **Line:** 482
- **Current:** "the telemedicine use significantly increase total service time"
- **Proposed:** "telemedicine use significantly increases total service time"

### 16. Extra closing parenthesis after citation
- **Line:** 152
- **Current:** `\citep{Cavapozzi2022, Hargittai2017})`
- **Proposed:** `\citep{Cavapozzi2022, Hargittai2017}`

### 17. Missing plural "patient" -> "patients"
- **Line:** 940
- **Current:** "service time of these patient compared"
- **Proposed:** "service time of these patients compared"

---

## MINOR Issues (13)

### 18. "U.S during" -- missing period
- **Line:** 87
- **Current:** "in the U.S during and after"
- **Proposed:** "in the U.S.\ during and after"

### 19. Extra space before period after citation
- **Line:** 119
- **Current:** `\citep{Bavafa2021} .`
- **Proposed:** `\citep{Bavafa2021}.`

### 20. `\cite` should be `\citet` (5 instances in active text)
- **Lines:** 129, 276, 597 (x2), 1030
- **Explanation:** Per INFORMS/natbib conventions, textual citations (Author as grammatical subject) should use `\citet`, not bare `\cite`.

### 21. "and/ or" -- extraneous space
- **Line:** 204
- **Current:** "and/ or whether"
- **Proposed:** "and/or whether"

### 22. Missing space before parenthesis (2 instances)
- **Lines:** 214 and 866
- **Current:** "rural areas($Rural_{it}$)" and "insurance($\beta_1"
- **Proposed:** "rural areas ($Rural_{it}$)" and "insurance ($\beta_1"

### 23. "Old adults are often more laggards"
- **Line:** 474
- **Current:** "Old adults are often more laggards in technology adoption"
- **Proposed:** "Older adults are often laggards in technology adoption"

### 24. Subject-verb agreement "shows...and do not control"
- **Line:** 484
- **Current:** "Table...shows results...and do not control"
- **Proposed:** "Table...shows results...and does not control"

### 25. Missing preposition "by"
- **Line:** 480
- **Current:** "We start our heterogeneity analysis applying"
- **Proposed:** "We start our heterogeneity analysis by applying"

### 26. Double spaces in running text (5 instances)
- **Lines:** 91, 467, 474, 597, 697

### 27. Space before `\footnote`
- **Line:** 866
- **Current:** `emergency. \footnote{According`
- **Proposed:** `emergency.\footnote{According`

### 28. Missing closing parenthesis in math expression
- **Line:** 482
- **Current:** `($(Tele*Retire)_{it}$.`
- **Proposed:** `($(Tele*Retire)_{it}$).`

### 29. "old-retired" -- awkward phrasing
- **Line:** 156
- **Current:** "for old-retired Medicare patients"
- **Proposed:** "for older retired Medicare patients"

### 30. Label misspelling "althernativemodel"
- **Lines:** 198 and 791
- **Current:** `\label{section:althernativemodel}`
- **Proposed:** `\label{section:alternativemodel}`
- **Note:** Label and reference match, so no compile error, but misspelling propagates.

---

## Summary by Category

| Category | Critical | Major | Minor | Total |
|----------|----------|-------|-------|-------|
| Typo | 0 | 8 | 6 | 14 |
| Grammar | 0 | 3 | 3 | 6 |
| Academic | 2 | 0 | 1 | 3 |
| Consistency | 0 | 0 | 1 | 1 |
| LaTeX | 0 | 0 | 2 | 2 |
| **Total** | **2** | **11** | **13** | **30** |
