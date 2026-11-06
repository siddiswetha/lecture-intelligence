# 03 — One-Page Spec: Lecture Intelligence

## Product

Lecture Intelligence — grounded summaries and practice questions from one lecture.

## Problem

Students miss lectures and revise from incomplete, fragmented notes. Faculty repeat the same clarifications every term. An ungrounded summariser invents definitions that students then learn as fact.

## User

A student who missed a lecture, or whose notes are incomplete, and needs a trustworthy way to catch up. A lecturer who reviews the summary for their own course before students see it.

## Input

**One lecture's notes / slides / transcript only.**

- One lecture at a time. Not a whole module, not several lectures combined.
- Accepted input: typed notes, handwritten notes, slides, or a transcript — for that one lecture only.
- If the input is incomplete, the output must say what is missing. It must not fill the gap from outside knowledge.

## Output

**(a) Structured summary**, with these sections:

- Definitions — each definition exactly as taught, with a source-line citation.
- Concepts — the main ideas, in the order taught, each with a source-line citation.
- Worked examples — each example with its steps and result, each with a source-line citation.

**(b) Five practice questions**, with answers:

- Exactly 5 questions per lecture.
- Each question tests a point from the summary.
- Each answer is linked to the summary section it comes from.
- A student who missed the lecture should be able to answer all 5 from the summary alone.

**(c) A hard rule:**

- **"Not in the lecture" must never appear.** No external knowledge is added, even if it is correct and helpful. If a point was not in the lecture, it is not in the summary.

## Grounding rule

Every summary line must be traceable to a source line. Each line carries a citation to the source line it came from. A line without a source is not allowed. Anything uncertain — for example, a poorly legible handwritten word — is flagged as uncertain, never guessed.

## In scope

- One lecture in, one structured summary and 5 practice questions out.
- Source-line citations on every summary line.
- Uncertainty flags for unclear or incomplete source material.
- Lecturer review mode: a lecturer reviews summaries for their own course before release to students.
- A "report an error" control on every summary, so errors feed back into the eval set.

## Out of scope

- Summarising a whole module, a textbook, or multiple lectures at once.
- Adding external knowledge, background reading, or extra examples not in the lecture.
- Reproducing long passages of copyrighted slide text.
- Grading students, predicting exam questions, or replacing attendance.
- Guessing illegible handwriting.
- Merging two similar definitions into one — similar definitions must stay separate.

## Primary metric

**Factual fidelity** — the percentage of summary claims fully supported by the source.

Pass bar: **≥95% supported, zero invented definitions.**

See `docs/04-eval.md` for the rubric and `docs/05-metrics.md` for the full metrics plan.

## Success criteria

- A student who missed the lecture can answer the 5 practice questions from the summary alone.
- A lecturer approves the summary after review, or corrects it with a clear, traceable change.
- No invented definitions in any released summary.
- Every error reported by a student or lecturer is added to the eval set and re-tested.

## Non-goals

- Longer summaries. Length is not the goal; fidelity is.
- Covering every possible subject. The product is tested on 6 lectures first, then expanded only if fidelity holds.
- Removing the lecturer from the loop. Lecturer review is part of the product, not a temporary step.
