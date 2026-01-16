# SOSC314_Shengjie_Shilin_Haowen

# Narrative Competition in Global Energy Transition: A Cross-National Media Analysis (2020-2026)

## 📖 Project Overview

This project is the final capstone for **SOSC 314: Computational Social Science** at Duke Kunshan University. It explores the "narrative divide" between Western and Chinese media regarding climate policy and energy transition. By leveraging 7,000 news articles, we investigate how different national entities use language to frame responsibility, energy security, and the transition to a low-carbon future.

The core research question asks: *How do the lexical features and thematic structures of energy transition reporting differ between Western (The Guardian, Reuters) and Chinese (China Daily, People's Daily) media?*

---

## 🔗 Quick Links

* **[📁 Dataset](https://www.google.com/search?q=./data)**: Access the processed CSV files of 7,000+ articles.
* **[🧹 Text Preprocessing](https://www.google.com/search?q=./notebooks/01_preprocessing.ipynb)**: Scripts for tokenization, N-grams, and data cleaning.
* **[📊 Topic Modeling (STM)](https://www.google.com/search?q=./scripts/topic_modeling.R)**: Structural Topic Modeling with covariates.
* **[⚔️ Fightin' Words Analysis](https://www.google.com/search?q=./notebooks/02_lexical_analysis.ipynb)**: Weighted log-odds analysis for narrative conflict.
* 




---

##  Data Description

The dataset consists of **7,000+ English articles** collected via the GDELT API and custom web scrapers:

* **Western Perspective (2,000 Articles):**
* *The Guardian*
* *Reuters*


* **Chinese Perspective (5,000 Articles):**
* *China Daily*
* *People's Daily (English Edition)*


* **Timeline:** 2020 – 2026.

---

## 🛠 Methodology & Tech Stack

We employ a multi-stage Machine Learning pipeline to analyze the corpora:


1. **Automated Collection:** Using `gdeltdoc` for metadata and `newspaper3k` for text extraction.


2. **Structural Topic Modeling (STM):** Analyzing how "Media Source" and "Time" influence topic prevalence.
3. **Fightin' Words:** Utilizing Dirichlet-prior weighted log-odds to identify polarized vocabulary between the two media groups.
4. **Deep Embeddings:** Measuring semantic shifts using pre-trained **BERT** models to compare the context of terms like "Energy Security".

---


##  Repository Structure

```text
├── data/                   # Processed article data (CSV/JSON)
├── code/              # Jupyter notebooks for exploratory analysis
│   ├── 01_Datagathering.ipynb
│   └── 02_DataCleaning.ipynb
│   └── 03_WordCloud.ipynb
├── visualizations/         # Exported plots and interactive HTML maps
└── README.md

```

---

##  Academic Context

**Course:** SOSC 314: Computational Social Science 

**Instructor:** [Markus Neumann](https://markusneumann.github.io/) 

**Institution:** Duke Kunshan University 
