# Rijul_BTP-Named_Entity_Recoginition

# Cross-Lingual NER for Indian Languages

**BTP**  
**Name:** Rijul Singla (22075070)  
**Department:** Computer Science and Engineering (B.Tech)  
**Note:** To properly see the formatted code download the code files and open through jupyter notebook or collab.  
[Presentation Link](https://drive.google.com/file/d/1Ke0r4xrm961EFudiAYn-XPXaSGzCYmbq/view?usp=sharing)

***

## Overview

### **Task 1: NER for Low-Resource Languages — Bhojpuri, Magahi, Maithili**

Fine-tuning the **IndicNER** model for three low-resource Indo-Aryan languages — **Bhojpuri, Magahi, and Maithili** — using multiple datasets:

- **Naamapadam dataset**  
- **BMM NER dataset** 
- **HiNER dataset**

Models were fine-tuned and evaluated using Precision, Recall, F1, and Accuracy.

A final score table for each language is provided below.

### **Task 2: Cross-Lingual NER for 7 Indic Languages**
Generating high-quality parallel NER-annotated datasets for Assamese, Bengali, Gujarati, Malayalam, Marathi, Tamil, and Telugu through cross-lingual projection from Hindi, followed by multilingual model fine-tuning achieving **aggregate F1: 0.789** across all languages.

[Generated Dataset](https://drive.google.com/drive/folders/1V7EETVly_vDpqS0uPqGAsDlv5VMPtwcb?usp=sharing)

***

## Project Structure

```
Rijul_BTP-Named_Entity_Recoginition/
│
├── Naamapadam_train_BMM.ipynb
│   └── Fine-tuning pipeline for Bhojpuri (used as example language), can be replaced with Magahi and Maithili
|
├── DatasetGeneration_with_NER_Tags.ipynb
│   └── Cross-lingual NER dataset generation pipeline
│       - Word alignment (SimAlign/Awesome-align)
│       - Tag projection to target languages
│       - 3-method evaluation (entity matching, tag consistency, token accuracy)
│
├── Finetuning_of_Model.ipynb
│   └── Fine-tuning on generated NER dataset
│       - Training on 7 Indic languages
│       - Per-language and aggregate evaluation
│
├── Evaluation_of_finetuned_model_on_our_Dataset.ipynb
│
└── README.md
    └── This comprehensive documentation
```

# Part 1: NER for Bhojpuri, Magahi, Maithili 

### **Problem Statement**

Develop Named Entity Recognition models for three low-resource Indic languages:

- **Bhojpuri (bho)**  
- **Magahi (mag)**  
- **Maithili (mai)**  

using transformer-based models, and multilingual datasets.

### **Methodology**

1. **Base Model**: ai4bharat/IndicNER  
2. **Datasets Used**:  
   - Naamapadam  
   - BMM NER dataset  
   - HiNER dataset  
3. **Fine-Tuning Setup**  
   - Token classification  
   - LR = 2e-5  
   - Epochs = 10  
   - Batch size = 4–8  
4. **Evaluation Metrics**: Precision, Recall, F1, Accuracy  

---

## **Final Evaluation Results**

### **Bhojpuri (bho)**  

| Language | Precision | Recall | F1 | Accuracy |
|----------|-----------|--------|----|----------|
| Bhojpuri | **0.776** | **0.78** | **0.778** | **0.952** |

---

### **Magahi (mag)**  

| Language | Precision | Recall | F1 | Accuracy |
|----------|-----------|--------|----|----------|
| Magahi | **0.735** | **0.705** | **0.738** | **0.949** |

---

### **Maithili (mai)**  

| Language | Precision | Recall | F1 | Accuracy |
|----------|-----------|--------|----|----------|
| Maithili | **0.755** | **0.725** | **0.76** | **0.949** |

---

## Entity-wise NER Results

| Language  | Entity Type | Precision | Recall | F1 Score |
|-----------|-------------|-----------|--------|----------|
| Bhojpuri  | PER         | 0.785  | 0.8   | 0.792 |
| Bhojpuri  | LOC         | 0.685  | 0.66  | 0.67  |
| Bhojpuri  | ORG         | 0.43   | 0.27  | 0.32  |
| Magahi    | PER         | 0.745  | 0.76  | 0.752 |
| Magahi    | LOC         | 0.645  | 0.63  | 0.637 |
| Magahi    | ORG         | 0.395  | 0.255 | 0.3   |
| Maithili  | PER         | 0.76   | 0.785 | 0.77  |
| Maithili  | LOC         | 0.65   | 0.65  | 0.65  |
| Maithili  | ORG         | 0.39   | 0.26  | 0.3   |


***

## Part 2: Cross-Lingual NER Dataset Generation

### Problem Statement

Generate high-quality NER-annotated parallel corpora for **7 low-resource Indic languages** using Hindi (Samanantar) as the pivot language.

**Target Languages**: Assamese, Bengali, Gujarati, Malayalam, Marathi, Tamil, Telugu  
**Labels**: B-PER, I-PER, B-LOC, I-LOC, B-ORG, I-ORG, O

***

### Methodology Pipeline

1. **Word Alignment**: SimAlign/Awesome-align for token-level alignment
2. **Tag Projection**: Transfer tags via word alignments
3. **Quality Validation**: 3-method evaluation

***

### Evaluation Results

#### **Method 1: Entity Matching Accuracy**

| Language | Entity Ratio
|----------|--------------|
| Assamese | 0.838 
| Bengali | 0.682 
| Gujarati | 0.829 
| Malayalam | 0.610 
| Marathi | 0.733 
| Tamil | 0.846 
| Telugu | 0.758 
| **Average** | **0.757** |

***

#### **Method 2: Tag Type Consistency**

| Language | Similarity Score 
|----------|------------------|
| Assamese | 0.981 
| Bengali | 0.916 
| Gujarati | 0.947 
| Malayalam | 0.910 
| Marathi | 0.884 
| Tamil | 0.874 
| Telugu | 0.900 
| **Average** | **0.916** |

***

#### **Method 3: Token-Level Alignment Accuracy**

| Language | Accuracy | Precision | Recall | F1 Score |
|----------|----------|-----------|--------|----------|
| Assamese | 83.8% | 0.834 | 0.838 | **0.836** |
| Bengali | 86.8% | 0.750 | 0.830 | **0.820** |
| Gujarati | 76.5% | 0.746 | 0.765 | **0.754** |
| Malayalam | 84.0% | 0.790 | 0.800 | **0.790** |
| Marathi | 85.0% | 0.800 | 0.790 | **0.790** |
| Tamil | 81.6% | 0.834 | 0.816 | **0.816** |
| Telugu | 90.0% | 0.790 | 0.800 | **0.754** |
| **Average** | **87.5%** | **0.792** | **0.806** | **0.820** |


***

## Part 3: Model Fine-tuning and Evaluation

### Model Architecture

**Base Model**: XLM-RoBERTa (xlm-roberta-base)
**Fine-tuning Setup**:
- Task: Token classification
- Training: 10 epochs, learning rate 2e-5-3e-5, batch size 4-8
- Optimization: AdamW with weight decay 0.01

***

### Results: Cross-Lingual NER Model

#### **Per-Language Performance**

| Language | F1 Score | Precision | Recall | Accuracy
|----------|----------|-----------|--------|----------
| **Assamese (as)** | **0.7900** | 0.7704 | 0.8104 | 96.04%
| **Bengali (bn)** | **0.7810** | 0.7610 | 0.8000 | 97.10%
| **Gujarati (gu)** | **0.7538** | 0.8238 | 0.7218 | 97.38% 
| **Malayalam (ml)** | **0.7857** | 0.7389 | 0.8057 | 97.57%
| **Marathi (mr)** | **0.8200** | 0.8450 | 0.8001 | 98.38%
| **Tamil (ta)** | **0.7610** | 0.7557 | 0.7991 | 96.20% 
| **Telugu (te)** | **0.8091** | 0.8377 | 0.7881 | 97.77%

***

#### **Aggregate Performance Across All Languages**

| Metric | Score |
|--------|-------|
| **F1 Score** | **0.7891 (78.91%)** |
| **Precision** | **0.7964** |
| **Recall** | **0.7790** |
| **Accuracy** | **97.97%** |


***

## Part 4: Devanagari Transliteration + Fine-tuning

Converted the entire multilingual NER dataset into the Devanagari script, and then fine-tune the model on the converted dataset.

Goal:

Check whether script normalization (all languages → Devanagari) improves cross-lingual NER performance.

All words from each language were transliterated into Devanagari using indic-transliteration (sanscript).

### Results:  

| Metric        | Score      |
| ------------- | ---------- |
| **Precision** | **0.8001** |
| **Recall**    | **0.7931** |
| **F1 Score**  | **0.7966** |

Conclusion:

Script normalization to Devanagari improved performance, outperforming the original results (0.7891 F1).
***

## Complete Results Summary

### Cross-Lingual NER Dataset Quality

| Method | Score |  
|--------|-------|  
| Entity Matching | 75.7% | 
| Tag Consistency | 91.6% | 
| Token F1 | 82.0% |

***

#### Cross-Lingual NER
| Metric | Score |
|--------|-------|
| **Aggregate F1** | **78.91%** |
| **Accuracy** | **97.97%** |

***

Devanagari Transliteration + Fine-tuning
| Metric        | Score      |
| ------------- | ---------- |
| **F1 Score**  | **0.7966** |
| **Precision** | 0.8001     |
| **Recall**    | 0.7931     |

## License

Academic use only. Datasets derived from publicly available sources.

***

## Author

**Rijul Singla**  
Roll Number: 22075070  
Computer Science & Engineering (B.Tech)  

***
