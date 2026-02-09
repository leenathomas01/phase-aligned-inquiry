# Lessons for PACI

**Date:** January 2026  
**Purpose:** Document what this case study reveals about PACI protocol behavior under real research conditions

This file examines what the HQG case study demonstrates about the Phase-Aligned Collaborative Inquiry protocol. It focuses on observable effects, not theoretical properties.

---

## What Would Normally Happen Without PACI

### When the 23.5% drift appeared

In typical research, when γ-invariance testing revealed J_crit drift of 23.5% (exceeding the 15% threshold), the following responses would be structurally likely:

**Threshold re-evaluation:** "15% was arbitrary. Let's reconsider whether 20% or 25% would be more appropriate given the noise characteristics of the system."

**Parameter space expansion:** "Perhaps invariance holds in a different γ regime. Let's test γ ∈ [0.10, 0.20] to find where it stabilizes."

**Measurement refinement:** "The ΔJ = 0.2 step size creates discretization error. If we use finer steps, we might find the drift falls within tolerance."

**Selective reporting:** "The γ=0.08 point passed (11.8% drift). Let's emphasize that result and note that γ=0.03 'requires further investigation.'"

**Silent pivot:** Begin discussing the β ≈ 0.33 scaling pattern without explicitly acknowledging that the invariance claim failed.

None of these are dishonest. They feel like reasonable scientific responses to marginal failure. But each one redefines success after seeing the data.

### When the t >100 timestep requirement was unmet

The Constrain phase specified that stability required correlation >10% amplitude for t >100 timesteps. The Execute phase ran to t_max = 50.

In typical research, this discrepancy would be handled by:

**Post-hoc justification:** "t = 50 is sufficient to demonstrate the transition. Extending to t >100 would be computationally expensive and is unlikely to change conclusions."

**Implicit redefinition:** Stop mentioning the t >100 requirement and report results as if t = 50 was always the criterion.

**Deferred verification:** "We observe stable behavior through t = 50. Full long-time stability will be verified in future work."

The Execute-Constrain mismatch would quietly disappear from the narrative.

### When the β ≈ 0.33 pattern became visible

Once the power law scaling emerged, typical research would:

**Retrofit the hypothesis:** Reframe the original claim as "exploring critical behavior" rather than "deriving an invariant constant," making it appear the scaling law was the goal all along.

**Merge narratives:** Present both the invariance claim and the scaling law as compatible results, avoiding explicit acknowledgment that one falsifies the other.

**Emphasize success:** Lead with β ≈ 0.33 discovery, mention invariance failure as a "caveat" in supplementary material.

The story would become about what succeeded, not what failed.

---

## What Actually Happened Because PACI Phases Were Respected

### Define phase: Pre-commitment locked observables

The Define artifact (01-define.md) stated explicitly:

> Property Z: Invariance. The saturation velocity must remain invariant (within <15% drift) across a 2x variation in γ.

This was locked in January 2026 before any simulations ran.

**Effect:** When drift measured 23.5%, there was no ambiguity about whether this constituted failure. The threshold was not negotiable because it had been committed to a timestamped document before results existed.

**What this prevented:** Retroactive threshold adjustment.

### Constrain phase: γ-sweep was designed to expose failure

The Constrain artifact (02-constrain.md) specified:

> γ test range: [0.03, 0.05, 0.08]  
> All three values must be tested  
> Results from all three must be reported  
> No selective reporting permitted

The γ-sweep was not exploratory. It was a deliberate falsification test.

**Effect:** When γ=0.03 showed 23.5% drift, this could not be dismissed as an outlier or deferred to "future work." The test was pre-specified, and failure was unambiguous.

**What this prevented:** Selective reporting and parameter cherry-picking.

### Execute phase: No interpretation, no tuning

The Execute artifact (03-execute.md) contains only:

- Parameter values used
- Files produced
- Anomalies observed (procedural only)

No J_crit values. No mention of success or failure. No discussion of what results mean.

**Effect:** The substrate did not know whether the hypothesis was succeeding or failing during execution. Parameters could not be unconsciously tuned toward desired outcomes.

**What this prevented:** Parameter drift guided by preliminary results.

### Falsify phase: Mechanical checklist application

The Falsify artifact (04-falsify.md) applied the Constrain checklist item-by-item. When Item 8 failed, the verdict was:

> **Hypothesis status:** FALSIFIED  
> **Reason:** Falsification checklist Item 8 failed. J_crit drift at γ=0.03 measured at 23.5%, exceeding pre-committed 15% invariance criterion.

No supporting evidence list. No interpretation. No alternative explanations. Just: checklist item failed.

**Effect:** The verdict was emotionally cold. There was no defense, no softening, no "however" clause. Failure was stated and the file ended.

**What this prevented:** Rationalization at the falsification stage.

### Interpret phase: Reclassification became possible

Because falsification was clean and final, the Interpret phase (05-interpret.md) could examine what the failure revealed without appearing to rescue the hypothesis.

The β ≈ 0.33 scaling law was presented as a discovery *enabled by* falsification, not a replacement for the falsified claim.

**Effect:** Reclassification from kinematic constant to thermodynamic phase transition was intellectually honest because it occurred *after* accepting that the original claim failed.

**What this prevented:** Narrative merging where failure and discovery are presented as if they were always the same claim.

---

## Key PACI Properties Revealed by This Case

### Property 1: Time-consistency of artifacts

Each phase artifact is frozen at the moment it was completed:

- 01-define.md contains no knowledge of what happened in Phases 2-5
- 02-constrain.md contains no knowledge of whether tests passed or failed
- 03-execute.md contains no J_crit values or interpretations
- 04-falsify.md contains no alternative explanations or conceptual reclassification

**Observable effect:** A reader can verify that constraints were not designed after seeing results. The artifacts are time-ordered and temporally innocent.

**Why this matters:** It removes the suspicion that PACI was retrofitted onto a narrative. The case study passes the forensic timeline test.

### Property 2: Each phase prevents a specific self-deception mechanism

| Phase | Prevents |
|-------|----------|
| Define | Retroactive redefinition of observables |
| Constrain | Designing tests that cannot fail |
| Execute | Parameter tuning toward desired outcomes |
| Falsify | Softening failure through interpretation |
| Interpret | Conflating discovery with hypothesis success |

**Observable effect:** At each phase transition, there was an opportunity for motivated reasoning to enter. The phase boundaries blocked it.

**Why this matters:** PACI does not rely on participants being more virtuous. It makes corruption structurally difficult.

### Property 3: Clean falsification enables discovery

The β ≈ 0.33 scaling law was always present in the data. But it only became interpretable after the invariance claim was definitively rejected.

**Counterfactual:** If the team had soft-failed on invariance (e.g., "drift is 16%, close to 15%, possibly acceptable"), the β pattern would have been invisible—buried under attempts to rescue the invariance claim.

**Observable effect:** Falsify phase brutally closed the invariance question. This freed Interpret phase to examine the data without defending the original hypothesis.

**Why this matters:** Discovery occurred *because of* falsification, not *despite* it.

### Property 4: Pre-commitment creates non-negotiable thresholds

The 15% invariance criterion was not obviously correct. It could have been 10%, 20%, or 25%. The specific value mattered less than the fact that it was locked before data existed.

**Observable effect:** When drift measured 23.5%, there was no debate about whether this counted as failure. The threshold was not subject to reconsideration.

**Why this matters:** Pre-commitment transforms subjective judgment into objective measurement. The hypothesis either passed or failed—there was no middle ground.

### Property 5: Role separation across time, not just agents

PACI separates roles not only by assigning different people to different functions, but by separating functions *temporally*.

The Substrate (Execute) cannot interpret because interpretation happens in a later phase. The Skeptic (Falsify) cannot reclassify because reclassification happens in a later phase.

**Observable effect:** Even if a single person performed all phases, the temporal separation enforces discipline. Each phase has a specific job and is forbidden from doing future phases' jobs.

**Why this matters:** PACI scales down to solo researchers if phase discipline is maintained.

### Property 6: Falsification produces evidence, not conviction

The Falsify phase did not argue that the hypothesis was wrong. It applied a checklist and recorded which items passed or failed.

**Observable effect:** The verdict ("FALSIFIED") is supported by mechanical application of pre-committed criteria, not by persuasive reasoning about why the hypothesis should be rejected.

**Why this matters:** This removes the need to convince anyone. The checklist either passed or failed. Argument is unnecessary.

---

## Why This Case Study Is Stronger Than a Theoretical Description

### A protocol description explains what PACI should do

Reading `methodology/01-paci-protocol.md` explains the phases, roles, and sequence discipline. It describes the structure.

But structure can sound compelling in theory and fail in practice.

### This case study shows what PACI actually did

The HQG case documents:

- A hypothesis with meaningful conceptual investment (emergent spacetime)
- Temptation to redefine success (23.5% drift "close to" 15%)
- Opportunities for parameter tuning (Execute phase)
- Pressure to merge narratives (invariance + scaling law)
- Discovery emerging from failure (β ≈ 0.33)

**What this reveals:** The phase boundaries were not bypassed when results were unfavorable.

### The case study is falsifiable in a way theory is not

Someone reading the methodology files might think: "This assumes perfect adherence. Real research won't follow these rules."

The HQG case study is evidence that adherence is possible. The artifacts are timestamped and phase-locked. The sequence is auditable.

**A skeptic can verify:** Did Constrain specify the γ-sweep before Execute ran? Yes (02-constrain.md predates 03-execute.md). Did Falsify apply the checklist mechanically? Yes (04-falsify.md contains no alternative explanations). Did Interpret occur after falsification? Yes (05-interpret.md explicitly references the verdict).

The case study passes forensic scrutiny. Theory alone cannot do this.

---

## Final Observation

When the 23.5% drift appeared, the 15% threshold could not be reconsidered because it had been pre-committed.

When β ≈ 0.33 became visible, the invariance claim could not be quietly replaced because falsification had already been recorded.

The artifacts show that each phase did only its assigned job.

The hypothesis failed. The data remained. Interpretation followed.

That sequence is what the protocol enforced.

---

**End of File**
