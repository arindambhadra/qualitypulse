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
6. Prioritize:
   - P0: must pass before merge or release.
   - P1: high-value regression with strong dependency or exposure.
   - P2: targeted confidence for plausible contained impact.
   - P3: optional monitoring or exploratory coverage.
7. Recommend the smallest test set that covers the risk and explain exclusions.
8. Run focused tests only when authorized. Report the command, result, and limitation exactly.

## Output

Lead with Low, Medium, High, or Critical regression risk and summarize the blast radius.

| Priority | Area or scenario | Impact path | Recommended test | Existing evidence | Confidence |
|---|---|---|---|---|---|

Then separate automated execution, manual/exploratory checks, data/environment needs, post-deployment monitoring, exclusions, and unknowns.

## Guardrails

- Cite files, symbols, tests, or artifacts supporting material impact paths.
- Label plausible but unevidenced paths as hypotheses.
- Do not recommend full regression reflexively.
- Do not assume passing tests are relevant or sufficient.
- Do not modify code unless the user separately requests implementation.
