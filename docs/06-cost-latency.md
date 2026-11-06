# 06 — Cost & Latency Estimate

## Purpose

Estimate what it costs to process lectures for a semester, and decide **when** processing happens: on upload, or overnight in a batch. The decision is a trade-off between latency (how fast the student gets the summary) and cost. This file gives the method and a worked template. It does not invent a real price — model prices change, so fill in the actual price from the provider you choose, on the date you check it.

## Inputs — fill in with real numbers

| Input | Value | Source / date checked |
|---|---|---|
| Lectures per week | [TEMPLATE — fill in, e.g. 3] | Course timetable |
| Weeks per semester | [TEMPLATE — fill in, e.g. 12] | Academic calendar |
| Total lectures per semester | Lectures per week × weeks | Calculated |
| Model chosen | [TEMPLATE — fill in, e.g. name of model] | Provider page |
| Cost per lecture processed (model) | [TEMPLATE — fill in, e.g. $X.XX] | Provider pricing, checked on [date] |
| Other cost per lecture (if any) | [TEMPLATE — fill in, or 0] | |
| Total cost per lecture | Model cost + other cost | Calculated |
| Lecturer review time per summary | [TEMPLATE — fill in, e.g. 10 minutes] | Lecturer interview, see `docs/02-research-notes.md` |

## Worked example — EXAMPLE numbers only

The numbers below are **EXAMPLE numbers to show the method**. They are not real prices and not a quote. Replace them with real prices before making a decision.

| Input | EXAMPLE value |
|---|---|
| Lectures per week | 3 |
| Weeks per semester | 12 |
| Total lectures per semester | 36 |
| Cost per lecture processed | $0.50 (EXAMPLE) |
| Cost per semester (model only) | 36 × $0.50 = **$18.00 (EXAMPLE)** |
| Cost per semester if cost per lecture were $2.00 (EXAMPLE) | 36 × $2.00 = **$72.00 (EXAMPLE)** |
| Cost per semester if cost per lecture were $5.00 (EXAMPLE) | 36 × $5.00 = **$180.00 (EXAMPLE)** |

Formula: **Cost per semester = lectures per week × weeks per semester × cost per lecture.**

Also calculate cost per success (see `docs/05-metrics.md`): if some summaries are rejected by the lecturer and must be re-run, the true cost per approved summary is higher than the cost per lecture.

## Latency options

### Option A — Process on upload

- **How it works:** as soon as notes are uploaded, the summary is generated.
- **Latency:** minutes. The student gets the summary almost immediately.
- **Cost:** usually higher. Each lecture is processed alone, at whatever time it arrives. No batching discount, if the provider offers one.
- **Best for:** a student who missed today's lecture and needs to catch up tonight.

### Option B — Overnight batch

- **How it works:** lectures uploaded during the day are processed together overnight, and summaries are ready the next morning.
- **Latency:** hours — ready next morning, not tonight.
- **Cost:** usually lower. Batching can reduce cost, and off-peak processing may be cheaper depending on the provider.
- **Best for:** routine revision, where the student does not need the summary the same evening.

## Decision

**Decision: overnight batch as the default, with on-upload processing as an exception.**

Reasoning, for student use:

1. **Most catch-up is not urgent to the minute.** A student who missed a lecture usually revises the next day, not within minutes of the lecture ending. A summary ready the next morning meets that need.
2. **Lecturer review needs time anyway.** In Stage 1 and Stage 2, a lecturer reviews the summary before students see it. That review step already adds hours. Same-minute processing does not make the summary reach the student faster if it still has to wait for review.
3. **Lower cost means more lectures can be covered.** For a fixed budget, overnight batching processes more lectures, which matters more to students than getting one summary a few hours earlier.
4. **Batching makes quality checks easier.** A batch can be audited together, and a failed fidelity check can block the whole batch before release.

**Exception:** process on upload when a student needs the summary the same evening — for example, before an exam the next day — and the lecturer has already approved the course for fast processing. That exception should be a deliberate choice, not the default.

This decision should be revisited after Stage 2, with real data: how often students asked for same-day summaries, what the real cost per lecture was, and whether lecturer review was actually the bottleneck.

## What to check before relying on this estimate

- Re-check the provider's price on the day you decide. Prices change.
- Test with a real lecture to measure the actual cost per lecture — token use depends on lecture length.
- Include re-runs: a rejected summary that is fixed and re-run costs twice.
- Include lecturer review time as a real cost, even if it is not a cash cost. If review takes 30 minutes per summary, that limits how many lectures can be covered, whatever the model costs.
