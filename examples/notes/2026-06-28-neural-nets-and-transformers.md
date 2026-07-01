---
title: Neural nets & why transformers won
source: pasted study notes "basic LLM.rtf"
date: 2026-06-28
tags: [neural-networks, transformers, attention, ai-fundamentals]
type: paper-note
---

# Neural nets & why transformers won

## In one line
A neural net is brain-inspired layers of nodes that learn patterns; transformers beat older RNNs by reading a whole sentence at once instead of word-by-word.

## Key points
- Neural network = layers of connected "neurons" that learn to spot patterns and predict; the base of all modern AI.
- Old RNNs read sequentially, so they forgot the start of a long sentence by the end.
- Transformers fixed this with **self-attention**: every word's relevance to every other word is computed at once (e.g. "bank" near "river" ≠ money).
- Reading words in **parallel** is the real unlock — it lets training scale to huge text corpora, which is what made tools like ChatGPT possible.

## Why I saved this
The clearest mental model for *why* transformers exist — the jumping-off point for everything else in my LLM notes.

## Source / raw
From pasted study notes "basic LLM.rtf" (archived 2026-06-28). Related: [[2026-06-28-transformer-forward-pass]], [[2026-06-28-beyond-transformers-ssm-hybrid-moe]].
