# Llama3.2-MedQuad-Finetune

## Project Overview
This project focuses on fine-tuning the Llama 3.2 3B model using the MedQuad dataset to optimize the model's ability to answer medical questions accurately. The goal is to enhance the model’s semantic similarity, lexical alignment, and factual correctness while carefully balancing these aspects to avoid compromising accuracy.

## Repository Structure
```
Llama3.2-MedQuad-Finetune/
├── data/                   # Raw and cleaned MedQuad datasets
├── models/                 # Pre-trained, LoRA fine-tuned, and fully fine-tuned models
├── notebooks/              # Jupyter notebooks for data processing and analysis
├── results/                # Evaluation results including BERT, BLEU, and DeepEval scores
├── scripts/                # Python scripts for model training and evaluation
└── README.md               # Project overview and instructions
```

## Key Components
1. **Data:** Contains the cleaned MedQuad dataset (`VerifiedQ_A.xlsx`) used for training and evaluation.
2. **Models:** Includes the pre-trained, LoRA fine-tuned, and fully fine-tuned Llama 3.2 3B models.
3. **Notebooks:** Jupyter notebooks for model fine-tuning, result generation, and comparative analysis.
4. **Results:** Contains the generated answers and evaluation scores (BERT, BLEU, DeepEval).
5. **Scripts:** Python files for data processing, model training, and benchmarking.

## Installation and Setup
1. Clone the repository:
   ```bash
   git clone https://github.com/username/Llama3.2-MedQuad-Finetune.git
   ```
2. Install required packages:
   ```bash
   pip install transformers datasets accelerate peft bitsandbytes torch openpyxl bert_score
   ```
3. Set up the environment:
   ```bash
   export TOKENIZERS_PARALLELISM=false
   ```

## Usage
### Running the Fine-Tuning Script
```bash
python scripts/fine_tune.py --model llama3.2 --dataset data/VerifiedQ_A.xlsx
```

### Generating Answers
```bash
python scripts/generate_answers.py --model fine-tune --input data/VerifiedQ_A.xlsx
```

### Evaluating Results
```bash
python scripts/evaluate.py --input results/generated_answers.xlsx
```

## Evaluation Metrics
- **BERT Score:** Measures semantic similarity between model-generated answers and reference answers.
- **BLEU Score:** Checks lexical similarity, focusing on n-gram overlap.
- **DeepEval Correctness:** Assesses factual accuracy.

## Results
The fine-tuned Llama3.2 model shows substantial improvements in semantic and lexical similarity over the pre-trained model, though maintaining factual accuracy remains a challenge. The comparative analysis suggests that while fine-tuning enhances the model's natural language generation, it requires careful balance to preserve factual consistency.

## Future Work
- Investigate why fine-tuning might reduce factual correctness despite improved fluency.
- Experiment with different prompting strategies and hybrid evaluation methods.

## Contributors
- Fung Chau (Primary Fine-Tuning and Evaluation)
- Bowen (Prompting Method Optimization)

## License
This project is licensed under the MIT License.
