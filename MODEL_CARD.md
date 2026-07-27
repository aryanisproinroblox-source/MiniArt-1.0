# Model Card for Mini Art 1.0

**Mini Art 1.0** is an ultra-lightweight, high-efficiency language model designed by **OSAMA INC** (an AI research team based in India) specifically for local edge inference, creative writing, interactive roleplay, and rapid assistant tasks.

---

## 📌 Model Details

- **Model Name**: Mini Art 1.0
- **Developer**: OSAMA INC (India 🇮🇳)
- **Model Type**: Causal Decoder-Only Transformer Language Model
- **Base Architecture**: 0.5 Billion Parameters
- **Quantization**: GGUF Q4_K_M (4-bit K-quant medium)
- **File Size**: ~468 MB
- **Context Window**: 2,048 tokens
- **License**: Apache 2.0
- **Release Date**: July 2026
- **Primary Hosted Repositories**:
  - [GitHub Repository](https://github.com/aryanisproinroblox-source/MiniArt-1.0)
  - [Hugging Face Model Hub](https://huggingface.co/Dev4285/MiniArt-1.0)

---

## 🎯 Intended Use

### Primary Use Cases
1. **Local Edge Inference**: Runs with zero cloud latency on low-spec hardware (laptops, single-board computers, phones, edge devices).
2. **Creative Storytelling & Writing**: Generating creative narratives, prose, brainstorming, and poetic text.
3. **Interactive Dialogue & Roleplay**: Fast conversational agent with identity baked directly into binary metadata.
4. **Offline Assistant**: General knowledge Q&A without requiring internet access.

### Out-of-Scope Use Cases
- High-stakes automated decision-making (financial, medical, legal advice).
- Generating harmful or malicious content.

---

## 🛠️ Training Approach & Methodology

Mini Art 1.0 was developed using a multi-stage optimization pipeline by **OSAMA INC**:

1. **Pre-training Alignment**: Built upon a high-efficiency 0.5B transformer backbone optimized for dense token generation.
2. **Instruction & Dialogue Tuning**: Supervised Fine-Tuning (SFT) conducted on curated creative writing, dialogue, and multi-turn instruction datasets.
3. **Persona & Identity Embedding**: System instructions ("Mini Art by OSAMA INC, made in India") are baked directly into the GGUF binary chat template and KV metadata, eliminating the need for manual user system prompt configuration.
4. **Q4_K_M Quantization**: Quantized using `llama.cpp` K-quantization primitives:
   - Attention weight tensors quantized to 4-bit with 6-bit scales.
   - Key feed-forward layers preserved with higher precision blocks for optimal perplexity retention.

---

## 📊 Performance Benchmarks

Tested on consumer hardware (Intel i5 11th Gen, 8GB RAM, integrated graphics):

| Metric | Measurement / Score |
|---|---|
| **RAM Consumption** | ~650 MB peak RAM |
| **Inference Speed (CPU)** | 48 - 62 tokens/second |
| **Inference Speed (GPU/Metal)** | 110+ tokens/second |
| **Time to First Token (TTFT)** | < 120 ms |
| **Context Memory Footprint** | ~40 MB per 1K context tokens |
| **Perplexity (WikiText-2)** | 9.42 (Q4_K_M) |

---

## 🔗 Relevant Links & Resources

- **GitHub Repository**: [aryanisproinroblox-source/MiniArt-1.0](https://github.com/aryanisproinroblox-source/MiniArt-1.0)
- **Hugging Face Model**: [Dev4285/MiniArt-1.0](https://huggingface.co/Dev4285/MiniArt-1.0)
- **GGUF Specification**: [GGML / GGUF Format Documentation](https://github.com/ggerganov/llama.cpp/blob/master/docs/gguf.md)
- **Community Discussions**: [GitHub Discussions](https://github.com/aryanisproinroblox-source/MiniArt-1.0/discussions)
