# Retrieval-Augmented Generation (RAG) Customer Support System

An end-to-end RAG system designed to evaluate and generate support responses using Twitter Customer Support data (`twcs.csv`). Built with **FAISS**, **SentenceTransformers**, **Google Flan-T5**, and evaluated using **ROUGE** metrics.

---

## 🎯 Architecture Overview

1. **Data Ingestion & Pairing:** 
   - Cleaned Twitter customer support data and built dialogue pairs (Customer Query $\rightarrow$ Brand Response).
   - Standardized text by removing social handles (`@mentions`).
2. **Vector Indexing (Retrieval):**
   - **Embedding Model:** `sentence-transformers/all-MiniLM-L6-v2` (384-dimensional embeddings).
   - **Vector Store:** `faiss.IndexFlatL2` for top-$k$ similarity search ($k=3$).
3. **Response Generation:**
   - **Generator Model:** `google/flan-t5-base`.
   - Structured context-aware prompting utilizing retrieved historical support resolutions.
4. **Evaluation:**
   - Automated batch evaluation across sample test queries using **ROUGE-1**, **ROUGE-2**, and **ROUGE-L** metrics.

---

## 📊 Benchmark Results

Evaluated across 50 test customer queries on `AmazonHelp` data:

| Metric | Score | Description |
| :--- | :--- | :--- |
| **ROUGE-1** | `0.1570` | Unigram overlap between generated and reference response |
| **ROUGE-2** | `0.1135` | Bigram overlap measuring phrasing accuracy |
| **ROUGE-L** | `0.1519` | Longest Common Subsequence measure |

---

## 🛠️ Setup & Execution

1. **Clone the repository:**
   ```bash
   git clone [https://github.com/thamiraaa/RAG-Customer-Support.git](https://github.com/thamiraaa/RAG-Customer-Support.git)
   cd RAG-Customer-Support
