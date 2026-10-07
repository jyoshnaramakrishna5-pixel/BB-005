# round-2 — Investigate

**Team:** BB-005
**Queries used:** 89

## What we concluded

Based on the Round-2 query results, the strongest APPROVE outcomes are associated with a combination of favorable parameter values rather than a single parameter acting alone.

* **anomaly_ratio** generally shows a positive relationship with the score.
* **badge_age_days** performs better in the observed lower range, particularly around 20–23 days.
* **clearance_level** is one of the strongest positive parameters. Values around 90–100 are repeatedly associated with high scores.
* **history_score** generally improves the score when it is in the higher observed range.
* **linked_badges** appears unfavorable when its value becomes high.
* **requested_zone** has a noticeable effect, with lower observed values generally producing stronger results.
* **site** appears relatively independent in the tested region because changing A/B/C/D does not consistently change the decision.
* **recent_denials** does not show a strong standalone relationship with the score.
* **tenure_years** generally has a positive association with higher scores.

The best observed result was **R2-89**, with a score of **0.9934** and an **APPROVE** decision.

## How we got there

We compared the Round-2 queries by looking for parameter changes that were followed by changes in score and decision.

Several groups of queries produced consistently high APPROVE scores, particularly queries around R2-20 through R2-89. The results show that high **clearance_level**, favorable **badge_age_days**, high **history_score**, and relatively low **linked_badges** frequently occur in high-scoring combinations.

The strongest negative evidence came from **R2-17 and R2-18**, where the score dropped to approximately **0.0320** and the decision changed to **DECLINE**. These queries contained relatively high **linked_badges** and unfavorable **requested_zone** values, indicating that their interaction may be important.

We also compared queries where categorical **site** values changed while most numerical parameters remained similar. The resulting scores remained high and the decision remained APPROVE, suggesting that site has limited standalone influence in this region.

## What we ruled out

* We did **not** find evidence that **site** alone determines APPROVE or DECLINE.
* We did **not** find evidence that **recent_denials** alone is a dominant driver of the score.
* We ruled out the assumption that one parameter alone explains the highest scores.
* We did not find a simple linear relationship where increasing every parameter always improves the result.
* Changes in **escorts** appear relatively weak compared with the stronger parameters.
* The DECLINE results cannot be attributed to a single parameter with certainty because multiple parameters changed together.

## What we are still unsure about

* The exact independent effect of each parameter is not fully established because many queries change more than one parameter at the same time.
* The interaction between **linked_badges** and **requested_zone** requires further investigation.
* The precise optimal value of **anomaly_ratio** is still uncertain; the observed high-performing region is around **0.725**, but additional queries are needed to determine whether higher or lower values can perform better.
* The exact contribution of **tenure_years** is not completely isolated from the other parameters.
* We need additional controlled queries where **only one parameter changes at a time** to distinguish causal effects from parameter interactions.
* Although R2-89 achieved **0.9934**, we have not yet demonstrated that this is the maximum possible score.

**Overall conclusion:** Round-2 indicates that the outcome is primarily driven by combinations of parameter values. The most promising region currently contains high clearance_level and history_score, moderate anomaly_ratio, badge_age_days around 20–23, and relatively low linked_badges/requested_zone values. Further controlled experimentation should focus on isolating individual effects and testing interactions.
