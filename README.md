# Llama3.2-MedQuad-Finetune

## Project Overview
This project aims to fine-tune the Llama3.2 3B model on the MedQuad dataset, comparing the performance of the pre-trained model, LoRA adaptation, and full fine-tuning. The primary goal is to evaluate and compare the performance of these models using medical question-answer pairs from the MedQuad dataset.

## Repository Structure
```
Llama3.2-MedQuad-Finetune/
│
├── fine-tune/
│   ├── bert_score_results.csv
│   ├── bleu_score_results.csv
│   ├── final_eval_results.xlsx
│   ├── generated_answers.xlsx
│   └── testllama32_BertDeepBLEU_FineT.ipynb
│
├── LoRA/
│   ├── bert_score_results.csv
│   ├── bleu_score_results.csv
│   ├── final_eval_results.xlsx
│   └── generated_answers.xlsx
│
├── pre-trained/
│   ├── bert_score_results.csv
│   ├── bleu_score_results.csv
│   ├── final_eval_results.xlsx
│   └── generated_answers.xlsx
│
├── model_compare.ipynb
└── VerifiedQ_A.xlsx
```

## Data Description
The dataset VerifiedQ_A.xlsx contains cleaned medical question-answer pairs from the MedQuad dataset. This file includes reference questions and their corresponding correct answers, which are used for model fine-tuning and evaluation.

## Evaluation Metrics
- **BERT Score:** Measures semantic similarity between model-generated answers and reference answers.
- **BLEU Score:** Checks lexical similarity, focusing on n-gram overlap.
- **DeepEval Correctness:** Assesses factual accuracy.

## Project Steps

1. **Data Preparation**:

  - Cleaned the MedQuad dataset to create VerifiedQ_A.xlsx.



2. Model Answer Generation:

  - Used the pre-trained Llama3.2 3B model to generate answers based on reference questions.

  - Stored results in generated_answers.xlsx.



3. Benchmarking Metrics Calculation:

- Calculated BERT score, BLEU score, and DeepEval correctness using the generated answers.

- Stored results in respective CSV/XLSX files.



4. Comparative Analysis:

  - Use `model_compare.ipynb` to compare the performance of three model configurations (pre-trained, LoRA, fine-tune).

  - Analyzed BERT F1, BLEU, and DeepEval Correctness scores.

  - Provided visualizations and interpretations.



## Key Findings
The fine-tuned Llama3.2 model shows substantial improvements in semantic and lexical similarity over the pre-trained model, though maintaining factual accuracy remains a challenge. The comparative analysis suggests that while fine-tuning enhances the model's natural language generation, it requires careful balance to preserve factual consistency.

1. Fine-tune Model:

  - Significant improvement in BERT F1 and BLEU scores compared to both pre-trained and LoRA.

  - Moderate drop in factual correctness compared to pre-trained.



2. LoRA Model:

  - Modest gain in BERT F1, but notable decrease in DeepEval correctness.



3. Pre-trained Model:

  - Consistently high factual accuracy but lacks semantic and lexical alignment improvements.

## Results
The fine-tuned Llama3.2 model shows substantial improvements in semantic and lexical similarity over the pre-trained model, though maintaining factual accuracy remains a challenge. The comparative analysis suggests that while fine-tuning enhances the model's natural language generation, it requires careful balance to preserve factual consistency.

## Usage:
- Run `testllama32_BertDeepBLEU_FineT.ipynb` to generate model answers and calculate benchmarking scores.
- Run `model_compare.ipynb` to compare model performances.

## Dependencies
`transformers`, `datasets`, `torch`, `accelerate`, `peft`, `bitsandbytes`, `openpyxl`, `bert_score`

## Future Work
- Investigate why fine-tuning might reduce factual correctness despite improved fluency.
- Experiment with different prompting strategies and hybrid evaluation methods.




