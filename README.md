# Exploring Model Behaviors with Google’s Language Interpretability Tool (LIT)

## Project Overview
This project evaluates the use of Google's **Language Interpretability Tool (LIT)** for understanding and analyzing Natural Language Processing (NLP) models. The focus is on leveraging LIT to gain insights into model behaviors, identify weaknesses, and enhance explainability, particularly in sentiment analysis tasks. Various NLP models, including SST-Tiny, DistilBERT, and RoBERTa, were analyzed using the SST-2 dataset from the Stanford Sentiment Treebank.

---

## Table of Contents

1. [Setup](#setup)
2. [Dataset Exploration](#dataset-exploration)
   - [Data Distribution](#data-distribution)
   - [Embeddings](#embeddings)
   - [Confusion Matrix](#confusion-matrix)
3. [Model Performance Analysis](#model-performance-analysis)
   - [Choice of Models](#choice-of-models)
   - [Positive Sentiment Subset](#positive-sentiment-subset)
   - [Negative Sentiment Subset](#negative-sentiment-subset)
   - [Length-Based Subset](#length-based-subset)
4. [Saliency & Attribution Analysis](#saliency--attribution-analysis)
   - [Attention in Longer Sentences](#attention-in-longer-sentences)
   - [Attention in Shorter Sentences](#attention-in-shorter-sentences)
   - [Model Challenges](#model-challenges)
5. [Counterfactual Analysis](#counterfactual-analysis)
   - [Effect of Punctuation](#effect-of-punctuation)
   - [Effect of Negative Words](#effect-of-negative-words)
6. [Insights and Recommendations](#insights-and-recommendations)
7. [Strengths and Limitations](#strengths-and-limitations)
8. [Future Improvements](#future-improvements)

---

## Setup

The project leverages **Google Colab** for execution and analysis:
- Install LIT using `pip install lit_nlp`.
- Ensure Python compatibility and load the required dataset and models from the Hugging Face library.

---

## Dataset Exploration

### **Dataset Overview**
- **Name:** SST-2 (Stanford Sentiment Treebank 2)
- **Type:** Binary Classification (Positive/Negative)
- **Source:** Rotten Tomatoes Movie Reviews
- **Size:** 
  - Train: 67,349 samples
  - Validation: 872 samples
  - Test: 1,821 samples

### **Data Distribution**
The dataset exhibits a balanced representation of positive and negative sentiment labels, ensuring reliable model evaluations.

### **Embeddings Visualization**
Using **UMAP** for dimensionality reduction, sentence embeddings reveal distinct clusters for positive and negative sentiments, showcasing the models' ability to encode sentiment-related features.

### **Confusion Matrix**
The SST-Tiny model misclassified ~9% of the validation samples due to its limited architecture compared to larger models like DistilBERT and RoBERTa.

---

## Model Performance Analysis

### **Models Used**
1. SST-Tiny: 6M parameters
2. DistilBERT: 66M parameters
3. RoBERTa: 125M parameters

### **Performance Evaluation**
The analysis was conducted on:
- Positive sentiment subsets
- Negative sentiment subsets
- Length-based subsets

#### Key Observations:
- **RoBERTa** consistently outperformed smaller models.
- **DistilBERT** exhibited better alignment with human sentiment understanding in specific cases.
- SST-Tiny struggled with complex linguistic patterns due to its compact architecture.

---

## Saliency & Attribution Analysis

### **Key Findings**
- Grad L2 Norm and Integrated Gradients provided insights into token importance.
- RoBERTa occasionally misinterpreted context, overemphasizing punctuation or specific words.
- DistilBERT demonstrated a balanced attention mechanism, handling nuanced contexts like sarcasm or irony more effectively.

---

## Counterfactual Analysis

### **Highlights**
1. **Effect of Punctuation:**
   Removing punctuation like `?` corrected misclassifications, revealing a model's sensitivity to non-semantic features.

2. **Effect of Negative Words:**
   Reducing the abundance of negative descriptors in sentences improved sentiment predictions, indicating biases toward prominent lexical cues.

---

## Insights and Recommendations

- Larger models like RoBERTa generally perform better but may still struggle with linguistic subtleties, such as sarcasm or irony.
- Models benefit from balanced datasets and attention mechanisms that prioritize context over isolated tokens.

---

## Strengths and Limitations

### **Strengths of LIT**
- User-friendly interface for visualizations.
- Support for multiple attribution methods.
- Effective for diagnosing model behaviors and weaknesses.

### **Limitations**
- Attribution methods may provide varying interpretations.
- Computational constraints for large models during runtime.

---

## Future Improvements

- **Hybrid Attribution Techniques:** Combine gradient-based and context-aware methods for comprehensive model interpretability.
- **Semantically Charged Counterfactuals:** Leverage counterfactual generators to create nuanced subsets for training.
- **Diverse Datasets:** Incorporate examples with sarcasm, irony, and complex sentiments to improve generalization.

---

Feel free to modify or expand this README to fit additional project-specific details!
