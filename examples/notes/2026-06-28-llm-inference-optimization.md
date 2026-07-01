---
title: LLM inference optimization toolkit
source: pasted study notes "basic LLM.rtf"
date: 2026-06-28
tags: [inference, kv-cache, quantization, speculative-decoding, flashattention, serving]
type: paper-note
---

# LLM inference optimization toolkit

## In one line
The main tricks for serving LLMs fast and cheap: manage the KV cache, shrink precision, guess-ahead decoding, and faster attention/batching.

## Key points
- **KV cache & PagedAttention:** the KV cache stores past keys/values so they aren't recomputed; it grows with length and becomes the memory bottleneck. PagedAttention (vLLM) manages it like OS virtual memory in small pages → kills fragmentation, ~2–4× better utilization → bigger batches. Prefix caching reuses cache across requests sharing a system prompt.
- **Quantization:** drop weights (and optionally KV cache) from 16-bit to 8/4-bit. Know GPTQ & AWQ (4-bit, ~4–8× smaller), FP8 (≈2× throughput + KV capacity), GGUF (llama.cpp local CPU/Metal). INT8 KV ≈ halves cache; with PagedAttention cut KV memory 4–8×.
- **Speculative decoding:** small draft model proposes tokens, big model verifies in one pass → 2–3× faster, *identical* output. Variants: separate draft, self-speculation (Eagle), n-gram. Caveat: bad speculation length wastes compute.
- **FlashAttention (v3):** exact attention, 2–4× faster, linear memory. **GQA:** shares K/V heads across query heads → smaller KV cache for free. **Continuous batching:** dynamically packs requests → 10–20× throughput vs static; default in modern serving.

## Why I saved this
Checklist of levers when making inference faster/cheaper — names to reach for (vLLM, AWQ, FP8, Eagle, GQA) without re-googling.

## Source / raw
From pasted study notes "basic LLM.rtf" (archived 2026-06-28). Related: [[2026-06-28-beyond-transformers-ssm-hybrid-moe]], [[2026-06-28-transformer-forward-pass]].
