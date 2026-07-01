---
title: Transformer forward pass (token → next token)
source: pasted study notes "basic LLM.rtf"
date: 2026-06-28
tags: [transformers, architecture, attention, embeddings, inference]
type: diagram
---

# Transformer forward pass (token → next token)

## In one line
How a transformer turns "Tom hit the ball" into a guess for the next word: tokenize → embed → repeat a stack of attention+MLP blocks → predict.

## Key points
- **Pipeline at a glance:** raw text → tokenizer → token files → model → training loop → checkpoints → generation.
- **Per token:** tokenize to integers → embedding-table lookup turns each into a vector of "raw meaning."
- **Each block (repeated, here ×6, own weights) does 9 steps:** RMSNorm → Q/K/V projections (split into heads) → RoPE (rotate by position) → Attention (scores → causal mask → softmax → blend V) → +residual → RMSNorm → SwiGLU MLP → +residual.
- After the last block: final RMSNorm → take the last token's vector → **LM Head** (dot with embedding table = *weight tying*) → logits → softmax → sample next token → append → repeat.

## Why I saved this
My go-to map when I need to remember what actually happens inside one transformer block, in order.

## Source / raw
From pasted study notes "basic LLM.rtf" (archived 2026-06-28); originally an ASCII "one-page summary" diagram. Related: [[2026-06-28-neural-nets-and-transformers]], [[2026-06-28-llm-training-loop]].
