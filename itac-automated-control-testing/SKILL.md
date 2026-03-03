# ITAC Automated Control Testing Skill

> Generate structured ITAC (IT Application Control) testing documentation
> from technical and business-process evidence — code snippets, configuration
> screenshots, data outputs, parameter tables, allocation datasets, routing
> logic, and threshold rules.

---

## Activation Triggers

Use this skill when asked to:

- "Validate automated logic"
- "Draft ITAC testing documentation"
- "Build a scenario test matrix"
- "Validate tolerance logic"
- "Document routing logic testing"
- "Assess allocation logic"
- "Separate design vs. operating effectiveness"
- "Draft IPE validation"
- "Make sense of this automated control"

---

## Purpose

This skill standardizes documentation for automated controls that:

- Perform deterministic decision logic
- Execute financial allocation
- Route transactions based on attributes
- Apply tolerance thresholds
- Aggregate or transform business data
- Generate automated outputs relied upon for financial reporting

---

## Core Principles

### 1. Separate Design and Operating Effectiveness

| Dimension | What It Evaluates |
|---|---|
| **Design** | Whether logic aligns with documented requirements · Whether thresholds and parameters are appropriate · Whether edge cases are addressed |
| **Operating** | Whether logic executed correctly during the in-scope period · Whether outputs match expected behavior · Whether monitoring captured failures |

---

### 2. Deterministic Logic Must Be Scenario Tested

Automated controls require all four of the following:

- Positive testing
- Negative testing
- Boundary testing
- Sensitivity testing

Single "happy path" testing is never sufficient.

---

### 3. Always Evaluate IPE

If the control relies on reports, data extracts, aggregated datasets,
or system-generated files — IPE completeness and accuracy must be
considered separately from the control itself.

---

### 4. Avoid Overstating Assurance

| Instead of... | Use... |
|---|---|
| "The control ensures..." | "Based on the procedures performed, the logic appears to function as designed." |
| "All transactions are..." | "For the in-scope sample reviewed..." |
| "Complete population..." | "Based on evidence inspected..." |

---

## Automated Control Types Supported

- Approval routing logic
- Risk-based decision engines
- Financial allocation controls
- Tolerance threshold controls
- Aggregation logic (MEA / MPE)
- Data transformation impacting financial reporting
- Master file generation logic
- Automated reconciliations
- Migration / logic modernization testing

---

## Output Structure

When activated, this skill executes in the following sequence:

1. Identify the control objective
2. Determine the logic type — Routing · Threshold · Allocation · Aggregation · Transformation
3. Determine whether IPE applies
4. Separate Design Effectiveness from Operating Effectiveness
5. Select the appropriate matrix template
6. Identify risks and red flags
7. Flag missing evidence where applicable

---

## Risk Indicators to Flag

| Risk | Description |
|---|---|
| Hard-coded thresholds | Values embedded in code rather than governed config |
| OR vs. AND misconfiguration | Multi-condition logic applied incorrectly |
| Missing negative testing | No exclusion or rejection scenario tested |
| Missing boundary testing | Threshold edges not validated |
| Unvalidated parameter tables | Config values not independently confirmed |
| Silent filtering logic | Records excluded upstream without disclosure |
| Manual overrides not logged | Exceptions processed outside audit trail |
| Legacy-embedded logic | Rules buried in undocumented legacy components |
| No production deployment evidence | Code reviewed but deployment unconfirmed |

---

## Documentation Guardrails

- Do not assume logic is deployed unless evidenced
- Do not assume parameter completeness without validation
- Do not assume no exceptions = effective control
- Do not assume a single sample proves universal logic behavior

---

## Escalation Indicators

Escalate if any of the following are present:

- No documentation of the underlying business rule
- Threshold logic is undocumented
- Parameter tables are editable without monitoring
- No testing of edge or boundary cases
- No production validation evidence
- Financial impact materiality is unclear

---

## Tone Requirements

All outputs must be:

- Structured and audit-defensible
- Risk-aware and technically accurate
- Business-context aware
- Clear and concise

---

*This skill provides documentation structure and workflow guidance for
IT audit and SOX testing workflows. It does not replace professional
judgment, control design evaluation, or formal audit standards.*
