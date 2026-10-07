# round-4 — Reconstruct

**Team:** BB-005
**Queries used:** 80 / 80

## What we concluded
The system produces a score between 0 and 1 along with an APPROVE or DECLINE decision. The observed results indicate that the decision depends on a combination of multiple input parameters rather than one parameter alone. Several different inputs produce DECLINE with a score of 0.0320, indicating a possible score floor or repeated rejection behavior.

<!-- The short version. What is this system doing? -->

## How we got there
We analyzed the 80 Round-4 observations using all 10 available parameters: anomaly_ratio, badge_age_days, clearance_level, escorts, history_score, linked_badges, recent_denials, requested_zone, site, and tenure_years. We compared repeated inputs, scores, and decisions to identify consistent behavior and changes across observations.

<!-- The experiments that mattered, in order. Why each one was worth a query. -->

## What we ruled out
We ruled out the assumption that any single input parameter independently determines the final decision. APPROVE and DECLINE outcomes occur across different ranges of the individual parameters, and the site value alone does not explain the observed decisions.

<!-- Hypotheses you rejected and what killed them. This section carries real marks. -->

## What we are still unsure about
The exact scoring formula, feature weights, thresholds, and interactions between parameters are still unknown. In particular, the reason for repeated 0.0320 DECLINE scores and the exact conditions that cause sharp score reductions require additional controlled queries to confirm.

<!-- Being honest here scores better than overclaiming. -->
