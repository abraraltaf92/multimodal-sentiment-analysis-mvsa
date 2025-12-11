# Multimodal Sentiment Analysis on the MVSA Dataset

---

## 📘 Project Overview
This project performs **sentiment analysis** on social media posts using **multimodal learning** — combining both **images and text**.  
The dataset used is **MVSA-Multiple**, which provides tweets paired with images and annotated sentiment labels.

We implement and compare three models:
1. **Text-Only Model (BERT)**
2. **Image-Only Model (ResNet18)**
3. **Multimodal Fusion Model (BERT + ResNet18)**

---

## 🎯 Problem Statement
Single-modality sentiment models (text-only or image-only) often fail to capture the full meaning of a social media post.  
Many posts rely on **sarcasm, memes, visual emotion cues**, or **ambiguous text**, making unimodal learning unreliable.

**Goal:** Build a multimodal deep-learning system that integrates both textual context and visual emotion cues to improve sentiment classification performance across:
- Positive  
- Neutral  
- Negative  

---

## 📂 Dataset: MVSA-Multiple
- **Samples:** 19,600 social media posts  
- Each sample contains:
  - An image
  - A text caption
  - Labels from 3 annotators (text + image sentiments)

### ✔ Label Cleaning
You apply **majority voting** to produce a final unified sentiment label.

Label distribution:
- **Positive:** 9367  
- **Neutral:** 9108  
- **Negative:** 1125  

### 🔗 Dataset Link  
[https://mmajlab.org/dataset/mvsa/](https://mcrlab.net/research/mvsa-sentiment-analysis-on-multi-view-social-data/)

---

## 🧠 Model Architectures

### 1️⃣ Text-Only Model (BERT)
```
[Text] → [Tokenizer] → [BERT Encoder] → [CLS] → [Classifier] → Sentiment
```

### 2️⃣ Image-Only Model (ResNet18)
```
[Image] → [ResNet18 Backbone] → [Feature Vector] → [Classifier] → Sentiment
```

### 3️⃣ Multimodal Fusion Model (BERT + ResNet18)
```
                ┌───────── BERT Embedding ─────────┐
[Text Input] ───┤                                  ├──► Concat ─► Dense ─► Output
                └──────── ResNet18 Embedding ──────┘
[Image Input] ──────────────────────────────────────┘
```

---

## 📊 Results Summary

| Model | Test Accuracy |
|-------|--------------|
| **Text-Only (BERT)** | **95.05%** |
| **Image-Only (ResNet18)** | **91.27%** |
| **Multimodal (BERT + ResNet18)** | **92.26%** |

---

## 🚀 How to Run

### 1. Clone repo
```bash
git clone https://github.com/<your-username>/multimodal-sentiment-analysis-mvsa
cd multimodal-sentiment-analysis-mvsa
```

### 2. Prepare dataset structure
```
/data/
    2499.jpg
    2499.txt
labels_clean.csv
```

### 3. Train models
```bash
# Train text-only model
python train_text.py

# Train image-only model
python train_image.py

# Train multimodal fusion model
python train_multimodal.py
```

---

## 📝 Citation
If you use the MVSA dataset, please cite:

```
@inproceedings{MVSA,
  author    = {Teng Niu and Shiai Zhu and Lei Pang and Abdulmotaleb El{-}Saddik},
  title     = {Sentiment Analysis on Multi-View Social Data},
  booktitle = {MultiMedia Modeling},
  pages     = {15--27},
  year      = {2016},
}
```

---
