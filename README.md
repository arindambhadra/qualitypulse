# QualityPulse: AI Quality Engineering Lead

Turn software evidence into confident quality decisions.

QualityPulse is a free, evidence-based Quality Engineering plugin for Cursor. It adds one coordinating QA Lead agent and three specialized skills:

- **Requirement Risk Reviewer**: finds ambiguity, missing acceptance criteria, testability gaps, and material delivery risks before development.
- **Regression Impact Analyzer**: traces credible change impact and recommends the smallest defensible regression scope.
- **Release Readiness Advisor**: evaluates test, defect, coverage, UAT, operational, and non-functional evidence to recommend GO, CONDITIONAL GO, or NO-GO.

Version 0.2.0 adds impact-by-likelihood risk scores, risk-based test-depth recommendations, and a weighted release-readiness score out of 100 with hard-stop gates.

## Example requests

```text
Use the QualityPulse QA Lead to review this Jira story before refinement.

Analyze the current Git diff and recommend a prioritized regression scope.

Based on these test results and open defects, is release 2.0 ready for production?
```

## Design principles

- Evidence over confidence
- Business risk over generic test catalogues
- Explicit assumptions and unknowns
- Focused regression over reflexive full regression
- No invented requirements, test results, approvals, or organizational thresholds

## Data and integrations

Version 0.2.0 has no external services, credentials, telemetry, or MCP connections. It analyzes information supplied in chat and repository evidence Cursor is already authorized to access. It does not modify code unless the user separately requests implementation.

## Local testing

Load the repository as a local Cursor plugin, then try each example request against non-sensitive sample artifacts. Confirm that the requested skill activates, material claims cite available evidence, and missing inputs are labeled as unknown.

## Installation

Clone or download this repository, then load it as a local Cursor plugin. The package follows Cursor's plugin layout and can also be prepared for Marketplace submission from this repository.

## License

MIT
