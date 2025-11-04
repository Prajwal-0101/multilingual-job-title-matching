##  **Fine-Tuned Sentence Transformer for Multilingual Job Title Matching**

---

## 🧩 Project Overview  

This project was developed as part of the **TalentCLEF 2025 – Task A: Multilingual Job Title Matching** shared task.  
The goal is to develop systems capable of **identifying and ranking job titles most similar to a given job title** across multiple languages — **English, Spanish, and German**.  

For each job title in a provided test set, the system generates a **ranked list of similar job titles** from a specified knowledge base.   
To achieve this, we fine-tune a **SentenceTransformer** model (`paraphrase-multilingual-mpnet-base-v2`) using **custom multilingual job title pairs** created from the **ESCO 1.2.0 dataset**.  
The ESCO dataset was processed to generate **similar-title sets** for each language, which were then combined to form a **multilingual training corpus**.  

After fine-tuning with **Cached Multiple Negatives Ranking Loss**, the trained model generates embeddings for query and corpus job titles.  
**Cosine similarity** is then used to compute similarity scores, and job titles are ranked accordingly.  
Model performance is evaluated using standard retrieval metrics — **Mean Average Precision (mAP)**, **Mean Reciprocal Rank (MRR)**, and **Precision@K**.

---

## 🗂️ Project Structure
```bash
Multilingual Job Title Matching/
│
├── data/
│ ├── raw/
│ │ ├── esco_dataset_version_1.2.0/ # Multilingual ESCO occupation data
│ │ ├── talent_clef_2025_task_a/ # TalentCLEF 2025 Task A dataset
│ │ └── README.md # Description of raw datasets
│ │
│ └── processed/
│ ├── esco_similar_titles/ # Generated ESCO similar-title sets
│ └── README.md # Details on processed data
│
├── notebooks/
│ ├── 1_create_esco_similar_titles.ipynb  # Build similar title sets from ESCO data
│ └── 2_model_training_and_evaluation.ipynb  # Train & evaluate SentenceTransformer
│
├── paper/
│  └── Fine_Tuned_Sentence_Transformer_for_Multilingual_Job_Title_Matching_CLEF2025.pdf
│
└── README.md # ← (This file)
```
---

## 📘 Workflow Summary

### 1. Generate Similar Titles
**Notebook:** [`1_create_esco_similar_titles.ipynb`](notebooks/1_create_esco_similar_titles.ipynb)
- Reads multilingual ESCO `occupation_XX.csv` files.  
- Extracts related job titles using preferred & alternate labels.  
- Creates `similar_title_sets_XX.csv` for English, Spanish, and German.  
  
### 2. Train and Evaluate Model
**Notebook:** [`2_model_training_and_evaluation.ipynb`](notebooks/2_model_training_and_evaluation.ipynb)
- Loads processed ESCO outputs (`similar_title_sets_XX.csv`) for all languages and **combines** them to create a multilingual pool of similar job titles.  
- Generates **all possible job-title pairs** from those similar-title sets (positive pairs).  
- Converts the pairs into the **SentenceTransformer training format** for model fine-tuning.  
- Fine-tunes a SentenceTransformer model using `Cached Multiple Negatives Ranking Loss`.  
- After training, **embeddings are generated** for each job title in the **query** and **corpus** files.  
- **Cosine similarity** is used to compute similarity scores between query and corpus embeddings.  
- For each query, corpus job titles are **ranked by similarity score**.  
- Model performance is evaluated using standard retrieval metrics, including:  
  - **Mean Average Precision (MAP)**  
  - **Mean Reciprocal Rank (MRR)**  
  - **Precision@K**

---

## 📊 Datasets

- **TalentCLEF 2025 Task A** — Multilingual job title pairs for training, validation, and testing.  
- **ESCO 1.2.0 Dataset** — Source of multilingual occupation data used to generate similar-title sets.

---


## 🧾 Working Notes Paper

This repository accompanies our CLEF 2025 Working Notes submission:

**Title:** Fine-Tuned Sentence Transformer for Multilingual Job Title Matching  
**Event:** CLEF 2025 – TalentCLEF Task A  
**Paper:** [`Fine_Tuned_Sentence_Transformer_for_Multilingual_Job_Title_Matching_CLEF2025.pdf`](paper/Fine_Tuned_Sentence_Transformer_for_Multilingual_Job_Title_Matching_CLEF2025.pdf)
