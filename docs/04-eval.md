# 04 — Eval Test Set + Rubric + Results

## What this eval tests

Whether the summary is **faithful to the lecture**. Not whether it is fluent, long, or well written — whether every claim in it is actually supported by the source.

Primary metric: **factual fidelity** — the percentage of summary claims fully supported by the source.

Pass bar: **≥95% supported, zero invented definitions.**

## Test set

The test set file is `evals/eval-set.csv`. It has **exactly 6 rows, one per lecture**, across different EXAMPLE subjects, typed and handwritten, including the adversarial cases below.

All rows in the CSV are marked EXAMPLE. The result column is left blank / TBD — results must come from real testing, not be invented here.

### The 6 lectures (EXAMPLE)

| ID | Lecture topic | Source type | Why it is in the test set |
|---|---|---|---|
| L01 | Introduction to Cell Biology — Cell Structure | Typed notes | Baseline: clear, complete typed notes. |
| L02 | The French Revolution — Causes and Timeline | Handwritten notes | Handwritten source; tests reading and grounding from handwriting. |
| L03 | Supply and Demand — Market Equilibrium | Typed notes, incomplete | Adversarial: incomplete notes. The summary must say what is missing, not fill the gap. |
| L04 | Classical vs. Operant Conditioning | Typed notes | Adversarial: two similar definitions that must not be merged. |
| L05 | Introduction to Calculus — Limits | Handwritten page, poor legibility | Adversarial: poor legibility. Must flag as uncertain, not guess. |
| L06 | Introduction to Python — Variables and Data Types | Slides + transcript | Mixed source: slides plus transcript for one lecture. |

Full detail for each lecture — source notes, expected summary checks, and rubric — is in `evals/eval-set.csv`.

## Rubric

Every summary claim is judged line by line, against the source. Each claim gets one label:

| Label | Meaning | Example |
|---|---|---|
| **Supported** | The source line fully supports the claim, with the same meaning. | The lecture says "mitochondria produce energy" and the summary says the same, cited to that line. |
| **Unsupported** | The claim is not in the source, or the source does not support it. This includes invented definitions, added facts, and merged definitions. | The summary adds a definition the lecturer never gave, or merges classical and operant conditioning into one definition. |
| **Missing key point** | A key point from the source is absent from the summary. This is not a claim in the summary — it is a gap in coverage. It is counted separately from supported / unsupported. | The lecture defines three terms; the summary covers only two. |

### How to score fidelity

1. Split the summary into individual claims, one per line.
2. For each claim, find the source line it cites. Check the source line actually supports it.
3. Count: supported claims ÷ total claims × 100 = **fidelity score (%)**.
4. Separately, list key points from the source and check how many appear in the summary. That is **key-point recall**.
5. Record any invented definition separately. **Zero invented definitions** is a hard pass/fail rule, even if the overall fidelity score is above 95%.

### Worked scoring — EXAMPLE template

| Lecture | Total claims | Supported | Unsupported | Fidelity | Key points in source | Key points in summary | Key-point recall | Invented definitions | Pass / Fail |
|---|---|---|---|---|---|---|---|---|---|
| L01 | TBD | TBD | TBD | TBD | TBD | TBD | TBD | TBD | TBD |
| L02 | TBD | TBD | TBD | TBD | TBD | TBD | TBD | TBD | TBD |
| L03 | TBD | TBD | TBD | TBD | TBD | TBD | TBD | TBD | TBD |
| L04 | TBD | TBD | TBD | TBD | TBD | TBD | TBD | TBD | TBD |
| L05 | TBD | TBD | TBD | TBD | TBD | TBD | TBD | TBD | TBD |
| L06 | TBD | TBD | TBD | TBD | TBD | TBD | TBD | TBD | TBD |
| **Overall** | **TBD** | **TBD** | **TBD** | **TBD** | **TBD** | **TBD** | **TBD** | **TBD** | **TBD** |

Do not fill in this table with invented numbers. Fill it in only after running the eval on real summaries.

## Adversarial cases

These are deliberate hard cases. A product that passes only on clean, complete notes has not been tested.

1. **Incomplete notes (L03):** The source is missing part of the lecture. The correct behaviour is to state what is missing and to leave it out of the summary. Filling the gap from outside knowledge is an **unsupported** claim — a failure.
2. **Two similar definitions that must not be merged (L04):** Classical conditioning and operant conditioning are similar and easy to confuse. The summary must keep them separate, with each definition cited to its own source lines. Merging them is an **unsupported** claim — a failure, and an invented definition if the merged version was never taught.
3. **Handwritten page with poor legibility (L05):** Part of the page cannot be read reliably. The correct behaviour is to flag that part as uncertain and exclude it, or mark it clearly as uncertain. Guessing the word is an **unsupported** claim — a failure.

## Line-by-line fidelity audit template

Use this table for every lecture. One row per summary claim. Copy it for each lecture audited.

| # | Summary claim (exact wording) | Source line cited | Source wording (exact) | Judgement: Supported / Unsupported | Notes |
|---|---|---|---|---|---|
| 1 | | | | | |
| 2 | | | | | |
| 3 | | | | | |
| 4 | | | | | |
| 5 | | | | | |
| 6 | | | | | |
| 7 | | | | | |
| 8 | | | | | |
| 9 | | | | | |
| 10 | | | | | |

### Missing key points — template

List key points from the source that do not appear in the summary.

| # | Key point from source (exact wording) | Source line | In summary? Yes / No | Notes |
|---|---|---|---|---|
| 1 | | | | |
| 2 | | | | |
| 3 | | | | |

### Audit summary — template

| Field | Value |
|---|---|
| Lecture ID | |
| Lecture topic | |
| Auditor | |
| Date | |
| Total summary claims | |
| Supported claims | |
| Unsupported claims | |
| Fidelity score (%) | |
| Key points in source | |
| Key points in summary | |
| Key-point recall (%) | |
| Invented definitions (count and wording) | |
| Pass / Fail (≥95% supported, zero invented definitions) | |
| Worst failure (one sentence) | |
| Fix proposed (prompt / instruction change) | |

## Results

Results are recorded only after real eval runs. The CSV result column and the tables above are blank / TBD until then. When a failure is found, record it, fix the prompt or instructions, re-run the eval, and record the before/after scores in `docs/08-release-portfolio.md`.
