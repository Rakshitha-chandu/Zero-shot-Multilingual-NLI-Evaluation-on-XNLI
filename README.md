# Zero-shot Multilingual NLI Evaluation on XNLI

## Overview
This project presents a controlled multilingual evaluation of Natural Language Inference (NLI) models across English and Indic languages. We study the zero-shot cross-lingual performance of multilingual pretrained models on the XNLI benchmark, with a focus on understanding cross-language performance gaps and their implications for responsible and equitable NLP.

The goal of this work is not to achieve state-of-the-art performance, but to analyze how multilingual models behave across languages in a standardized evaluation setting.

---

## Motivation
Multilingual NLP models are increasingly deployed across languages with diverse linguistic, cultural, and resource characteristics. While these models promise broad language coverage, their actual performance across languages is often uneven and poorly understood.

This project aims to:
- Evaluate multilingual models in a controlled benchmark setting
- Compare performance across languages rather than across tasks
- Highlight limitations of zero-shot cross-lingual transfer
- Frame findings from a responsible AI and fairness perspective

---

## Dataset
- **XNLI (Cross-lingual Natural Language Inference)**
- Task: 3-class classification  
  - entailment  
  - neutral  
  - contradiction
- Languages evaluated:
  - English (`en`)
  - Hindi (`hi`)
  - Urdu (`ur`)

The evaluation uses the validation split of XNLI. Each language is evaluated separately to enable controlled cross-lingual comparison.

---

## Models Evaluated

### 1. mBERT (Baseline)
- Model: `bert-base-multilingual-cased`
- Setting: Zero-shot (no fine-tuning on XNLI)
- Purpose: Establish a weak multilingual baseline

### 2. XLM-R
- Model: `joeddav/xlm-roberta-large-xnli`
- Fine-tuned on XNLI
- Evaluated in a zero-shot multilingual inference setting

---

## Experimental Setup
- Sentence-pair tokenization of premise and hypothesis
- Maximum sequence length: 128
- No additional fine-tuning performed
- Evaluation metric: Accuracy
- Evaluation conducted separately for each language

---

## Results

| Language | mBERT Accuracy | XLM-R Accuracy |
|--------|----------------|----------------|
| English | ~0.33 | ~0.33 |
| Hindi   | ~0.33 | ~0.34 |
| Urdu    | ~0.33 | ~0.33 |

---

## Key Observations
- Both models exhibit near-chance accuracy (~33%) across all evaluated languages.
- This indicates the limitations of naive zero-shot multilingual transfer for NLI.
- Differences across languages are small, suggesting that uniformly poor performance can mask deeper inequities unless carefully analyzed.
- Results highlight the sensitivity of multilingual NLI to preprocessing and task-specific calibration.

---

## Responsible AI Perspective
Uniformly low performance across languages can be misleading if interpreted as fairness. Without careful multilingual evaluation, deployment of such models may obscure real-world disparities in language coverage and cultural representation.

This study emphasizes the importance of transparent benchmarking and language-aware evaluation when assessing multilingual NLP systems, particularly in Global South contexts.

---

## Limitations
- Zero-shot evaluation only; no task-specific fine-tuning
- Limited to languages supported by XNLI
- Focused on accuracy without deeper linguistic error categorization

---

## Future Work
- Fine-tuning models on multilingual NLI data
- Evaluation on Indic-specific benchmarks (e.g., IndicGLUE)
- Analysis of error patterns across scripts and linguistic families
- Evaluation using culturally grounded datasets

---

## Repository Structure
```
├── xnli_multilingual_evaluation.ipynb # Main experiment notebook //
├── results/ # Tables and plots
├── report/ # Short research-style PDF summary
├── README.md
```


---

## Notes
This project is intended as a research-oriented exploration of multilingual evaluation rather than a production-ready system. All results are reported honestly and without performance tuning.



