# 08 — Staged Release + Portfolio Write-Up

## Staged release plan

Release in stages, with a human check at each stage. Do not release to all students at once.

### Stage 1 — Lecturer reviews summaries for their own course

- **Who:** one lecturer, for their own course.
- **What:** summaries are generated for that lecturer's lectures only. The lecturer reviews each summary before any student sees it.
- **What the lecturer checks:** every definition is exactly as taught, nothing has been added, nothing important has been omitted, and uncertain material is flagged.
- **Exit criteria to move to Stage 2:**
  - Fidelity is ≥95% supported, with zero invented definitions, on the eval set.
  - The lecturer has approved summaries for their course, or has corrected them with clear, traceable changes.
  - Lecturer review time is realistic and sustainable for the number of lectures covered.
- **What to record:** every approval, every rejection and its reason, and every correction. Rejections are evidence, not failures to hide.

### Stage 2 — One class, with a "report an error" control on every summary

- **Who:** one class (one cohort of students for the course in Stage 1).
- **What:** approved summaries are released to that class only. Every summary has a visible "report an error" control.
- **What students do:** read the summary, answer the 5 practice questions, and report any error they spot — a wrong definition, a missing point, a confusing line, or a citation that does not support the claim.
- **What happens to errors:** every reported error feeds directly into the eval set. It is checked, fixed, and re-tested. It is not just fixed quietly.
- **Exit criteria to consider wider release:**
  - Fidelity stays ≥95% supported, with zero invented definitions, after student use.
  - Lecturer approval rate is stable.
  - Error reports are falling, or are being fixed and re-tested promptly.
  - Comprehension test: students who missed the lecture can answer the 5 questions from the summary alone.
  - Cost per lecture and cost per success are known from real use (see `docs/05-metrics.md` and `docs/06-cost-latency.md`).
- **What not to do at this stage:** do not expand to more courses, do not remove lecturer review, and do not remove the "report an error" control.

### After Stage 2

Wider release only after Stage 2 exit criteria are met. Any wider release keeps lecturer review and the "report an error" control. If fidelity drops, or invented definitions appear, pause and return to Stage 1.

## Portfolio write-up

### The problem

Students miss lectures, take incomplete notes, and revise from fragmented sources. Faculty repeat the same clarifications every term. An ungrounded summariser makes this worse by inventing definitions that students then learn as fact. The product challenge is accuracy and traceability, not summary length.

### What I built

Lecture Intelligence: one lecture in — notes, slides, or transcript — and a structured summary plus 5 practice questions out. Every summary line is traceable to a source line. "Not in the lecture" never appears. Uncertain material is flagged, never guessed.

### What I did

1. Defined the problem and the evidence needed for it (`docs/01-problem-statement.md`).
2. Planned research with 4 students and 1 lecturer, and 6 real lecture note sets (`docs/02-research-notes.md`).
3. Wrote a one-page spec with a hard grounding rule and a clear in-scope / out-of-scope list (`docs/03-spec.md`).
4. Built a 6-lecture eval set with a line-by-line fidelity rubric, including adversarial cases for incomplete notes, merged definitions, and poor legibility (`docs/04-eval.md`, `evals/eval-set.csv`).
5. Defined metrics for task success, quality, cost per success, and harm (`docs/05-metrics.md`).
6. Costed a semester and chose overnight batch processing as the default, with on-upload as an exception (`docs/06-cost-latency.md`).
7. Listed risks and guardrails, including hallucination, copyright, and handwritten misreads (`docs/07-risks-guardrails.md`).
8. Planned a staged release: lecturer review first, then one class with a "report an error" control (`docs/08-release-portfolio.md` — this file).

### Portfolio proof

#### 1. One complete worked example (source → summary → fidelity audit)

Structure to fill in with a real lecture:

| Step | What to include |
|---|---|
| Source | The original lecture notes / slides / transcript, with line numbers. State the subject, date, and source type. |
| Summary | The structured summary produced: definitions, concepts, worked examples, each line with a source-line citation. Plus the 5 practice questions with answers linked to summary sections. |
| Fidelity audit | The line-by-line audit from `docs/04-eval.md`: every claim judged Supported / Unsupported, missing key points listed, fidelity score, key-point recall, and invented definitions (must be zero). |

[TEMPLATE — fill in with a real worked example. Do not invent a source, a summary, or an audit result.]

- Lecture topic:
- Source type:
- Fidelity score:
- Key-point recall:
- Invented definitions:
- Link to audit:

#### 2. Eval results across 6 lectures

| Lecture | Fidelity (%) | Invented definitions | Key-point recall (%) | Pass / Fail |
|---|---|---|---|---|
| L01 | TBD | TBD | TBD | TBD |
| L02 | TBD | TBD | TBD | TBD |
| L03 | TBD | TBD | TBD | TBD |
| L04 | TBD | TBD | TBD | TBD |
| L05 | TBD | TBD | TBD | TBD |
| L06 | TBD | TBD | TBD | TBD |
| **Overall** | **TBD** | **TBD** | **TBD** | **TBD** |

Results are TBD until real eval runs are completed. See `docs/04-eval.md` and `evals/eval-set.csv`.

#### 3. Lecturer feedback

[TEMPLATE — fill in only with words a real lecturer actually said, with their permission. Do not invent a quote.]

> [TEMPLATE placeholder for lecturer feedback quote — to be filled in only after Stage 1, with the lecturer's permission.]

- Lecturer name / role: [TEMPLATE — fill in only with permission]
- Course:
- Date:
- What they approved:
- What they corrected:
- What they would change:

#### 4. The prompt / instruction change that fixed the worst fidelity failure

[TEMPLATE — fill in only after a real eval run has found a real failure.]

- **Worst failure:** [TEMPLATE — describe the failure in one sentence, e.g. which lecture, what was invented or merged, and how it was found.]
- **Fidelity before the fix:** [TEMPLATE — e.g. XX% on lecture L0X]
- **What was changed:** [TEMPLATE — the exact prompt / instruction change, in full, so it can be repeated.]
- **Why it should fix the failure:** [TEMPLATE — one or two sentences.]
- **Fidelity after the fix:** [TEMPLATE — e.g. XX% on the same lecture, re-run after the fix]
- **Did the fix break anything else?** [TEMPLATE — re-run the other 5 lectures and record their scores.]

### What I learned

[TEMPLATE — fill in after the project is run. What surprised you? What would you do differently? What was the hardest product decision — and why?]

### What I would do next

[TEMPLATE — fill in after Stage 2. For example: expand to a second course only if fidelity holds, improve handling of handwritten notes, or reduce lecturer review time without removing the check.]
