# A/B Test Analysis: Onboarding & Activation Campaign

## Problem Statement
A subscription based product for the Company tested a new onboarding and activation campaign against the existing experience. 

- The decision to be made is  the best path forward, i.e Fully launch, Reject, Continue testing or Selectively launch the new onboarding experience.

- The decision will impact the new users, the customer support teams, the product and the marketing teams and also the Business stake holders. 

- For the new campaign to be considered a success, it should drive measurable improvements in the following primary KPIs :

    - Primary Conversion
    - Revenue Uplift
    - Upstream Activation

- The following metrics must be actively monitored to understand the risk of the new campaign deployment:

    - Increased flux in **Support Ticket** within the first month of product usage.

    - Any spike in users **requesting refunds**, which would indicate user dissatisfction or accidental conversions.

    - Instances of **dropping engagement score**.

- Before advising a final decision, the following evidence must be analysed:

    - **Statistical Significance** : Proof that any observed uplift in conversion rates and 30-day revenue in the treatment group is statistically significant, rather than random variance.

    - **Stability**: Clear evidence that the new campaign did not trigger a disproportionate or unacceptable increase in refund rates or support tickets compared to the control group.

    - **Segment Analysis**: A deep dive into demographics (device type, traffic source, region, plan type) to identify if the campaign's success is spread out or isolated to specific user cohorts, which would justify a targeted launch.

    - **Net Gain**: Confirmation that the financial gains from increased conversions outweigh the operational costs of any additional support tickets or refunded revenue.



## Dataset Description
The dataset contained 1,400 unique user records split across Control (690 users) and Treatment (710 users) groups. It had data regarding the following:

- It tracked user progression through an activation funnel - landing page visits, trial starts, onboarding completion, final paid conversions, 30-day revenue..

- Iy contained critical guardrail metrics like support tickets, refund requests. 

- It contained additional demographic and acquisition data including region, device type, traffic source, plan type which is instrumental for segment analysis. 

## North Star Metric Selected
**Paid Conversion Rate** - This metric was selected as the North Star because it is the definitive indicator of successful activation. 

While leading indicators (like onboarding completion) show progress, they do not guarantee that the user recognized sufficient product value to warrant a purchase.

For an A/B test evaluating a new onboarding and activation campaign, the North Star metric should be the Paid Conversion Rate—the percentage of users who successfully transition from a free or trial state to a paid subscription (converted_to_paid = 1).

### Why this metric is the main success metric

- The fundamental purpose of any onboarding and activation flow is to guide users to the point where they recognize the product's value. 

- If the new campaign successfully communicates this value and removes friction, the most definitive proof of that success will be the user's willingness to pay. 

- It is the clearest, most direct signal that the activation phase has achieved its goal.

### Why other metrics are supporting metrics instead of the North Star

- Other metrics in the dataset provide critical context, but they are either leading indicators, proxies, or lagging indicators, rather than the core measure of activation success:

    - **Funnel Metrics** : It includes visited_landing_page, started_trial, and  completed_onboarding. These are leading indicators and are excellent for diagnosing where users drop off in the funnel, however optimizing for them doesn't guarantee business value.
    
            For example: A user might complete onboarding just to make a notification go away or on peer feedback, without ever intending to subscribe.

    - **Proxy Metrics** : The engagement_score is a strong behavioral signal, but it is still a proxy for value. High engagement without conversion means the product is interesting, but not necessarily useful enough to warrant a purchase.

    - **Lagging Metrics** : While revenue_30d metric indicating revenue in last 30 days is the ultimate business goal, using it as the strict North Star for an onboarding test can be noisy. 
    
            For example: Revenue can be heavily skewed by a small handful of users choosing the "Premium" plan, masking the fact that the campaign might have actually failed to activate the broader majority of free/ trial users.

### How this metric connects to business growth

The Paid Conversion Rate is a fundamental multiplier in a subscription business model. 

Improving this metric directly increases the volume of the active, paying customer base. 

By converting a higher percentage of the top-of-funnel traffic, the business effectively lowers its Customer Acquisition Cost payback period, increases overall Monthly Recurring Revenue, and drives sustainable, scalable growth without needing to artificially inflate marketing spend.

### What could go wrong if this metric is optimized blindly

Relentlessly optimizing for the highest possible conversion rate can severely backfire if user intent and satisfaction are ignored.

If the new campaign relies on misleading trial terms, countdown timers, or confusing UI that causes accidental subscriptions—the Paid Conversion Rate will spike artificially. However, this blind optimization leads to:

- Operational Strain: A massive surge in support_tickets_30d as confused users try to cancel.

- Revenue Churn: Immediate spikes in refund_requested, turning "new revenue" into a liability and incurring payment processing penalties.

- Long-Term Damage: Immediate churn in first few months will cause permanent damage to brand reputation, ultimately destroying Customer Lifetime Value despite a technically "winning" A/B test.

## KPI Tree Summary
The North Star metric was broken down into the following drivers:
* **Top-of-Funnel Engagement:** Landing Page Visit Rate, Average Engagement Score
* **Onboarding & Activation Success:** Onboarding Completion Rate, Trial Initiation Rate
* **Purchase Decision Effectiveness:** Average Days to Convert, Premium Plan Adoption Rate

## Experiment Analysis Approach
1.  **Data Quality Checks:** The dataset was checked for missing values, group balance, duplicate IDs, invalid binary flags, revenue outliers, and segment distribution to ensure the validity of the A/B test. 

2.  **Summary Statistics:** Calculated aggregate metrics and segment-level breakdowns of Region, Device, Traffic, Plan was done to effectively compare Control vs. Treatment performance.

3.  **Statistical Testing:** Conducted a formal hypothesis test to determine if the observed uplift in the primary metric was statistically significant.

## Hypothesis Test Summary
* **Test Used:** Two-Proportion Z-Test (One-tailed)
* **Null Hypothesis ($H_0$):** The new campaign does not increase the Paid Conversion Rate.
* **Significance Level:** $\alpha = 0.05$
* **Results:** The Treatment group showed a conversion rate of 7.04% compared to the Control group's 3.19%. The test yielded a Z-statistic of 3.2640 and a p-value of 0.0005. 
* **Statistical Conclusion:** Because the p-value is $< 0.05$, we reject the null hypothesis. The increase in conversion rate is highly statistically significant.

## Guardrail Metrics Considered
* **Support Ticket Rate:** Increased from 14.78% (Control) to 24.79% (Treatment).
* **Refund Rate:** Increased from 0.00% (Control) to 0.42% (Treatment).
* **Average Revenue Per Converted User (ARPPU):** Plummeted from Rs 1,630.10 (Control) to Rs 770.41 (Treatment).

## Final Recommendation
**Decision: Reject the campaign in its current form.**
While the statistical test proves the campaign successfully drove more users to convert, the guardrail metrics reveal a toxic user experience. The massive drop in Average Revenue Per Converted User (ARPPU) combined with the near-doubling of support tickets indicates the new flow is highly confusing and pushes users solely into the lowest tier, placing an unacceptable operational burden on the business. Send the onboarding flow back to the product team to fix these friction points before re-testing.

## Assumptions and Limitations
* **Time Horizon:** Revenue and support tickets are limited to a 30-day window. Long-term retention (LTV) and churn beyond month one cannot be assessed with this dataset.
* **Attribution:** It is assumed that all metrics recorded for a user within the 30-day window are directly attributable to their assigned onboarding experience.
* **Engagement Score:** The internal engagement score is assumed to be a valid and consistent proxy for user interest, though the exact calculation method is unknown.

## Screenshots Included
* summary_metrics.png
* hypothesis_test_output.png
* kpi_tree_preview.png