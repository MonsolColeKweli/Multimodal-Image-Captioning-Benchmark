# Multimodal Image Captioning Benchmark  
**CSE 434 – Generative AI Final Project**

## Overview

This project presents a comparative evaluation of proprietary and open-source multimodal vision–language models on the task of image captioning.

The central research question:

> How does a proprietary multimodal model compare to an open-source vision–language model in generating semantically accurate image captions when evaluated on the same dataset?

Models evaluated:

- Gemini 2.5 Flash-Lite (Proprietary, API-based)
- Qwen3-VL-8B-Abliterated-Caption-it (Open-source, local inference via Hugging Face)

Both models were evaluated on a controlled subset of the Flickr8k dataset using standardized prompts and automated semantic evaluation metrics.

---

## Purpose

Multimodal large language models (MLLMs) combine visual perception with language generation. While proprietary systems often demonstrate strong performance, open-source models offer transparency and reproducibility.

This project aimed to:

- Benchmark caption quality using semantic similarity metrics  
- Compare multimodal grounding across architectures  
- Analyze trade-offs between API-based inference and local deployment  
- Explore evaluation strategies beyond simple n-gram overlap  

---

## Dataset

- Dataset: Flickr8k  
- 8,000 total images (controlled subset used for evaluation)  
- 5 human-authored reference captions per image  
- Identical image samples selected using a fixed random seed  

Ground-truth captions were shared across both models to ensure fair comparison.

---

## Technical Architecture

### Environment
- Python  
- Google Colab  
- Hugging Face Transformers  

### Caption Generation Pipeline

1. Load image from dataset  
2. Apply standardized neutral captioning prompt  
3. Generate one caption per model  
4. Store outputs for evaluation  
5. Compute semantic similarity metrics  

The open-source model was run locally via Hugging Face, allowing explicit control over preprocessing and inference configuration. The proprietary model was accessed via API, introducing rate limits and latency constraints.

---

## Evaluation Strategy

While BLEU was initially considered, the evaluation shifted toward metrics better aligned with semantic similarity.

Final metrics used:

- ROUGE-L (Longest Common Subsequence overlap)  
- BERTScore (Precision, Recall, F1 using contextual embeddings)  

An attempt was made to integrate METEOR, but implementation constraints prevented full incorporation into final analysis.

---

## Results

### Quantitative Findings

- Gemini 2.5 Flash-Lite achieved higher average ROUGE-L and BERTScore values  
- BERTScore F1 indicated stronger semantic alignment in complex scenes  
- Qwen3-VL-8B produced coherent captions but showed greater variance in action-heavy scenarios  

### Qualitative Observations

- People-centric scenes: Proprietary model captured relational dynamics more consistently  
- Object-focused scenes: Both models performed comparably  
- Complex interactions: Open-source model occasionally generalized or omitted secondary details  

---

## Key Learnings

- Multimodal transformer architecture design  
- Vision encoder + language model integration  
- Practical benchmarking methodology  
- Semantic evaluation theory beyond lexical overlap  
- Engineering trade-offs between proprietary APIs and open-source deployment  
- Managing runtime stability and memory constraints in Google Colab  

This project reinforced that model selection involves not only performance, but also accessibility, reproducibility, and engineering feasibility.

---

## Limitations

- Reduced dataset size due to API rate limits and runtime constraints  
- No formal category labeling for deeper statistical analysis  
- Proprietary model architecture details unavailable  

---

## Future Work

- Human evaluation alongside automatic metrics  
- Category-based caption segmentation  
- Prompt variation experiments  
- Cost-performance benchmarking  

---

## Technologies Used

- Python  
- Google Colab  
- Hugging Face Transformers  
- ROUGE  
- BERTScore  
- Multimodal Transformer Models  
- API-based Model Inference  
