# Llama-2 7B QLoRA Fine-tuning

![Python](https://img.shields.io/badge/Python-3.12-blue)
![Transformers](https://img.shields.io/badge/Framework-HuggingFace%20Transformers-yellow)
![QLoRA](https://img.shields.io/badge/Method-QLoRA-green)
![Dataset](https://img.shields.io/badge/Dataset-Guanaco%201k-orange)

## 📌 Overview
This project fine-tunes Meta's Llama-2 7B Chat model using QLoRA (Quantized Low-Rank Adaptation) on the Guanaco dataset. The model is quantized to 4-bit precision to fit on a free-tier Google Colab T4 GPU (15GB VRAM).

## 🧠 What is QLoRA?
QLoRA combines two techniques:
- **Quantization** — compresses the model from 32-bit to 4-bit, reducing memory by 8x
- **LoRA** — adds small trainable matrices instead of updating all 7 billion parameters
- Together they make fine-tuning a 7B model possible on a single 15GB GPU

## 🗂️ Dataset
- **Name:** Guanaco Llama2 1k
- **Source:** [HuggingFace](https://huggingface.co/datasets/mlabonne/guanaco-llama2-1k)
- **Examples used:** 1000 instruction-response pairs

## ⚙️ Model Details
| Parameter | Value |
|-----------|-------|
| Base Model | NousResearch/Llama-2-7b-chat-hf |
| Fine-tuning Method | QLoRA |
| Quantization | 4-bit (NF4) |
| LoRA Rank | 64 |
| LoRA Alpha | 16 |
| LoRA Dropout | 0.1 |
| Framework | HuggingFace Transformers + PEFT + TRL |

## 🏋️ Training Configuration
| Parameter | Value |
|-----------|-------|
| Epochs | 1 |
| Batch Size | 1 |
| Gradient Accumulation Steps | 4 |
| Learning Rate | 2e-4 |
| Max Sequence Length | 512 |
| Optimizer | paged_adamw_8bit |
| LR Scheduler | Cosine |
| Gradient Checkpointing | Enabled |

## 🚀 How to Run
1. Open the notebook in Google Colab
2. Select T4 GPU runtime (Runtime → Change runtime type → T4 GPU)
3. Run all cells in order

## 📦 Requirements
- Google Colab (Free T4 GPU)
- HuggingFace Account + Token
- trl==0.9.6
- transformers==4.42.0
- peft==0.11.1
- accelerate==0.31.0
- bitsandbytes

## 📁 Project Structure
```
├── README.md
├── .gitignore
└── FineTuneLlama2.ipynb
```

## 🔗 References
- [Llama-2 Model](https://huggingface.co/meta-llama/Llama-2-7b-chat-hf)
- [Guanaco Dataset](https://huggingface.co/datasets/mlabonne/guanaco-llama2-1k)
- [QLoRA Paper](https://arxiv.org/abs/2305.14314)
- [PEFT Library](https://github.com/huggingface/peft)

## 👤 Author
**me-nabi** 
