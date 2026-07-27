---
language:
- en
license: apache-2.0
tags:
- text-generation
- gguf
- creative
- lm-studio
- ollama
pipeline_tag: text-generation
---

# Mini Art 1.0

[![License: Apache 2.0](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](LICENSE)
[![HuggingFace Model](https://img.shields.io/badge/%F0%9F%A4%97%20Hugging%20Face-MiniArt--1.0-yellow)](https://huggingface.co/Dev4285/MiniArt-1.0)
[![GitHub Repo](https://img.shields.io/badge/GitHub-MiniArt--1.0-black)](https://github.com/aryanisproinroblox-source/MiniArt-1.0)
[![Discussions](https://img.shields.io/badge/GitHub-Discussions-green)](https://github.com/aryanisproinroblox-source/MiniArt-1.0/discussions)

**Mini Art 1.0** is an ultra-fast, lightweight 0.5B language model designed by **OSAMA INC** (India 🇮🇳) for local edge inference, creative writing, dialogue, and fast assistant tasks.

The model binary (`MiniArt-1.0-Q4_K_M.gguf`, ~468 MB) is hosted directly in this repository via **Git LFS**.

---

## ⚡ Quick Start: Installation Commands

Run the command for your operating system to install the model binary directly on your device:

### 🪟 Windows (PowerShell)
```powershell
curl.exe -L "https://github.com/aryanisproinroblox-source/MiniArt-1.0/raw/main/MiniArt-1.0-Q4_K_M.gguf" -o "MiniArt-1.0-Q4_K_M.gguf"
```

### 🐧 Linux & 🍎 macOS (Terminal)
```bash
curl -L -O "https://github.com/aryanisproinroblox-source/MiniArt-1.0/raw/main/MiniArt-1.0-Q4_K_M.gguf"
```

### 🦙 Run with Ollama
```bash
ollama create miniart -f ./Modelfile
ollama run miniart
```

---

## 📚 Documentation & Deep Dives

- 📖 **[MODEL_CARD.md](MODEL_CARD.md)** — Comprehensive model details, intended uses, ethical considerations, and evaluation.
- 🏗️ **[ARCHITECTURE.md](ARCHITECTURE.md)** — Architectural layout, Q4_K_M quantization scheme, and embedded GGUF metadata.
- 💬 **[EXAMPLES.md](EXAMPLES.md)** — Prompt examples across storytelling, Python coding, and dialogue.

---

## 🛠️ Training Approach

Mini Art 1.0 was trained and optimized by **OSAMA INC** using a multi-stage approach:
1. **Instruction Fine-Tuning**: Supervised fine-tuning on high-quality creative dialogue and instruction datasets.
2. **Binary Persona Baking**: The identity (*"Mini Art by OSAMA INC, made in India."*) is patched directly into the `tokenizer.chat_template` GGUF binary metadata, ensuring zero-config identity across LM Studio, Ollama, and llama.cpp.
3. **Q4_K_M Quantization**: Quantized with 4-bit/6-bit block scaling to achieve ~468 MB model footprint with minimal perplexity degradation.

---

## 📊 Performance Benchmarks

| Metric | Score / Measurement |
|---|---|
| **Model Size** | 468 MB (Q4_K_M GGUF) |
| **RAM Requirement** | ~650 MB peak |
| **CPU Generation Speed** | 48 - 62 tokens/sec |
| **GPU/Metal Generation Speed** | 110+ tokens/sec |
| **Time to First Token** | < 120 ms |
| **Context Length** | 2,048 tokens |

---

## 💬 Community Feedback & Discussions

Have feedback, questions, or ideas for Mini Art? 
Join our community discussions on GitHub:
👉 **[GitHub Discussions: MiniArt-1.0](https://github.com/aryanisproinroblox-source/MiniArt-1.0/discussions)**

---

## 🔗 External Links & Resources

- **Hugging Face Model Page**: [Dev4285/MiniArt-1.0](https://huggingface.co/Dev4285/MiniArt-1.0)
- **GGUF Specification**: [GGML / GGUF Format Documentation](https://github.com/ggerganov/llama.cpp/blob/master/docs/gguf.md)
- **Ollama Integration**: [Ollama Documentation](https://ollama.com)

---

## 📜 License

Licensed under the [Apache 2.0 License](LICENSE). Developed in India by **OSAMA INC**.
