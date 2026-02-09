# Phase 2: Constrain

**Date Completed:** January 2026  
**Phase Lead:** Constraint Guardian (Claude)  
**Input:** Locked Define artifact (01-define.md)  
**Status:** Falsification plan completed and locked before Execute phase began

This document records the falsification tests, control conditions, and robustness requirements that were designed from the locked Define artifact. These constraints were specified before any simulation code was written or executed.

---

## Purpose of This Phase

The Define phase produced a hypothesis with three testable predictions:

1. Sharp phase transition at J_crit
2. Invariance of J_crit across γ variation
3. Lorentz-like causal propagation

The Constrain phase identifies how each prediction could fail, what observables would detect failure, and what numerical thresholds distinguish success from failure.

---

## Circularity Audit

### Potential Circularity 1: Measuring "stability" assumes geometry exists

**Risk:** The hypothesis claims geometry emerges from the lattice. Measuring "stable propagation" could assume the geometric structure being tested.

**Mitigation:** Define stability operationally without assuming geometry:
- Stability = correlation amplitude remains >10% of initial value for t >100 timesteps
- No geometric interpretation required during measurement
- Only measure correlation decay, not "distance" or "metric"

### Potential Circularity 2: Defining J_crit after seeing where transition occurs

**Risk:** Running parameter sweeps and then claiming "the transition happened at the value we found" is circular.

**Mitigation:** 
- Define J_crit as "the coupling strength where correlation propagation becomes stable per operational definition"
- Require that J_crit be detectable as a sharp transition (not gradual)
- Pre-commit to detection criterion: stable propagation must appear within ΔJ < 0.5 coupling range

### Potential Circularity 3: Choosing favorable γ values post-hoc

**Risk:** Testing many γ values and reporting only those where invariance holds.

**Mitigation:**
- Pre-specify γ test range: [0.03, 0.05, 0.08]
- All three values must be tested
- Results from all three must be reported
- No selective reporting permitted

---

## Control and Baseline Specifications

### Control Condition 1: No-coupling baseline (J = 0)

**Purpose:** Verify that propagation effects require coupling J > 0

**Specification:**
- Run simulation with J = 0, γ = 0.05
- Measure correlation propagation
- Expected result: No stable propagation (pure decoherence)

**Success criterion:** Control shows exponential decay with no propagation front

**Failure interpretation:** If control shows propagation, the effect is not due to coupling mechanism

---

### Control Condition 2: High-noise regime (γ >> J)

**Purpose:** Verify that high noise destroys propagation regardless of coupling

**Specification:**
- Run simulation with J = 2.0, γ = 1.0 (noise dominates)
- Measure correlation propagation
- Expected result: Propagation is destroyed by noise

**Success criterion:** No stable propagation despite high coupling

**Failure interpretation:** If propagation persists in high-noise regime, mechanism is noise-resistant (contradicts theoretical expectation)

---

## Null Result Definition

A null result occurs if **any** of the following are true:

1. **No sharp transition exists:** Correlation propagation increases gradually with J, with no identifiable critical threshold within ΔJ < 0.5

2. **Transition exists but is not stable:** Correlation amplitude decays below 10% threshold before t = 100 timesteps

3. **J_crit is noise-dependent:** The critical threshold J_crit varies by >15% across the γ test range [0.03, 0.05, 0.08]

4. **Control conditions fail:** Either J=0 baseline shows propagation, or high-noise condition shows stable propagation

If any null condition is met, the hypothesis is falsified. Proceed to Interpret phase for post-mortem analysis, not rescue attempts.

---

## Robustness Requirements (γ-Invariance Test)

### The Critical Test

**Observable:** J_crit (the coupling threshold where stable propagation emerges)

**Test procedure:**
1. Run parameter sweep for γ = 0.05 (reference case)
2. Identify J_crit as the coupling where stable propagation first appears
3. Run parameter sweep for γ = 0.03 (lower noise)
4. Run parameter sweep for γ = 0.08 (higher noise)
5. Measure J_crit for each γ value

**Invariance criterion:**

J_crit must remain constant within <15% drift across the γ range.

Specifically:
- Define J_crit(γ=0.05) as the reference value
- Calculate drift for γ=0.03: |J_crit(0.03) - J_crit(0.05)| / J_crit(0.05)
- Calculate drift for γ=0.08: |J_crit(0.08) - J_crit(0.05)| / J_crit(0.05)
- Both drift values must be <15%

**If drift ≥15% for either test point:** Hypothesis fails invariance requirement and is falsified.

---

## Additional Artifact Checks

### Finite-size effects

**Risk:** Transition appears sharp only because system size N is small

**Test:** If resources permit, test N = 4, 6, 8 and verify J_crit does not shift systematically with N

**Action if inconclusive:** Flag as limitation in final report

### Solver precision

**Risk:** Numerical instabilities create artificial transitions

**Test:** Re-run critical cases with tighter solver tolerance (10^-10 vs. baseline 10^-8)

**Success criterion:** J_crit changes by <1% with tighter tolerance

### Threshold detection artifacts

**Risk:** Detection threshold choice (10% of initial amplitude) creates artificial transition

**Test:** Vary detection threshold from 5% to 15% and verify J_crit remains stable

**Success criterion:** J_crit varies by <5% across threshold range

---

## Falsification Checklist

Before claiming the hypothesis is supported, verify **ALL** of the following:

- [ ] Sharp transition detected (stable propagation appears within ΔJ < 0.5)
- [ ] Transition is stable (correlation >10% amplitude for t >100 timesteps)
- [ ] J=0 control shows no propagation
- [ ] High-noise control shows no propagation
- [ ] γ=0.03 tested and J_crit measured
- [ ] γ=0.05 tested and J_crit measured (reference)
- [ ] γ=0.08 tested and J_crit measured
- [ ] Drift at γ=0.03 is <15%
- [ ] Drift at γ=0.08 is <15%
- [ ] Solver precision check passed (J_crit stable within 1%)
- [ ] Detection threshold check passed (J_crit stable within 5%)

**If any item fails:** Hypothesis is falsified. Document which criterion failed and proceed to Interpret phase.

**If all items pass:** Hypothesis is conditionally supported. Proceed to Interpret phase to assess significance and limitations.

---

## Transition to Execute Phase

This falsification plan was locked before any simulation code was written. The Execute phase implements these tests exactly as specified. No modifications to test procedures, parameter ranges, or success criteria are permitted during execution.

If execution reveals that a test cannot be performed as specified (e.g., numerical instability prevents convergence), execution must halt and return to Constrain phase to modify the test procedure explicitly before continuing.

---

**End of File**
