Data Science Lab: A/B Testing, Statistical Power, and Selection Bias

Project Overview

In this lab, I evaluated an underpowered A/B test and investigated selection bias in an observational wellness-program study. I used statistical power calculations, Cohen's h, logistic regression, and inverse probability weighting (IPW) to assess experimental design and improve treatment-effect estimation.

1. A/B Testing and Statistical Power

I audited an A/B test in which a product manager allocated only 1,000 of 50,000 users (2%) to the treatment group and 49,000 to the control group.

The experiment had only 19.8% power to detect a 0.8 percentage-point improvement in conversion rates, from 5.0% to 5.8%.

Cohen's h was 0.0354, indicating a small effect size.

Achieving 80% power required 12,514 users per group, meaning the original treatment group was 11,514 users short.

I developed a power_check function using Cohen's h and the normal distribution and checked its calculations against the lab's statistical power analysis.

Splitting the same 50,000 users evenly into groups of 25,000 would have increased statistical power to approximately 97.7%.

This demonstrated how unequal sample allocation can substantially reduce an experiment's ability to detect meaningful changes.

2. Diagnosing Selection Bias

I investigated a wellness-program comparison involving 5,000 employees, including 2,111 participants and 2,889 non-participants.

The naive comparison produced the following results:

Average participant cost: $11,725

Average non-participant cost: $13,121

Naive estimated effect: -$1,396

True treatment effect: -$500

Naive estimation bias: -$896

The initial analysis suggested that the wellness program saved $1,396 per employee, substantially exaggerating the true savings of $500.

This demonstrated how differences in baseline health and treatment selection can distort conclusions drawn from observational data.

3. Correcting Selection Bias With IPW

I estimated propensity scores using logistic regression, with baseline health as the predictor of wellness-program participation. I then applied inverse probability weighting to adjust for differences in treatment assignment probabilities.

The analysis produced the following results:

True treatment effect: -$500

Naive treatment-effect estimate: -$1,396

IPW-adjusted estimate: -$522

Naive estimation bias: -$896

IPW estimation bias: -$22

The IPW adjustment reduced the absolute estimation bias from $896 to $22, a reduction of approximately 97.5%.

The estimated propensity scores ranged from 0.145 to 0.936 overall. The treated and untreated groups had overlapping propensity-score ranges, providing evidence of overlap in their estimated treatment probabilities.

These results showed that IPW substantially improved the treatment-effect estimate by accounting for observed differences in treatment selection.

4. Key Findings

The lab highlighted two important challenges in data science: insufficient statistical power and selection bias.

The A/B testing analysis demonstrated that allocating only 2% of users to treatment resulted in low statistical power, despite having 50,000 total users. A balanced allocation would have made the experiment considerably more effective.

The wellness-program analysis showed that an unadjusted comparison substantially overstated program savings. Applying IPW reduced the estimation bias by approximately 97.5%, bringing the estimated effect much closer to the true value.

Conclusion

This lab strengthened my understanding of experimental design, statistical power, causal inference, and bias correction. I learned how to calculate sample size requirements, evaluate A/B testing power, estimate propensity scores, and apply inverse probability weighting.

The results demonstrated that reliable data-driven conclusions require both appropriate experimental design and careful adjustment for confounding factors in observational studies.# econ5200-lab06-experiment-audit
