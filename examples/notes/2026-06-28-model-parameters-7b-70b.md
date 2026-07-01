---
title: What "7B / 70B parameters" means
source: pasted study notes "Basic of AI.rtf"
date: 2026-06-28
tags: [llm, parameters, model-size, ai-fundamentals]
type: paper-note
---

# What "7B / 70B parameters" means

## In one line
Parameters are the learned weights ("knobs") inside a model — 70B = 70 billion knobs, NOT 70 billion words it knows.

## Key points
- Parameters = internal numbers the network adjusts during training; picture a giant board of knobs, training = tuning them all.
- They store patterns: grammar, word relationships, and (to a degree) reasoning — think brain *connections*, not vocabulary.
- Loose analogy: human brain ≈ 86B neurons; an LLM ≈ 70B parameters. More params → more capacity for complex patterns.
- Bigger is *usually* better (more patterns, reasoning, generalization) but not always — costs more compute, runs slower, diminishing returns.

## Why I saved this
Kills the common confusion that "70B = knows 70 billion words" — the right mental model for reading model sizes.

## Source / raw
From pasted study notes "Basic of AI.rtf" (archived 2026-06-28). Related: [[2026-06-28-neural-nets-and-transformers]], [[2026-06-28-transformer-forward-pass]].
