Purpose

This document defines:

Types of evidence commonly provided for ITAC controls

What each evidence type proves

What it does NOT prove

When IPE procedures are required

When supplemental evidence is required

Claude must reference this before concluding operating effectiveness.

1️⃣ Source Code (Java, Python, SQL, Go, etc.)
What It Proves

Logic structure

Conditional statements (IF/ELSE)

Threshold definitions

Aggregation formulas

Allocation sequencing

Inclusion/exclusion criteria

Parameter usage

Null handling behavior

What It Does NOT Prove

That code is deployed to production

That logic executed during the period

That parameter tables were unchanged

That monitoring is active

That edge cases were exercised

Required Supplements

Git history / last change evidence

Production execution logs

Parameter table snapshot

Scenario output evidence

Risk If Used Alone

Testing design only (not operating)

QA-only logic

Outdated branch reviewed

2️⃣ Configuration / Parameter Tables

Examples:

Approval grids

Risk rating mapping tables

Threshold configuration tables

Product routing tables

What It Proves

Decision criteria values

Routing mappings

Tolerance thresholds

Attribute-to-grid relationships

What It Does NOT Prove

That logic references the table correctly

That changes are controlled

That parameters were active during period

That table is complete

Required Supplements

Code reference confirming table usage

Change monitoring evidence

Version snapshot

Boundary scenario validation

Common Risk

Hard-coded override exists outside configuration.

3️⃣ Production Execution Logs

Examples:

Job run logs

Lambda execution logs

Step function runs

Cron job success logs

What It Proves

Automation executed

Timestamp validation

Error handling evidence

Batch success/failure

What It Does NOT Prove

Correct logic result

Correct routing outcome

Field-level accuracy

Proper aggregation

Required Supplements

Sample output

Field-level comparison

Scenario validation

4️⃣ UI Screenshots

Examples:

Dashboard outputs

Approval routing screens

Calculated values shown in system

Allocation display

What It Proves

System behavior for that scenario

User-visible output

Routing result

Calculated output displayed

What It Does NOT Prove

Complete population

All logic branches tested

No upstream filtering

Production execution timing

Configuration correctness

Required Supplements

Underlying query

Code inspection

Additional scenarios

Population validation

5️⃣ Query Outputs (Snowflake, Postgres, SQL Server, etc.)

Examples:

Extracted dataset

Record counts

Field-level comparisons

Reconciliation outputs

What It Proves

Dataset values at point in time

Record counts

Field comparisons

Aggregation results

What It Does NOT Prove

Query parameters were correct

No filters excluded records

Complete population

No manual manipulation

IPE Required?

Yes.

Must validate:

Source system

Query parameters

Timeframe

Record count tie-out

6️⃣ Monitoring & Alert Evidence (PagerDuty, Splunk, SNS, etc.)
What It Proves

Alert configuration exists

Error detection capability

Notification path

Incident handling example

What It Does NOT Prove

Business logic correctness

All failures would trigger alert

Parameter change detection

Required Supplements

Alert rule definition

Trigger condition review

Sample triggered alert

7️⃣ Git History / Version Control Evidence
What It Proves

Last modification date

Commit author

Change frequency

Branch validation

What It Does NOT Prove

Deployed version matches reviewed version

No configuration changes

Logic integrity at runtime

Required Supplements

Deployment pipeline evidence

Production environment confirmation

Release note confirmation

8️⃣ Data Flow Diagrams / Architecture Diagrams
What It Proves

Intended system architecture

Upstream/downstream dependencies

Logical data movement

What It Does NOT Prove

Real-time execution

Filtering behavior

Error handling implementation

Active system state

Required Supplements

Code inspection

Execution logs

Field-level validation

9️⃣ Scenario-Based Sample Evidence

Examples:

One credit action tested

One payment allocation example

One tolerance case

What It Proves

Logic worked for that scenario

Deterministic outcome observed

What It Does NOT Prove

All branches validated

Boundary cases handled

Sensitivity to attribute change

Completeness of logic

Required Supplements

Boundary case

Negative case

Sensitivity test

🔟 Reconciliation Evidence (Counts / Balances)
What It Proves

No dropped records (if properly tied out)

Total balance integrity

Before/after comparisons

What It Does NOT Prove

Correct individual record transformation

Correct routing logic

No duplicate processing

Required Supplements

Field-level comparison

Deduplication testing

Grouping key validation

IPE Trigger Guide

IPE procedures are required when:

Testing relies on reports

Query outputs are used as population

Dashboard exports are relied upon

Reconciliation spreadsheets are provided

Record counts are used to conclude completeness

Minimum IPE validation:

Confirm source system

Confirm parameter filters

Confirm timeframe

Tie record count to independent source

Spot-check fields

Evidence Strength Ranking (Strongest to Weakest)

Code + Production execution logs + Scenario outputs

Code + Scenario outputs + Parameter snapshot

Scenario outputs + Monitoring logs

UI screenshots alone

Narrative explanations only

Claude should not conclude operating effectiveness using evidence types ranked 4 or 5 alone.

Escalation Triggers

Escalate if:

No boundary testing

No negative scenario

Parameter tables not governed

QA-only evidence provided

No production execution validation

Logic differs from documented policy

Single sample used to conclude determinism

Default Conclusion Guardrail

When evidence is partial:

Use language such as:

“Based on evidence inspected…”

“For the in-scope scenario…”

“No exceptions were noted for the sample reviewed…”

“Testing was limited to…”

Never state:

“The control ensures…”

“All transactions…”

“Complete population…”