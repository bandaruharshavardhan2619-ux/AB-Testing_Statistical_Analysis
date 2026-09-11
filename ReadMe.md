# A/B Testing Statistical Analysis: Website Redesign Impact

## Overview
Comprehensive statistical analysis of an A/B test evaluating the impact of a website redesign on user engagement metrics.

## Business Problem
An e-commerce company needed to determine if a website redesign actually improved user engagement. Key questions:
- Does the redesign increase session duration?
- Does it improve conversion rate?
- Is the effect consistent across user segments?

## Dataset
- **Size:** 10,000 user sessions
- **Features:** Group (control/treatment), device, age, session duration, clicks, conversion
- **Split:** 50% control / 50% treatment

## Statistical Methods
1. **Two-Sample T-Test** — Session duration comparison
2. **Chi-Square Test** — Conversion rate analysis
3. **Mann-Whitney U Test** — Non-parametric click analysis
4. **Confidence Intervals (95%)** — All key metrics
5. **Effect Size (Cohen's d)** — Practical significance
6. **Segment Analysis** — Device-level treatment effects

## Key Findings
| Metric | Control | Treatment | Lift | P-value |
|--------|---------|-----------|------|---------|
| Conversion Rate | 2.8% | 3.4% | +21% | <0.001 |
| Session Duration | 245s | 280s | +14% | <0.001 |
| Clicks | 2.9 | 3.6 | +24% | <0.001 |

**Effect Size:** Cohen's d = 0.45 (moderate)

## Business Recommendations
1. Implement redesign — statistically and practically significant
2. Investigate desktop experience — weakest segment improvement
3. Run follow-up test — control for seasonality
4. Monitor long-term effects

## Technologies
- Python (pandas, NumPy, SciPy, Matplotlib, Seaborn)
- Statistical Analysis
- Data Visualization

## Files
- `ab_test_analysis.ipynb` — Full analysis notebook
- `ab_test_data.csv` — Dataset
- `ab_test_analysis.png` — Visualizations
- `business_recommendations.md` — Detailed findings

## Author
Harshavardhan Bandaru
- LinkedIn: [your link]
- Email: bandaruharshavardhan2619@gmail.com