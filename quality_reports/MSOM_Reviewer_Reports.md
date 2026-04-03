# Simulated MSOM Reviewer Reports

**Manuscript:** "Does Virtual Take Longer? An Empirical Investigation of Service Time in Telemental Health"
**Authors:** Yupu Sun, Ersin Korpeoglu, Wei Miao
**Journal:** Manufacturing & Service Operations Management (MSOM)
**Date:** 2026-03-30

---

## Reviewer 1 Report

**Recommendation:** Major Revision

**Overall Assessment:**

This paper investigates the causal impact of telemedicine use on psychotherapy service time using patient-level insurance claims data. The research question is timely and operationally relevant. The paper makes a reasonable contribution by documenting that telemedicine increases both visit frequency and per-visit service time, and that these effects are heterogeneous across patient demographics. However, I have several substantive concerns regarding identification, measurement, and interpretation that should be addressed before the paper is suitable for publication in MSOM.

### Major Comments

**1. Instrumental Variable Validity (Exclusion Restriction)**

The primary IV --- lagged state-level fuel price --- raises concerns about the exclusion restriction. While the authors argue that fuel prices affect telemedicine adoption through travel costs, fuel prices are also correlated with broader macroeconomic conditions (e.g., inflation, consumer sentiment, economic activity) that could independently affect mental health service utilization patterns, appointment scheduling behavior, and session duration. For example:

- During periods of high fuel prices, patients may experience financial stress that worsens mental health symptoms and requires longer sessions.
- Fuel prices correlate with economic cycles; recessions and booms differentially affect mental health demand and provider behavior.
- Regional and quarter fixed effects may not fully absorb these channels, especially if within-region, within-quarter variation in fuel prices captures local economic shocks.

The authors should provide more rigorous evidence for the exclusion restriction. I recommend:
(a) A formal discussion of potential violations and their direction of bias.
(b) Sensitivity analysis using methods such as Conley et al. (2012) bounds for plausible violations of the exclusion restriction.
(c) Reduced-form analysis directly regressing outcomes on the IV to show the magnitude is consistent with the hypothesized channel.

**2. Measurement of Service Time**

The paper uses CPT billing codes as a proxy for service time, where each code corresponds to a time range (e.g., 90832 for 16--37 minutes, mapped to 30 minutes). This is a coarse, categorical measure that introduces substantial measurement error:

- Within each billing category, there is a wide range of actual service times (e.g., 21 minutes of variation within the 30-minute code). The paper cannot distinguish whether telemedicine causes providers to spend more actual time or whether it causes them to "upcode" (bill for a higher time category).
- The authors acknowledge this measurement issue in the conclusion but treat it as leading to conservative estimates. However, if telemedicine systematically changes upcoding behavior (e.g., providers bill higher codes for virtual visits to compensate for lower reimbursement or perceived higher effort), then the estimates would be biased, not conservative.
- I recommend the authors explicitly discuss billing incentives in telemedicine vs. in-person visits. Do reimbursement rates differ by modality for the same CPT code? If so, differential billing incentives could confound the results.

**3. Decomposition of Total Service Time**

The decomposition of monthly service time into visit frequency and per-visit duration is mechanical (TimeMonth = VisitNum x TimeVisit), not structural. The 2SLS estimates for the components do not necessarily add up to the total effect estimate because log transformations of ratios do not preserve linearity. The authors should:

(a) Verify that the decomposition is internally consistent (i.e., that the coefficient on ln(TimeMonth) approximately equals the sum of coefficients on ln(VisitNum) and ln(TimeVisit)).
(b) Discuss whether the IV affects these components through the same channel or potentially through different mechanisms.

**4. Interpretation: Digital Literacy vs. Alternative Explanations**

The paper's preferred interpretation --- that telemedicine increases service time because elderly patients have low digital literacy --- is plausible but not the only explanation. Alternative mechanisms include:

- **Selection on severity timing:** Even without differences in baseline severity, patients who use telemedicine may time their visits differently (e.g., seeking care at different stages of an episode), leading to different service durations.
- **Provider behavior:** Providers may systematically spend more time in virtual sessions due to documentation requirements, platform-related overhead, or compensating for reduced ability to conduct physical examinations.
- **Therapeutic alliance:** Building rapport virtually may inherently require more time regardless of patient digital literacy.

The retirement-based heterogeneity is consistent with the digital literacy story but also consistent with other explanations (e.g., retired patients have more flexible schedules and may be less time-constrained, leading to longer sessions). I encourage the authors to be more careful in attributing the mechanism and to discuss alternative explanations more thoroughly.

**5. Sample Period and COVID-19 Confounding**

The study period (January 2021 -- March 2023) coincides with the pandemic and its aftermath. While the authors include a post-COVID subsample analysis, several concerns remain:

- During this period, the composition of patients using telemedicine vs. in-person care was likely non-random in ways that evolved over time. Early adopters of telemedicine may differ systematically from later adopters.
- Provider experience with telemedicine platforms improved substantially over this period, which could attenuate the digital literacy channel over time. A time-varying analysis of the treatment effect would be informative.
- The pandemic period saw widespread changes in mental health severity, provider burnout, and healthcare system strain that could affect service times independently of telemedicine modality.

### Minor Comments

1. The paper uses region (4--5 groups) and quarter (9 groups) fixed effects. Given the large sample size, finer geographic fixed effects (e.g., state or county) would be feasible and would better absorb local confounders. Why not use state fixed effects?

2. Table 1 reports 10% missing values for Retire in the private sample and 27.1% in the Medicare sample. The treatment of missing retirement status as a separate category (RetireMiss) is unusual. The authors should discuss potential selection into missingness and whether results are robust to excluding these observations entirely.

3. The paper mentions that "Age is scaled by 100." This is an unusual transformation. Please clarify the interpretation of the Age coefficient. For Medicare patients, the coefficient on Age_scale in the first stage is -1.05 --- this implies that a unit increase in Age_scale (i.e., aging by 100 years) is associated with a 1.05 decrease in the telemedicine proportion, which is not directly interpretable.

4. The writing in Section 2 (Literature Review and Hypothesis Development) could be tightened. The hypothesis development section presents competing hypotheses for per-visit service time (H3a vs. H3b) but does not provide a clear prior about which should dominate, making the hypotheses feel post-hoc.

5. The weak instrument test uses cluster-robust Wald statistics. Please also report the effective F-statistic from Olea and Pflueger (2013) or the Kleibergen-Paap rk Wald F-statistic, which are more appropriate for clustered standard errors.

6. The correlation test in Table 3 showing that the IV has low correlation with observed patient characteristics is suggestive but does not constitute a formal test of the exclusion restriction. The exclusion restriction concerns correlation with *unobserved* factors.

---

## Reviewer 2 Report

**Recommendation:** Major Revision

**Overall Assessment:**

This paper studies a practically important question: does telemedicine use affect the duration of psychotherapy visits? The use of large-scale claims data and the IV approach are commendable. However, I have concerns about the contribution relative to existing literature, the econometric framework, and the policy implications drawn from the results.

### Major Comments

**1. Contribution Relative to Existing Literature**

The paper positions itself relative to Bavafa et al. (2018, MS) and Ayabakan et al. (2023, MS), among others. However, the contribution over these papers needs to be sharpened:

- Bavafa et al. already show that e-visit usage increases office visit frequency. The finding that telemedicine increases visit frequency (H2) is therefore not new.
- The novel contribution appears to be the finding that telemedicine increases per-visit service time (H3b) and the heterogeneity by retirement status (H4). However, the per-visit service time effect is modest (11--19% for a complete switch from in-person to virtual), and the mechanism remains speculative.
- The paper should more clearly articulate what the specific MSOM contribution is. Is it the measurement approach (using billing codes), the decomposition, or the heterogeneity analysis? A clearer statement of the paper's unique contribution would strengthen the positioning.

**2. Endogeneity of Telemedicine Adoption: The Continuous Treatment Problem**

The treatment variable $Tele_{it}$ is the proportion of telemedicine visits in a given month. This is a continuous endogenous variable instrumented with a continuous IV. However:

- The proportion is mechanically related to the number of visits (the denominator). Since visit frequency is also an outcome variable, there is a built-in mechanical relationship between the treatment and one of the outcomes. This creates a "bad control" problem when the same denominator appears in both the treatment definition and outcome construction.
- For a patient who has 1 visit in a month, $Tele_{it}$ is either 0 or 1. For a patient with 4 visits, $Tele_{it}$ can take values in {0, 0.25, 0.5, 0.75, 1}. The distribution of $Tele_{it}$ is therefore mechanically correlated with visit frequency, creating a confound.
- I recommend the authors consider an alternative treatment definition, such as a binary indicator for any telemedicine use, or use the number of telemedicine visits directly (instrumenting separately).

**3. LATE vs. ATE Interpretation**

The 2SLS estimates identify a local average treatment effect (LATE) for compliers --- patients whose telemedicine adoption is affected by fuel prices. This population may differ substantially from the average patient:

- Compliers are likely marginal telemedicine users who are sensitive to travel costs. These patients may have different characteristics (e.g., living in areas with poor public transportation, lower income, different severity profiles) than the average telemedicine user.
- The external validity of the estimates to the broader telemedicine population is therefore unclear. The paper should discuss the LATE interpretation and characterize the complier population.
- The policy implications (e.g., regarding elderly patients) may not generalize if elderly compliers are a non-representative subset.

**4. Fixed Effects Granularity**

Using only 4--5 region groups and 9 quarter groups as fixed effects is unusually coarse for a study with over 13 million observations:

- State-level or even county-level fixed effects would be standard in applied health economics.
- Year-quarter fixed effects with only 9 periods (Q1 2021 through Q1 2023) cannot absorb month-to-month variation in pandemic intensity, policy changes, or provider adaptation.
- I strongly recommend the authors adopt state x year-quarter fixed effects at minimum, and consider state x month fixed effects if computationally feasible. This would substantially strengthen the identification.

**5. Instrumental Forest Analysis**

The instrumental forest analysis (Section 5.2) is an interesting addition, but several aspects need clarification:

- The forest estimates CATEs, but the paper does not report confidence intervals for the heatmap cells in Figure 3. Without uncertainty quantification, it is difficult to assess whether the differences across cells are statistically meaningful.
- The residualization step (removing region-quarter fixed effects before running the forest) is non-standard. How sensitive are the results to this pre-processing step?
- The paper should report the forest's out-of-bag calibration metrics (e.g., the calibration test from Chernozhukov et al., 2018) to validate that the estimated heterogeneity is genuine rather than noise.
- Variable importance scores from the forest would help readers understand which covariates drive the heterogeneity.

**6. Missing Discussion of Provider-Side Mechanisms**

The paper focuses almost exclusively on patient-side explanations (digital literacy, communication challenges). However, provider behavior is equally important:

- Do providers adjust their session length based on modality? For example, some providers may have a minimum session length for virtual visits that is longer than for in-person visits.
- Do providers conduct additional documentation or administrative tasks during virtual sessions that inflate the billed time?
- Is there strategic billing behavior? Providers may systematically bill higher time codes for virtual visits if they perceive the administrative overhead as justifying a longer code.

Without controlling for provider fixed effects or analyzing within-provider variation across modalities, the paper cannot distinguish patient-side from provider-side mechanisms. Adding provider fixed effects (if provider IDs are available in the data) would substantially strengthen the analysis.

### Minor Comments

1. The abstract states "Problem definition," "Methodology/results," and "Managerial implications" in bold --- this follows the MSOM format, which is good. However, the abstract could be more concise about the specific magnitudes.

2. Hypothesis 4 states that telemedicine leads to "a larger increase in psychotherapy service time per visit for old-retired Medicare patients," but the main analysis tests this on total service time per month, not per visit. The hypothesis and the test should be aligned.

3. The falsification test (Section 6.4) is well-designed but the private insurance sample shows a marginally significant PayerType2 coefficient in the first stage, which deserves discussion.

4. In the summary statistics (Table 2), the VisitNum variable ranges up to 13 (private) and 12 (Medicare) visits per month. Are these outliers? A robustness check trimming extreme values would be reassuring.

5. The paper should discuss whether the results vary by specific CPT code type (psychotherapy-only vs. E/M add-on), beyond just controlling for the EM dummy. This could shed light on whether the telemedicine effect is driven by certain types of encounters.

6. References to "parity laws" appear in the MSOM abstract but this analysis appears to have been removed from the main paper. The paper should ensure consistency between versions.

---

## Associate Editor Report

**Recommendation:** Major Revision (with encouragement to resubmit)

**Summary:**

This paper examines whether telemedicine use affects the duration of psychotherapy visits, using large-scale U.S. health insurance claims data and an instrumental variable approach. The research question is timely and relevant to the MSOM community, particularly given the sustained adoption of telemedicine post-COVID-19. Both reviewers found merit in the paper but raised substantive concerns that need to be addressed. I concur with these assessments and provide my own synthesis below.

### Key Issues Requiring Attention

**1. Identification Strategy (Priority: High)**

Both reviewers raise concerns about the instrumental variable. R1 questions the exclusion restriction for the fuel price IV, noting plausible channels through which fuel prices could affect service time directly (e.g., via economic stress affecting mental health). R2 notes the coarse fixed effects structure that may be insufficient to absorb confounders. I recommend:

- Adopting state x year-quarter (or state x month) fixed effects, which is standard in the applied health economics literature for claims-based studies.
- Conducting formal sensitivity analysis for the exclusion restriction (e.g., plausibly exogenous instruments framework).
- Discussing the LATE interpretation and complier characterization.

The alternative IV (parity law) is helpful but faces its own exclusion restriction concerns (parity laws may directly affect session length through reimbursement incentives, not just through telemedicine adoption). The authors should address this.

**2. Measurement and Interpretation (Priority: High)**

The use of billing codes as a proxy for service time is pragmatic but introduces concerns about upcoding and billing incentives that both reviewers flag. The authors should:

- Discuss whether reimbursement rates differ between telemedicine and in-person visits for the same billing code.
- Acknowledge that their measure captures billed time, not necessarily actual clinical contact time.
- Consider whether the results could be driven by differential billing behavior rather than actual differences in time spent.

**3. Mechanism and Contribution (Priority: High)**

R1 and R2 both note that the digital literacy explanation, while plausible, is under-identified. Multiple alternative mechanisms (provider behavior, scheduling flexibility, therapeutic alliance) are consistent with the same patterns. To strengthen the contribution:

- If provider IDs are available, include provider fixed effects to isolate within-provider, across-modality variation.
- Consider analyzing the time trend of the telemedicine effect --- if digital literacy is the mechanism, the effect should attenuate as patients gain experience with telemedicine over the sample period.
- More carefully distinguish the paper's contribution from Bavafa et al. (2018) on visit frequency and from the broader telemedicine-and-operations literature.

**4. Econometric Concerns (Priority: Medium)**

- The mechanical relationship between the treatment variable (proportion of tele-visits) and the outcome (visit frequency) noted by R2 is an important concern. Consider using a binary treatment indicator as a robustness check.
- The decomposition of ln(TimeMonth) into ln(VisitNum) and ln(TimeVisit) should be verified for internal consistency.
- Report appropriate weak instrument statistics for clustered data (effective F-statistic).

**5. Heterogeneity Analysis (Priority: Medium)**

The instrumental forest analysis is a nice complement to the 2SLS heterogeneity analysis. However, as R2 notes, confidence intervals and calibration diagnostics are needed. The discrepancy between the subsample 2SLS results (significant retirement effect) and the interacted 2SLS (insignificant interaction) deserves more careful discussion --- the current explanation (nonlinear heterogeneity) is somewhat ad hoc.

### Additional Suggestions

1. The paper would benefit from a conceptual framework (even informal) that maps the channels through which telemedicine affects service time. This would discipline the empirical analysis and help readers understand which mechanisms are tested and which remain speculative.

2. The title "Does Virtual Take Longer?" is engaging, and the answer appears to be unambiguously "yes." Consider whether the paper can sharpen its message around the access-efficiency tradeoff, which seems to be the most novel insight.

3. The writing is generally clear but could be more concise in places, particularly in the literature review and hypothesis development sections. Some tables could be moved to an appendix to improve readability.

4. Ensure consistency across the manuscript. The MSOM abstract mentions parity laws analysis that does not appear in the main text. If this analysis was removed, update the abstract accordingly.

I encourage the authors to address these concerns and resubmit. The question is important, the data are valuable, and the paper has the potential to make a solid contribution to the healthcare operations literature at MSOM.

---

*End of Reports*
