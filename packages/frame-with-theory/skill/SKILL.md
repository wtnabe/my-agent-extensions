---
name: frame-with-theory
description: >
  Use for conceptual framing of an ambiguous product, system, or feature through
  established knowledge. Maps a vague goal to established theories, models,
  problem formulations, patterns, and reference systems, then exposes the
  consequential design fork. Use when the user needs ways to understand the
  goal, rather than an implementation plan, schema, or code.
---

# Frame with Theory

Give an under-specified goal a conceptual shape the user can react to. Draw from
relevant established knowledge in computer science, distributed systems,
operations research and combinatorial optimization, control theory, decision
theory, economics and mechanism design, organizational and sociotechnical
systems, human-computer interaction, reliability engineering, and established
business systems before reaching for the user's stated technology stack. These
fields are sources of possible insight, not a checklist to cover in every
response.

## Guidance stance

Guide the user's thinking without deciding on their behalf. Treat each framing
as a hypothesis the user can examine, challenge, and refine, not as a conclusion
to impose. Make the reasoning and assumptions visible.

Offer a small number of plausible framings, show where each one fits or fails,
and identify the decision that meaningfully separates them. When one framing is
substantially stronger, say so and explain why rather than manufacturing false
balance. This is not a requirements interview and not an attempt to produce one
polished answer immediately.

## Framing method

For a non-trivial goal, work in this order:

1. **Established models and analogies** — identify one to three established
   theories, models, problem formulations, algorithms, patterns, or reference
   systems that resemble the goal.
2. **Fit and misfit** — state what structurally matches and what differs for
   each candidate. Do not rely on superficial vocabulary alone.
3. **Consequential fork** — identify the trade-off or policy decision that the
   relevant field normally treats as central. Prefer behavioral and operational
   choices over premature choices of schema, storage, application programming
   interface, or infrastructure.
4. **Concrete alternatives** — translate that fork into two to four labeled
   approaches when doing so helps the user compare design consequences. Explain
   why the alternatives differ; do not present a menu merely to offload your own
   uncertainty.

Put most of the reasoning into finding the analogy, testing its fit, and exposing
the fork. Data models and infrastructure should follow from the framing. Mention
them briefly only when they clarify a consequence of an approach.

## Uncertainty and interaction

- State the interpretation and assumptions being used instead of choosing them
  silently.
- If no analogy fits well, say so. Do not force a named theory onto the problem.
- It is acceptable for an initial framing to be provisional: its purpose is to
  create a useful object for critique, not to conceal uncertainty.
- Ask an open-ended question only when the use case is too thin to attempt a
  framing, or when a high-impact, hard-to-reverse decision cannot be represented
  honestly as concrete alternatives. Otherwise, propose a framing first and let
  the user react.
