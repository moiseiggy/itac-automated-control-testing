# ITAC Evidence Types — Reference Guide

> This document defines common ITAC evidence types, what each proves,
> what it does NOT prove, and when supplemental procedures are required.
>
> Claude must reference this before concluding operating effectiveness.

---

## Evidence Index

| # | Evidence Type | IPE Required? |
|---|---|---|
| 1 | Source Code | No — but requires supplements |
| 2 | Configuration / Parameter Tables | No — but requires supplements |
| 3 | Production Execution Logs | No — but requires supplements |
| 4 | UI Screenshots | No — but requires supplements |
| 5 | Query Outputs | **Yes** |
| 6 | Monitoring & Alert Evidence | No — but requires supplements |
| 7 | Git History / Version Control | No — but requires supplements |
| 8 | Data Flow / Architecture Diagrams | No — but requires supplements |
| 9 | Scenario-Based Sample Evidence | No — but requires supplements |
| 10 | Reconciliation Evidence | No — but requires supplements |

---

## 1. Source Code
*(Java, Python, SQL, Go, etc.)*

| What It Proves | What It Does NOT Prove |
|---|---|
| Logic structure and conditional statements | Code is deployed to production |
| Threshold definitions | Logic executed during the period |
| Aggregation formulas | Parameter tables were unchanged |
| Allocation sequencing | Monitoring is active |
| Inclusion / exclusion criteria | Edge cases were exercised |
| Null handling behavior | |

**Required Supplements:**
- Git history / last change evidence
- Production execution logs
- Parameter table snapshot
- Scenario output evidence

**Risk if used alone:** Testing design only (not operating) · QA-only logic · Outdated branch reviewed

---

## 2. Configuration / Parameter Tables
*(Approval grids · Risk rating mapping tables · Threshold config tables · Product routing tables)*

| What It Proves | What It Does NOT Prove |
|---|---|
| Decision criteria values | Logic references the table correctly |
| Routing mappings | Changes are controlled |
| Tolerance thresholds | Parameters were active during period |
| Attribute-to-grid relationships | Table is complete |

**Required Supplements:**
- Code reference confirming table usage
- Change monitoring evidence
- Version snapshot
- Boundary scenario validation

**Common Risk:** Hard-coded override exists outside the configuration table.

---

## 3. Production Execution Logs
*(Job run logs · Lambda execution logs · Step function runs · Cron job success logs)*

| What It Proves | What It Does NOT Prove |
|---|---|
| Automation executed | Correct logic result |
| Timestamp validation | Correct routing outcome |
| Error handling evidence | Field-level accuracy |
| Batch success / failure | Proper aggregation |

**Required Supplements:**
- Sample output
- Field-level comparison
- Scenario validation

---

## 4. UI Screenshots
*(Dashboard outputs · Approval routing screens · Calculated values · Allocation display)*

| What It Proves | What It Does NOT Prove |
|---|---|
| System behavior for that scenario | Complete population |
| User-visible output | All logic branches tested |
| Routing result | No upstream filtering |
| Calculated output displayed | Production execution timing |
| | Configuration correctness |

**Required Supplements:**
- Underlying query
- Code inspection
- Additional scenarios
- Population validation

---

## 5. Query Outputs
*(Snowflake · Postgres · SQL Server · Extracted datasets · Record counts · Reconciliation outputs)*

| What It Proves | What It Does NOT Prove |
|---|---|
| Dataset values at point in time | Query parameters were correct |
| Record counts | No filters excluded records |
| Field comparisons | Complete population |
| Aggregation results | No manual manipulation |

**IPE Required? Yes.**

Must validate:
- Source system
- Query parameters
- Timeframe
- Record count tie-out

---

## 6. Monitoring & Alert Evidence
*(PagerDuty · Splunk · SNS · Alert configurations)*

| What It Proves | What It Does NOT Prove |
|---|---|
| Alert configuration exists | Business logic correctness |
| Error detection capability | All failures would trigger alert |
| Notification path | Parameter change detection |
| Incident handling example | |

**Required Supplements:**
- Alert rule definition
- Trigger condition review
- Sample triggered alert

---

## 7. Git History / Version Control Evidence

| What It Proves | What It Does NOT Prove |
|---|---|
| Last modification date | Deployed version matches reviewed version |
| Commit author | No configuration changes |
| Change frequency | Logic integrity at runtime |
| Branch validation | |

**Required Supplements:**
- Deployment pipeline evidence
- Production environment confirmation
- Release note confirmation

---

## 8. Data Flow / Architecture Diagrams

| What It Proves | What It Does NOT Prove |
|---|---|
| Intended system architecture | Real-time execution |
| Upstream / downstream dependencies | Filtering behavior |
| Logical data movement | Error handling implementation |
| | Active system state |

**Required Supplements:**
- Code inspection
- Execution logs
- Field-level validation

---

## 9. Scenario-Based Sample Evidence
*(One credit action · One payment allocation · One tolerance case)*

| What It Proves | What It Does NOT Prove |
|---|---|
| Logic worked for that scenario | All branches validated |
| Deterministic outcome observed | Boundary cases handled |
| | Sensitivity to attribute changes |
| | Completeness of logic |

**Required Supplements:**
- Boundary case
- Negative case
- Sensitivity test

---

## 10. Reconciliation Evidence
*(Counts / balances · Before/after comparisons)*

| What It Proves | What It Does NOT Prove |
|---|---|
| No dropped records (if properly tied out) | Correct individual record transformation |
| Total balance integrity | Correct routing logic |
| Before / after comparisons | No duplicate processing |

**Required Supplements:**
- Field-level comparison
- Deduplication testing
- Grouping key validation

---

## IPE Trigger Guide

IPE procedures are required when testing relies on any of the following:

- Reports
- Query outputs used as a population
- Dashboard exports
- Reconciliation spreadsheets
- Record counts used to conclude completeness

### Minimum IPE Validation Steps

- [ ] Confirm source system
- [ ] Confirm parameter filters
- [ ] Confirm timeframe
- [ ] Tie record count to independent source
- [ ] Spot-check fields

---

## Evidence Strength Ranking

| Rank | Evidence Combination |
|---|---|
| **1 — Strongest** | Code + production execution logs + scenario outputs |
| **2** | Code + scenario outputs + parameter snapshot |
| **3** | Scenario outputs + monitoring logs |
| **4 — Weak** | UI screenshots alone |
| **5 — Weakest** | Narrative explanations only |

> Claude should not conclude operating effectiveness using evidence ranked 4 or 5 alone.

---

## Escalation Triggers

Escalate if any of the following are present:

- No boundary testing performed
- No negative scenario included
- Parameter tables not governed
- QA-only evidence provided
- No production execution validation
- Logic differs from documented policy
- Single sample used to conclude determinism

---

## Default Conclusion Guardrail

**When evidence is partial, use language such as:**

- "Based on evidence inspected..."
- "For the in-scope scenario..."
- "No exceptions were noted for the sample reviewed..."
- "Testing was limited to..."

**Never state:**

- "The control ensures..."
- "All transactions..."
- "Complete population..."

---

*This reference guide supports IT audit documentation workflows.
It does not replace professional judgment or formal audit standards.*
