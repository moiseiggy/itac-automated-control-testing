Purpose

This cheat sheet guides consistent, defensible ITAC testing for automated logic controls. It helps determine what to test, how to test, and how to document conclusions without overstating assurance.

1) Core ITAC Testing Mindset
ITAC testing must answer two questions:

Design: Is the logic designed to meet the control objective?

Operating: Did the logic operate as designed during the in-scope period?

A “happy path” demonstration alone is not sufficient. Automated logic requires scenario validation.

2) Logic Pattern Recognition

Use this to identify what you’re actually testing.

A. Routing / Decision Engine Logic

Common pattern:

if (attribute A) -> route to path X

if (A and B) -> route to Y

table-driven grid mapping

Testing emphasis:

sensitivity to attribute changes

OR vs AND correctness

parameter table governance

B. Threshold / Tolerance Logic

Common pattern:

if value >= threshold -> trigger

if abs(variance) <= tolerance -> accept

rounding + boundary behavior

Testing emphasis:

below / equal / above threshold

rounding rules

equality operator correctness (>= vs >)

C. Allocation / Sequencing Logic

Common pattern:

apply payments to fees → interest → principal

ordering by posting sequence and/or ordering keys

partial payment tolerance rules

Testing emphasis:

ordering correctness

before/after balance effects

multi-bucket allocations

D. Aggregation / Transformation Logic

Common pattern:

group by keys (account, facility, obligor)

sum, max, pick-highest logic

null handling default to zero

deduplication

Testing emphasis:

grouping key correctness

inclusion/exclusion rules

duplicate handling

3) Minimum Scenario Set (Default)

Unless clearly inapplicable, include:

Routing Controls

Positive (standard)

Elevated risk

Lower-bound case

Upper-bound case

Negative/exclusion case

Sensitivity test (change one attribute at a time)

Threshold Controls

Just below threshold

Exactly at threshold

Just above threshold

Invalid/edge input

Rounding edge (if applicable)

Allocation Controls

Standard payment

Partial payment (tolerance interaction)

Overpayment

Multi-component balances (fees + interest + principal)

Ordering collision (multiple transactions same day)

Aggregation Controls

Single-record aggregation

Multi-record aggregation

Duplicate record scenario (dedup)

Null-handling scenario

Sensitivity test (change one input)

4) Design Effectiveness Checklist

Use these prompts during walkthrough or code/config review:

What attributes drive the decision?

Where are the thresholds stored (code vs config)?

Is logic table-driven (grid) or hard-coded?

Are there overrides? If yes, how are overrides logged/approved?

Are there known exclusions (LGD A/B, statuses, etc.)?

What happens for null/missing attributes?

What is the expected behavior at boundary values?

What monitoring exists if the automated job fails?

What evidence proves logic is in production?

5) Operating Effectiveness Checklist

To confirm the logic ran during the period, look for:

Production execution logs / job runs

Output records showing logic branches executed

UI screenshots showing computed outputs

Downstream tables reflecting processed results

Monitoring alerts (or evidence of no exceptions)

Configuration version in effect during period

Avoid relying solely on:

QA testing

static screenshots without timestamps

“we didn’t change anything” without evidence

6) IPE (Information Produced by Entity) — When to Apply

IPE applies when testing relies on:

reports

system extracts

query outputs used as populations

reconciliation spreadsheets

IPE minimum expectations:

Identify source system / dataset

Confirm completeness (counts / tie-out)

Confirm accuracy (field-level spot check)

Confirm parameters (filters) and timeframe are appropriate

If IPE cannot be validated directly:

document reliance on downstream controls or system logs

scope conclusions accordingly

7) Common Logic Testing Pitfalls (Red Flags)
OR vs AND confusion

Evidence shows multiple criteria — verify if logic requires all conditions or any condition.

Hidden upstream filters

Data may be filtered before it reaches the tested UI/output.

Table-driven logic not tested

If routing uses mapping tables, validate table completeness and governance.

Single-sample testing

One sample cannot demonstrate deterministic logic across all branches.

Equality edge cases not tested

>= vs > errors only show up at boundaries.

Rounding assumptions

Interest/allocations frequently differ due to day count, rounding, compounding.

Null handling not validated

Missing attributes may default to zero or trigger fallbacks.

8) “Good Evidence” Map (What To Prefer)
Strongest evidence for ITAC:

Code/config + production execution evidence + scenario outputs

Acceptable combinations:

Code/config + production sample outputs

UI outputs + logs showing automation run + parameter table snapshot

Weak evidence (needs supplement):

QA-only testing

diagram-only

reviewer signoff only

summary narrative without artifacts

9) Documentation Language Guardrails

Use:

“tester determined…”

“based on evidence inspected…”

“appears to…”

“for the in-scope period…”

Avoid:

“ensures”

“guarantees”

“complete population” without count validation

“code in production” without deployment evidence

10) Quick “Pick the Right Matrix” Guide

Routing / decision engine → Scenario-Based Logic Matrix + Sensitivity Matrix

Threshold/tolerance → Boundary Matrix + Negative Matrix

Allocation → Allocation Sequence Matrix + Tolerance Matrix

Aggregation/transformation → Field-level + Sensitivity + Dedup/Null scenarios

Parameter table driven → Parameter Validation Matrix + Change Monitoring overlay

Migration/update → Pre/Post comparison + edge case validation

11) If Evidence Is Incomplete: Default Next Requests

production job execution logs for sample day

parameter table snapshot (as of in-scope date)

1 negative scenario output

monitoring alert configuration + one triggered example

code version / last change evidence (Git history)