# A/B Test Analysis: Website Redesign Impact

## Executive Summary
An A/B test with 10,000 simulated users evaluated whether a website redesign improved user engagement. Results show a statistically significant improvement in session duration and a marginally significant improvement in conversion rate. The practical effect size is small, so this reads as a promising but not decisive result.

## Methodology
- **Sample:** 10,000 users, randomly assigned (5,076 control / 4,924 treatment)
- **Data:** simulated, generated to mimic realistic engagement patterns (see `ReadMe.md` for the data-generating process)
- **Primary metrics:** conversion rate, session duration
- **Secondary metrics:** clicks, device-segment performance

## Statistical Results

| Metric | Control | Treatment | Change | P-value | Significant? |
|---|---|---|---|---|---|
| Conversion rate | 46.55% | 48.68% | +4.6% relative | 0.0349 | Yes, but marginally |
| Session duration | 264.75s | 305.23s | +15.3% relative | <0.00001 | Yes, strongly |
| Clicks | 2.98 | 4.51 | +51.3% relative | <0.00001 (Mann-Whitney) | Yes |

**Effect size (Cohen's d, session duration): 0.140** — a small effect by conventional standards. The statistical significance here is substantially a function of the large sample size (n=10,000); it should not be read as evidence of a large business impact.

## Segment Analysis (directional only — not formally tested)
- Desktop: 50.17% → 54.47% (+8.6% relative) — largest relative lift
- Tablet: 50.74% → 54.51% (+7.4% relative)
- Mobile: 44.04% → 44.72% (+1.5% relative) — smallest lift, and the largest user segment by volume

This is a reversal of a common assumption that redesigns land best on mobile; here, desktop and tablet show the stronger response while mobile — the majority of traffic — barely moves. That imbalance matters more for the overall rollout decision than the topline number does, since mobile dominates total volume.

## Business Recommendations
1. **Do not ship to all users yet.** The topline conversion result is statistically significant but only marginally so (p=0.035, small effect size), and it's driven disproportionately by desktop/tablet, which are smaller segments. A confirmatory follow-up test is warranted before committing to a full rollout.
2. **Investigate the mobile experience specifically.** Since mobile carries the most traffic but shows the smallest lift, understand whether the redesign is actually working as intended on mobile devices before treating this as a company-wide win.
3. **Run a follow-up test with a pre-registered power analysis.** Define the minimum effect size that would be commercially meaningful, calculate the required sample size in advance, and avoid post-hoc rationalization of a marginal p-value.
4. **If shipping, consider a phased rollout weighted toward desktop/tablet** where the effect is stronger, while continuing to test on mobile.
5. **Monitor for novelty effects.** This analysis is a single snapshot; a redesign's engagement lift sometimes fades once the initial novelty wears off, which this test cannot detect.

## Limitations
- Data is simulated, not from real users — treat this as a methodology exercise, not a production business result
- Segment differences are descriptive; no significance testing or multiple-comparison correction was applied at the device level
- No pre-test power analysis was performed; sample size was fixed by the simulation setup rather than derived from a minimum-detectable-effect target
- Single fixed-endpoint test; no data on whether the effect persists over time
- External factors (seasonality, concurrent promotions) are not present in this simulated dataset and would need to be controlled for in a real test
