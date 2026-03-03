ITAC Scenario-Based Test Matrix Templates

Automated controls must be tested using structured scenario validation.

Claude must always:

Identify logic type

Identify required test dimensions

Include positive, negative, and boundary scenarios

Separate design vs operating effectiveness

Avoid relying on a single “happy path” test

All matrices must be Excel-friendly (pipe-delimited).

1️⃣ Scenario-Based Logic Validation Matrix (General)

Use for:

Approval routing

Risk-based decision engines

Attribute-based logic

Deterministic branching

Control Objective:

[State objective clearly]

Logic Type:

Routing / Threshold / Allocation / Aggregation / Transformation

Design Effectiveness – Scenario Testing
Scenario ID	Input Attributes	Expected Logic Outcome	Rationale (Business Rule)	Observed Outcome	Match (Y/N)	Notes
S1						
S2						

Scenarios must include:

Standard condition

Elevated risk condition

Lower-bound condition

Upper-bound condition

Negative / exclusion condition

Operating Effectiveness – Production Evidence
Scenario ID	Production Evidence Reviewed	Evidence Source	Output Verified	Conclusion
2️⃣ Threshold / Tolerance Validation Matrix

Use for:

$X tolerance rules

Trigger conditions

Exposure thresholds

Limit validations

Control Objective:

Validate that automated logic triggers appropriately when threshold conditions are met.

Boundary Testing
Scenario ID	Input Value	Threshold	Expected Behavior	Observed Behavior	Boundary Type (Below/Equal/Above)	Match (Y/N)	Notes
B1							
B2							

Boundary scenarios must include:

Just below threshold

Exactly at threshold

Just above threshold

Negative Testing
Scenario ID	Invalid / Edge Input	Expected System Handling	Observed Handling	Match (Y/N)
3️⃣ Allocation Logic Validation Matrix

Use for:

Principal vs interest allocation

Sequencing validation

Multi-step financial logic

Partial payments

Control Objective:

Validate allocation sequencing and financial impact are applied per documented business rules.

Allocation Sequence Validation
Scenario ID	Transaction Type	Input Amount	Expected Allocation Order	Observed Allocation Order	Balance Impact Verified (Y/N)	Variance	Conclusion
Tolerance Impact Validation (If Applicable)
Scenario ID	Payment Amount	Tolerance Rule	Expected Behavior	Observed Behavior	Match (Y/N)	Notes
4️⃣ Aggregation / Transformation Logic Matrix

Use for:

MEA/MPE aggregation

Master file logic

Exposure calculations

Risk scoring aggregation

Control Objective:

Validate that aggregation and transformation logic produce accurate outputs.

Field-Level Validation
Scenario ID	Input Records	Aggregation Rule	Expected Output	Observed Output	Match (Y/N)	Notes
Sensitivity Testing
Scenario ID	Attribute Modified	Expected Impact	Observed Impact	Match (Y/N)
5️⃣ Parameter Table Validation Matrix

Use for:

Config-driven logic

Editable parameter tables

Risk grids

Approval matrices

Control Objective:

Validate parameter configuration supports intended automated logic.

Parameter Completeness
Parameter Name	Configured Value	Expected Value	Source of Truth	Match (Y/N)	Notes
Parameter Change Monitoring
Parameter	Editable? (Y/N)	Change Logged?	Approval Required?	Monitoring Present?	Conclusion
6️⃣ Migration / Update Logic Validation Matrix

Use for:

Lift-and-shift claims

Modernization testing

Backend migration validation

Control Objective:

Validate logic integrity maintained following migration.

Pre/Post Comparison
Component	Legacy Logic Output	New Logic Output	Variance	Explanation	Conclusion
Edge Case Comparison
Scenario ID	Legacy Result	New Result	Match (Y/N)	Notes
7️⃣ IPE Validation Overlay

If control relies on system-generated output, include:

IPE Completeness
Report Name	Source System	Record Count	Independent Tie-Out Performed?	Conclusion
IPE Accuracy
Sample ID	Source Value	Reported Value	Match (Y/N)	Notes
Enforcement Rules for Claude

When generating matrices:

Always include boundary testing where thresholds apply.

Always include negative scenario where logic excludes conditions.

Do not rely on a single scenario.

Separate design vs operating evidence.

Flag missing production validation.

Flag missing parameter monitoring.

Do not assume code shown = deployed.