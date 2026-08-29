# QualityPulse: AI Quality Engineering Lead

Turn requirements, code changes, and release evidence into clear, measurable quality decisions.

QualityPulse is an AI QA leadership toolkit for QA Managers, Quality Engineering Leads, Test Leads, and release decision-makers. It converts scattered delivery evidence into scored risks, focused test priorities, and defensible release recommendations. This helps leaders find expensive gaps earlier, direct limited testing effort toward the highest exposure, avoid unnecessary full regression, and communicate release risk consistently to Product, Engineering, and business stakeholders.

Every material risk is scored using impact multiplied by likelihood. Release assessments include a weighted readiness score out of 100 plus hard-stop gates that prevent critical blockers from being hidden by a high total.

## Leadership impact

- **Earlier risk visibility**: expose ambiguous requirements and missing controls before they become production defects or rework.
- **Smarter test investment**: increase coverage for high-risk areas and reduce effort on low-value regression.
- **Consistent governance**: apply the same transparent scoring logic across stories, changes, and releases.
- **Stronger release conversations**: replace subjective confidence with cited evidence, explicit unknowns, accountable conditions, and measurable readiness.
- **Faster executive communication**: provide concise risk summaries and release recommendations backed by detailed analysis.

## Included capabilities

- **QualityPulse QA Lead**: routes a request to the right workflow and produces a concise quality recommendation.
- **Requirement Risk Reviewer**: identifies ambiguity, missing acceptance criteria, testability gaps, and material delivery risks before development.
- **Regression Impact Analyzer**: traces code and dependency impact, scores regression risk, and recommends the smallest defensible test scope.
- **Release Readiness Advisor**: evaluates functional, integration, regression, defect, security, performance, UAT, deployment, monitoring, and rollback evidence to recommend GO, CONDITIONAL GO, or NO-GO.

## Installation

### Install from the Cursor Marketplace

After QualityPulse is approved and listed:

1. Open **Customize** in Cursor.
2. Search for **QualityPulse**.
3. Select **Install**.
4. Choose user scope to use it across projects or project scope for one workspace.

### Install locally on Windows

Open a PowerShell terminal in Cursor and run:

```powershell
New-Item -ItemType Directory -Force "$HOME\.cursor\plugins\local"
git clone https://github.com/arindambhadra/qualitypulse.git "$HOME\.cursor\plugins\local\qualitypulse"
```

Then press `Ctrl+Shift+P` and run `Developer: Reload Window`.

### Install locally on macOS or Linux

```bash
mkdir -p ~/.cursor/plugins/local
git clone https://github.com/arindambhadra/qualitypulse.git ~/.cursor/plugins/local/qualitypulse
```

Then reload Cursor using `Developer: Reload Window`.

### Update a local installation

Windows PowerShell:

```powershell
git -C "$HOME\.cursor\plugins\local\qualitypulse" pull
```

macOS or Linux:

```bash
git -C ~/.cursor/plugins/local/qualitypulse pull
```

Reload the Cursor window after updating.

## Verify the installation

1. Open **Customize** in Cursor.
2. Confirm that `qualitypulse-qa-lead` appears under Plugins.
3. Open **Skills** and confirm these skills appear:
   - `requirement-risk-reviewer`
   - `regression-impact-analyzer`
   - `release-readiness-advisor`

Skills can be selected automatically by the QualityPulse QA Lead or invoked directly with `/skill-name` in Agent chat.

## Usage examples

### Review a requirement before development

```text
Use /requirement-risk-reviewer to review this story before refinement.

As a customer, I can change the destination account for a scheduled recurring transfer. The change takes effect immediately.

Identify missing requirements and acceptance criteria. Score each material risk using impact multiplied by likelihood, and recommend test coverage based on the score.
```

Expected output includes a readiness assessment, prioritized risk table, 1-to-25 risk scores, proposed clarifications, and risk-based test coverage.

### Analyze regression impact from code changes

```text
Use /regression-impact-analyzer to analyze the current Git diff.

Trace direct and downstream impact, score each material regression risk, recommend the smallest defensible regression scope, and explain which areas can be excluded.
```

Expected output includes changed behavior, impact paths supported by repository evidence, P0-to-P3 priorities, risk scores, recommended tests, exclusions, and unknowns.

### Assess release readiness

```text
Use /release-readiness-advisor with this evidence:

- 196 of 200 regression tests passed
- Two failed tests affect payment processing
- One release-blocking payment defect remains open
- Security and performance testing passed
- UAT was approved
- Monitoring is ready
- Rollback has not been tested

Calculate the weighted readiness score out of 100 and recommend GO, CONDITIONAL GO, or NO-GO. Identify hard stops and the actions required to change the decision.
```

Expected output includes a weighted category scorecard, overall score, hard-stop evaluation, release recommendation, blockers, conditions, owners, and residual risk controls.

### Let the QA Lead select the workflow

```text
Use the QualityPulse QA Lead to evaluate this ticket, the related code changes, and the current release evidence. Run the applicable workflows in SDLC order and provide one consolidated quality recommendation.
```

## Scoring models

Requirement and regression risks use:

```text
Risk score = Impact × Likelihood
```

- 1 to 4: Low
- 5 to 9: Medium
- 10 to 16: High
- 17 to 25: Critical

Release-readiness candidates use these proposed thresholds unless an organization supplies approved thresholds:

- 90 to 100: GO candidate
- 75 to 89: CONDITIONAL GO candidate
- Below 75: NO-GO candidate

A confirmed blocker or failed mandatory gate overrides the numeric score.

## Design principles

- Evidence over confidence
- Business risk over generic test catalogues
- Explicit assumptions and unknowns
- Focused regression over reflexive full regression
- No invented requirements, test results, approvals, or organizational thresholds
- Scores supported by rationale rather than false precision

## Data and integrations

QualityPulse 1.0.0 has no external services, credentials, telemetry, or MCP connections. It analyzes information supplied in chat and repository evidence Cursor is already authorized to access. It does not modify code unless the user separately requests implementation.

## License

MIT
