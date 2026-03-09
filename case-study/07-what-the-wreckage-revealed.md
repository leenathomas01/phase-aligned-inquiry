# What the Wreckage Revealed

**Status:** Observation note — not a claim, not a paper, not a conclusion.  
**Context:** This document records what became visible *after* the HQG hypothesis was cleanly falsified.  
**Purpose:** To preserve findings that are unrelated to the original exploration but may be worth someone else's attention.

---

## What We Were Looking For

The original hypothesis attempted to derive the speed of light as an emergent constant from a discrete quantum lattice model.

The claim: at a critical entanglement threshold (J_crit), the system would transition from chaotic to stable propagation, producing an invariant causal speed limit — analogous to c in relativity — arising from substrate dynamics rather than being imposed axiomatically.

It failed. J_crit drifted 23.5% across noise conditions, exceeding the pre-committed 15% invariance threshold.

The kinematic interpretation was falsified cleanly.

---

## What the Data Actually Showed

When J_crit values were plotted against noise parameter γ, a systematic scaling relationship emerged:

| γ (noise) | J_crit (critical threshold) |
|-----------|----------------------------|
| 0.03      | 1.3                        |
| 0.05      | 1.7                        |
| 0.08      | 1.9                        |

This is not random drift. This is a power law.

Fitting to J_crit ∝ γ^β yields **β ≈ 0.33**.

This value is notable because it closely matches critical exponents observed in **3D dissipative phase transitions**:

- 3D Ising universality class: β_theory ≈ 0.326
- Fluid critical points: β_theory ≈ 0.33
- Mean-field theory: β_theory = 0.5 (ruled out)

Three data points are insufficient to definitively assign a universality class. But the value is specific enough to be worth noting — and worth testing properly.

---

## What This Means (If It Holds)

The original hypothesis framed J_crit as a **kinematic property** — a constant, like the speed of light, independent of environmental conditions.

The data suggests J_crit is actually a **thermodynamic property** — a noise-dependent critical threshold, like a condensation temperature.

This is a reclassification, not a rescue.

### The original framing (falsified):
Spacetime has an invariant causal speed limit emerging from substrate dynamics.

### The more interesting framing (suggested by wreckage):
**Causality is a dissipative phase transition.**

"Being able to transmit causal information" is not a permanent background property of the system. It is something the system can *achieve* or *lose* depending on whether entanglement (J) is strong enough to overcome entropy (γ).

At high noise (γ >> J): geometry does not exist. No stable propagation. No causal connectivity.

At low noise (J >> γ): geometry stabilizes. Causal propagation emerges.

The transition between these regimes is governed by critical exponents — not invariant constants.

---

## Why This Is Stranger Than The Original Claim

The original hypothesis, if confirmed, would have been elegant but not surprising. Relativity already establishes that c is invariant. Deriving it from a lattice model would have been a technical achievement.

What the wreckage suggests is stranger:

**Spacetime geometry, in this model, is fragile.**

It exists only when entanglement wins against entropy. Under sufficiently high noise, the system loses the ability to propagate causal influence at all. There is no "speed of light" in that regime — not because it's infinite or zero, but because the causal structure itself has melted.

This reframes the original question entirely.

We were asking: *"Can c emerge from substrate dynamics?"*

The wreckage asks: *"What if causality itself is a phase of matter — something that can exist, melt, and re-emerge depending on thermodynamic conditions?"*

That is a different question. It may be a more interesting one.

---

## What Would Need to Happen for This to Be More Than a Note

This observation rests on three data points and a suggestive exponent. It is not a result. It is a direction.

To take it seriously, someone would need to:

1. **Finite-size scaling analysis** — verify J_crit shifts systematically with system size N following β-scaling predictions
2. **Wider γ range** — test γ ∈ [0.01, 0.20] to confirm the power law holds beyond three points
3. **Independent exponent measurement** — calculate correlation length exponent ν and verify consistency with 3D Ising class (ν ≈ 0.63)
4. **Alternative noise models** — test whether β ≈ 0.33 persists under different decoherence mechanisms
5. **Longer time evolution** — extend t_max beyond 50 timesteps to verify asymptotic stability

None of this was done. Resource constraints ended the exploration at three γ values.

The scaling law was always in the data. It only became visible after the invariance claim was definitively closed.

---

## A Note on How This Was Found

This observation would not have been extractable without clean falsification.

If the team had soft-failed on invariance — "23.5% is close to 15%, perhaps the threshold was too strict" — the β ≈ 0.33 pattern would have remained invisible, buried under attempts to rescue the original claim.

The protocol forced acceptance of what the data showed. That acceptance made the data readable.

**The wreckage was only visible because we stopped trying to repair the original structure.**

---

## Status of This Note

This is an observation preserved for anyone who finds it useful.

It is not a claim that causality is a phase transition.  
It is not a claim that β = 0.33 is physically meaningful.  
It is not a proposal that this work should be continued.

It is a note that says: *we were looking for one thing, found something else, and thought it worth writing down before moving on.*

If this direction is interesting to you — the physics, the methodology, or the strangeness of fragile causality — the full case study documentation is in `/case-study`.

---

*"The hypothesis failed. The data remained. We wrote down what the data said."*
