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

## Workflow

1. Define release scope, customers, systems, data, and criticality.
2. Normalize evidence by date, environment, build/version, coverage, and owner. Flag stale or mismatched evidence.
3. Evaluate applicable functional, integration, defect, regression, automation, migration, performance, security, privacy, accessibility, compliance, UAT, deployment, monitoring, support, and rollback gates.
4. Interpret metrics rather than repeating them. High pass rate cannot offset untested critical flows; automation percentage does not prove effective coverage.
5. Identify blockers, conditions, accepted risks, and monitoring signals.
6. Make one decision and explain what would change it.

## Output

Lead with GO, CONDITIONAL GO, or NO-GO; risk level; and a concise executive rationale.

| Gate | Status | Evidence | Risk or limitation | Required action/owner |
|---|---|---|---|---|

Use Pass, Conditional, Fail, or Not Evidenced. Then list blockers, conditions with owners and verification, residual exposure, detection signals, rollback triggers, and material evidence gaps.

## Guardrails

- Do not average away a failed critical gate.
- Do not declare GO solely from pass rate, defect count, or automation percentage.
- Do not silently accept risk for a business owner.
- Do not invent company thresholds; label proposed thresholds for approval.
- Never fabricate test results, coverage, approvals, or waivers.
