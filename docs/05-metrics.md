# 05 — Metrics Plan

## How this plan is organised

Metrics are grouped into four types: **task success, quality, cost per success, and harm**. Each metric has a definition, a target where one is set, and a note on how it is measured. No metric in this file has a real result yet — results tables are blank / TBD until real testing and real use.

## 1. Task success

Did the student actually complete the task the product exists for?

| Metric | Definition | Target | How it is measured |
|---|---|---|---|
| Catch-up completion | A student who missed the lecture reads the summary and answers all 5 practice questions. | TBD after pilot | Count of students who complete all 5 questions ÷ students who start. |
| Comprehension from summary alone | A student who missed the lecture answers the 5 questions correctly using only the summary. | TBD after pilot — set a target after the first comprehension test | Comprehension test: give the summary only (no source notes), ask the 5 questions, record correct answers. |
| Lecturer approval | A lecturer reviews a summary for their own course and approves it for students. | TBD after Stage 1 | Approved summaries ÷ summaries reviewed. Record reasons for every rejection. |

### Comprehension test — template

| Lecture | Student | Questions correct (out of 5) | Used summary only? Yes / No | Notes |
|---|---|---|---|---|
| | | | | |
| | | | | |

## 2. Quality

Is the output accurate, complete, and trustworthy?

| Metric | Definition | Target | How it is measured |
|---|---|---|---|
| Fidelity score | % of summary claims fully supported by the source. | **≥95% supported** | Line-by-line fidelity audit — see `docs/04-eval.md`. |
| Invented definitions | Number of definitions in a summary that were not in the source. | **Zero** | Counted in the fidelity audit. Any invented definition is a fail, even if fidelity is ≥95%. |
| Key-point recall | % of key points from the source that appear in the summary. | TBD after first eval run | Source key points found in summary ÷ total source key points. |
| Lecturer approval rate | % of reviewed summaries a lecturer approves. | TBD after Stage 1 | Approved ÷ reviewed. |
| Error reports | Number of errors reported through the "report an error" control, per summary. | Track and reduce over time | Count reports; every report feeds the eval set. |
| Uncertainty flag accuracy | When the product flags something as uncertain, was it genuinely uncertain? When it did not flag, should it have? | TBD after first eval run | Check flagged items against the source in the audit. |

### Quality results — template

| Lecture | Fidelity (%) | Invented definitions | Key-point recall (%) | Lecturer approval | Error reports |
|---|---|---|---|---|---|
| L01 | TBD | TBD | TBD | TBD | TBD |
| L02 | TBD | TBD | TBD | TBD | TBD |
| L03 | TBD | TBD | TBD | TBD | TBD |
| L04 | TBD | TBD | TBD | TBD | TBD |
| L05 | TBD | TBD | TBD | TBD | TBD |
| L06 | TBD | TBD | TBD | TBD | TBD |

## 3. Cost per success

What does one good outcome cost?

| Metric | Definition | How it is measured |
|---|---|---|
| Cost per lecture processed | Total cost to process one lecture (model + any other processing cost). | See `docs/06-cost-latency.md`. |
| Cost per approved summary | Cost per lecture ÷ lecturer approval rate. A summary that is rejected and re-run costs more than one that is approved first time. | Cost per lecture ÷ approval rate. |
| Cost per successful catch-up | Cost per lecture ÷ share of students who complete the catch-up and answer the questions. | Cost per lecture ÷ catch-up completion rate. |

A low cost per lecture is not success on its own. If a cheap summary is wrong, the cost per *successful* catch-up is high — and the harm is worse. Cost must always be read alongside fidelity.

## 4. Harm

What could go wrong for the student, the lecturer, or the course — and how would we know?

| Harm | Signal / metric | How it is measured |
|---|---|---|
| A student learns a wrong definition as fact | Unsupported claims in released summaries; error reports; wrong answers in the comprehension test that trace back to a summary error. | Fidelity audit + error reports + comprehension test analysis. |
| A student trusts a guessed reading of illegible handwriting | Uncertain items that were not flagged, found in audit. | Audit: count of guessed items that should have been flagged. |
| Copyrighted slide text reproduced at length | Long verbatim passages in summaries. | Audit: check summary lines against source for long verbatim reproduction. See `docs/07-risks-guardrails.md`. |
| A student relies on summaries instead of attending | Attendance change after release; lecturer feedback. | Track attendance before and after release in the pilot class; ask the lecturer. Do not assume a cause without evidence. |
| A lecturer's teaching is misrepresented | Lecturer rejections and corrections. | Record every rejection reason in Stage 1. |

## What not to measure

- Summary length, or number of words. Length is not quality.
- Number of lectures processed, on its own. Volume without fidelity is a risk, not a success.
- Student satisfaction alone. A student can be satisfied with a fluent, confident summary that is wrong. Satisfaction must be read alongside fidelity and comprehension.

## Review cadence

- After every eval run: update fidelity, key-point recall, and invented definitions.
- After Stage 1 (lecturer review): update lecturer approval rate and rejection reasons.
- After Stage 2 (one class): update catch-up completion, comprehension, error reports, and cost per success.
- Before any wider release: all four metric groups must be reviewed together. Do not release on cost or speed alone.
