# A/B Testing Statistical Analysis: Website Redesign Impact

## Overview
Statistical analysis of a simulated A/B test evaluating the impact of a website redesign on user engagement metrics.

## Business Problem
An e-commerce company needed to determine if a website redesign actually improved user engagement. Key questions:
- Does the redesign increase session duration?
- Does it improve conversion rate?
- Is the effect consistent across user segments?

## Dataset
- **Type:** Simulated (not real user data) — generated with `numpy`, seed 42, to practice a full analysis pipeline on data with known structure
- **Size:** 10,000 users (5,076 control / 4,924 treatment — random assignment doesn't guarantee an exact 50/50 split)
- **Features:** group (control/treatment), device, age, session duration, clicks, conversion
- **Data-generating logic:** session duration is drawn from an exponential distribution (right-skewed, as real session times typically are), scaled up 1.15x for treatment and down 0.8x for mobile; conversion probability is a logistic function of session duration, so the conversion effect is mechanically downstream of the duration effect, not independent of it; clicks are Poisson-distributed with a 1.5x rate multiplier for treatment

## Statistical Methods
1. **Two-Sample T-Test** — session duration comparison
2. **Chi-Square Test** — conversion rate comparison
3. **Mann-Whitney U Test** — non-parametric check on session duration and clicks
4. **95% Confidence Intervals** — conversion rate, by group
5. **Effect Size (Cohen's d)** — practical significance of the session duration difference
6. **Segment Analysis** — conversion rate by device

## Key Findings

| Metric | Control | Treatment | Change | Test | Statistic | P-value |
|---|---|---|---|---|---|---|
| Conversion rate | 46.55% | 48.68% | +2.13 pts (+4.6% relative) | Chi-square | χ²=4.451 | 0.0349 |
| Session duration (mean) | 264.75s | 305.23s | +40.5s (+15.3% relative) | Two-sample t-test | t=6.976 | <0.00001 |
| Session duration (Mann-Whitney) | — | — | — | Mann-Whitney U | U=13,288,163 | <0.00001 |
| Clicks (mean) | 2.98 | 4.51 | +1.53 | Mann-Whitney U | U=17,791,972 | <0.00001 |

**95% CI, conversion rate:** control 0.4655 (0.4518–0.4793), treatment 0.4868 (0.4728–0.5008) — note the intervals overlap slightly, consistent with a real but modest effect.

**Effect size:** Cohen's d = 0.140 (session duration) → **small effect** by conventional thresholds (0.2/0.5/0.8 = small/medium/large). The conversion result clears p<0.05 but not by a wide margin. With n=10,000, even modest effects reach statistical significance, so effect size — not just the p-value — is the number to lead with.

## Segment Analysis (conversion rate by device)

| Device | Control | Treatment | Lift |
|---|---|---|---|
| Desktop | 50.17% (n=1,786) | 54.47% (n=1,744) | +4.30 pts (+8.6% relative) |
| Mobile | 44.04% (n=3,020) | 44.72% (n=2,925) | +0.68 pts (+1.5% relative) |
| Tablet | 50.74% (n=270) | 54.51% (n=255) | +3.77 pts (+7.4% relative) |

Desktop and tablet show the largest relative lift; mobile (the largest segment by user count) shows the smallest. These are descriptive comparisons only — no significance test or multiple-comparison correction has been applied at the segment level, so they should be treated as directional, not confirmed.

## Business Recommendations
See `Business_recommendations.md` for the full write-up. Summary: the result is promising but marginal — a confirmatory follow-up test is recommended before a full rollout decision, rather than treating this as conclusive.

## Limitations
- Simulated data, not real user behavior — treat findings as a methodology demonstration, not a business result
- No a priori power analysis was run to justify n=10,000; sample size was fixed by the simulation
- Segment-level differences are visualized but not formally tested, and no multiple-comparison correction has been applied
- Single fixed-endpoint analysis; no check for novelty effects or effect persistence over time
- T-test normality assumption not formally verified (session duration is exponentially distributed); the Mann-Whitney U test partially addresses this as a non-parametric robustness check

## Technologies
- Python (pandas, NumPy, SciPy, Matplotlib, Seaborn)
- Statistical hypothesis testing
- Data visualization

## Files
- `project2.ipynb` — full analysis notebook
- `ab_test_analysis.png` — visualizations
- `Business_recommendations.md` — detailed findings and recommendations

## Author
Harshavardhan Bandaru
- Email: bandaruharshavardhan2619@gmail.com
