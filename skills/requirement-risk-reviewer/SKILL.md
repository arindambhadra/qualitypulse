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
5. Prioritize findings:
   - Critical: credible severe financial, legal, security, safety, or irreversible data harm.
   - High: likely release blocker or major customer/business disruption.
   - Medium: meaningful defect or operational friction with a viable workaround.
   - Low: localized quality issue or clarification with limited impact.
6. Draft acceptance criteria only for material gaps. Use Given/When/Then when it improves precision.
7. Recommend the minimum effective test approach, data, and environment needs.

## Output

Lead with a risk level and Ready, Ready with Clarifications, or Not Ready for Development.

| Priority | Gap or ambiguity | Why it matters | Proposed clarification or criterion | Evidence |
|---|---|---|---|---|

Then provide the highest-value test strategy, assumptions used to proceed, and material questions with a recommended owner.

## Guardrails

- Do not convert every conceivable edge case into a blocker.
- Do not claim an unavailable linked artifact lacks information.
- Do not invent expected results; label proposed behavior for Product confirmation.
- Separate supplied facts, derived findings, assumptions, and unknowns.
