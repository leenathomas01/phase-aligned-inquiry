# Sequence Discipline: What PACI Looks Like in Practice

This document shows what each phase looks like when a team is actually running it. Assume you have `01-paci-protocol.md` open for reference.

---

## Phase 1: Define

### What the team is doing
* **Orchestrator:** States: "We are now in Define phase. No code, no experiments until this completes."
* **Ontologist:** Takes the informal hypothesis and writes it formally. Identifies every technical term and asks: "What does this mean numerically? How would we measure it?"
* **Team:** Argues until a numerical definition emerges. Definitions are written in a locked document (version control, shared doc, or time-stamped email).

### Required Outputs
* **Formal hypothesis statement:** (One paragraph, no ambiguous terms).
* **Technical term definitions:** (Glossary format with numerical thresholds).
* **Observable specifications:** (What, how, precision, units).
* **Pre-committed success/failure criteria:** (Explicit thresholds).

### Exit Criteria
- [ ] Every technical term has a numerical definition.
- [ ] All observables have specified measurement procedures.
- [ ] Success and failure conditions are written explicitly.
- [ ] Ontologist confirms: "I cannot think of a way to redefine these terms after seeing data."

**Corruption Warning:** "We'll define it more precisely later." *Correction:* Stop immediately. If you can't define it, the hypothesis isn't ready to test.

---

## Phase 2: Constrain

### What the team is doing
* **Orchestrator:** States: "Guardian leads. No execution until falsification plan is complete."
* **Guardian:** Asks: "How could this be circular?" and "Does measuring this assume what we're trying to prove?" Designs control conditions and specifies parameter ranges.
* **Skeptic:** Suggests artifact checks (e.g., "What if this is a finite-size effect?").

### Required Outputs
* **Circularity audit:** (List of potential circular reasoning and mitigations).
* **Control/baseline specifications:** (Experimental vs. Control setups).
* **Null result definition:** (Explicit statement of what failure looks like).
* **Falsification checklist:** (A "to-do" list for the Skeptic).

### Exit Criteria
- [ ] All observables checked for circular assumptions.
- [ ] Control conditions specified.
- [ ] Parameter sensitivity tests specified with numerical thresholds.
- [ ] Guardian confirms: "I cannot think of an additional test that would catch bias."

---

## Phase 3: Execute

### What the team is doing
* **Substrate:** Sets up experiment exactly as specified. Runs experimental and control conditions. Documents all parameters, settings, and seeds. Reports raw results **without explanation**.
* **Orchestrator:** Interrupts any attempts at interpretation: "No interpretation until Falsify phase."

### Required Outputs
* **Raw data files:** (Machine-readable, e.g., CSV/HDF5).
* **Parameter log:** (Every setting for every run).
* **Anomaly flags:** (Procedural notes only, no "reasons").

**Corruption Warning:** "Let me just try this slightly different parameter value." *Correction:* If parameters change, you must return to the Constrain phase and relock the doc.

---

## Phase 4: Falsify

### What the team is doing
* **Skeptic:** Reads the falsification checklist. Checks pass/fail for each item. Hunts for numerical artifacts and proposes alternative explanations.
* **Guardian:** Pushes the Skeptic: "How do you know? Show me the sensitivity test."
* **Team:** Resists the urge to soften failures. (e.g., accepting 16% drift when the threshold was 15%).

### Required Outputs
* **Falsification report:** (Checklist with pass/fail/inconclusive).
* **Artifact analysis:** (Tests performed on solver precision, thresholds, etc.).
* **Overall verdict:** (Hypothesis supported / falsified / inconclusive).

### Exit Criteria
- [ ] Every checklist item marked.
- [ ] At least 3 alternative explanations tested.
- [ ] Skeptic confirms: "I cannot think of another way this could be an artifact."

---

## Phase 5: Interpret

### What the team is doing
* **Team:** Synthesizes what was learned. No one argues with the falsification verdict.
* **If Falsified:** The team asks "Why did it fail?" and "What did we learn?" rather than attempting to rescue the hypothesis.
* **Decision:** Iterate (start over at Phase 1), Pivot (new hypothesis), or Close (final report).

### Required Outputs
* **Synthesis document:** (Verdict, lessons learned, conceptual reclassification).
* **Process integrity check:** (Did any sequence violations occur?).
* **Decision/Next Steps.**

---

## Cross-Phase Integrity Checks

| Violation Pattern | Detection | Recovery |
| :--- | :--- | :--- |
| **Interpretation during Execute** | Someone says "This means X" while data is running. | Stop. Discard contaminated work. Restart phase. |
| **Execution before Constrain** | "Let's just start, we'll add controls later." | Halt. Do not run until falsification plan is locked. |
| **Defining after seeing data** | "I think 'stable' should actually mean..." | Definitions are invalid. Revert to Phase 1. |

---
**End of File**
