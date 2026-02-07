# When to Use PACI

PACI is not a general research methodology. It is appropriate only for a narrow class of falsifiable claims where structural bias is likely. This document helps you decide whether PACI is appropriate for your research problem.

---

## Use PACI When...

### 1. Your claim is falsifiable
The hypothesis makes testable predictions. There exists a measurement or experiment that could show the hypothesis is wrong.
* **Examples:** "Algorithm X reduces error by >15%", "Mechanism Y produces signature Z."
* **Non-examples:** "This approach is elegant", "Consciousness involves information integration" (too vague).

### 2. Confirmation bias is a significant risk
The researcher has personal, career, or intellectual investment in the outcome. PACI prevents the resulting unconscious bias structurally.

### 3. Resources exist for role separation
Generation, constraint, execution, and falsification can be divided across different people or AI agents. 
* **Minimum:** Two distinct components (one to generate, one to validate).

### 4. The stakes justify the overhead
PACI is slower than normal research. Use it when getting the answer *right* matters more than getting an answer *quickly* (e.g., peer-reviewed publications, high-stakes policy, foundational work).

### 5. Pre-commitment to failure criteria is possible
You can define what counts as success and failure **before** looking at the data.

---

## Do NOT Use PACI When...

* **Work is in exploration or ideation mode:** Exploration requires cognitive flexibility; PACI enforces rigidity. Use exploration to *generate* hypotheses, then PACI to *test* them.
* **The problem is unfalsifiable:** Philosophical, aesthetic, or preference-based claims (e.g., "This UI feels more intuitive").
* **Consensus or stakeholder buy-in is the goal:** PACI preserves contradictions and does not optimize for harmony.
* **The context is emotionally supportive:** PACI is adversarial and truth-prioritizing; it is inappropriate for contexts requiring emotional care.
* **Time pressure prevents discipline:** Under pressure, PACI becomes performative and the structure collapses.
* **Single-agent work without external pre-commitment:** Solo PACI requires extreme discipline and rarely satisfies true role separation.

---

## Use PACI Later (Not Now)

1.  **During exploratory research:** Wait until a specific falsifiable claim exists.
2.  **During rapid prototyping:** Wait until you are ready to make a claim that others will depend on.
3.  **Before resources are available:** Incomplete PACI is worse than honest exploratory work.
4.  **Before the domain is ready:** Wait until established baselines and measurement techniques exist.

---

## Domain-Specific Examples

| Domain | Use PACI For... | Do NOT Use PACI For... |
| :--- | :--- | :--- |
| **Physics / Eng** | Model predictions, mechanism testing. | Early-stage sketching, parameter exploration. |
| **Machine Learning** | Benchmark performance, interpretability. | Hyperparameter tuning, architecture search. |
| **Economics / SocSci** | Intervention effects, predictive variables. | Descriptive statistics, qualitative interviews. |
| **Medicine / Bio** | Treatment efficacy, genetic risk ratios. | Compound screening, exploratory omics. |
| **Software Eng** | Latency optimization, scalability testing. | Code refactoring, UX research. |

---

## Decision Framework

1.  **Does a specific falsifiable hypothesis exist with pre-committable success criteria?**
    * *No: Do not use PACI (yet).*
2.  **Can generation be separated from validation?**
    * *No: Improve resources or structure first.*
3.  **Is confirmation bias a real risk?**
    * *Yes: Continue.*
4.  **Can the overhead (time/discipline) be afforded?**
    * *No: Acknowledge the work is fast exploratory research.*

### Final Question:
*"Is this the kind of claim where self-deception about truth is structurally likely?"*
If **yes**: Use PACI.

---
**End of File**
