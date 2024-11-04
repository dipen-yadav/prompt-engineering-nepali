# Prompt Engineering for Nepali Named Entity Recognition: A Case Study for Low-Resource Languages

## Abstract
This repository contains the code and resources used in the paper, *Prompt Engineering for Nepali Named Entity Recognition: A Case Study for Low-Resource Languages*. The study evaluates the effectiveness of prompt engineering for Named Entity Recognition (NER) in Nepali, a low-resource language. Using Meta's quantized LLaMA 3.1 70B model, both zero-shot and few-shot prompting strategies were applied. Results highlight the challenges of prompt-based NER in low-resource languages, demonstrating limited performance compared to transformer models trained with larger datasets.

## Project Structure

### 1. **Dataset Preparation**
   - **Dataset**: The Nepali [EBIQUITY](https://github.com/oya163/nepali-ner) NER dataset was used, containing sentences labeled with `B-LOC`, `I-LOC`, `B-ORG`, `I-ORG`, `B-PER`, `I-PER`, and `O`.
   - **Train-Test Split**: 2796 sentences for training and 493 for testing.
   - **Sentence Selection**: An algorithm was used to select sentences with maximum entity diversity for few-shot prompts.

### 2. **Prompting Strategies**
   - **Zero-Shot Prompting**: Only test sentences and basic task instructions are provided to the model.
   - **Few-Shot Prompting**: Example sentences from the training dataset are included to guide the model, selected using a sentence selection strategy prioritizing diversity and completeness.

### 3. **Model**
   - **LLaMA 3.1 70B**: A quantized version of Meta's 70B model was used to reduce memory and computational requirements. Experiments were conducted on a system with four NVIDIA RTX 4090 GPUs.

### 4. **Evaluation**
   - **Metrics**: Precision, Recall, F1-score, and Confusion Matrix were used to evaluate model performance.
   - **Statistical Significance**: The Kruskal-Wallis test was applied to assess performance differences across zero-shot and few-shot configurations.

### 5. **Experiment Flow**
   The experimental pipeline includes:
   - Data preparation and train-test splitting.
   - Prompt construction based on chosen strategy (zero-shot or few-shot).
   - Model inference with response validation and retry logic (up to 3 retries).
   - Alignment checking for correct tagging and word order.
   - Performance evaluation and statistical testing.

## Code Structure

- **Data Preparation**: Scripts to load and preprocess the dataset, including sentence selection.
- **Prompt Engineering**: Templates for zero-shot and few-shot prompts with XML tags for structured output.
- **Model Inference**: Function to generate predictions with retry logic if tagging fails validation.
- **Evaluation**: Computes precision, recall, F1-score, and confusion matrix; includes Kruskal-Wallis test for significance.


