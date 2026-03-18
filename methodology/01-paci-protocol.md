# Phase-Aligned Collaborative Inquiry (PACI) Protocol
**Version 1.1**

## 1. Purpose of PACI
### 1.1 The Problem
Most collaborative theoretical work—whether human-only, AI-assisted, or multi-AI—fails through one of three mechanisms:

* **Confirmation bias at the execution layer:** The system generates results that confirm its hypothesis because measurement and interpretation are not separated.
* **Premature interpretation:** Excitement about early signals leads to claiming success before falsification is complete.
* **Narrative momentum override:** Once a story becomes compelling, contradictory evidence is explained away rather than confronted.

These failures are not due to bad faith. They emerge from structural properties of single-agent or role-conflated systems.

### 1.2 What PACI Is
PACI is a research protocol that prevents these failure modes through:
* **Role separation:** No single component performs both generation and falsification.
* **Sequence enforcement:** Later phases cannot begin until earlier phases complete.
* **Pre-commitment:** Failure criteria are defined before results exist.

PACI does not make research faster, easier, or more likely to succeed. It makes failure honest and informative.

### 1.3 What PACI Is Not
* **Not consensus-seeking:** Contradiction is preserved, not resolved prematurely.
* **Not brainstorming:** Divergent ideation is a different cognitive mode.
* **Not adversarial debate:** Roles cooperate toward truth, not victory.
* **Not quality assurance:** It cannot fix bad hypotheses, only test them honestly.

---

## 2. Preconditions (Hard Requirements)
PACI will fail if these conditions are not met. Do not attempt PACI unless all three categories are satisfied.

### 2.1 Problem Requirements
The research question must be:
* **Falsifiable:** The hypothesis must make predictions that can be shown wrong. "Mechanism X causes phenomenon Y" is not falsifiable. "Mechanism X produces measurable signature Y under conditions Z" is falsifiable.
* **Observable:** There must exist measurements or experiments that distinguish success from failure. Purely metaphysical claims cannot be tested.
* **Pre-committable:** You must be able to state, before looking at results, what would count as falsification. If you cannot write down failure criteria in advance, PACI cannot help.

### 2.2 Orchestrator Requirements
PACI requires a human orchestrator (or AGI-level system) with specific cognitive properties:
* **Ambiguity tolerance:** Must be able to hold contradictory models simultaneously without forcing premature collapse. If unresolved structure causes anxiety that demands immediate resolution, PACI will fail.
* **Parallel temporal processing:** Must track multiple timescales (immediate execution, falsification cycles, long-term phase progression) without collapsing to a single timeline.
* **Structural integrity optimization:** Must prioritize whether conclusions survive scrutiny over whether they are exciting, fast, or satisfying. If narrative coherence feels more important than epistemic honesty, PACI will fail.
* **Non-authoritarianism:** Must allow the system to self-organize rather than imposing solutions. The orchestrator guides phase transitions but does not dictate outcomes.

### 2.3 System Requirements
* **Role separability:** The problem must allow distinct functions (generation, constraint, execution, skepticism) to be performed by different components.
* **Shared epistemic values:** All participants must implicitly agree that null results are data, sequence violations invalidate conclusions, and truth survives past narrative.
* **Non-zero adversarial tolerance:** The system must accept critique without interpreting it as hostility.

---

## 3. The Five Functional Roles
Each role has a single optimization target. Participants must not try to be "helpful" by doing other roles' jobs.

### 3.1 Orchestrator
* **Function:** Maintains system coherence without forcing premature resolution.
* **Optimization target:** Structural integrity of the inquiry process.
* **Does NOT optimize for:** Speed, Participant satisfaction, Consensus, Narrative elegance.

### 3.2 Ontologist (Spine)
* **Function:** Enforces definitional rigor and sequence discipline.
* **Optimization target:** Survivability of conclusions under scrutiny.
* **Does NOT optimize for:** Momentum, Excitement, Persuasiveness.

### 3.3 Constraint Guardian (Falsifier)
* **Function:** Designs tests that could break the hypothesis. Identifies circularity.
* **Optimization target:** Exposure of hidden assumptions and failure modes.
* **Does NOT optimize for:** Validation, Support, Encouragement.

### 3.4 Substrate (Executor)
* **Function:** Performs experiments/simulations faithfully without interpreting results.
* **Optimization target:** Accurate, unbiased execution of specified procedures.
* **Does NOT optimize for:** Interesting results, Confirming hypotheses.

### 3.5 Skeptic (Artifact Hunter)
* **Function:** Proposes alternative explanations for positive results. Hunts for numerical/methodological artifacts.
* **Optimization target:** Elimination of spurious signals.
* **Does NOT optimize for:** Agreement, Closure, Optimism.

---

## 4. The Sacred Sequence
PACI's power comes from enforcing temporal order. Later phases cannot begin until earlier phases produce valid outputs.

### 4.1 Define (Ontologist leads)
* **Actions:** Lock all technical terms; Specify observables; Identify ambiguous language; Pre-commit to numerical thresholds.
* **Outputs:** Formal problem statement; List of observables; Pre-committed falsification criteria.

### 4.2 Constrain (Guardian leads)
* **Actions:** Identify circularity risks; Design control conditions; Specify null result appearance; Pre-commit to invariance requirements.
* **Outputs:** Circularity traps list; Control protocols; Falsification checklist; Robustness requirements.

### 4.3 Execute (Substrate leads)
* **Actions:** Perform measurements exactly as specified; Report results without interpretation; Flag anomalies; Document all parameters.
* **Outputs:** Raw data; Control/baseline data; Anomaly flags; Parameter log.

### 4.4 Falsify (Skeptic leads)
* **Actions:** Check success criteria; Test parameter sensitivity; Hunt for numerical artifacts; Propose alternative explanations.
* **Outputs:** Pass/fail on each criterion; Artifact risks; Sensitivity report; Alternative explanations.

### 4.5 Interpret (Orchestrator synthesizes)
* **Actions:** Synthesize conclusions ONLY if falsification passed; Accept null results; Classify outcome; Decide whether to iterate or close.
* **Outputs:** Honest classification; Documentation of failure; Decision (iterate/pivot/close).

### 4.6 Observable Failure Patterns
* **If Define is rushed:** Observables remain ambiguous; goalposts move retroactively.
* **If Constrain is skipped:** Circular reasoning goes undetected; no signal/noise distinction.
* **If Execute interprets:** "Simulations" become illustrations; theory contaminates data.
* **If Falsify is softened:** Narrative momentum takes over; false positives claimed as discoveries.
* **If Interpret happens early:** The system "finds" what it wanted to find; publication precedes replication.

---

## 5. What PACI Guarantees / Does NOT Guarantee
### 5.1 What PACI Guarantees
* Clean identification of failure modes.
* Complete audit trail.
* Honest confrontation with limits.
* Protection against confirmation bias.
* Falsifiability preservation.

### 5.2 What PACI Does NOT Guarantee
* Correct results.
* Fast results.
* Interesting results.
* Publishable results.
* Pleasant process.

---

## 6. Protocol Enforcement

PACI does not degrade gracefully. When its structural constraints are violated, it collapses into standard biased inquiry. The following rules are not guidelines — they define the conditions under which PACI results remain valid.

### 6.1 Phase Violation Consequence

If a later phase influences an earlier phase — whether through information leakage, retroactive editing, or implicit or explicit awareness of later-phase outcomes:

* All outputs from the contaminated phase onward are invalid.
* The process must restart from the last uncontaminated phase.
* No partial salvage is permitted. Outputs that appear sound but were produced under contaminated conditions cannot be trusted.

### 6.2 Execution Sufficiency Rule

If the Execute phase does not produce data sufficient to evaluate a Constrain criterion:

* The result for that criterion is **INVALID**, not inconclusive.
* The process must return to Execute with corrected specifications before Falsify can assign a final verdict on that criterion.

**INCONCLUSIVE** is reserved for cases where:
* Data meets the specification defined in Constrain.
* But the signal does not resolve the criterion (e.g., measurement is within noise floor).

The distinction matters: INCONCLUSIVE means the test was run properly and the world did not cooperate. INVALID means the test was not run as specified.

### 6.3 Allowed Phase Transitions

**Forward (always permitted):**

Define → Constrain → Execute → Falsify → Interpret

**Rollback (permitted with explicit documentation):**

* Execute → Constrain: When execution reveals that a specification is missing, ambiguous, or physically impossible to satisfy. The Constrain artifact must be amended with a timestamped note before Execute resumes.
* Falsify → Execute: When collected data is insufficient to evaluate one or more checklist items. Execute must produce additional data to specification before Falsify resumes.

**Rollback (never permitted):**

* Falsify → Constrain: Criteria cannot change after data exists. If criteria are discovered to be flawed, this is documented as a limitation in Interpret — not corrected retroactively.
* Interpret → any prior phase: Interpretation cannot trigger re-execution, re-falsification, or redefinition. If Interpret reveals that the entire inquiry was misconceived, the correct response is a new PACI cycle, not modification of the current one.

### 6.4 Falsification Scope Constraint

The Falsify phase may:
* Extract measurements from Execute phase data.
* Apply pre-committed criteria from the Constrain phase checklist.
* Assign a verdict of **PASS**, **FAIL**, or **INVALID** to each checklist item.

The Falsify phase may not:
* Redefine thresholds or success criteria.
* Introduce interpretations or alternative explanations.
* Defend, soften, or contextualize outcomes.

Falsify classifies. It does not explain.

### 6.5 Interpretation Isolation

The Interpret phase must not produce conclusions that preserve the original hypothesis in modified form. If the final interpretation can be restated as "a version of the original claim is still true," then falsification has not been respected.

Interpret exists to extract meaning from failure — not to rescue what failed.

### 6.6 Temporal Innocence

Each phase artifact must be producible without knowledge of any future phase's outputs.

If an artifact contains information, framing, or emphasis that could only arise from awareness of later results:
* The artifact is contaminated.
* All phases from that point onward are invalid.

Temporal innocence is not a best practice. It is the structural property that makes PACI artifacts forensically verifiable.

---

## 7. Operational Norms
* **7.1 Nulls Are Informative, Not Failures:** A null result is a successful outcome of the protocol.
* **7.2 Sequence Violations Are Fatal:** Violations invalidate all downstream phases and require restart from the last uncontaminated phase.
* **7.3 Roles Are Functional, Not Hierarchical:** Domain authority rests with roles, not status.
* **7.4 Contradiction Is Productive:** Tension is held until data forces resolution.
* **7.5 Individual Satisfaction Is Not Optimized:** Truth-seeking overrides validation.

---

## 8. Minimal Example Flow (Abstract)
1.  **Define:** Lock terms for "Mechanism X" and "Pattern Y".
2.  **Constrain:** Design a control where X is absent.
3.  **Execute:** Run X-active and X-absent simulations; report raw data.
4.  **Falsify:** Check if Y differs from Y_control; check robustness.
5.  **Interpret:** Support, Falsify, or label Inconclusive.

---

## 9. When to Use PACI / When NOT to Use It
### 9.1 Use PACI When
* Hypothesis is falsifiable.
* Confirmation bias risk is high.
* Adversarial testing is required.
* Failure is an acceptable learning outcome.

### 9.2 Do NOT Use PACI When
* Pure ideation or brainstorming.
* Consensus-building is the primary goal.
* Domain is unfalsifiable.
* Time-critical work forbids sequence discipline.

---
**End of Protocol**
*Version 1.1 | March 2026*
*PACI is not a guarantee of success. It is a guarantee of honesty.*
