# Statistical Hypothesis Testing Documentation

This document formalizes the hypothesis parameters, core testing design, and interpretation criteria used to validate the activation experiment.

## 1. Experimental Setup & Parameters
- *Primary Tested Metric:* Paid Conversion Rate ($P$)
- *Significance Level ($\alpha$):* 0.05 (Standard 95% Confidence Interval baseline)
- *Statistical Test Selection:* Two-Tailed Z-Test for Two Independent Proportions
- *Business Justification:* A two-tailed configuration is intentionally applied to protect the organization against bidirectional risk. It checks if the new onboarding campaign creates a statistically superior lift or if it unexpectedly degrades the baseline user conversion journey compared to the legacy control cohort.

## 2. Hypothesis Formalization
- *Null Hypothesis ($H_0$):* $P_{\text{Treatment}} = P_{\text{Control}}$
  * Business Interpretation: The new onboarding and activation campaign experience has no statistical impact on the user's paid conversion rate. Any observed variance between the cohorts is entirely due to random sampling noise or baseline variance.
- *Alternative Hypothesis ($H_1$):* $P_{\text{Treatment}} \neq P_{\text{Control}}$
  * Business Interpretation: The new onboarding and activation campaign experience drives a mathematically significant difference in the paid conversion rate compared to the existing legacy workflow.

## 3. Metric Selection Rationale
The *Paid Conversion Rate* is established as the sole target metric for this hypothesis validation because it serves as the ultimate revenue-driving metric for subscription businesses. While leading indicators like landing page visit rates or onboarding step completions track initial engagement, they do not confirm a user's baseline financial commitment to cross the commercial paywall.

## 4. Interpretation Decision Rules
To make an objective data-backed decision, the following evaluation rules are set against the computed P-value:
- *Reject $H_0$ ($P\text{-value} < 0.05$):* We formally drop the Null Hypothesis. This serves as mathematical proof that the campaign lift is genuine, moving the decision forward to the operational risk and guardrail assessment phase.
- *Fail to Reject $H_0$ ($P\text{-value} \geq 0.05$):* We retain the Null Hypothesis. This indicates that the treatment group’s variance is mathematically insignificant, meaning the new campaign cannot be recommended for public rollout.

## 5. Statistical Test Execution Output
The calculation metrics processed from the A/B testing raw records show the following exact figures:

| Calculation Field Element | Control Baseline Value | Treatment Variant Value |
| :--- | :---: | :---: |
| Total Experimental Population ($n$) | 690 Users | 710 Users |
| Unique Paid Conversions ($x$) | 22 Conversions | 50 Conversions |
| Calculated Conversion Rate ($P$) | 3.19% | 7.04% |
| *Computed Z-Statistic Score* | *3.3165* | |
| *Two-Tailed Computed P-Value* | *0.0009* | |

## 6. Business Evaluation and Decision Rule Verification
- *Statistical Decision:* Since the calculated P-value ($0.0009$) is strictly less than our pre-determined significance threshold ($\alpha = 0.05$), we formally *REJECT the Null Hypothesis ($H_0$)*.
- *Business Interpretation:* The positive expansion of the Paid Conversion Rate from 3.19% to 7.04% is statistically valid. The lift is not a product of random sampling fluctuation or systematic database noise. The new onboarding layout drives a genuine behavioral modification that increases user conversion intent.