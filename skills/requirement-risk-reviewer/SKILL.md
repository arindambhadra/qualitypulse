---
name: requirement-risk-reviewer
description: Review Jira stories, requirements, specifications, acceptance criteria, designs, and API contracts for ambiguity, missing behavior, testability gaps, and material delivery risk before development.
---

# Requirement Risk Reviewer

Review the supplied requirement before implementation. Proceed with explicit unknowns when only a short story is available.

## Workflow

1. State the intended user outcome and affected business capability.
2. Extract explicit actors, triggers, preconditions, rules, states, inputs, outputs, integrations, permissions, and success conditions.
3. Identify ambiguity, contradiction, missing behavior, untestable wording, and undefined terminology.
4. Examine relevant happy, alternate, negative, boundary, state-transition, concurrency, retry, idempotency, time-zone, localization, accessibility, authorization, privacy, audit, data, performance, resilience, observability, migration, and compatibility risks. Exclude irrelevant dimensions.
5. Score each material risk using `Risk score = Impact × Likelihood`:
   - Impact: 1 Negligible, 2 Minor, 3 Moderate, 4 Major, 5 Severe.
   - Likelihood: 1 Rare, 2 Unlikely, 3 Possible, 4 Likely, 5 Almost certain.
   - Risk bands: 1-4 Low, 5-9 Medium, 10-16 High, 17-25 Critical.
   Explain the evidence behind each rating and label uncertain ratings provisional.
6. Scale test coverage to risk: comprehensive critical-path, integration, negative, boundary, recovery, relevant non-functional, and monitoring coverage for Critical; broad functional and integration coverage for High; focused changed-path and dependency coverage for Medium; proportionate smoke or exploratory coverage for Low.
7. Draft acceptance criteria only for material gaps. Use Given/When/Then when it improves precision.
8. Recommend the minimum effective test approach, data, and environment needs.

## Output

Lead with a risk level and Ready, Ready with Clarifications, or Not Ready for Development.

| Risk | Impact | Likelihood | Score | Gap or ambiguity | Proposed clarification or criterion | Evidence |
|---|---:|---:|---:|---|---|---|

Then provide the highest-value test strategy, assumptions used to proceed, and material questions with a recommended owner.

## Guardrails

- Do not convert every conceivable edge case into a blocker.
- Do not claim an unavailable linked artifact lacks information.
- Do not invent expected results; label proposed behavior for Product confirmation.
- Separate supplied facts, derived findings, assumptions, and unknowns.
- Do not present a score without explaining its evidence and uncertainty.
