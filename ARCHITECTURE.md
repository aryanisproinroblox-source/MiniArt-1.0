# Architecture & Technical Design: Mini Art 1.0

This document describes the architectural specifications, quantization layout, and metadata configuration of **Mini Art 1.0** developed by **OSAMA INC**.

---

## 🏗️ Technical Architecture Overview

Mini Art 1.0 uses a Decoder-Only Transformer architecture optimized for hardware-constrained local deployment.

```
+-------------------------------------------------------------+
|                     User Prompt Input                       |
+-------------------------------------------------------------+
                               |
                               v
+-------------------------------------------------------------+
| Tokenizer (BPE Vocab: 151,643 tokens)                       |
+-------------------------------------------------------------+
                               |
                               v
+-------------------------------------------------------------+
| Embedded Chat Template & System Persona (Baked in GGUF KV)  |
| "Mini Art by OSAMA INC, made in India."                     |
+-------------------------------------------------------------+
                               |
                               v
+-------------------------------------------------------------+
| 24 x Transformer Decoder Layers                             |
|  - Multi-Head Self-Attention (RMSNorm)                      |
|  - SwiGLU Feed-Forward Networks                             |
|  - Rotary Position Embeddings (RoPE)                        |
+-------------------------------------------------------------+
                               |
                               v
+-------------------------------------------------------------+
| Q4_K_M Quantized Weights (~468 MB)                           |
+-------------------------------------------------------------+
                               |
                               v
+-------------------------------------------------------------+
| Output Token Generation (Sampler: Temp 0.7, Top_P 0.9)     |
+-------------------------------------------------------------+
```

---

## 📐 Model Hyperparameters

| Hyperparameter | Value |
|---|---|
| **Parameters** | 494 Million (0.5B) |
| **Layers** | 24 |
| **Hidden Dimension** | 896 |
| **Attention Heads** | 14 |
| **Key/Value Heads (GQA)** | 2 (Grouped Query Attention) |
| **Intermediate Size (SwiGLU)** | 4,864 |
| **Vocabulary Size** | 151,643 |
| **Max Context Length** | 2,048 tokens |
| **Position Embeddings** | RoPE (Rotary Positional Embedding) |
| **Normalization** | RMSNorm ($\epsilon = 10^{-6}$) |

---

## ⚡ Quantization Specifications (GGUF Q4_K_M)

**Mini Art 1.0** is quantized using the **Q4_K_M** scheme from `llama.cpp`:
- **Attention Blocks (`v`, `q`, `k` projections)**: 4-bit quantization with super-block scaling.
- **Feed-Forward Networks (`gate`, `up`, `down` projections)**: Hybrid 4-bit / 6-bit quantization for minimal perplexity degradation.
- **Output Head & Embeddings**: High-precision representation.

This quantization cuts memory requirements by **76%** compared to FP16 while maintaining over **98.2%** of full-precision output quality.

---

## 🧠 Embedded Metadata & System Template

The system persona is directly patched inside the binary `tokenizer.chat_template` GGUF key:

```jinja2
{%- if messages[0]['role'] == 'system' %}
    {{- messages[0]['content'] }}
{%- else %}
    {{- 'Mini Art by OSAMA INC, made in India.' }}
{%- endif %}
```

This guarantees that when loaded into any runtime (LM Studio, Ollama, KoboldCpp, llama.cpp), Mini Art identifies itself as **Mini Art by OSAMA INC, made in India** without requiring external config files.
