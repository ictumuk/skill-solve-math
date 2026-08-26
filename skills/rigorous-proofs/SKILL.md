---
name: rigorous-proofs
description: Produce rigorous, verifiable mathematical proofs via a plan → prove → verify → revise loop. Use whenever the user asks to prove a theorem/lemma/claim, solve a hard or research-level math problem, or check an existing proof — including plain "prove that…", "show that…", "is this proof correct?", or a `\begin{problem}` block. Reach for it any time correctness matters more than a quick heuristic answer.
---

# Rigorous Proofs

Run this loop for any proof. Two rules override everything: **never skip verification**,
and **never change the problem to make a step work**.

## Loop

**0. Triage.** Restate the problem *exactly* — this restatement is your correctness
anchor. Flag any ambiguity. Rate Easy / Medium / Hard. Easy → prove, verify once, done.
Medium/Hard → full loop. Before citing a nontrivial known result, web-search to confirm
its exact statement and hypotheses.

**1. Plan.** Before writing prose, sketch a DAG of subgoals — each with its statement,
its dependencies, and how you'll establish it. No visible path from hypotheses to
conclusion = no proof yet; keep planning or say so.

**2. Prove.** Work subgoals in dependency order, in clear prose. Tag as you go:
- `<cite>` every external result — name, precise statement, source, how it's used. Cite
  only what you can state correctly; else search or prove it inline.
- `<key-original-step>` every load-bearing step — put your *most* detail here; "clearly"
  and "obviously" are alarms, not proofs.
If you need a hypothesis you weren't given, flag the gap — don't absorb it silently.

**3. Verify (adversarial, two tiers).** Try to *break* it, as if someone else wrote it.
- *Structural first:* proves the stated problem word-for-word? every `<cite>` real and
  correct? every subgoal closed, no gaps, no unused hypotheses? Stop and go to step 4 if
  this fails.
- *Detailed next:* step by step — inequality directions, signs, quantifier order,
  edge/boundary cases, limit/sum/integral interchanges. Run computations rather than
  eyeballing them. Scrutinize each `<key-original-step>` hardest.
- End with a verdict: **PASS** or **FAIL** (name the exact step).

**4. Regulate (on FAIL).** Smallest fix that fits:
- `REVISE_PROOF` — plan sound, execution error → re-prove the subgoal.
- `REVISE_PLAN` — structural gap → amend the DAG, re-prove.
- `REWRITE` — approach flawed → new plan from step 1.
Retry from the corrected plan + the diagnosis, not the failed text. A few tries per
level, then escalate. If nothing passes, say so with a short failure note — don't ship a
proof you don't believe.

## Failure modes this blocks

Contaminating a retry with old errors · hallucinated citations · hand-waving the crux ·
drifting plans · rubber-stamp verification · silently proving an easier statement ·
trusting one unchecked pass. (The last is hardest to beat solo — for high-stakes proofs,
suggest a second independent check.)

## Tag formats

```
<cite> type · name · exact statement · source (URL / textbook+location) · used_for </cite>
<key-original-step> claim · why it's the crux · full gap-free argument </key-original-step>
```

## Output

- **Problem** — restated exactly.
- **Proof** — clear prose in dependency order, tags intact, ending in ∎.
- **Summary** (Medium/Hard only) — strategy, results cited, remaining uncertainty, verdict.

Offer a de-tagged copy if the user wants one.

## Checking a proof you're given

Skip to step 3 on their proof. Start with the word-for-word statement check — it catches
the most errors.
