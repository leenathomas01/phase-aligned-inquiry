# Sequence Discipline: What PACI Looks Like in Practice

This document shows what each phase looks like when a team is actually running it. Assume you have [`01-paci-protocol.md`](01-paci-protocol.md) open for reference.

---

## Phase 1: Define

### What the team is doing

**Orchestrator actions:**
- Calls a meeting or opens a shared document
- States: "We are now in Define phase. No code, no experiments until this completes."
- Asks Ontologist to lead

**Ontologist actions:**
- Takes the informal hypothesis and writes it formally
- Identifies every technical term
- For each term, asks: "What does this mean numerically? How would we measure it?"
- Writes down each definition
- Asks: "If we used this definition, could we redefine it later to make results look better?"
- If yes: makes the definition more precise

**Team actions:**
- Someone proposes: "Let's use 'stable' to mean..."
- Ontologist asks: "Stable over what timescale? Stable under what perturbations? Stable compared to what baseline?"
- Team argues until a numerical definition emerges
- Definition is written in a locked document (version control, shared doc with edit history, sent via email)

### What artifacts are being produced

**Required outputs:**

1. **Formal hypothesis statement** (one paragraph, no ambiguous terms)

   Example:
   > "Mechanism X produces observable pattern Y with property Z, where Y is defined as [specific measurement with units], Z is defined as [numerical threshold or invariance criterion], and the claim succeeds if Y exceeds baseline by >20% AND Z holds across parameter variations of ±15%."

2. **Technical term definitions** (glossary format)

   Example:
```
   Term: "Convergence"
   Definition: Simulation reaches steady state when the maximum change 
   in observable Q over 100 timesteps is <0.01% of mean(Q).
   Measurement: Track max(|Q(t) - Q(t-100)|) / mean(Q) every 100 steps.
```

3. **Observable specifications** (what will be measured, how, with what precision)

   Example:
```
   Observable: Propagation delay
   Measurement: Time between perturbation at node 0 and threshold 
   crossing (>10% of baseline) at node N.
   Units: Simulation timesteps
   Precision: Record to nearest integer timestep
   Null case: If threshold never crossed within t_max=1000, record as "no arrival"
```

4. **Pre-committed success/failure criteria**

   Example:
```
   Success requires ALL of:
   - Observable Y > baseline + 2σ
   - Property Z invariant under γ ∈ [0.03, 0.08] (drift <15%)
   - Control condition shows Y_control ≈ baseline ± σ
   
   Failure if ANY of:
   - Y ≤ baseline + 2σ
   - Z drifts >15% across γ range
   - Control condition also shows elevated Y
```

### How you know this phase is complete

**Exit criteria checklist:**

- [ ] Every technical term in the hypothesis has a numerical definition
- [ ] All observables have specified measurement procedures
- [ ] Success and failure conditions are written explicitly
- [ ] At least one person tried to find an ambiguous term and couldn't
- [ ] The definitions are locked (version controlled, time-stamped, or sent to external party)
- [ ] Ontologist confirms: "I cannot think of a way to redefine these terms after seeing data"

**Test:** Hand the definition document to someone outside the project. Ask them: "Could you measure this?" If they say "I don't know what X means," Define phase is incomplete.

### What must exist before moving to next phase

A locked document containing:
- Formal hypothesis (1 paragraph)
- All technical term definitions (numerical, measurable)
- Observable specifications (what, how, precision, units)
- Success/failure criteria (explicit thresholds)

**Format:** Text file, Google Doc with revision history, GitHub commit, or email with timestamp. Must be difficult to modify retroactively.

### The 3 most common ways this phase gets corrupted

**Corruption 1: "We'll define it more precisely later"**

Someone says: "Let's keep the definition flexible for now, we'll tighten it once we see what the data looks like."

**Why this is fatal:** This allows unconscious redefinition to make results look better.

**Correction:** Stop immediately. Do not proceed until the term is defined numerically. If you genuinely don't know how to define it, the hypothesis is not ready to test.

---

**Corruption 2: Definitions that assume the conclusion**

Someone defines "causal influence" as "propagation faster than background noise" when the hypothesis is about whether causal influence exists at all.

**Why this is fatal:** The definition assumes what you're trying to prove.

**Correction:** Guardian role challenges: "This definition assumes X already exists. Define it without assuming the conclusion."

---

**Corruption 3: Moving to Constrain phase with informal agreement**

Team discusses definitions verbally, everyone nods, no one writes anything down. Orchestrator says "Okay, let's move on."

**Why this is fatal:** Informal agreement masks incompatible interpretations. Six weeks later, you'll argue about what you meant.

**Correction:** Nothing is defined until it's written and locked. Verbal agreement does not count.

---

## Phase 2: Constrain

### What the team is doing

**Orchestrator actions:**
- States: "We are now in Constrain phase. Guardian leads. No execution until falsification plan is complete."
- Provides Guardian with the locked Define outputs

**Guardian actions:**
- Reads the hypothesis and asks: "How could this be circular?"
- For each observable, asks: "Does measuring this assume what we're trying to prove?"
- Designs control conditions
- Writes down what a null result looks like
- Specifies parameter ranges that must be tested for robustness
- Creates a falsification checklist

**Team actions:**
- Guardian proposes: "We should test whether the threshold is parameter-dependent"
- Someone asks: "How much variation?"
- Guardian specifies numerical ranges
- Skeptic suggests: "What if the effect is just a finite-size artifact?"
- Guardian adds finite-size checks to the falsification plan

### What artifacts are being produced

**Required outputs:**

1. **Circularity audit** (list of potential circular reasoning)

   Example:
```
   Observable: "Distance" between nodes
   Circularity risk: Defining distance assumes the geometry we're trying to derive.
   
   Mitigation: Measure correlation decay instead. Define effective distance 
   as log(correlation) without assuming metric exists.
```

2. **Control/baseline specifications**

   Example:
```
   Experimental condition: System with mechanism X active
   Control condition: System with mechanism X removed
   Baseline: Measure observable Y in control, this is Y_baseline
   
   Success requires: Y_experimental > Y_baseline + 2σ
   If Y_experimental ≈ Y_baseline: Null result (X has no effect)
```

3. **Null result definition**

   Example:
```
   Null result means ANY of:
   - Observable Y does not exceed baseline
   - Property Z fails invariance test
   - Control shows same effect as experimental
   
   If null: Document as "Hypothesis falsified" and proceed to Interpret phase 
   for post-mortem, not rescue attempt.
```

4. **Robustness requirements**

   Example:
```
   Parameter: γ (noise strength)
   Test range: [0.03, 0.05, 0.08]
   Invariance criterion: Critical threshold J_crit must vary <15% across this range
   
   If drift >15%: Result is parameter-dependent, not invariant. 
   Hypothesis must be reclassified or modified.
```

5. **Falsification checklist**

   Example:
```
   Before claiming success, verify ALL of:
   [ ] Observable Y measured in both experimental and control
   [ ] Y_experimental > Y_baseline + 2σ
   [ ] Control shows Y_control ≈ Y_baseline ± σ
   [ ] Property Z tested at three γ values
   [ ] Z drift across γ is <15%
   [ ] Finite-size check: Result holds for N=4,6,8 or shows systematic scaling
   [ ] Solver precision check: Result unchanged with tighter tolerances
```

### How you know this phase is complete

**Exit criteria checklist:**

- [ ] All observables checked for circular assumptions
- [ ] Control conditions specified (what to measure, what it should show)
- [ ] Null result explicitly defined
- [ ] Parameter sensitivity tests specified with numerical thresholds
- [ ] Falsification checklist written (what must pass before claiming success)
- [ ] Guardian confirms: "I cannot think of an additional test that would catch bias"
- [ ] Skeptic reviews and proposes at least one additional artifact check

**Test:** Hand the falsification plan to someone skeptical. Ask: "Could this hypothesis still be wrong even if all these checks pass?" If yes, add more checks.

### What must exist before moving to next phase

A locked document containing:
- Circularity audit (potential circular reasoning identified and mitigated)
- Control/baseline specifications
- Null result definition
- Robustness requirements (parameters, ranges, thresholds)
- Falsification checklist (all tests that must pass)

### The 3 most common ways this phase gets corrupted

**Corruption 1: "We'll add controls if the results look weird"**

Team skips specifying control conditions, planning to add them "if needed" after seeing data.

**Why this is fatal:** Controls added after seeing data are unconsciously designed to support the result.

**Correction:** No execution without pre-specified controls. Period.

---

**Corruption 2: Robustness tests that are too narrow**

Guardian specifies: "Test γ = 0.05 and γ = 0.06" (tiny range, unlikely to show parameter dependence).

**Why this is fatal:** Narrow ranges hide parameter sensitivity. The team can claim robustness without actually testing it.

**Correction:** Parameter ranges must be wide enough to matter. If γ can realistically vary 2x-3x, test that range.

---

**Corruption 3: Falsification checklist written by the hypothesis originator**

The person who proposed the hypothesis also writes the falsification tests.

**Why this is fatal:** They'll unconsciously design tests they know the hypothesis can pass.

**Correction:** Guardian role must be someone different from the hypothesis originator. If unavoidable, external review of the falsification plan is mandatory.

---

## Phase 3: Execute

### What the team is doing

**Orchestrator actions:**
- States: "We are now in Execute phase. Substrate leads. No interpretation until Falsify phase."
- Provides Substrate with locked Define and Constrain outputs
- Monitors for interpretation drift

**Substrate actions:**
- Reads the measurement specifications
- Sets up experiment/simulation exactly as specified
- Runs experimental condition
- Runs control condition identically
- Documents all parameters, settings, random seeds
- Reports raw results without explaining them
- Flags anomalies ("Curve behaves unexpectedly at t>500") but does not interpret them

**Team actions:**
- Someone sees preliminary data and says: "Oh interesting, it looks like—"
- Orchestrator interrupts: "No interpretation until Falsify phase."
- Data is saved in raw form
- Parameters are logged
- If something breaks (code error, numerical instability), execution pauses and returns to Constrain to add error-handling specifications

### What artifacts are being produced

**Required outputs:**

1. **Raw data files**

   Example structure:
```
   experiment_gamma_0.05_run_001.csv
   control_gamma_0.05_run_001.csv
   experiment_gamma_0.08_run_001.csv
   control_gamma_0.08_run_001.csv
```

2. **Parameter log**

   Example:
```
   Run ID: exp_001
   Date: 2026-01-15
   Code version: commit a3f8d92
   Parameters:
     N = 4
     J = 1.73
     γ = 0.05
     t_max = 50
     dt = 0.1
     solver_tol = 1e-8
     random_seed = 42
   Observable Y: 0.847
   Control Y: 0.102
   Anomalies flagged: None
```

3. **Anomaly flags** (without interpretation)

   Example:
```
   Anomaly: Solver failed to converge at t=487 for γ=0.10
   Action taken: Re-ran with tighter tolerance (1e-10)
   Result: Converged successfully
   Interpretation: [none - flagged for Falsify phase]
```

4. **Execution notes** (procedural only)

   Example:
```
   - Ran experimental condition first, then control
   - Control condition required 20% longer runtime (expected for lower coupling)
   - Data saved to /results/2026-01-15/
   - No code changes made during execution
```

### How you know this phase is complete

**Exit criteria checklist:**

- [ ] All experimental conditions specified in Constrain have been run
- [ ] All control conditions have been run identically
- [ ] Raw data saved in non-interpretable format (CSV, HDF5, not plots)
- [ ] Parameter log complete for every run
- [ ] Anomalies flagged but not interpreted
- [ ] No one on the team has discussed what the results "mean"
- [ ] Substrate confirms: "I executed exactly what was specified. I did not tune anything."

**Test:** Hand the raw data and parameter logs to someone outside the project. Ask: "Can you reproduce this?" If they say "I don't know what you ran," documentation is incomplete.

### What must exist before moving to next phase

- Raw data files (all experimental and control conditions)
- Complete parameter logs (every setting, every run)
- Anomaly flags (if any)
- Execution notes (what was done, when, in what order)

**Format:** Structured files, not narratives. Data must be machine-readable.

### The 3 most common ways this phase gets corrupted

**Corruption 1: "Let me just try this slightly different parameter value"**

Substrate sees that a result is "almost" good and tweaks a parameter to "see if it gets better."

**Why this is fatal:** This is parameter tuning guided by desired outcomes. The result is no longer a test of the hypothesis.

**Correction:** If parameters need adjustment, stop Execute, return to Constrain, document why the adjustment is principled, lock the new specification, then restart Execute.

---

**Corruption 2: Interpreting while executing**

Substrate shows preliminary data to the team. Someone says: "This proves X!" Excitement spreads. Remaining runs are executed with this interpretation in mind.

**Why this is fatal:** Interpretation contaminates execution. Unconscious decisions (which runs to prioritize, which anomalies to investigate) become biased.

**Correction:** Raw data is not shown to anyone until Execute completes. If someone sees it accidentally, Orchestrator calls a halt and decides whether Execute is compromised.

---

**Corruption 3: Selective execution**

Substrate runs the experimental condition, sees it looks good, and skips the control condition "because it's probably fine."

**Why this is fatal:** Controls exist to catch false positives. Skipping them means you'll never know if your result is an artifact.

**Correction:** All conditions specified in Constrain must be run. No exceptions. If time/compute is limited, reduce scope in Constrain phase, not Execute phase.

---

## Phase 4: Falsify

### What the team is doing

**Orchestrator actions:**
- States: "We are now in Falsify phase. Skeptic leads. No celebration until all checks pass."
- Provides Skeptic with raw data and the falsification checklist from Constrain

**Skeptic actions:**
- Reads the falsification checklist
- For each item, checks whether it passes
- Proposes alternative explanations for positive results
- Tests parameter sensitivity
- Hunts for numerical artifacts (solver precision, finite-size effects, threshold artifacts)
- Documents which checks passed, which failed, which are inconclusive
- Does NOT soften failures or explain them away

**Guardian actions:**
- Reviews Skeptic's work
- Asks: "Did you check for [specific artifact]?"
- If Skeptic says "The result looks robust," Guardian pushes: "How do you know? Show me the sensitivity test."

**Team actions:**
- Skeptic says: "The invariance test failed. J_crit drifts 16% across γ."
- Someone says: "But 16% is close to 15%, maybe we should—"
- Guardian interrupts: "The threshold was 15%. This is a fail. Document it."
- Team resists urge to re-interpret the threshold

### What artifacts are being produced

**Required outputs:**

1. **Falsification report** (checklist with pass/fail/inconclusive for each item)

   Example:
```
   Falsification Checklist Results:
   
   [ PASS ] Observable Y > baseline + 2σ
     Experimental: Y = 0.847 ± 0.03
     Control: Y = 0.102 ± 0.02
     Difference: 7.4σ
   
   [ FAIL ] Property Z invariant under γ variation
     γ=0.03: J_crit = 1.46
     γ=0.05: J_crit = 1.73 (reference)
     γ=0.08: J_crit = 2.01
     Drift: 16.2% (threshold was <15%)
     Conclusion: Parameter-dependent, not invariant
   
   [ PASS ] Control shows Y_control ≈ baseline
     Expected: 0.10 ± 0.02
     Measured: 0.102 ± 0.02
     Conclusion: Control behaves as expected
   
   [ INCONCLUSIVE ] Finite-size scaling
     N=4: J_crit = 1.73
     N=6: Not tested (insufficient compute)
     N=8: Not tested
     Conclusion: Cannot rule out finite-size artifact
```

2. **Artifact analysis**

   Example:
```
   Artifact Check: Solver precision
   Test: Re-ran with tolerance 1e-10 (vs. baseline 1e-8)
   Result: J_crit changed by 0.003 (0.2%)
   Conclusion: Result is numerically stable
   
   Artifact Check: Threshold detection
   Test: Varied detection threshold from 0.05 to 0.15 of max signal
   Result: Arrival time changed by <3%
   Conclusion: Not sensitive to threshold choice
   
   Artifact Check: Time window
   Test: Extended t_max from 50 to 100
   Result: No new arrivals detected
   Conclusion: Non-arrivals are real, not time-limited
```

3. **Alternative explanations**

   Example:
```
   Alternative Explanation 1: Effect is just noise averaging
   Test: Ran 10 independent trials with different random seeds
   Result: Effect present in 10/10 trials, variance < 5%
   Conclusion: Not a noise fluctuation
   
   Alternative Explanation 2: Control is broken
   Test: Verified control produces expected baseline behavior in isolation
   Result: Control matches theoretical prediction
   Conclusion: Control is functioning correctly
   
   Alternative Explanation 3: Parameter choice is cherry-picked
   Test: Checked if J=1.73 was selected after seeing results
   Result: J=1.73 was pre-specified in Constrain phase (locked document dated prior to execution)
   Conclusion: Not cherry-picked
```

4. **Overall verdict**

   Example:
```
   Falsification Verdict: HYPOTHESIS FALSIFIED
   
   Reason: Property Z failed invariance test (drift 16.2% > 15% threshold)
   
   What this means:
   - Observable Y is real (passes control comparison)
   - But Y is parameter-dependent, not invariant
   - Original hypothesis claimed invariance
   - Claim must be reclassified or abandoned
   
   Recommendation: Proceed to Interpret phase for conceptual reclassification
```

### How you know this phase is complete

**Exit criteria checklist:**

- [ ] Every item on falsification checklist marked pass/fail/inconclusive
- [ ] At least 3 alternative explanations considered and tested
- [ ] Parameter sensitivity tested per Constrain specifications
- [ ] Artifact checks performed (solver, threshold, finite-size where applicable)
- [ ] Overall verdict written (hypothesis supported / falsified / inconclusive)
- [ ] Skeptic confirms: "I cannot think of another way this could be an artifact"
- [ ] Guardian confirms: "The falsification was honest, not performative"

**Test:** Show the falsification report to someone who wants the hypothesis to be false. Ask: "Is there a loophole?" If yes, close it.

### What must exist before moving to next phase

- Falsification report (pass/fail for each checklist item)
- Artifact analysis (tests performed, results)
- Alternative explanations (considered and ruled out or confirmed)
- Overall verdict (hypothesis supported / falsified / inconclusive)

### The 3 most common ways this phase gets corrupted

**Corruption 1: "16% is basically 15%"**

A check fails marginally (16% vs. 15% threshold). Team argues it's "close enough" and marks it as pass.

**Why this is fatal:** Thresholds exist to prevent this exact rationalization. If 16% is acceptable, the threshold should have been 20%.

**Correction:** Threshold violations are failures. Period. If the threshold was wrong, that's a lesson for next time, not an excuse to ignore it now.

---

**Corruption 2: Falsification feels like a formality**

Skeptic goes through the checklist but doesn't seriously try to break the result. Checks are performed but not pushed hard.

**Why this is fatal:** Performative falsification misses real artifacts.

**Correction:** Guardian monitors Skeptic and asks: "If you wanted this hypothesis to fail, what would you test?" If Skeptic isn't testing those things, falsification is incomplete.

---

**Corruption 3: Alternative explanations are strawmen**

Skeptic proposes obviously wrong alternatives ("Maybe the computer is broken") that are easy to rule out, rather than plausible alternatives that threaten the result.

**Why this is fatal:** This creates the appearance of thorough falsification without the substance.

**Correction:** Guardian reviews alternative explanations and asks: "Would a serious critic propose this?" If not, generate better alternatives.

---

## Phase 5: Interpret

### What the team is doing

**Orchestrator actions:**
- States: "We are now in Interpret phase. We synthesize what we learned."
- Provides everyone with Define, Constrain, Execute, and Falsify outputs
- Asks: "What does the falsification verdict mean?"

**Team actions:**
- If verdict is SUPPORTED:
  - Team discusses what was learned
  - Identifies caveats and limitations
  - Decides whether to iterate with refined hypothesis or close
  
- If verdict is FALSIFIED:
  - Team discusses *why* it failed
  - Asks: "What did we learn from the failure?"
  - Considers whether the hypothesis can be reclassified or must be abandoned
  - No rescue attempts—if the falsification says it failed, it failed
  
- If verdict is INCONCLUSIVE:
  - Team discusses what additional tests would resolve ambiguity
  - Decides whether to iterate with better observables or close

**No one argues with the falsification verdict.** The team interprets the verdict, not relitigates it.

### What artifacts are being produced

**Required outputs:**

1. **Synthesis document**

   Example (for falsified hypothesis):
```
   Hypothesis: Mechanism X produces invariant property Z
   
   Falsification Verdict: FALSIFIED
   Reason: Property Z is parameter-dependent (16% drift across γ range)
   
   What we learned:
   - Observable Y is real and robust
   - But Y exhibits noise-dependent scaling, not invariance
   - The relationship follows J_crit ∝ γ^β with β ≈ 0.33
   
   Conceptual reclassification:
   - Original framing: Kinematic (invariant speed limit)
   - Revised understanding: Thermodynamic (dissipative phase transition)
   
   This is not a failure. This is a successful falsification that revealed 
   unexpected structure.
```

2. **Lessons learned**

   Example:
```
   What worked:
   - Pre-commitment to 15% invariance threshold prevented rationalization
   - Control conditions caught baseline effects we would have missed
   - Artifact checks ruled out solver precision issues
   
   What we'd do differently:
   - Define β (scaling exponent) in Phase 1, not discover it post-hoc
   - Test wider γ range earlier (0.01-0.20 instead of 0.03-0.08)
   - Add finite-size scaling to falsification checklist upfront
   
   Process integrity:
   - No sequence violations occurred
   - Falsification was honest (we accepted the 16% drift as failure)
   - Role separation held throughout
```

3. **Decision: Iterate, Pivot, or Close**

   Example:
```
   Decision: PIVOT
   
   New hypothesis (for future testing):
   "Mechanism X produces a noise-dependent phase transition with 
   critical exponent β ∈ [0.30, 0.35]"
   
   Why this is different from rescue:
   - We are not claiming the original hypothesis succeeded
   - We are documenting that it failed and proposing a different question
   - The new hypothesis will go through Define phase from scratch
   
   If we run this: Start PACI from Phase 1 with the new hypothesis
```

### How you know this phase is complete

**Exit criteria checklist:**

- [ ] Falsification verdict summarized honestly
- [ ] What was learned documented (even from failure)
- [ ] Caveats and limitations stated explicitly
- [ ] Decision made: iterate / pivot / close
- [ ] If iterating: New hypothesis written, ready for Phase 1
- [ ] If closing: Final report completed
- [ ] No rescue attempts made to salvage failed hypothesis

**Test:** Show the synthesis to someone skeptical. Ask: "Does this honestly represent what happened?" If they say "You're spinning this," interpretation is dishonest.

### What must exist before closing

- Synthesis document (verdict, what was learned, reclassification if applicable)
- Lessons learned (what worked, what didn't, process integrity check)
- Decision (iterate / pivot / close, with rationale)

If iterating: New hypothesis statement ready for Phase 1

If closing: Archival-quality documentation of the full process

### The 3 most common ways this phase gets corrupted

**Corruption 1: Rescue attempts**

Hypothesis failed falsification. Team says: "But what if we redefine Z to mean..." and reinterprets the failed result as success.

**Why this is fatal:** This undoes all the work of Phases 1-4. The hypothesis failed. Changing definitions now makes it unfalsifiable.

**Correction:** Accept the failure. Document what was learned. If you want to test a different hypothesis, start PACI from Phase 1 with new definitions.

---

**Corruption 2: "Lessons learned" that blame tools instead of process**

Team writes: "The simulation was too small" or "We needed better computers" instead of "We should have pre-committed to finite-size tests."

**Why this is fatal:** Blaming tools prevents learning. The issue wasn't the tools—it was the process that didn't account for their limitations.

**Correction:** Lessons learned should focus on what *you* would do differently in Define/Constrain phases, not external factors.

---

**Corruption 3: Interpretation without falsification**

Team skips directly from Execute to Interpret because "the results are obviously good."

**Why this is fatal:** "Obviously good" results are often artifacts. Skipping falsification means you'll never know.

**Correction:** No interpretation without falsification. If results look good, falsification should be fast. But it's never skippable.

---

## Cross-Phase Checks

### How to detect sequence violations in real time

**Violation pattern: Interpretation during Execute**

Someone says: "This curve means X" while data is still being generated.

**Detection:** Orchestrator stops immediately and asks: "Are we in Falsify phase yet?" If no, interpretation must cease.

---

**Violation pattern: Execution before Constrain completes**

Someone says: "Let's just start running it, we can add controls later."

**Detection:** Guardian asks: "Where is the falsification checklist?" If it doesn't exist, execution cannot begin.

---

**Violation pattern: Defining terms after seeing data**

Someone says: "Now that we see the results, I think 'stable' should mean..."

**Detection:** Ontologist asks: "When was this term defined?" If the answer is "just now," the definition is invalid.

---

### How to recover from sequence violations

**If violation detected early (same phase):**

1. Stop immediately
2. Identify what was contaminated
3. Discard contaminated work
4. Restart the phase correctly

**If violation detected late (next phase):**

1. Stop immediately
2. Return to the phase where violation occurred
3. Redo all subsequent phases
4. Do not attempt to salvage contaminated outputs

**If violation detected after publication:**

1. Retract or issue correction
2. Document what went wrong
3. Rerun with proper sequence discipline

---

**End of File**

---

This document shows what PACI looks like when a team is actually running it. Everything else is in [`01-paci-protocol.md`](01-paci-protocol.md).
