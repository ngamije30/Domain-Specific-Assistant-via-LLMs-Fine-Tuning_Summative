# Domain-Specific Assistant via LLM Fine-Tuning (Healthcare)

Open In Colab: https://colab.research.google.com/drive/1Qo9MyNfSwcicVvTTGlEEBATSfnKEgcBP?usp=sharing
Demo video: https://drive.google.com/file/d/1CH1EVSMVSTexaxSjEf0zdgesqgn4JD45/view?usp=sharing
## Overview

This project builds a healthcare Q and A assistant by fine-tuning TinyLlama-1.1B-Chat on medical flashcard data. The goal is to produce concise, domain-relevant answers and demonstrate a complete end-to-end pipeline: data preparation, LoRA fine-tuning, evaluation, and Gradio deployment.

## Domain and Problem

- Domain: Healthcare (medical question answering)
- Problem: General LLMs often provide vague or unsafe answers in medical topics
- Solution: Fine-tune a modern open LLM with domain-specific Q and A pairs and validate improvements

## Model and Dataset

- Base model: TinyLlama/TinyLlama-1.1B-Chat-v1.0
- Dataset: medalpaca/medical_meadow_medical_flashcards
- Dataset size: 10,178 samples (full dataset), 2,000 used for training, 200 for validation
- Task type: Generative QA with instruction-response format

## Methodology (Notebook Summary)

1. Environment setup and dependency installation
2. Dataset loading and exploration
3. Prompt template creation
4. Tokenization and formatting (512 max token length)
5. LoRA fine-tuning with 4-bit quantization on GPU
6. Hyperparameter experiments (3 configurations)
7. Evaluation with BLEU, ROUGE, and perplexity
8. Qualitative testing and base vs fine-tuned comparison
9. Gradio deployment for interactive chat

## Hyperparameter Experiments

| Experiment | Learning Rate | Epochs | Batch Size | Grad Accum | Warmup Steps |
|-----------|---------------|--------|------------|------------|--------------|
| Baseline  | 2e-4          | 1      | 2          | 4          | 100          |
| Lower LR  | 1e-4          | 2      | 2          | 4          | 100          |
| Optimized | 5e-5          | 2      | 4          | 2          | 50           |

## Evaluation Metrics

- BLEU (sacrebleu)
- ROUGE-1, ROUGE-2, ROUGE-L
- Perplexity (exp of eval loss)
- Qualitative examples with medical questions
- Base vs fine-tuned comparison

## How to Run (Colab)

1. Open the notebook with the Colab badge
2. Set runtime to GPU (T4 recommended)
3. Run all cells in order (Runtime > Run all)
4. The Gradio interface will show a public URL

## How to Deploy on Gradio (Colab)

1. Run the Gradio install cell in the notebook
2. Run the chat function cell (speed or ultra-fast variant)
3. Run the Gradio launch cell
4. A public link appears in the output for sharing

## Local Setup (Optional)

```bash
pip install datasets transformers accelerate peft bitsandbytes
pip install evaluate rouge-score sacrebleu gradio torch
```

Note: On Windows, bitsandbytes 4-bit quantization may not be supported. The notebook falls back to full precision if needed.

## Repository Contents

- Healthcare_Assistant_Fine_Tuning (1).ipynb: full pipeline notebook
- README.md: project overview and usage
- REPORT.md: full report content to convert to PDF

## Demo Video

- Link: ADD_YOUR_DEMO_VIDEO_URL
- Length: 7 to 10 minutes

## Authors

- Name: NGAMIJE RUHUMULIZA Davy
- Course: Domain-Specific Assistant via LLM Fine-Tuning
- Date: February 2026

## Disclaimer

This is an educational project and is not medical advice. Always consult a qualified professional.
