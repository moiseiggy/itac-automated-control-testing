# ITAC Logic Testing Cheat Sheet

> A quick-reference guide for consistent, defensible automated control testing.
> Covers what to test, how to test it, and how to document conclusions
> without overstating assurance.

---

## 1. Core Testing Mindset

Every ITAC engagement must answer two questions:

| Question | Focus |
|---|---|
| **Design** | Is the logic designed to meet the control objective? |
| **Operating** | Did the logic operate as designed during the in-scope period? |

A "happy path" demonstration alone is never sufficient.
Automated logic requires scenario validation.

---

## 2. Logic Pattern Recognition

### A. Routing / Decision Engine Logic

**Common patterns:**
- `if (attribute A) -> route to path X`
- `if (A and B) -> route to Y`
- Table-driven grid mapping

**Testing emphasis:** Sensitivity to attribute changes · OR vs. AND correctness · Parameter table governance

---

### B. Threshold / Tolerance Logic

**Common patterns:**
- `if value >= threshold -> trigger`
- `if abs(variance) <= tolerance -> accept`
- Rounding + boundary behavior

**Testing emphasis:** Below / equal / above threshold · Rounding rules · Equality operator correctness (`>=` vs `>`)

---

### C. Allocation / Sequencing Logic

**Common patterns:**
- Apply payments: fees → interest → principal
- Ordering by posting sequence and/or ordering keys
- Partial payment tolerance rules

**Testing emphasis:** Ordering correctness · Before/after balance effects · Multi-bucket allocations

---

### D. Aggregation / Transformation Logic

**Common patterns:**
- Group by keys (account, facility, obligor)
- Sum / max / pick-highest logic
- Null handling defaulting to zero
- Deduplication

**Testing emphasis:** Grouping key correctness · Inclusion/exclusion rules · Duplicate handling

---

## 3. Minimum Scenario Sets

### Routing Controls
- Positive (standard)
- Elevated risk
- Lower-bound case
- Upper-bound case
- Negative / exclusion case
- Sensitivity test (change one attribute at a time)

### Threshold Controls
- Just below threshold
- Exactly at threshold
- Just above threshold
- Invalid / edge input
- Rounding edge *(if applicable)*

### Allocation Controls
- Standard payment
- Partial payment (tolerance interaction)
- Overpayment
- Multi-component balances (fees + interest + principal)
- Ordering collision (multiple transactions same day)

### Aggregation Controls
- Single-record aggregation
- Multi-record aggregation
- Duplicate record scenario (dedup)
- Null-handling scenario
- Sensitivity test (change one input)

---

## 4. Design Effectiveness Checklist

Ask these during walkthrough or code/config review:

- [ ] What attributes drive the decision?
- [ ] Where are thresholds stored — code vs. config?
- [ ] Is logic table-driven (grid) or hard-coded?
- [ ] Are there overrides? If yes, how are they logged/approved?
- [ ] Are there known exclusions (LGD A/B, statuses, etc.)?
- [ ] What happens for null / missing attributes?
- [ ] What is expected behavior at boundary values?
- [ ] What monitoring exists if the automated job fails?
- [ ] What evidence proves logic is in production?

---

## 5. Operating Effectiveness Checklist

To confirm logic ran during the period, look for:

- [ ] Production execution logs / job runs
- [ ] Output records showing logic branches executed
- [ ] UI screenshots showing computed outputs (with timestamps)
- [ ] Downstream tables reflecting processed results
- [ ] Monitoring alerts (or evidence of no exceptions)
- [ ] Configuration version in effect during the period

**Avoid relying solely on:**
- QA testing only
- Static screenshots without timestamps
- "We didn't change anything" without supporting evidence

---

## 6. IPE Validation — When to Apply

IPE applies when testing relies on:

- Reports
- System extracts
- Query outputs used as populations
- Reconciliation spreadsheets

### IPE Minimum Expectations

| Step | What to Do |
|---|---|
| Source | Identify source system / dataset |
| Completeness | Confirm counts / tie-out |
| Accuracy | Perform field-level spot check |
| Parameters | Confirm filters and timeframe are appropriate |

**If IPE cannot be validated directly:**
document reliance on downstream controls or system logs and scope conclusions accordingly.

---

## 7. Common Testing Pitfalls

| Red Flag | What to Watch For |
|---|---|
| OR vs. AND confusion | Verify if logic requires all conditions or any condition |
| Hidden upstream filters | Data may be filtered before reaching the tested output |
| Table-driven logic not tested | Validate mapping table completeness and governance |
| Single-sample testing | One sample cannot demonstrate all logic branches |
| Equality edge cases missed | `>=` vs `>` errors only surface at boundaries |
| Rounding assumptions | Allocations differ due to day count, rounding, compounding |
| Null handling not validated | Missing attributes may default to zero or trigger fallbacks |

---

## 8. Evidence Quality Map

| Strength | Evidence Combination |
|---|---|
| **Strongest** | Code/config + production execution evidence + scenario outputs |
| **Acceptable** | Code/config + production sample outputs |
| **Acceptable** | UI outputs + automation run logs + parameter table snapshot |
| **Weak — supplement required** | QA-only testing |
| **Weak — supplement required** | Diagram only |
| **Weak — supplement required** | Reviewer sign-off or summary narrative without artifacts |

---

## 9. Documentation Language Guardrails

| Use | Avoid |
|---|---|
| "Tester determined..." | "Ensures" |
| "Based on evidence inspected..." | "Guarantees" |
| "Appears to..." | "Complete population" (without count validation) |
| "For the in-scope period..." | "Code in production" (without deployment evidence) |

---

## 10. Quick Matrix Selection Guide

| Control Type | Use These Matrices |
|---|---|
| Routing / decision engine | Scenario-Based Logic Matrix + Sensitivity Matrix |
| Threshold / tolerance | Boundary Matrix + Negative Matrix |
| Allocation | Allocation Sequence Matrix + Tolerance Matrix |
| Aggregation / transformation | Field-Level + Sensitivity + Dedup/Null Scenarios |
| Parameter table-driven | Parameter Validation Matrix + Change Monitoring Overlay |
| Migration / update | Pre/Post Comparison + Edge Case Validation |

---

## 11. If Evidence Is Incomplete — Default Next Requests

- Production job execution logs for a sample day
- Parameter table snapshot (as of in-scope date)
- At least one negative scenario output
- Monitoring alert configuration + one triggered example
- Code version / last change evidence (e.g. Git history)

---

*This cheat sheet provides structured reasoning guidance for IT audit workflows.
It does not replace professional judgment or formal audit standards.*
