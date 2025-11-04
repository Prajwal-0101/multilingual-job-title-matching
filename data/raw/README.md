# 📂 Raw Data Overview

This directory contains two main datasets used in the **Multilingual Job Title Matching** project:
1. **TalentCLEF 2025 Task A dataset** – the primary multilingual dataset for training and evaluation.
2. **ESCO Dataset (version 1.2.0)** – a supplementary occupational taxonomy dataset used for generating similar job title pairs.

## 📂 Folder Structure
```bash
data/raw/
│
├── talent_clef_2025_task_a/
│   │
│   ├── training/
│   │   ├── english/
│   │   │   └── taskA_training_en.tsv
│   │   ├── spanish/
│   │   │   └── taskA_training_es.tsv
│   │   └── german/
│   │       └── taskA_training_de.tsv
│   │
│   ├── validation/
│   │   ├── english/
│   │   │   ├── queries
│   │   │   ├── corpus_elements
│   │   │   └── qrels.tsv
│   │   ├── spanish/
│   │   ├── german/
│   │
│   └── test/
│       ├── english/
│       │   ├── queries
│       │   └── corpus_elements
│       ├── spanish/
│       ├── german/
│
└── esco_dataset_version_1.2.0/
    ├── english/
    │   └── occupation_en.csv
    ├── spanish/
    │   └── occupation_es.csv
    └── german/
        └── occupation_de.csv
```

## 📘 Dataset Descriptions

### **1️⃣ TalentCLEF 2025 Task A**
The **TalentCLEF 2025 Task A** dataset provides multilingual job title data for training, validation and testing.

It includes three languages: **English**, **Spanish**,and **German**.

#### **Training Set**
Each training file (`taskA_training_XX.tsv`) contains job title pairs with the following columns:
- `family_id`: ISCO family identifier representing the job group.
- `id`: ESCO identifier.
- `jobtitle_1`: The first job title in the pair.
- `jobtitle_2`: A second job title related to `jobtitle_1`.

#### **Validation Set**
Each language folder contains:
- `queries`: Query job titles.
- `corpus_elements`: Job titles forming the search corpus.
- `qrels.tsv`: Relevance mapping between queries and corpus elements.
  - Columns: `q_id`, `iter`, `c_id`, `relevance`

#### **Test Set**
Each language folder contains:
- `queries`
- `corpus_elements`

Used for generating TREC-format run files during evaluation.


---
### **2️⃣ ESCO Dataset (Version 1.2.0)**
This dataset provides multilingual occupational taxonomy data from the **European Skills, Competences, Qualifications and Occupations (ESCO)** database.

**Available Languages:**
- English (`english/`)
- Spanish (`spanish/`)
- German (`german/`)

Each language folder contains a single file named `occupation_XX.csv`, where `XX` represents the language code (e.g., `en`, `es`, `de`).  
These files list job titles and related occupational metadata used to construct **similar title pairs** during preprocessing.

### 📝 Note
The folder structure above is shown for the **English** language only.  
The **same structure** is followed for **Spanish** and **German** datasets in the `training`, `validation`, and `test` folders.
