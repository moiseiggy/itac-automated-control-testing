Automated Control Objective → Testing Approach Mapper

This document maps ITAC control objectives to:

Required testing approach

Required scenario dimensions

Required matrices

IPE requirements

Design vs Operating considerations

Common failure risks

Escalation indicators

Claude must use this to structure outputs intelligently.

1️⃣ Approval Routing / Decision Engine Controls
Objective Type:

Ensure transactions route to appropriate approval authority based on defined attributes.

Common Inputs:

Risk Rating

LGD / PD

Exposure

Product Type

Region

Customer Segment

Required Testing Approach:

Positive scenario

Elevated risk scenario

Lower-bound scenario

Upper-bound scenario

Attribute sensitivity testing

Negative/exclusion scenario

Required Matrices:

Scenario-Based Logic Validation Matrix

Sensitivity Testing Matrix

Parameter Table Validation Matrix (if grid-based)

IPE Required?

Yes — if routing output is reported or exported.

Design Effectiveness Focus:

Does logic reflect documented policy?

Is OR vs AND logic correct?

Are grid mappings accurate?

Are edge cases documented?

Operating Effectiveness Focus:

Evidence of real transaction routing

No manual override without logging

Production validation sample

Common Risks:

OR vs AND misconfiguration

Hard-coded attribute values

Silent filtering upstream

Missing negative condition testing

Grid parameters editable without approval

Escalate If:

Routing logic undocumented

Parameter table unmonitored

No evidence of production scenario

No validation of boundary cases

2️⃣ Threshold / Tolerance Controls
Objective Type:

Ensure automated logic triggers appropriately when financial or risk thresholds are met.

Common Examples:

$X tolerance rule

Exposure trigger threshold

Approval escalation threshold

Exception flag trigger

Required Testing Approach:

Below threshold

Exactly at threshold

Above threshold

Negative input condition

Multi-trigger condition (if applicable)

Required Matrices:

Threshold / Tolerance Validation Matrix

Boundary Testing Matrix

IPE Required?

Sometimes — if tolerance output is reported externally.

Design Effectiveness Focus:

Is threshold documented?

Is value configurable?

Is rounding logic considered?

Are equality conditions handled correctly?

Operating Effectiveness Focus:

Sample where threshold triggered

Sample where threshold did not trigger

Production evidence of trigger logic

Common Risks:

= vs > logic errors

Hard-coded tolerance values

Boundary condition not tested

Rounding misapplied

Escalate If:

No documentation of threshold rationale

No boundary testing performed

Parameter change not monitored

3️⃣ Financial Allocation Controls
Objective Type:

Ensure financial transactions are allocated according to defined sequencing and business rules.

Common Examples:

Principal vs Interest allocation

Payment sequencing

Partial payment handling

Fee prioritization

Required Testing Approach:

Standard payment

Partial payment

Overpayment

Multi-component balance

Tolerance rule interaction (if applicable)

Required Matrices:

Allocation Logic Validation Matrix

Tolerance Impact Matrix

IPE Required?

Yes — if allocation results feed financial reporting.

Design Effectiveness Focus:

Sequencing logic

Ordering keys

Priority rules

Edge-case handling

Operating Effectiveness Focus:

Balance before/after validation

Transaction-level evidence

No unexplained variance

Common Risks:

Allocation order incorrect

Hidden sequencing key

Partial payments mishandled

Balance impact not reconciled

Escalate If:

Allocation code not reviewed

No balance reconciliation

No test of edge conditions

4️⃣ Aggregation / Exposure Calculation Controls
Objective Type:

Ensure automated aggregation logic accurately computes risk or financial values.

Common Examples:

MEA / MPE calculations

Exposure roll-ups

Risk scoring aggregation

Master file generation

Required Testing Approach:

Multiple input records scenario

Single input scenario

Modified attribute sensitivity test

Edge-case input

Required Matrices:

Aggregation / Transformation Matrix

Sensitivity Testing Matrix

IPE Required?

Yes — typically feeds reporting.

Design Effectiveness Focus:

Aggregation formula accuracy

Inclusion/exclusion rules

Grouping keys validated

Operating Effectiveness Focus:

Field-level comparison

Output tie-out to independent calculation

Production sample validation

Common Risks:

Missing records in aggregation

Duplicate inclusion

Silent filtering

Incorrect grouping key

Escalate If:

Aggregation rule undocumented

No independent recalculation

No validation of grouping logic

5️⃣ Data Transformation Logic (Business Impacting)
Objective Type:

Ensure transformation logic preserves integrity of key data elements.

Common Examples:

KDE mapping

Field conversions

Status flag generation

Classification logic

Required Testing Approach:

Field-level comparison

Scenario-based transformation validation

Sensitivity testing

Negative scenario

Required Matrices:

Transformation Matrix

KDE Validation Matrix

IPE Required?

Yes — if relied upon for downstream decisions.

Design Effectiveness Focus:

Mapping documentation

Transformation formula accuracy

Conditional logic tested

Operating Effectiveness Focus:

Sample field tie-out

Before/after validation

No unexpected transformation

Common Risks:

Field mis-mapping

Hard-coded exclusions

Missing conditional branch

Silent null handling

Escalate If:

No mapping documentation

No production sample

No independent validation

6️⃣ Modernization / Migration of ITAC Logic
Objective Type:

Ensure control logic integrity maintained post-migration.

Required Testing Approach:

Pre/post comparison

Edge-case comparison

Parameter integrity validation

Monitoring validation

Required Matrices:

Migration Comparison Matrix

Edge Case Validation Matrix

IPE Required?

Usually yes.

Design Effectiveness Focus:

Logic unchanged

Parameters migrated correctly

No new filtering introduced

Operating Effectiveness Focus:

Production evidence from new environment

No unexpected variance

Common Risks:

Lift-and-shift claim without validation

New rounding behavior

Table structure changes

Monitoring not migrated

Escalate If:

No comparison performed

No evidence of production execution

No review of configuration

Master Rule for Claude

When evaluating ITAC:

Identify objective type.

Identify logic type.

Determine if IPE applies.

Require boundary testing where threshold exists.

Require sensitivity testing where attributes drive decisions.

Separate design and operating effectiveness.

Do not allow single-scenario validation.

Flag hard-coded logic.

Flag undocumented parameters.

Scope conclusions strictly to inspected evidence.