---
title: LLM training loop (forward → loss → backward → update)
source: pasted study notes "basic LLM.rtf"
date: 2026-06-28
tags: [training, backpropagation, optimization, adamw, fine-tuning]
type: diagram
---

# LLM training loop (forward → loss → backward → update)

## In one line
The repeating cycle that makes a model less wrong: predict, measure error, push gradients backward, nudge every weight, repeat.

## Key points
- **Forward pass:** input tokens flow through layers 1→N to produce a prediction.
- **Loss:** one number for "how wrong?" (e.g. 2.45).
- **Backward pass:** gradients flow N→1; PyTorch's autograd does this automatically.
- **Weight update (AdamW):** `W = W − lr × gradient` — a tiny nudge per weight; loss ticks down (2.45 → 2.43...).
- Repeat for many steps (example run: 40 optimizer steps, loss ~1.45 by epoch 5).

## Why I saved this
The whole "how does it actually learn" cycle in one picture — quick refresher before any fine-tuning.

## Source / raw
From pasted study notes "basic LLM.rtf" (archived 2026-06-28); originally an ASCII training-cycle diagram. Related: [[2026-06-28-transformer-forward-pass]].
