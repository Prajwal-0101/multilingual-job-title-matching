# 📂 Processed Data — ESCO Similar Titles

This directory contains **language-specific processed datasets** derived from the multilingual **ESCO (European Skills, Competences, Qualifications and Occupations)** database.  
Each file includes **sets of similar job titles** generated for use in the multilingual job title matching task.

---
## 🗂️ Folder Structure
data/processed/
    └── esco_similar_titles/
        ├── english/
        │   └── similar_title_sets_english.csv
        ├── spanish/
        │   └── similar_title_sets_spanish.csv
        └── german/
            └── similar_title_sets_german.csv

---

## 📘 File Descriptions

### `similar_title_sets_english.csv`
- Derived from: `data/raw/esco_dataset_version_1.2.0/english/occupation_en.csv`
- Contains groups of **semantically similar English job titles** 

### `similar_title_sets_spanish.csv`
- Derived from: `data/raw/esco_dataset_version_1.2.0/spanish/occupation_es.csv`
- Contains groups of **semantically similar Spanish job titles**.

### `similar_title_sets_german.csv`
- Derived from: `data/raw/esco_dataset_version_1.2.0/german/occupation_de.csv`
- Contains groups of **semantically similar German job titles**.

---

## 🧩 Generation Details
All processed files were generated using the notebook:

[`notebooks/1_create_esco_similar_titles.ipynb`](../../../notebooks/1_create_esco_similar_titles.ipynb)

This notebook:
- Reads the **`occupation_XX.csv`** file for each language.
- Extracts **related and alternative job titles**.
- Creates grouped sets of similar titles, stored as `similar_title_sets_XX.csv`.

---

## 📝 Notes
- Each row in a `similar_title_sets_XX.csv` file represents a **set of equivalent or closely related job titles**.
- These datasets are later used in model training to generate **all job title pairs** for contrastive learning.

