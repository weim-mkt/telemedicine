# Manuscript Critique & Response Strategy

**Paper:** Does Virtual Take Longer? Service Time in Telemental Health
**Target:** MSOM / OPRE
**Date:** 2026-04-03
**R&R probability at MSOM: ~35-50%**

---

## Critique 2: The Mechanism (Digital Literacy) Is Assumed, Not Tested

### The Concern
The paper's core interpretive claim is that older/retired patients struggle with technology, lengthening sessions. But digital literacy is never directly measured. Equally plausible alternatives:
- Retired patients have more time and fewer opportunity costs, so they *prefer* longer sessions (not friction -- preference).
- Retired patients have more complex mental health needs. CCI and chronic conditions are physical comorbidity measures, not mental health severity.

### How to Address

**Option A: Audio-only vs. video visits (PRIORITY: HIGH).**
CMS modifier codes distinguish audio-only (modifier 93, POS 10) from video visits. If separable in the data:
- Audio-only should show *even longer* durations (less nonverbal information, more friction).
- This creates a dose-response within telemedicine itself, pinning the mechanism to communication modality.
- Effort: Medium. Payoff: High.

**Option B: Broadband moderation (PRIORITY: HIGH).**
State-level broadband adoption data from the FCC. Interact Tele x LowBroadband. If the telemedicine effect is larger in low-broadband states, that's consistent with technology friction and inconsistent with "retirees prefer longer chats."
- Effort: Low. Payoff: Medium.

**Option C: Learning curve / telemedicine experience (PRIORITY: MEDIUM).**
Construct cumulative prior telemedicine experience per patient. If the service time penalty *declines* with experience, that's consistent with digital literacy (learnable skill) rather than preferences or severity.
- Effort: Medium. Payoff: High.

**Option D: Within-patient modality switchers (PRIORITY: MEDIUM).**
For patients who switch between tele and in-person across months, compare their own service time. If the same patient has longer sessions when using tele, the "different patients sort into tele" story is ruled out.
- Effort: Medium. Payoff: High.

**Narrative defense (even without new tests):**
If the effect were purely preference-based, it should be similar across ages within retirees. The IV forest shows the effect *increases with age* among retirees. A 70-year-old retiree and an 85-year-old retiree have similar free time but very different tech comfort. This pattern favors the digital literacy story over the opportunity cost story.

---

## Critique 3: Fuel Price IV Exclusion Restriction

### The Concern
Fuel prices correlate with macroeconomic conditions (recessions, inflation). Economic stress may independently affect mental health severity and thus session length. State-level economic shocks (e.g., oil-producing vs. non-oil states) create differential exposure. A reviewer will ask: "Aren't fuel prices just proxying for local economic distress?"

Additionally, fuel prices may affect patient selection into treatment altogether (not just mode), violating the stable population assumption.

### How to Address

**Add state-level unemployment rate as a control (PRIORITY: HIGH).**
BLS has monthly state unemployment data. If the coefficient on Tele barely moves after including it, fuel prices aren't proxying for economic distress.
- Effort: Low.

**Overidentification test (PRIORITY: HIGH).**
Use both IVs (fuel price + parity law) simultaneously in a single 2SLS and report the Hansen J statistic. If you fail to reject the null, both instruments are consistent.
- Effort: Low.

**Fuel price decomposition (PRIORITY: LOW).**
Use only the crude oil supply-driven component of fuel prices (e.g., global oil supply shocks from Kilian's decomposition or OPEC production surprises). This strips out demand-side variation that correlates with local economic conditions.
- Effort: High.

**Narrative defense:** Quarter FE absorb national macro trends and regional FE absorb level differences. The remaining identifying variation is state-month deviations in fuel prices, which are harder to link to mental health severity than to transportation cost.

---

## Critique 4: The Two IVs Give Different Estimates

### The Concern
Fuel price IV: beta = 1.13 for Medicare. Parity law IV: beta = 0.56. That's a 2x difference. Reviewers will notice and question which is credible.

### How to Address

**Overidentification test (Hansen J).** If you fail to reject, the difference is sampling variation. If you reject, proceed to the next steps.

**Discuss different complier populations.** Fuel prices affect patients on the travel-cost margin (suburban/rural). Parity laws affect providers on the reimbursement margin (providers who wouldn't offer tele without equal pay). Different compliers, different LATEs.

**Show complier characteristics for each IV separately.** If fuel-price compliers are more rural/older and parity-law compliers are more urban, the magnitude difference makes economic sense.

**Present both as bounds.** The policy-relevant estimate depends on which margin the policymaker targets. Frame the range as informative rather than problematic.

---

## Critique 5: CPT Billing Code Is a Coarse Service Time Measure

### The Concern
CPT codes map to 30/45/60-minute bins. This measures billing code assignment, not actual minutes. Providers may upcode telemedicine visits differently. This could be a billing behavior story, not a clinical time story.

### How to Address

**Ordered choice model (PRIORITY: MEDIUM).**
Run an IV ordered probit where the DV is the CPT code category (30, 45, 60 min). Report marginal effects: "telemedicine increases the probability of being in the 60-min category by X pp." Avoids mapping codes to exact minutes.
- Effort: Low.

**Upcoding test (PRIORITY: MEDIUM).**
Compare the distribution of CPT codes for tele vs. in-person visits, conditional on provider. If the same provider bills the same code mix across modalities, upcoding is less likely. Show this descriptively.
- Effort: Low.

**Reframe as a strength for the OM audience.** Billing codes determine scheduling slots, staffing models, and revenue. For operations, the billing code *is* the relevant service time -- it determines the resource block allocated. Whether the provider spent 43 or 47 minutes within a 45-min slot is second-order for capacity planning.

**Acknowledge the conservative bias.** Discretization compresses within-code variation, so estimates are conservative relative to actual treatment impact. The paper already says this; lean into it harder.

---

## Critique 6: Provider Sorting / Supply-Side Selection

### The Concern
Without provider fixed effects, it's hard to rule out that the effect is driven by *who delivers telemedicine* rather than *the modality itself*. Providers who adopt telemedicine may have longer baseline session styles, different therapeutic orientations, or different caseload pressures.

### How to Address

**Restrict to providers who do both modalities (PRIORITY: HIGH).**
Limit the sample to providers observed delivering both tele and in-person visits during the sample period. This within-provider comparison removes the "different types of therapists" story.
- Effort: Low. Payoff: High.

**Add provider FE in an OLS robustness check (PRIORITY: MEDIUM).**
You lose the IV, but showing consistent sign and direction bounds the concern.
- Effort: Low.

**Control for provider specialty/credentials more granularly (PRIORITY: LOW).**
If available in MarketScan (psychiatrist vs. psychologist vs. LCSW).
- Effort: Low.

---

## Critique 7: No Patient Fixed Effects Weakens Causal Claims

### The Concern
Without patient FE, you're comparing different patients who use more vs. less telemedicine. Unobserved patient heterogeneity (severity, personality, therapy preferences) could drive both telemedicine choice and session length.

### How to Address

**Mundlak/CRE approach (PRIORITY: HIGH).**
For each patient, compute the time-series mean of all time-varying covariates. Include these patient-level means as additional regressors. This approximates patient FE without absorbing the IV's variation.
- Effort: Medium.

**Patient FE + OLS as a bound (PRIORITY: MEDIUM).**
Run patient-FE OLS (no IV). If sign and magnitude are broadly consistent with IV estimates, unobserved patient heterogeneity isn't flipping the result.
- Effort: Low.

**Restrict to patients with within-patient Tele variation (PRIORITY: MEDIUM).**
Patients who appear in multiple months with varying Tele intensity. Run the IV on this subsample.
- Effort: Low.

**Oster (2019) sensitivity analysis (PRIORITY: MEDIUM).**
Compute delta (coefficient stability). If delta > 1, it's unlikely unobservables can overturn the finding.
- Effort: Low.

---

## Critique 8: LATE Interpretation / Complier Representativeness

### The Concern
The IV identifies a Local Average Treatment Effect for compliers -- patients whose telemedicine use is influenced by gas prices. These are likely suburban/rural patients with meaningful commutes. The effect may not generalize to urban patients or those with strong modal preferences.

### How to Address

**Characterize the compliers (PRIORITY: HIGH).**
Following Angrist and Pischke, compute E[X|complier] = E[X * first_stage] / E[first_stage]. Show age, gender, rural/urban, and retirement distribution of compliers.
- Effort: Low.

**Compare IV to OLS.** If IV > OLS, discuss what this means about compliers. Typical interpretation: compliers are those most affected by the treatment.

**Frame compliers as policy-relevant.** Patients sensitive to travel cost are precisely the population that parity laws and telehealth expansion aim to serve. The LATE is the policy-relevant ATE.

---

## Critique 9: Missing Retirement Status (27% in Medicare)

### The Concern
Over a quarter of Medicare observations have missing employment status. Dropping them for heterogeneity analysis raises concerns about selective attrition.

### How to Address

**Balance table (PRIORITY: HIGH).**
Compare observables (age, gender, CCI, chronic, provider type) between missing and non-missing groups. If similar, missingness is plausibly random conditional on observables.
- Effort: Low.

**Bounds analysis (PRIORITY: MEDIUM).**
Run heterogeneity results assigning all missing patients to "retired" and then to "employed." If qualitative conclusion holds under both extremes, missing data isn't driving the result.
- Effort: Low.

**Inverse probability weighting (IPW) (PRIORITY: MEDIUM).**
Model probability of observing retirement status, then weight the heterogeneity analysis by inverse propensity scores.
- Effort: Medium.

---

## Critique 10: Post-COVID Coefficients Are Substantially Smaller

### The Concern
Post-COVID estimates (0.26 and 0.48) are much smaller than main results (0.83 and 1.13). This suggests much of the effect is pandemic-driven, changing the policy message considerably.

### How to Address

**Interpret honestly and reframe.** The smaller post-COVID effect is a *more credible* steady-state estimate. Frame the main result as an upper bound (includes pandemic disruption) and post-COVID as the lower bound. Both are significant and positive -- the story holds qualitatively.

**Rolling-window coefficients (PRIORITY: MEDIUM).**
Plot the 2SLS coefficient over rolling 12-month windows. If declining and stabilizing, that's natural pandemic recovery, not a threat. If stable post-mid-2022, the steady-state effect is clearly positive.
- Effort: Medium.

**Interact Tele with a post-pandemic indicator (PRIORITY: MEDIUM).**
Formally test whether the effect attenuates in the full sample.
- Effort: Low.

---

## Critique 11: More Service Time Could Be Good

### The Concern
Without outcome data, you can't distinguish "inefficient communication friction" from "richer therapeutic engagement." Longer sessions might reflect better care, not worse efficiency.

### How to Address

**Check treatment episode duration (PRIORITY: MEDIUM).**
Compare the total months of treatment (first to last visit) across tele-heavy vs. in-person patients. If telemedicine increases time per session but patients resolve faster, the efficiency story reverses.
- Effort: Medium.

**Check no-show/cancellation rates (PRIORITY: LOW).**
If observable in claims (voided/reversed claims). If telemedicine reduces no-shows, the net capacity effect is ambiguous.
- Effort: Low.

**Frame carefully in the paper.** Regardless of whether longer sessions are good or bad for patients, providers still face increased workload and reduced throughput. The paper's contribution is documenting the operational consequence; quality implications are a separate question (acknowledged as future work).

---

## Critique 12: Standing Out in a Crowded Field

### The Concern
Bavafa et al. (2018, 2021), Ayabakan et al. (2023), Tushe et al. (2025), Delana et al. (2023) -- the telemedicine shelf at MSOM is getting full. Differentiation rests on "service time" as DV and "retirement" as moderator, which may not feel like enough novelty.

### How to Address

**Add a positioning table in the literature review:**

| Paper | Setting | DV | Method | Key Finding |
|-------|---------|-----|--------|------------|
| Bavafa+ 2018 | Primary care | Visit freq, appt duration | Patient FE | More visits, no duration change |
| Bavafa+ 2021 | Primary care | Panel size | DiD | Larger panels |
| Ayabakan+ 2023 | Multi-specialty | Cost | IV | Cost reduction for virtualizable |
| Tushe+ 2025 | Multi-channel | Congestion | Structural | Altered routing |
| **This paper** | **Psychotherapy** | **Service time** | **IV + IV forest** | **More time, worse for elderly** |

**Emphasize the IV forest as methodological contribution.** Most telemedicine papers do subgroup 2SLS. The IV forest (Athey et al. 2019) applied to telemedicine heterogeneity is novel in this literature.

**Connect to broader OM literature.** The access-efficiency tradeoff from technology adoption appears in self-checkout, chatbots, automated triage, etc. This paper provides causal evidence in a high-stakes setting, broadening the audience beyond healthcare OM.

**Add a counterfactual policy exercise using the IV forest CATEs:**
- Simulate digital training for retirees (reducing their CATE to non-retired level). How much service time saved?
- Simulate hybrid routing (elderly to in-person, younger to tele). Capacity gain?
- Back-of-envelope is sufficient. Transforms the paper from "here's what happens" to "here's what to do about it."

---

## Priority Ranking for Maximum R&R Probability

| Priority | Action | Effort | Payoff | Critique |
|----------|--------|--------|--------|----------|
| 1 | Audio-only vs. video separation | Medium | High | #2 (Mechanism) |
| 2 | Provider-who-does-both subsample | Low | High | #6 (Provider sorting) |
| 3 | Back-of-envelope capacity calculation | Low | High | #1 (Incremental) |
| 4 | Overidentification test with both IVs | Low | Medium | #3, #4 (IV validity) |
| 5 | Broadband moderation | Low | Medium | #2 (Mechanism) |
| 6 | Complier characterization | Low | Medium | #8 (LATE) |
| 7 | Learning curve / tele experience | Medium | High | #2 (Mechanism) |
| 8 | Positioning table in lit review | Low | Medium | #12 (Crowded field) |
| 9 | Oster (2019) sensitivity | Low | Medium | #7 (No patient FE) |
| 10 | Balance table for missing retirement | Low | Medium | #9 (Missing data) |
| 11 | Policy simulation with CATEs | Medium | High | #1, #12 (Impact) |
| 12 | Rolling-window time-varying coefficients | Medium | Medium | #10 (Post-COVID) |
| 13 | Ordered probit on CPT categories | Low | Low-Med | #5 (Measurement) |

**Items 1-6: recommended before first submission.**
**Items 7-13: natural R&R additions.**
