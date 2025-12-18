# Fine-Tuned Llama-3 for Automated Python Code Repair

This project demonstrates **parameter-efficient fine-tuning (PEFT)** of the **Llama-3-8B** model to detect and fix bugs in Python code. 

## 🚀 Project Overview
- **Base Model:** Llama-3-8B (Quantized to 4-bit)
- **Technique:** QLoRA (Quantized Low-Rank Adaptation) via `unsloth`
- **Dataset:** `iamtarun/python_code_instructions_18k_alpaca` (subset)
- **Infrastructure:** Trained on a single T4 GPU (Google Colab)

## 🛠️ Tech Stack
- **Unsloth:** For optimized 2x faster training
- **Hugging Face `trl`:** Supervised Fine-Tuning (SFT)
- **Peft:** LoRA adapter management
- **BitsAndBytes:** 4-bit quantization

## 📊 Results
The model was fine-tuned to take broken Python code as input and output the corrected version.
- **Training Loss:** Decreased from ~2.0 to ~0.8 (Converged successfully)
- **Inference Speed:** 2x faster inference using Unsloth native bindings

## 💻 How to Run
You can run this notebook directly in Google Colab
