# 🦙 Fine-Tuned Llama-3 for Automated Python Code Repair

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](INSERT_YOUR_COLAB_LINK_HERE)
![Python](https://img.shields.io/badge/Python-3.10%2B-blue)
![Library](https://img.shields.io/badge/Unsloth-Fast_Llama-green)
![GPU](https://img.shields.io/badge/GPU-T4%20Compatible-orange)

This project demonstrates the **parameter-efficient fine-tuning (PEFT)** of the **Llama-3-8B** model to specifically detect and fix logic and syntax errors in Python code. 

By leveraging **QLoRA (Quantized Low-Rank Adaptation)** and the **Unsloth** library, this 8-billion parameter model was fine-tuned on a single commodity GPU (Tesla T4) while maintaining high inference accuracy.

---

## 🚀 Project Overview

Most modern LLMs are general-purpose. This project focuses on **transfer learning** to specialize a model for a single domain: **Software Engineering**.

* **Objective:** Input broken Python code $\rightarrow$ Output corrected, functional code.
* **Technique:** Fine-tuned `Llama-3-8B-bnb-4bit` using LoRA adapters to update only 1-2% of parameters, keeping the base model frozen.
* **Optimization:** Utilized **4-bit quantization** to reduce VRAM usage by ~70%, making training feasible on free tier Google Colab instances.

---

## 🛠️ Tech Stack & Methodology

* **Model Architecture:** [Llama-3 8B (Unsloth Version)](https://huggingface.co/unsloth/llama-3-8b-bnb-4bit)
* **Fine-Tuning Library:** [Unsloth](https://github.com/unslothai/unsloth) (2x faster training, 60% less memory)
* **Adapter Framework:** Hugging Face `PEFT` (LoRA)
* **Training Loop:** Hugging Face `TRL` (SFTTrainer)
* **Dataset:** [iamtarun/python_code_instructions_18k_alpaca](https://huggingface.co/datasets/iamtarun/python_code_instructions_18k_alpaca)

---

## 📊 Training Results

The model was trained for 60 steps to demonstrate convergence capability on the coding dataset.

* **Training Loss:** Decreased from **~1.8** to **~0.8** (indicating strong learning convergence).
* **Inference:** Capable of correcting logic errors (e.g., swapping subtraction for addition in an `add` function) that the base model might overlook without specific instructions.

### Example Output
**Input (Broken Code):**
```python
def add(a, b): return a - b

Model Prediction (Fixed Code):
def add(a, b): return a + b
