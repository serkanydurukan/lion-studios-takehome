# Post-Experiment Analysis

---

### Q1. For all KPIs evaluated: describe your choices in evaluating them

- **Shop Icon Open Rate (Primary KPI):**  
  The main metric was the rate at which users opened the shop via the icon. This directly captures the behavior the new icon was intended to influence. The hypothesis was a +10% lift, so measuring icon click-through was the most direct way to test success.

- **Purchase Conversion Rate:**  
  We evaluated the percentage of users who made an in-app purchase. If more users visit the shop, ideally more should purchase. This downstream KPI shows if shop visits converted into transactions.

- **Revenue per User (ARPU):**  
  We tracked average revenue per user to measure monetization impact. Even if purchase rates shift, ARPU reveals whether revenue per user went up or down, capturing the net financial effect.

- **Engagement & Guardrail Metrics:**  
  Secondary metrics such as **any shop opens (via icon or interstitial)**, **sessions**, **levels played**, and **playtime** were examined to ensure the new design didn’t harm broader engagement. These guardrails confirm the icon didn’t unintentionally reduce gameplay or retention.

---

### Q2. What other data about users and their behaviour would you have also liked to have to evaluate this AB test?

- **Long-Term Retention & Revenue:**  
  Metrics like Day-7 or Day-14 retention would show if the effect persisted or evolved over time.

- **User Journey & Funnels:**  
  Data on **time-to-first-shop-open** or interstitial exposures per user would clarify if differences were due to the icon or other prompts.

- **Richer Segmentation:**  
  More user attributes (age, device type, prior spending behavior) could reveal subgroup-specific effects.

- **Qualitative Insights:**  
  User surveys or usability tests could help explain *why* the new icon was less effective (e.g., hard to notice, unclear purpose).

---

### Q3. For all statistical tests performed: describe those statistical tests, their assumptions, and why they are the appropriate choice

- **Two-Proportion z-Test (for rates):**  
  Used for binary outcomes like shop icon open rate and purchase conversion.  
  - **Assumptions:** independent random samples, large enough counts for normal approximation.  
  - With ~10k users per group, assumptions were satisfied, and results were highly significant.

- **Two-Sample Welch’s t-Test (for means):**  
  Applied to continuous metrics (ARPU, playtime, sessions).  
  - **Assumptions:** independent samples, approximate normality of sampling distribution of the mean.  
  - With large sample sizes, the Central Limit Theorem ensures validity even for skewed metrics like revenue. Welch’s test relaxes equal-variance assumptions.

- **Non-Parametric Check (Mann-Whitney U):**  
  Considered as robustness for skewed revenue distributions; results were consistent with t-tests.

Overall, the tests chosen matched the metric types and assumptions, ensuring validity of results.

---

### Q4. What was the outcome of the experiment?

The new shop icon **underperformed**:

- **Primary KPI (shop icon open rate):** Significantly lower in the variant group than control.  
- **Purchase Conversion & ARPU:** Both decreased in the variant.  
- **Engagement Metrics:** Shop opens, playtime, and sessions also dropped in the variant group.  

The outcome was the opposite of the intended +10% lift — instead, the redesign reduced shop engagement and monetization.

---

### Q5. How confident are you in this result? Why?

Confidence is **very high** due to:

- **Statistical significance:** p-values << 0.001 across key KPIs.  
- **Large sample size (~20k users):** high power, narrow confidence intervals.  
- **Consistency:** All major metrics pointed in the same negative direction.  
- **Proper randomization:** Groups were balanced, ensuring causal attribution.  

The chance that this is a false signal is negligible.

---

### Q6. What are your recommendations for Product as a result of this outcome?

- **Do not roll out the new icon.** The control clearly outperformed the variant.  
- **Investigate why the new icon failed.** Possible issues: visibility, intuitiveness, or visual clarity. Gather qualitative feedback.  
- **Iterate with new designs.** Consider making the shop button more prominent, adding a label, or using visual cues. Test again with A/B experiments.  
- **Explore alternative approaches.** Beyond icon design, try prompts, tutorials, or time-limited offers to increase shop visits.  
- **Maintain guardrail metrics.** Always ensure engagement and revenue are not harmed by UI changes.  

**Conclusion:** The tested icon design hurt performance. Stick with the current design while iterating on a better solution, guided by both quantitative and qualitative insights.
