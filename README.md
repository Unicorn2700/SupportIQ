# SupportIQ – AI Escalation & Resolution Optimization Engine

## Project Overview

SupportIQ is an NLP-based machine learning system designed to predict escalation risk from customer complaint text.

Instead of performing traditional sentiment analysis, the problem is reframed as a **business-driven escalation risk prediction task**, helping support teams prioritize high-risk complaints and minimize operational losses.

---

## Problem Statement

Airlines receive thousands of customer complaints daily via social media and support channels. Delayed handling of high-risk complaints can lead to:

- Customer churn  
- Brand reputation damage  
- Escalations and legal risk  
- Financial loss  

The objective of this project is to:

1. Predict whether a complaint is **high risk** (likely to escalate).
2. Optimize the decision threshold based on **business cost**, not just accuracy.
3. Provide a structured and scalable NLP pipeline for operational use.

---

## Methodology

### 1️. Data Preparation

- Dataset: Twitter Airline Customer Complaints
- Selected features:
  - `text` (complaint content)
  - `airline_sentiment`
- Reframed sentiment into binary escalation risk:
  - Negative → High Risk (1)
  - Neutral/Positive → Not High Risk (0)

---

### 2️. NLP Preprocessing

- Lowercasing
- URL removal
- Mention and hashtag removal
- Punctuation and number removal
- Stopword removal

Created a `clean_text` column for structured modeling.

---

### 3️. Feature Engineering

- TF-IDF vectorization (max 5000 features)
- Stratified train-test split (80/20)

---

### 4️. Model Training

Model: Logistic Regression  

**Performance:**
- Accuracy: 83%
- High-Risk Recall: 91%
- ROC-AUC: 0.90

This establishes a strong classical NLP baseline.

---

## Business-Oriented Threshold Optimization

Instead of using the default probability threshold (0.5), a cost-sensitive framework was introduced:

- ₹5000 loss per missed high-risk complaint
- ₹500 cost per false alarm

By simulating operational cost across thresholds:

**Optimal Threshold Identified: 0.2**

This reduced total expected operational loss compared to the default decision boundary.

This demonstrates alignment between ML modeling and real-world business impact.

---

## Key Insights

- Accuracy alone is insufficient for operational systems.
- Precision-recall trade-offs must align with business priorities.
- Threshold tuning significantly affects financial outcomes.
- Cost-sensitive modeling transforms ML from academic to production-ready.

---

## Tech Stack

- Python
- Pandas
- NumPy
- Scikit-learn
- NLTK
- TF-IDF Vectorization

---

## Future Enhancements (Planned)

- LLM-based ticket summarization
- Automated response generation
- Embedding-based semantic search
- Retrieval-Augmented Generation (RAG) for historical case retrieval
- Model explainability (SHAP)
- Deployment via Streamlit / FastAPI

---

## 📌 Conclusion

SupportIQ is not just a sentiment classifier.  
It is a **risk-aware decision optimization system** that integrates NLP, predictive modeling, and business-cost simulation to assist customer support operations.
