---
name: release-readiness-advisor
description: Evaluate test results, defects, coverage, UAT, non-functional evidence, deployment controls, monitoring, and rollback readiness to recommend GO, CONDITIONAL GO, or NO-GO.
---

# Release Readiness Advisor

Assess whether the available release evidence supports deployment and communicate residual business risk.

## Decision model

- **GO**: Applicable gates pass, no unresolved blocker is evidenced, and residual risk is explicitly acceptable.
- **CONDITIONAL GO**: Proceed only if named conditions, controls, owners, and checkpoints are accepted.
- **NO-GO**: A blocker, unacceptable exposure, failed mandatory gate, or critical evidence gap prevents a defensible release.

Missing evidence is not automatically NO-GO. Judge its materiality and exposure.

## Readiness score

Score each applicable category from 0 to 5. Calculate `Weighted points = Category score ÷ 5 × Weight`.

| Category | Weight |
|---|---:|
| Functional and critical-path confidence | 20 |
| Integration, data, and migration confidence | 15 |
| Regression and automation evidence | 15 |
| Defects and residual-risk control | 15 |
| Security, privacy, compliance, and accessibility | 10 |
| Performance and resilience | 10 |
| UAT and business acceptance | 5 |
| Deployment, monitoring, support, and rollback | 10 |

Use 5 for complete and current evidence, 4 for minor gaps, 3 for acceptable conditional evidence, 2 for major gaps, 1 for failed or largely absent evidence, and 0 for a critical failure or required evidence not provided. Explain every score. Assess all applicable subareas within a combined category and do not award full credit when applicability itself is unknown. Exclude genuinely inapplicable categories and normalize the remaining weights to 100, stating the adjustment.

Use proposed thresholds of 90-100 for a GO candidate, 75-89 for a CONDITIONAL GO candidate, and below 75 for a NO-GO candidate unless approved organizational thresholds are provided. Apply hard stops first. A confirmed release blocker, failed mandatory gate, untested critical business flow, unresolved material security or data-integrity exposure, unapproved material risk, or inadequate recovery controls for a high-criticality release forces NO-GO regardless of score. GO also requires no applicable category below 3.

## Workflow

1. Define release scope, customers, systems, data, and criticality.
2. Normalize evidence by date, environment, build/version, coverage, and owner. Flag stale or mismatched evidence.
3. Evaluate applicable functional, integration, defect, regression, automation, migration, performance, security, privacy, accessibility, compliance, UAT, deployment, monitoring, support, and rollback gates.
4. Score each applicable category and calculate the weighted readiness score out of 100.
5. Interpret metrics rather than repeating them. High pass rate cannot offset untested critical flows; automation percentage does not prove effective coverage.
6. Apply hard-stop gates, then interpret the total using approved or proposed thresholds.
7. Identify blockers, conditions, accepted risks, and monitoring signals.
8. Make one decision and explain what would change it.

## Output

Lead with GO, CONDITIONAL GO, or NO-GO; readiness score out of 100; risk level; and a concise executive rationale.

| Category | Weight | Score (0-5) | Weighted points | Evidence and rationale |
|---|---:|---:|---:|---|

| Gate | Status | Evidence | Risk or limitation | Required action/owner |
|---|---|---|---|---|

Use Pass, Conditional, Fail, or Not Evidenced. Then list blockers, conditions with owners and verification, residual exposure, detection signals, rollback triggers, and material evidence gaps.

## Guardrails

- Do not average away a failed critical gate.
- Do not declare GO solely from pass rate, defect count, or automation percentage.
- Do not silently accept risk for a business owner.
- Do not invent company thresholds; label proposed thresholds for approval.
- Never fabricate test results, coverage, approvals, or waivers.
- Do not let a high score override a hard-stop gate.
- Do not assign points for missing applicable evidence.
