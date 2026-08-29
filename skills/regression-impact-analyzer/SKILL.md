---
name: regression-impact-analyzer
description: Analyze Git diffs, pull requests, commits, changed files, release notes, or change descriptions to trace credible blast radius and recommend a prioritized, risk-based regression scope.
---

# Regression Impact Analyzer

Determine what the change could break and recommend a focused, defensible regression scope.

## Workflow

1. Summarize behavioral change separately from implementation detail.
2. Inspect changed files and trace imports, callers, shared types, configuration, schemas, events, APIs, persistence, feature flags, and deployment boundaries.
3. Locate relevant unit, component, API, integration, end-to-end, performance, security, and migration tests.
4. Separate direct impact, evidenced downstream impact, and uncertain impact. Do not equate code proximity with business risk.
5. Consider compatibility, authorization, data integrity, caching, async processing, retries, concurrency, observability, rollback, and failure recovery when relevant.
6. Score each material risk using `Risk score = Impact × Likelihood`:
   - Impact: 1 Negligible, 2 Minor, 3 Moderate, 4 Major, 5 Severe.
   - Likelihood: 1 Rare, 2 Unlikely, 3 Possible, 4 Likely, 5 Almost certain.
   - Risk bands: 1-4 Low, 5-9 Medium, 10-16 High, 17-25 Critical.
   Explain the evidence behind each rating and label uncertain ratings provisional.
7. Map risk to priority and coverage: P0 Critical gets comprehensive critical-path, integration, recovery, relevant non-functional, and monitoring coverage; P1 High gets broad functional, integration, negative, and boundary coverage; P2 Medium gets focused changed-path and dependency coverage; P3 Low gets proportionate smoke, exploratory, or monitoring coverage.
8. Recommend the smallest test set that covers the risk and explain exclusions.
9. Run focused tests only when authorized. Report the command, result, and limitation exactly.

## Output

Lead with Low, Medium, High, or Critical regression risk and summarize the blast radius.

| Priority | Risk | Impact | Likelihood | Score | Area or scenario | Impact path | Recommended test | Evidence |
|---|---|---:|---:|---:|---|---|---|---|

Then separate automated execution, manual/exploratory checks, data/environment needs, post-deployment monitoring, exclusions, and unknowns.

## Guardrails

- Cite files, symbols, tests, or artifacts supporting material impact paths.
- Label plausible but unevidenced paths as hypotheses.
- Do not recommend full regression reflexively.
- Do not assume passing tests are relevant or sufficient.
- Do not modify code unless the user separately requests implementation.
- Do not present a score without explaining its evidence and uncertainty.
