# Role Architecture: Mapping PACI to Real Teams

The protocol defines five functional roles. Reality rarely gives you five separate people who can each specialize cleanly. This document shows how to map PACI onto the team you actually have—including the compromises you'll need to make and the failure modes to watch for.

---

## Scenario 1: Solo Researcher
**Your situation:** You're one person. You cannot literally separate generation from falsification.
**Can you run PACI?** Barely, and only with strict external structure.

### How to approximate role separation:
* **Orchestrator (you):** Maintain the overall timeline and phase discipline.
* **Ontologist (time-delayed you):** Write definitions in a locked document before any code exists. Commit to GitHub. Make it costly to change retroactively.
* **Constraint Guardian (external checklist):** Before running anything, write down null results, parameter variations, and control conditions. Treat this as non-negotiable.
* **Substrate (automated tools):** Use deterministic scripts. Do not iterate interactively—this allows interpretation to contaminate execution.
* **Skeptic (time-delayed you + external review):** Wait 24-48 hours after results exist before interpreting. Ask: *"If someone else got this result, would I believe it?"*

**The brutal reality:** Solo PACI works only if you treat your past self's commitments as if they came from someone else.

---

## Scenario 2: Two-Person Team
**Your situation:** You and one collaborator.
**Can you run PACI?** Yes, by splitting roles carefully.

### Mapping Option: Generator vs. Adversary
* **Person 1 (Builder):** Ontologist (defines) and Substrate (executes).
* **Person 2 (Breaker):** Constraint Guardian (designs tests) and Skeptic (hunts artifacts).
* **Both:** Alternate Orchestrator duties.

**Critical Rule:** Person 1 cannot interpret results until Person 2 has completed falsification. 
**Diagnostic Check:** If neither of you has ever said *"I think we need to restart this phase,"* your role separation is too weak.

---

## Scenario 3: Human + AI Systems
**Your situation:** You (human) plus multiple AI agents (Claude, GPT, Gemini, etc.).
**Can you run PACI?** Yes. This is one of the cleanest mappings because AI systems lack personal investment in outcomes.

### Recommended Mapping:
* **You (Orchestrator):** Maintain phase discipline; decide when to proceed vs. iterate.
* **AI Agent 1 (Ontologist):** Prompt: *"Your job is to ensure definitions are locked before execution. Be pedantic. Do not let me proceed with ambiguous terms."*
* **AI Agent 2 (Constraint Guardian):** Prompt: *"Design tests that could break my hypothesis. Be adversarial. Assume I'm unconsciously biased."*
* **Computational Tool (Substrate):** Run simulations exactly as specified.
* **AI Agent 3 (Skeptic):** Prompt: *"Explain why these results might be artifacts. Don't accept my interpretations unless they survive your challenges."*

---

## Scenario 4: Three-Person Team
**Your situation:** You plus two collaborators. This is close to ideal.

### Recommended Mapping:
* **Person 1 (Ontologist + Orchestrator):** Enforces discipline and rigor.
* **Person 2 (Substrate):** Executes experiments faithfully; reports without interpretation.
* **Person 3 (Guardian + Skeptic):** Full adversarial role; designs tests and hunts artifacts.

---

## Scenario 5: One Person Wearing Two Hats
Which combinations are safe vs. dangerous:

| Safe (Low Corruption Risk) | Dangerous (High Corruption Risk) |
| :--- | :--- |
| **Ontologist + Orchestrator:** Both enforce discipline. | **Substrate + Ontologist:** Executor shouldn't define success. |
| **Guardian + Skeptic:** Both adversarial roles. | **Substrate + Guardian:** Executor shouldn't design their own test. |
| **Substrate + Automation:** Machine-led execution. | **Any Role + Substrate:** The executor must not interpret. |

---

## Detecting Role Bleed (Diagnostic Checklist)

### Role separation is WORKING if:
* Definitions were locked before any code was written.
* Control conditions were specified before data collection.
* Someone challenged an interpretation and won.
* Raw results were documented before anyone explained them.

### Role separation is FAILING if:
* Definitions changed after seeing preliminary data.
* Controls were added retrospectively to "make the comparison fair."
* Falsification felt like a formality rather than a real test.
* Negative results were explained away rather than documented.

---

## What To Do When Perfect Separation Is Impossible
At a bare minimum, separate **Generation** (designing and running) from **Falsification** (determining validity). 

**Compensating controls:**
1.  **Pre-commitment artifacts:** Use version-controlled docs for criteria.
2.  **Time delays:** Insert mandatory waiting periods between execution and interpretation.
3.  **External review:** Share raw results with an outsider before sharing interpretations.

---
**End of File**
