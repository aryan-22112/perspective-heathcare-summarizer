# Perspective-Aware Healthcare Summarization Model

## Overview

This project introduces a novel approach to healthcare summarization that focuses on generating summaries from multiple perspectives. By leveraging advanced language models and custom energy-based loss functions, the model can generate context-aware summaries that capture different viewpoints in medical information.

## Dataset Description

This project leverages the **PUMA (Perspective sUMmarization dAtaset)** — a perspective-aware summary-annotated corpus built within the healthcare domain.

- 🧵 **3,167 Community Question-Answering (CQA) threads**
- 💬 **~10,000 answers** across these threads
- 🗂 **Each answer is manually annotated with five possible perspectives:**
  - Cause
  - Suggestion
  - Experience
  - Question
  - Information
- ✍️ **Each thread includes at most five manually written summaries**, one per perspective, offering a rich multi-view summarization ground truth.

**Note:** The PUMA dataset was provided for research purposes and was not created by us. All annotations and summaries were originally developed by the dataset authors as part of their published work.

## Key Features

- 🏥 **Perspective-aware summarization**
- 🤖 **Uses BART with LoRA for efficient fine-tuning**
- 📊 **Custom energy-based loss function**
- **Supports multiple perspectives.

## Model Architecture

The model consists of two main components:

- **Perspective Classifier**: A RoBERTa-based classifier that identifies the perspective of medical text.
- **Summarization Model**: A BART model with LoRA, trained to generate perspective-specific summaries.

### Perspective Energy Calculation

The model uses a novel energy calculation method combining three key components:

- **Ep (Perspective Energy)**: Probability of the summary matching the target perspective
- **Ea (Anchor Energy)**: Similarity of summary start to perspective-specific anchor text
- **Et (Tone Energy)**: Cosine similarity between summary and perspective-specific tone keywords

## Evaluation Results

We evaluated the model using several standard NLP metrics:

### ROUGE Scores
- **ROUGE-1**: 28.31%
- **ROUGE-2**: 11.61%
- **ROUGE-L**: 17.92%
- **ROUGE-Lsum**: 17.92%

### Other Metrics
- **METEOR**: 34.46%
- **BLEU**: 5.22%

### BERTScore
- **Precision**: 81.62%
- **Recall**: 87.87%
- **F1 Score**: 84.61%

#### Metric Interpretation
- **ROUGE Scores**: Measure the overlap between generated and reference summaries.
- **METEOR**: Considers synonyms and paraphrases, providing a more nuanced evaluation.
- **BLEU**: Measures exact n-gram matches (lower score typical for abstractive summarization).
- **BERTScore**: Uses contextual embeddings to assess semantic similarity.

### Key Observations
- High BERTScore indicates strong semantic alignment with reference summaries.
- Moderate ROUGE scores reflect the challenge of abstractive summarization in medical domains.
- METEOR score suggests good semantic preservation.
