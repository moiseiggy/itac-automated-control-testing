# ITAC Automated Control Testing Skill

> A structured framework for generating high-quality ITAC (IT Application Control)
> testing documentation from technical evidence.

---

## Supported Evidence Types

- Source code (Java, Python, SQL, Go)
- Configuration tables
- Query outputs
- Production logs
- UI screenshots
- Monitoring evidence
- Architecture diagrams

---

## What It Generates

- Tester write-ups ("tester determined...")
- Design vs. Operating effectiveness assessments
- Completeness & Accuracy considerations
- IPE validation procedures
- Scenario-based testing matrices
- Sensitivity and boundary testing
- Control objective alignment
- Streamlined test programs

All outputs are structured and suitable for formal audit workpapers.

---

## Why This Exists

Testing automated controls is fundamentally different from manual controls.

Many audit failures stem from:

- Single-sample testing of deterministic logic
- No boundary testing
- Missing sensitivity analysis
- Incomplete IPE validation
- Over-reliance on screenshots
- Lack of production execution confirmation

This repository provides a repeatable methodology to avoid those pitfalls.

---

## Intended Audience

IT auditors · SOX testers · Risk & compliance professionals
GRC teams · Internal audit functions · Audit automation builders

---

## Control Types Supported

- Approval routing / decision engines
- Threshold & tolerance logic
- Financial allocation sequencing
- Aggregation & exposure calculations (MEA / MPE / roll-ups)
- Data transformation & KDE validation
- Parameter-table-driven controls
- Migration / modernization validation
- Monitoring & alert validation

---

## Repository Structure

    itac-automated-control-testing/
    |
    |-- SKILL.md
    |-- README.md
    |
    |-- templates/
    |   |-- automated-control-test-template.md
    |   |-- tester-writeup-templates.md
    |   +-- test-matrix-template.md
    |
    +-- references/
        |-- automated-control-objective-mapper.md
        |-- logic-testing-cheatsheet.md
        +-- common-itac-evidence-types.md

---

## How It Works

The skill operates in three layers:

### 1. Control Objective Mapping
Identifies the control type and selects required scenario dimensions, matrix
structure, IPE procedures, and boundary testing requirements.

### 2. Logic Testing Engine
Applies structured evaluation across OR vs. AND validation, threshold boundary
testing, sensitivity analysis, null handling review, parameter governance
validation, and migration comparison logic.

### 3. Evidence Classification
Determines what the evidence proves, what it does not prove, whether
supplemental evidence is required, and whether operating effectiveness
can be concluded.

---

## Example Prompts
"Write a tester determined statement based on this code."
"Make sense of this automated routing logic."
"What boundary testing should we perform?"
"How do I validate this threshold control?"
"Is this evidence sufficient for operating effectiveness?"
"Create a matrix for testing allocation sequencing."
"Draft completeness and accuracy procedures for this report."
"What IPE procedures are required here?"

---

## Methodology Highlights

| Area | What the Framework Enforces |
|---|---|
| Design vs. Operating | Evaluated separately, never conflated |
| Boundary Testing | Mandatory where thresholds exist |
| Sensitivity Testing | Required for decision-based logic |
| IPE Validation | Explicit procedures required |
| Overstatement | Avoided through guardrail language |
| Parameter Governance | Table-driven controls checked at source |
| Migration Validation | Pre/post comparison logic applied |
| Evidence Sufficiency | Evaluated before concluding effectiveness |

---

## ⚙️ Installation & Setup
To use this skill in your Claude environment:

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/your-username/itac-automated-control-testing.git

2. **Load Into Claude:**
   Project Mode: Upload the SKILL.md file and the references/ folder to your Claude Project's knowledge base
   Claude Code/Desktop: Direct Claude to read the project directory so it can access the templates in
3. **Verify Activation:** Ask Claude "Are you ready to perform ITGC control testing using the provided Skill logic?"

Use the templates and references when drafting control walkthrough documentation,
test programs, testing matrices, design effectiveness write-ups, and operating
effectiveness conclusions.

Integrate into AI audit workflows, Claude Skills, internal audit playbooks,
GRC documentation standards, or SOX control libraries.

---

## What This Is Not

This is a structured reasoning engine for automated control evaluation.

It is not a substitute for professional judgment, not accounting advice,
not specific to any single company, and not a static checklist.

---

## Future Enhancements

- Scenario matrix library expansion
- Example annotated case studies
- Migration comparison toolkit
- Parameter governance validation module
- Automated risk flag scoring

---

## About the Author

Built by an IT audit & GRC professional with hands-on experience testing
approval routing engines, financial allocation controls, exposure aggregation
systems, data pipeline transformations, threshold & tolerance logic,
parameter-driven risk grids, and enterprise modernization migrations.

---

## Contributing

Suggestions and improvements welcome.
If you are building AI-assisted audit workflows, feel free to fork and extend.

---

*This framework provides documentation structure and workflow guidance.
It does not replace professional judgment, control design evaluation,
or formal audit standards.*
