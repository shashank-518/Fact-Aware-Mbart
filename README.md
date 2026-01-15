# Fact-Aware Cross-Lingual News Summarization using mBART

This project explores the problem of **factual inconsistency in cross-lingual news summarization** and proposes a **fact-aware training framework** built on top of mBART to address it.

The primary goal is to move beyond surface-level evaluation metrics (such as ROUGE) and explicitly analyze and improve **factual correctness**, with a focus on:
- Named entity preservation
- Numerical consistency
- Semantic faithfulness across languages

---

## 🔍 What is the Problem?

Cross-lingual summarization aims to generate summaries in one language (e.g., English) from news articles written in another language (e.g., Hindi).

While modern transformer-based models generate fluent summaries and achieve high ROUGE scores, they often:
- Drop important named entities (people, locations, organizations)
- Distort numerical information (dates, quantities, percentages)
- Produce summaries that look correct but are **factually unreliable**

This issue becomes more severe in **cross-lingual settings**, where translation noise and semantic drift amplify factual errors.

---

## 💡 What Does This Project Propose?

Instead of modifying model architecture or decoding strategies, this project introduces a **FACT-AWARE training approach**.

The key idea is simple:

> If we explicitly penalize factual errors during training, the model will learn to preserve facts better.

### Core Contributions:
- A **fact-aware loss formulation** added on top of standard cross-entropy loss
- Explicit supervision for:
  - Entity recall
  - Number preservation
- Empirical comparison between:
  - Direct mBART (baseline)
  - FACT-AWARE mBART (proposed model)

---

## 🧪 Experiments Conducted

All experiments are conducted on the **NewsSumm dataset** in a **Hindi → English** cross-lingual setting.

Important characteristics of the setup:
- Only **100 articles** are used (low-resource setting)
- No multi-document training
- Same architecture for baseline and proposed model
- Only the **training objective differs**

This makes the comparison clean and controlled.

---

## 📊 What Do the Results Show?

### 1️⃣ Baseline Model Comparison

Initial experiments compare PEGASUS, BART, and mT5 in a cross-lingual setting.

Key observations:
- BART achieves the highest ROUGE scores
- PEGASUS performs poorly in cross-lingual transfer
- mT5, being embedding-oriented, struggles with abstractive summarization
- **All models show extremely low entity recall and number preservation**

This motivates deeper investigation beyond ROUGE.

---

### 2️⃣ FACT-AWARE mBART vs Direct mBART

The proposed FACT-AWARE mBART model is compared against a direct mBART baseline.

Across multiple evaluation metrics:
- ROUGE-1, ROUGE-2, and ROUGE-L improve consistently
- BERTScore-F1 shows improved semantic similarity
- **Entity recall improves noticeably**
- Number preservation remains low for both models

📌 Key insight:
> Improving factual supervision does not harm fluency or abstraction — it improves overall reliability.

---

## 📈 Understanding the Visual Results

The screenshots and graphs included in this project illustrate:

- ROUGE-L improvements across models
- Entity recall differences between baseline and fact-aware training
- BERTScore-F1 semantic alignment
- Number preservation behavior and its limitations

Each visualization corresponds to quantitative outputs generated during evaluation and is intended to provide **intuition**, not just raw numbers.

---

## 📁 Outcomes and Outputs

All quantitative results generated during training and evaluation are stored in:


This folder contains:
- Model-wise performance scores
- Metric-level results (ROUGE, BERTScore, Entity Recall, Number Preservation)
- Outputs used to generate graphs and tables in the paper

If you want to reproduce plots or verify numbers, this folder contains the final experimental outputs.

---

## 🧠 Why This Work Matters

Most summarization research focuses on:
- Larger models
- Better decoding
- Higher ROUGE scores

This project shows that:
- **Training objectives matter more than architecture**
- Factual degradation is a loss-design problem
- Explicit factual supervision is effective even with limited data

---

## ⚠️ Limitations

- Number preservation remains low for both baseline and fact-aware models
- Experiments are conducted in a low-resource setting
- Only single-document summarization is explored

These limitations are intentional and help isolate the effect of fact-aware training.

---

## 🔮 Future Directions

- Designing better numerical alignment losses
- Joint entity–number reasoning mechanisms
- Extending to multi-document summarization
- Scaling experiments to larger multilingual datasets

---

## 📄 Research Status

This project forms the experimental foundation of an ongoing research paper:

**“Fact-Aware Cross-Lingual News Summarization using mBART”**

---

## 👤 Author

**Shashank S**  
Research Focus: Cross-Lingual NLP, Summarization, Factual Consistency

---

## 📜 License

This project is intended for academic and research use.


