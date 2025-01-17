# LLM Fine-Tuning Project

This repository contains scripts and resources for fine-tuning the [Falcon-7B](https://huggingface.co/tiiuae/falcon-7b) model for dialogue generation tasks using the Persona-Chat dataset. The project includes custom preprocessing, training, and evaluation pipelines with BLEU and ROUGE-L metrics.

## Project Highlights

- **Choice of LLM:** Falcon-7B
- **Fine-Tuning Method:** LoRA with 4-bit precision
- **Justifications:** Explained below
- **Link to Model Weights:** [Hugging Face Repository](https://huggingface.co/HarshBhati/Falcon-7b-FineTuned-weights/tree/main)

---

## 1. **Choice of LLM**
We chose **Falcon-7B** as our base language model because:
- It is a high-performing, open-source causal language model designed for text generation tasks.
- It is lightweight (7 billion parameters) compared to larger models, making it computationally efficient for fine-tuning.
- It supports advanced quantization techniques such as 4-bit precision, reducing memory requirements without significant performance loss.

---

## 2. **Choice of Fine-Tuning Method**
### **Low-Rank Adaptation (LoRA)**
- LoRA is a parameter-efficient fine-tuning technique that modifies only a subset of model parameters while keeping the base model frozen.
- In this project:
  - **Rank (`r`)**: 16
  - **Alpha**: 32
  - **Dropout**: 0.05
- LoRA allows efficient training on consumer-grade GPUs (e.g., NVIDIA RTX 3090) while maintaining strong downstream task performance.

### **Quantization with 4-bit Precision**
- Quantization reduces the memory footprint and computational overhead.
- We use **NF4 quantization**, which is designed to maximize performance in transformer-based models.

---

## 3. **Justifications**
1. **Efficiency:**
   - The combination of LoRA and 4-bit quantization ensures the fine-tuning process is both memory- and compute-efficient.
   - This enables fine-tuning even on limited hardware resources without sacrificing model quality.

2. **Reproducibility:**
   - The scripts in this repository are designed to be modular and reusable for similar text generation tasks.

3. **Metrics for Evaluation:**
   - BLEU and ROUGE-L are industry-standard metrics for evaluating text generation tasks.
   - These metrics provide insight into the quality, fluency, and informativeness of the generated responses.

---

## 4. **Objective Function**
The training objective is **causal language modeling**, where the model predicts the next token in a sequence based on the previous context. 

Below is a visual representation of the cross-entropy loss used during training:

![Objective Function](https://github.com/HBX814/Falcon-7b-FineTuned/blob/main/Images/Image1.png)

---

## 5. **Model Weights**
The fine-tuned model weights and tokenizer are available on Hugging Face:
- [Fine-Tuned Falcon-7B](https://huggingface.co/HarshBhati/Falcon-7b-FineTuned-weights/tree/main)

---

## Getting Started
### **Install Dependencies**
Install the required libraries using:
```bash
pip install -r requirements.txt
