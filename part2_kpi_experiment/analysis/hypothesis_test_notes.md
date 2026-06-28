# Hypothesis Test Notes

## Selected Metric
**Metric Being Tested:** Paid Conversion Rate (`converted_to_paid`)

**Reason for Choosing That Metric:** As defined in the North Star metric analysis, the Paid Conversion Rate is the definitive indicator of successful activation.

 While leading indicators (like onboarding completion) provide context, they do not guarantee business value. We must test the conversion rate to ensure the new campaign actually drives users to recognize product value and make a purchase, directly impacting the business's bottom line and customer acquisition efficiency.

## Statistical Analysis

### Null Hypothesis ($H_0$)
The new onboarding campaign (Treatment) does not increase the Paid Conversion Rate compared to the existing experience (Control).

### Alternate Hypothesis ($H_1$)
The new onboarding campaign (Treatment) significantly increases the Paid Conversion Rate compared to the existing experience (Control).


### Test Directionality
**One-tailed or Two-tailed:** One-tailed test.


### Significance Level ($\alpha$)
**Significance Level Used:** $\alpha = 0.05$


## Interpretation Logic & Business Decision Matrix

After calculating the p-value from the statistical test, we will interpret the results alongside the guardrail metrics to make a final recommendation:

1. **If p-value < 0.05 AND Guardrails are stable:**
   * *Interpretation:* We reject the Null Hypothesis. The uplift is statistically significant, and the business is not at risk from high refunds or support strain.
   * *Business Decision:* **Fully Launch** the new campaign.

2. **If p-value < 0.05 BUT Guardrails are breached (e.g., Support tickets spike):**
   * *Interpretation:* We reject the Null Hypothesis (conversion increased), but the "quality" of the conversion is bad for the business. 
   * *Business Decision:* **Reject** the campaign in its current form. Send back to the product team to fix the friction/confusion causing the support overhead before re-testing.

3. **If p-value $\ge$ 0.05:**
   * *Interpretation:* We fail to reject the Null Hypothesis. The observed increase in conversion is not statistically significant and could be due to random chance. 
   * *Business Decision:* **Reject** the campaign, or analyze segment data to see if a **Selective Launch** is warranted for specific user cohorts where the campaign performed exceptionally well.
