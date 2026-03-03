# Automated Control Objective → Testing Approach Mapper

> This document maps ITAC control objectives to required testing approaches,
> scenario dimensions, matrices, IPE requirements, and escalation indicators.
>
> Claude uses this to structure outputs intelligently.

---

## Mapper Index

| # | Control Type | Core Objective |
|---|---|---|
| 1 | Approval Routing / Decision Engine | Route transactions to appropriate approval authority |
| 2 | Threshold / Tolerance | Trigger automated logic when financial or risk thresholds are met |
| 3 | Financial Allocation | Allocate transactions per defined sequencing and business rules |
| 4 | Aggregation / Exposure Calculation | Accurately compute risk or financial values |
| 5 | Data Transformation Logic | Preserve integrity of key data elements |
| 6 | Modernization / Migration | Maintain control logic integrity post-migration |

---

## 1. Approval Routing / Decision Engine Controls

**Objective:** Ensure transactions route to the appropriate approval authority
based on defined attributes.

**Common Inputs:** Risk Rating · LGD / PD · Exposure · Product Type · Region · Customer Segment

### Required Testing Approach

- Positive scenario
- Elevated risk scenario
- Lower-bound scenario
- Upper-bound scenario
- Attribute sensitivity testing
- Negative / exclusion scenario

### Required Matrices

- Scenario-Based Logic Validation Matrix
- Sensitivity Testing Matrix
- Parameter Table Validation Matrix *(if grid-based)*

### IPE Required?
Yes — if routing output is reported or exported.

### Effectiveness Focus

| Dimension | What to Evaluate |
|---|---|
| Design | Does logic reflect documented policy? Is OR vs. AND logic correct? Are grid mappings accurate? Are edge cases documented? |
| Operating | Evidence of real transaction routing · No manual override without logging · Production validation sample |

### Common Risks

- OR vs. AND misconfiguration
- Hard-coded attribute values
- Silent filtering upstream
- Missing negative condition testing
- Grid parameters editable without approval

### Escalate If

- Routing logic is undocumented
- Parameter table is unmonitored
- No evidence of production scenario
- No validation of boundary cases

---

## 2. Threshold / Tolerance Controls

**Objective:** Ensure automated logic triggers appropriately when financial or
risk thresholds are met.

**Common Examples:** $X tolerance rule · Exposure trigger threshold · Approval escalation threshold · Exception flag trigger

### Required Testing Approach

- Below threshold
- Exactly at threshold
- Above threshold
- Negative input condition
- Multi-trigger condition *(if applicable)*

### Required Matrices

- Threshold / Tolerance Validation Matrix
- Boundary Testing Matrix

### IPE Required?
Sometimes — if tolerance output is reported externally.

### Effectiveness Focus

| Dimension | What to Evaluate |
|---|---|
| Design | Is threshold documented? Is value configurable? Is rounding logic considered? Are equality conditions handled correctly? |
| Operating | Sample where threshold triggered · Sample where threshold did not trigger · Production evidence of trigger logic |

### Common Risks

- `=` vs `>` logic errors
- Hard-coded tolerance values
- Boundary condition not tested
- Rounding misapplied

### Escalate If

- No documentation of threshold rationale
- No boundary testing performed
- Parameter change not monitored

---

## 3. Financial Allocation Controls

**Objective:** Ensure financial transactions are allocated according to defined
sequencing and business rules.

**Common Examples:** Principal vs. interest allocation · Payment sequencing · Partial payment handling · Fee prioritization

### Required Testing Approach

- Standard payment
- Partial payment
- Overpayment
- Multi-component balance
- Tolerance rule interaction *(if applicable)*

### Required Matrices

- Allocation Logic Validation Matrix
- Tolerance Impact Matrix

### IPE Required?
Yes — if allocation results feed financial reporting.

### Effectiveness Focus

| Dimension | What to Evaluate |
|---|---|
| Design | Sequencing logic · Ordering keys · Priority rules · Edge-case handling |
| Operating | Balance before/after validation · Transaction-level evidence · No unexplained variance |

### Common Risks

- Allocation order incorrect
- Hidden sequencing key
- Partial payments mishandled
- Balance impact not reconciled

### Escalate If

- Allocation code not reviewed
- No balance reconciliation
- No test of edge conditions

---

## 4. Aggregation / Exposure Calculation Controls

**Objective:** Ensure automated aggregation logic accurately computes risk or
financial values.

**Common Examples:** MEA / MPE calculations · Exposure roll-ups · Risk scoring aggregation · Master file generation

### Required Testing Approach

- Multiple input records scenario
- Single input scenario
- Modified attribute sensitivity test
- Edge-case input

### Required Matrices

- Aggregation / Transformation Matrix
- Sensitivity Testing Matrix

### IPE Required?
Yes — typically feeds reporting.

### Effectiveness Focus

| Dimension | What to Evaluate |
|---|---|
| Design | Aggregation formula accuracy · Inclusion/exclusion rules · Grouping keys validated |
| Operating | Field-level comparison · Output tie-out to independent calculation · Production sample validation |

### Common Risks

- Missing records in aggregation
- Duplicate inclusion
- Silent filtering
- Incorrect grouping key

### Escalate If

- Aggregation rule undocumented
- No independent recalculation
- No validation of grouping logic

---

## 5. Data Transformation Logic (Business Impacting)

**Objective:** Ensure transformation logic preserves integrity of key data elements.

**Common Examples:** KDE mapping · Field conversions · Status flag generation · Classification logic

### Required Testing Approach

- Field-level comparison
- Scenario-based transformation validation
- Sensitivity testing
- Negative scenario

### Required Matrices

- Transformation Matrix
- KDE Validation Matrix

### IPE Required?
Yes — if relied upon for downstream decisions.

### Effectiveness Focus

| Dimension | What to Evaluate |
|---|---|
| Design | Mapping documentation · Transformation formula accuracy · Conditional logic tested |
| Operating | Sample field tie-out · Before/after validation · No unexpected transformation |

### Common Risks

- Field mis-mapping
- Hard-coded exclusions
- Missing conditional branch
- Silent null handling

### Escalate If

- No mapping documentation
- No production sample
- No independent validation

---

## 6. Modernization / Migration of ITAC Logic

**Objective:** Ensure control logic integrity is maintained post-migration.

### Required Testing Approach

- Pre/post comparison
- Edge-case comparison
- Parameter integrity validation
- Monitoring validation

### Required Matrices

- Migration Comparison Matrix
- Edge Case Validation Matrix

### IPE Required?
Usually yes.

### Effectiveness Focus

| Dimension | What to Evaluate |
|---|---|
| Design | Logic unchanged · Parameters migrated correctly · No new filtering introduced |
| Operating | Production evidence from new environment · No unexpected variance |

### Common Risks

- Lift-and-shift claim without validation
- New rounding behavior introduced
- Table structure changes
- Monitoring not migrated

### Escalate If

- No comparison performed
- No evidence of production execution
- No review of configuration

---

## Master Rule for Claude

When evaluating any ITAC control:

1. Identify the objective type
2. Identify the logic type
3. Determine if IPE applies
4. Require boundary testing where a threshold exists
5. Require sensitivity testing where attributes drive decisions
6. Separate design and operating effectiveness
7. Do not allow single-scenario validation
8. Flag hard-coded logic
9. Flag undocumented parameters
10. Scope conclusions strictly to inspected evidence

---

*This mapper provides structured reasoning guidance for IT audit workflows.
It does not replace professional judgment or formal audit standards.*
