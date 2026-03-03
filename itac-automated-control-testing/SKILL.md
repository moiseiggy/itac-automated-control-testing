ITAC Automated Control Testing Skill
Description

Generate structured ITAC (Information Technology Application Control) testing documentation from technical and business-process evidence, including code snippets, configuration screenshots, data outputs, parameter tables, allocation datasets, routing logic, and threshold rules.

Use when the user asks to:

“Validate automated logic”

“Draft ITAC testing documentation”

“Build scenario test matrix”

“Validate tolerance logic”

“Document routing logic testing”

“Assess allocation logic”

“Separate design vs operating effectiveness”

“Draft IPE validation”

“Make sense of this automated control”

Purpose

This skill standardizes documentation for automated controls that:

Perform deterministic decision logic

Execute financial allocation

Route transactions based on attributes

Apply tolerance thresholds

Aggregate or transform business data

Generate automated outputs relied upon for financial reporting

Core Principles
1️⃣ Separate Design and Operating Effectiveness

Design Effectiveness evaluates:

Whether logic aligns with documented requirements

Whether thresholds and parameters are appropriate

Whether edge cases are addressed

Operating Effectiveness evaluates:

Whether logic executed correctly during the in-scope period

Whether outputs match expected behavior

Whether monitoring captured failures

2️⃣ Deterministic Logic Must Be Scenario Tested

Automated controls require:

Positive testing

Negative testing

Boundary testing

Sensitivity testing

Single “happy path” testing is insufficient.

3️⃣ Always Evaluate IPE (Information Produced by the Entity)

If the control relies on:

Reports

Data extracts

Aggregated datasets

System-generated files

Then IPE completeness and accuracy must be considered separately.

4️⃣ Avoid Overstating Assurance

Never state:

“The control ensures…”

Instead state:

“Based on the procedures performed, the logic appears to function as designed.”

Automated Control Types Supported

This skill applies to:

Approval routing logic

Risk-based decision engines

Financial allocation controls

Tolerance threshold controls

Aggregation logic (e.g., MEA / MPE)

Data transformation impacting financial reporting

Master file generation logic

Automated reconciliations

Migration / logic modernization testing

Output Structure Rules

When activated, the skill must:

Identify control objective

Determine logic type:

Routing

Threshold

Allocation

Aggregation

Transformation

Determine whether IPE applies

Separate:

Design Effectiveness

Operating Effectiveness

Select appropriate matrix template

Identify risks and red flags

Flag missing evidence if applicable

Risk Indicators to Flag

Hard-coded thresholds

OR vs AND misconfiguration

Missing negative testing

Lack of boundary testing

Unvalidated parameter tables

Silent filtering logic

Manual overrides not logged

Logic embedded in legacy components

No evidence of production deployment

Documentation Guardrails

Do not assume logic deployed unless evidenced.

Do not assume parameter completeness without validation.

Do not assume no exceptions = effective control.

Do not assume single sample proves universal logic.

Escalation Indicators

Escalate if:

No documentation of business rule

Threshold logic undocumented

Parameter tables editable without monitoring

No testing of edge cases

No production validation

Financial impact materiality unclear

Tone Requirements

Outputs must be:

Structured

Audit-defensible

Risk-aware

Technically accurate

Business-context aware

Clear and concise