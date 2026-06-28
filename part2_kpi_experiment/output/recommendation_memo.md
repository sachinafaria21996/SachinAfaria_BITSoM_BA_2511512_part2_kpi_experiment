# Recommendation Memo: Onboarding & Activation Campaign A/B Test

## Executive Summary

- We recently concluded an A/B test evaluating a new onboarding and activation campaign (Treatment) against our existing experience (Control). The primary goal was to increase the percentage of new signups who successfully become paid subscribers.

- While the new campaign successfully drove a statistically significant increase in top-of-funnel conversions, it simultaneously triggered severe operational and revenue-quality guardrails.

- The new flow caused a ~67% increase in support tickets and a >50% drop in Average Revenue Per Converted User (ARPPU). 

- Because the costs (operational strain and revenue cannibalization) heavily outweigh the benefits of raw conversion volume, the recommendation is to NOT launch the campaign in its current state.

## North Star Metric

**Paid Conversion Rate**
- The percentage of total signed-up users who successfully transition to a paid subscription. 

- This was chosen as the North Star because it is the most definitive, bottom-line indicator that the onboarding experience successfully drove users to discover and pay for product value.

## KPI Tree Explanation

- To ensure a holistic view of the campaign, our North Star was supported by a KPI tree breaking down the user journey:

    - Top-of-Funnel: Landing Page Visit Rate, Average Engagement Score.

    - Activation: Onboarding Completion Rate, Trial Initiation Rate.

    - Purchase: Average Days to Convert, Plan Adoption Rate.

- Guardrails (Risk Protections): Support Ticket Rate, Refund Rate, and Average Revenue Per Converted User (ARPPU).

## Experiment Result Summary

- The test included 1,400 total users (690 Control, 710 Treatment).

- Control Conversion Rate: 3.19% (22 conversions)

- Treatment Conversion Rate: 7.04% (50 conversions)
The new campaign successfully pushed more than double the volume of users through the final conversion step.

## Hypothesis Test Interpretation

- Test Performed: Two-Proportion Z-Test (One-Tailed)

- Significance Level (Alpha): 0.05

- P-Value: 0.0005

- Conclusion: We reject the null hypothesis. The increase in the Paid Conversion Rate from 3.19% to 7.04% is highly statistically significant and not due to random chance.

## Guardrail Analysis

Despite the statistical win on the primary metric, the campaign violently breached our established risk guardrails:

- Support Ticket Rate (HIGH RISK): Increased from 14.78% to 24.79%. The new flow is generating massive user confusion, placing an unacceptable burden on the support team.

- Revenue Quality / ARPPU (HIGH RISK): Plunged from Rs 1,630.10 in the Control group to just Rs 770.41 in the Treatment group.

- Refund Rate (LOW-MEDIUM RISK): Ticked up from 0.00% to 0.42%, indicating a slight increase in buyer's remorse or accidental conversions.

## Segment-Level Insight

The severe drop in ARPPU reveals a critical segment-level behavioral shift. While the new onboarding flow is highly effective at getting users to click "Subscribe", the UX is almost entirely cannibalizing our Premium segment. 

Converting users in the Treatment group are overwhelmingly selecting the lowest-tier plans, destroying the aggregate value of the newly acquired customer base.

## Final Recommendation: Do Not Launch

- Decision: Do not launch the new onboarding campaign.
Although it successfully drives raw conversion volume, it sacrifices user experience (evidenced by the support ticket spike) and revenue quality (evidenced by the ARPPU crash). Launching this would result in a high-maintenance, low-value customer base that degrades overall business health.

## Risks and Limitations

- Time Horizon: This analysis is limited to a 30-day window. It is entirely possible that the low-tier users acquired by this campaign also exhibit higher month-two churn, which would make the ROI even worse than currently projected.

- Attribution: We assume the spike in support tickets is directly tied to onboarding friction, but we have not yet run NLP/text analysis on the actual ticket contents to confirm the exact nature of the user complaints.

## Next Steps

- UX Audit: The Product and Design teams must review the screen recordings and support ticket logs from the Treatment group to identify the exact friction points causing the 67% spike in support requests.

- Redesign Plan Selection: Overhaul the pricing/plan selection step within the new campaign to better highlight the value of Premium tiers and prevent the current race-to-the-bottom behavior.

- Iterate and Re-test: Once the friction points and plan selection architecture are fixed, launch a V2 of this campaign as a new A/B test.