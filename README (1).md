# AI–Human Hybrid Hospital Workflow
### A system design for real-time patient safety — from triage to discharge and beyond.

> *"AI prepares. Human decides. System remembers. No patient is left unwatched."*

---

## Background

This system was designed in response to the **UK MenB outbreak of March 2026** — an invasive meningococcal disease cluster linked to Canterbury, Kent, that resulted in 29+ confirmed cases and 2 deaths, primarily among university students.

The outbreak exposed a gap that exists in most hospitals worldwide: not a gap in medical knowledge, and not a gap in technology — but a gap in **coordinated, real-time, end-to-end workflow** that ensures no patient becomes invisible between clinical touchpoints.

A patient sent home with early MenB symptoms. Stable at discharge. No ongoing monitoring. No system watching what happened next. She came back by ambulance.

That gap is what this system is designed to close.

---

## Core Philosophy

This is not an autonomous AI system. It is a **hybrid workflow** where:

- **AI** handles detection, preparation, orchestration, monitoring, and audit
- **Humans** hold every decision gate — no clinical action executes without senior doctor approval and senior nurse verification
- **The system** maintains a real-time, immutable log of every recommendation and every decision

The AI is helpful, not pushy. It surfaces what matters and steps back.

---

## System Overview

```
Patient Arrival
      ↓
[AI] Risk Detection
      ↓
[AI] Prepares Full Workflow Package
      ↓
[HUMAN] Senior Doctor Approval
      ↓
[HUMAN] Senior Nurse Verification
      ↓
[AI] Executes Orchestration
      ↓
[HUMAN] Procedure & Treatment
      ↓
[AI + WEARABLE] Continuous Monitoring ←──────────────┐
      ↓                                               │
  Alert fired? → False Positive Control Layer        │
      ↓                                               │
  Confirmed → Re-triggers workflow loop ─────────────┘
      ↓
[AI + NETWORK] Multi-Hospital Coordination (Pipeline)
      ↓
[HUMAN] Final Oversight
      ↓
[AI] Real-Time Immutable Audit Log
```

---

## Full Stage Breakdown

### Stage 0 — Patient Arrival and Intake
- Patient enters symptoms or triage nurse records vitals
- AI triage scans for danger patterns: sepsis, meningitis, stroke
- System clock starts

---

### Stage 1 — AI Risk Detection
AI analyses:
- Vitals, symptoms, age, history
- Red-flag pattern combinations

If high-risk → AI flags "Possible Meningitis / Sepsis"

This is a signal for human review — not a diagnosis.

---

### Stage 2 — AI Prepares Full Workflow Package
The most time-critical and currently absent layer in most hospitals.

AI drafts:
- Lumbar puncture order
- Blood culture order
- Antibiotic recommendation
- Consent form
- Lab request
- Room reservation

AI simultaneously checks:
- Nurse availability
- Lab tech availability
- Room availability
- Equipment readiness

The doctor receives a complete, ready-to-execute package. Coordination time: near zero.

---

### Stage 3 — Senior Doctor Approval
Doctor reviews the AI proposal across four dimensions:
- Safety
- Ethics
- Necessity
- Clinical appropriateness

**Approved** → workflow proceeds
**Rejected** → AI cancels all pending actions cleanly

The doctor decides. The AI coordinates. Never the reverse.

---

### Stage 4 — Senior Nurse Verification
Nurse independently checks:
- Forms and consent
- Equipment
- Staff assignment

Confirms logistics. Workflow is unlocked.

Two independent human checkpoints. Neither optional.

---

### Stage 5 — AI Executes Orchestration
AI:
- Reserves room
- Assigns nurse and lab tech
- Sends instructions to each team member
- Prepares equipment
- Coordinates timing across all teams

This is the orchestration layer that most hospitals do not have. It is where things fall through the cracks — not because of negligence, but because real-time multi-party coordination under pressure is beyond reliable human bandwidth.

---

### Stage 6 — Procedure and Treatment
- Doctor performs lumbar puncture
- Nurse assists
- Lab processes sample
- Antibiotics administered

Clinical work happens — supported, not interrupted.

---

### Stage 7 — AI Continuous Monitoring via Wearable Device

**This stage exists because of patients who were discharged and deteriorated at home.**

Every patient — in-ward, waiting, or discharged to home observation — wears a hospital-grade device monitoring:

| Sensor | Signal |
|---|---|
| Heart rate | Tachycardia, bradycardia |
| Oxygen saturation (SpO2) | Hypoxia |
| Temperature | Fever, hypothermia |
| Blood pressure | Hypotension, shock |
| Respiratory rate | Respiratory distress |
| Movement / accelerometer | Collapse detection |
| Skin perfusion | Early sepsis indicators |

#### False Positive Control Layer
A critical sub-layer between sensor and alarm:

- Consecutive readings must breach tiered thresholds before escalation
- Specificity target: **≥ 95%** — the system is tuned for precision, not just sensitivity
- Rationale: alert fatigue is how good systems get ignored. A nurse interrupted 50 times by false alarms will hesitate on the 51st. That hesitation can be fatal.

When a genuine alert fires:
- AI checks staff availability
- AI checks room availability
- AI checks nearby hospitals if at capacity
- AI prepares workflow package
- **Senior doctor approves**
- **Senior nurse confirms**
- Response begins

No patient left unwatched. Discharged does not mean safe.

---

### Stage 8 — Multi-Hospital Coordination *(Pipeline → Future)*

The current failure mode: Hospital A is full. The burden falls on the family — desperate, exhausted, calling ward after ward while the patient deteriorates.

This stage removes that burden entirely.

**Central Bed Control System:**
- Real-time cross-hospital availability: beds, staff, equipment
- AI agent queries the network on behalf of the hospital
- Identifies nearest viable option
- Prepares transfer documents
- Notifies ambulance team
- Presents recommendation to senior doctor for approval
- Family is notified *by the system* — not asked to coordinate it

Critical during:
- Epidemic surges
- Overnight shifts
- Rural hospital limitations
- Mass casualty events

The inter-hospital safety net. No family holds the phone.

---

### Stage 9 — AI Safety Guardrails *(Pipeline)*
System enforces at every step:

- No step skipped
- No form missing
- No lab request lost
- No deterioration ignored
- No over-activation (false positive rate monitored continuously)
- No unethical pressure

The AI surfaces what matters. It does not push.

---

### Stage 10 — Human Final Oversight
Senior doctor and senior nurse review:
- Diagnosis
- Treatment plan
- Lab results
- Patient stability

**Humans make the final call. Always. No exceptions.**

---

### Stage 11 — AI Post-Case Audit (Real-Time, Immutable Log)
Every AI recommendation is logged. Every human decision is logged. Every timestamp is logged.

**Write-once ledger** — cannot be altered after the fact.

Generates:
- Safety reports
- Workflow bottleneck analysis
- Staff workload review
- Missed step detection
- Systemic failure flags

Two functions:
1. **Operational** — the system learns where it is failing before humans notice
2. **Legal / ethical** — complete, unalterable record of what the AI recommended and what the human decided. Accountability is preserved in the system, not assigned to it after the fact.

---

## System Readiness Status

| Component | Status |
|---|---|
| AI triage alerts | ✅ Current |
| AI risk detection | ✅ Current |
| Senior doctor / nurse approval | ✅ Current |
| AI staff + room availability checks | 🔶 Emerging |
| AI auto-preparing forms and orders | 🔶 Emerging |
| Post-case audit (real-time immutable log) | 🔶 Emerging |
| False positive rate control layer | 🔶 Emerging |
| AI full workflow orchestration | 🔷 Future |
| Wearable patient monitoring | 🔷 Future |
| Central bed control system | 🔷 Future |
| Multi-hospital AI coordination | ⬜ Pipeline |
| AI safety guardrails | ⬜ Pipeline |

---

## Key Design Decisions

**Why two human checkpoints (doctor + nurse)?**
Independent verification at different professional levels catches errors that single-point approval misses. In time-critical disease, a missed consent or wrong equipment assignment can be as dangerous as the disease itself.

**Why specificity ≥ 95% for wearable alerts?**
Alert fatigue is a documented cause of clinical harm. Sensitivity without specificity creates noise. The system is designed to be trusted — and that requires being precise.

**Why an immutable audit log?**
When something goes wrong in medicine, the question is always: who knew what, and when? An immutable log does not assign blame — it preserves truth. That is what makes a system trustworthy enough to deploy in a hospital.

**Why does the AI never close the loop autonomously?**
Because clinical decision-making involves context, ethics, and human judgment that no current AI system can fully replicate. The AI's role is to eliminate friction, not to replace judgment. The moment the AI closes the loop without a human, it stops being a tool and starts being a liability.

---

## Repository Structure

```
/
├── README.md                   ← this file
├── diagrams/
│   └── workflow.svg            ← full system architecture diagram
├── docs/
│   ├── system-spec.md          ← full stage-by-stage specification
│   ├── false-positive-layer.md ← wearable alert threshold design (planned)
│   └── audit-log-schema.md     ← immutable log data structure (planned)
└── CHANGELOG.md                ← version history as system evolves
```

---

## Version History

| Version | Date | Notes |
|---|---|---|
| v0.1 | March 2026 | Initial concept — 11-stage hybrid workflow |
| v0.2 | March 2026 | Added false positive control layer (Stage 7) |
| v0.3 | March 2026 | Added real-time immutable audit log (Stage 11), central bed control system (Stage 8) |

---

## Contributing and Feedback

This is a design proposal, not a deployed system. It requires clinical validation, regulatory review, and engineering input to move toward implementation.

If you are a clinician, health tech builder, researcher, or policy person with feedback, critique, or interest in collaboration — contributions and issues are welcome.

The goal is not a product. The goal is a standard of care.

---

## Related

- Full narrative post: [Substack — She Was Sent Home. She Came Back in an Ambulance.](#)
- UK MenB Outbreak Technical Briefing: [UKHSA GOV.UK](https://www.gov.uk/government/publications/invasive-meningococcal-disease-outbreak-2026-technical-briefings/invasive-meningococcal-disease-outbreak-2026-technical-briefing-1)
- UKHSA Live Case Count: [GOV.UK](https://www.gov.uk/government/publications/invasive-meningococcal-disease-statistical-releases/notified-cases-of-invasive-meningococcal-disease)

---

*System design concept. Not yet deployed. Not medical advice.*
