# Hard Requirements

PACI will fail if these conditions are not met. Do not attempt PACI unless all requirements in this document are satisfied. This is not guidance; these are eligibility criteria.

---

## Problem Requirements

### 1. The hypothesis must be falsifiable
* **Requirement:** The hypothesis must make predictions that can be shown wrong through measurement or experiment.
* **Why:** PACI depends on pre-committing to failure. If the hypothesis cannot fail, there is nothing to pre-commit to.
* **Test:** Can a specific result be written down that would force the hypothesis to be abandoned? If not, do not use PACI.

### 2. Observables must be definable numerically
* **Requirement:** Terms like "better," "stable," or "robust" must be expressed as measurements with units, thresholds, or explicit procedures.
* **Why:** Ambiguity allows unconscious redefinition to make results appear successful.
* **Test:** Hand the definitions to an outsider. If they cannot execute measurements without clarification, the observables are not defined.

### 3. Pre-commitment to failure criteria must be possible
* **Requirement:** Success and failure criteria must be locked (version-controlled/time-stamped) before any data exists.
* **Why:** This prevents motivated reasoning where thresholds are adjusted to "fit" marginal results.

---

## Orchestrator Requirements

### 4. Must tolerate ambiguity without forcing premature resolution
* **Requirement:** The orchestrator must be comfortable with unresolved questions and not force closure due to psychological pressure.
* **Why:** If the orchestrator optimizes for closure over integrity, the sacred sequence collapses.

### 5. Must process multiple timescales simultaneously
* **Requirement:** Must distinguish between execution failures (immediate), test inconclusiveness (medium), and phase incompleteness (long).
* **Why:** Without this, the orchestrator will either declare failure too early or push past legitimate phase-gate requirements.

### 6. Must prioritize structural integrity over narrative coherence
* **Requirement:** Integrity must win when it conflicts with momentum, morale, or "exciting" results.
* **Why:** PACI is uncomfortable. If the narrative (success, speed, satisfaction) is prioritized, the protocol becomes performative.

### 7. Must allow self-organization rather than impose solutions
* **Requirement:** Must guide transitions but not dictate outcomes. Role authority (like the Guardian’s) must be respected even when inconvenient.

---

## Team/System Requirements

### 8. Roles must be functionally separable
* **Requirement:** At minimum, generation (producing results) and validation (testing them) must be performed by different components.
* **Why:** Bias is prevented by ensuring the same agent does not both produce and validate work.

### 9. Participants must tolerate adversarial pressure
* **Requirement:** Critique and blocking must not be interpreted as hostility. Working relationships must survive a "this phase is incomplete" or "this result is an artifact" verdict.

### 10. Shared epistemic values must exist
* **Requirement:** Implicit agreement that null results are data, sequence violations are fatal, and truth matters more than momentum.

### 11. Resources must exist for full execution
* **Requirement:** Sufficient time, compute, and materials must be available for controls and sweeps. Cutting corners due to resource constraints is not permitted.

---

## Compound Failures
If two or more requirements are missing, PACI will fail catastrophically rather than degrading gracefully. For example, an Orchestrator who cannot tolerate ambiguity paired with a conflict-averse team will always produce a corrupted, performative process that "proves" what they already believed.

---

## Self-Assessment
**Problem:**
- [ ] Hypothesis makes predictions that could be shown wrong.
- [ ] All observables can be defined numerically.
- [ ] Failure criteria can be written and locked before data exists.

**Orchestrator:**
- [ ] Can hold contradictions without forcing resolution.
- [ ] Can track multiple timescales simultaneously.
- [ ] Prioritizes integrity over narrative.
- [ ] Allows self-organization without overriding roles.

**Team/System:**
- [ ] Roles can be separated functionally.
- [ ] Adversarial pressure does not damage relationships.
- [ ] Null results are treated as data, not failures.
- [ ] Resources exist for full execution.

**If any checkbox remains unchecked, PACI requirements are not satisfied.**

---
**Final Statement**
These requirements are not negotiable. They are not best practices. They are the minimum conditions under which PACI can function.

*End of File*
