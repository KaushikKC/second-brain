---
title: Beyond plain transformers — SSM, Hybrid, MoE
source: pasted study notes "basic LLM.rtf"
date: 2026-06-28
tags: [architecture, ssm, mamba, mixture-of-experts, transformers]
type: paper-note
---

# Beyond plain transformers — SSM, Hybrid, MoE

## In one line
Three architecture tweaks that fix the transformer's long-sequence and memory costs: state-space models, hybrids, and mixture-of-experts.

## Key points
- **SSM (State Space Models):** an "advanced RNN" with a structured *state matrix* instead of a tiny vector. A math trick lets it train in parallel like a transformer, avoids vanishing gradients, and at generation reads only a **fixed-size state** — not every past token — so long-context generation is cheap.
- **Transformer cost it solves:** a transformer rereads all past tokens' keys/values for each new token; SSM just reads its fixed state whether it's 10 or 10,000 tokens.
- **Hybrid models:** interleave SSM and attention layers — SSM is fast/cheap for long sequences, a few attention layers give precise recall where it matters.
- **MoE (Mixture-of-Experts):** many small expert sub-networks; each token is routed to only a few, so only a **fraction of parameters are active** per token → far fewer weights read from memory → faster generation. Orthogonal to SSM/attention.

## Why I saved this
Quick reference for the main alternatives/additions to vanilla transformers and *why* each exists (speed + memory for long context).

## Source / raw
From pasted study notes "basic LLM.rtf" (archived 2026-06-28). Related: [[2026-06-28-neural-nets-and-transformers]], [[2026-06-28-llm-inference-optimization]].
