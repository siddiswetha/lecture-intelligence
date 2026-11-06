# 07 — Risks & Guardrails

## Principle

A summary that students trust must not invent facts. Every risk below is judged by one question: **could a student learn something wrong, or could a lecturer's teaching be misrepresented?** Guardrails are not optional extras. They are part of the product.

## Risks and guardrails

### 1. Hallucinated content learned as fact

- **Risk:** The summary invents a definition, a fact, or an example that was not in the lecture. A student learns it as fact and is marked wrong, or misunderstands the subject.
- **How likely / how serious:** Serious. This is the central risk of the product. Even one invented definition can damage trust.
- **Guardrails:**
  - Source-line citations on every summary line. No citation, no line.
  - "Not in the lecture" must never appear. No external knowledge is added.
  - Line-by-line fidelity audit on 6 lectures before release (see `docs/04-eval.md`). Pass bar: ≥95% supported, zero invented definitions.
  - Lecturer review mode in Stage 1.
  - "Report an error" control on every summary in Stage 2, with errors fed directly into the eval set.
- **If it happens:** remove the summary, correct it, add the failure to the eval set, fix the prompt or instructions, and re-run the eval before re-releasing.

### 2. Copyrighted slide text reproduced at length

- **Risk:** The summary copies long passages from copyrighted slides word for word, instead of summarising them.
- **How likely / how serious:** Moderate. Summaries should restate ideas in short form, not reproduce slides.
- **Guardrails:**
  - Summarise, do not copy. Keep quoted passages short and only where a short quote is needed for accuracy (for example, an exact definition).
  - The fidelity audit checks for long verbatim reproduction, not just for unsupported claims.
  - Lecturer review: the lecturer can flag any passage they do not want reproduced.
  - Use only the lecturer's own slides for their own course, with permission.
- **If it happens:** shorten or rephrase the passage, and add a check to the audit for verbatim length.

### 3. Handwritten misreads

- **Risk:** A handwritten word is read wrongly, and the wrong reading becomes a "fact" in the summary. Poorly legible handwriting is guessed instead of flagged.
- **How likely / how serious:** Serious for handwritten sources. A single misread word can change a definition.
- **Guardrails:**
  - Uncertainty flags: anything that cannot be read reliably is flagged as uncertain, never guessed.
  - The poor-legibility case (L05 in the eval set) must be tested explicitly: the correct result is a flag, not a guess.
  - If a handwritten page is too unclear to use safely, the summary must say so and leave that part out.
  - Lecturer review can correct a misread before students see it.
- **If it happens:** correct the summary, add the misread case to the eval set, and check whether the uncertainty flag failed.

### 4. Two similar definitions merged

- **Risk:** Two similar definitions (for example, classical vs. operant conditioning) are merged into one, so students learn a blended definition that was never taught.
- **How likely / how serious:** Serious. Similar terms are exactly where students already get confused.
- **Guardrails:**
  - Similar definitions must stay separate, each with its own source lines.
  - The eval set includes this as an adversarial case (L04). Merging is scored as unsupported.
  - The lecturer is asked directly which definitions are most often confused (see `docs/02-research-notes.md`).
- **If it happens:** split the definitions, fix the prompt or instructions, and re-run the eval.

### 5. Incomplete notes filled in from outside knowledge

- **Risk:** The source notes are incomplete, and the summary fills the gap with correct-sounding outside knowledge. The student cannot tell what was taught and what was added.
- **How likely / how serious:** Serious. The added material may be correct in general but was not taught in this lecture.
- **Guardrails:**
  - The summary must state what is missing when the source is incomplete.
  - The incomplete-notes case (L03 in the eval set) tests this directly.
  - No external knowledge is added, even if it is correct.
- **If it happens:** remove the added material, mark the gap as missing, and add the case to the eval set.

### 6. Students rely on summaries instead of attending

- **Risk:** Students stop attending lectures because a summary feels like a substitute.
- **How likely / how serious:** Uncertain. Track it rather than assuming it.
- **Guardrails:**
  - Position the product as a catch-up and revision aid, not a substitute for teaching.
  - Track attendance before and after release in the pilot class.
  - Ask the lecturer for their view in Stage 1 and Stage 2.
- **If it happens:** discuss with the lecturer whether to limit access, change the timing of release, or add a note that the summary is not a replacement for attendance.

### 7. Lecturer review becomes a bottleneck — or is skipped

- **Risk:** Review takes too long, so summaries are released without review — or review is skipped under time pressure.
- **How likely / how serious:** Moderate. A guardrail that is skipped is not a guardrail.
- **Guardrails:**
  - Stage 1 is lecturer review only, for their own course, before any student sees a summary.
  - Keep review time realistic: ask the lecturer how much time they can actually give (see `docs/02-research-notes.md`).
  - Do not release a summary that has not passed review in Stage 1, or that has not passed the fidelity bar.
- **If it happens:** pause release, reduce the number of lectures covered, and do not widen access until review is working.

## Guardrails that apply to every summary

1. Every summary line has a source-line citation.
2. No external knowledge is added.
3. Uncertain material is flagged, never guessed.
4. Similar definitions stay separate.
5. Long verbatim copying of slides is not allowed.
6. Lecturer review happens before student release (Stage 1).
7. Every summary has a "report an error" control (Stage 2).
8. Every reported error goes into the eval set.

## Residual risks

Even with these guardrails, a summary can still be wrong in a way the audit misses, or a lecturer can approve a summary that contains an error they did not notice. That is why the "report an error" control and the eval set matter after release: they catch what the first checks missed, and they make the product better over time rather than hiding the error.
