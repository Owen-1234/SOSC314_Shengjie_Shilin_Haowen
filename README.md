
# SOSC314: Narrative Competition in Global Energy Transition

### A Cross-National Media Analysis (2020-2026)

## 🚀 Project Overview

This project is the final capstone for SOSC 314: Computational Social Science at Duke Kunshan University. It explores the "narrative divide" between Western and Chinese media regarding climate policy and energy transition. By leveraging 7,000 news articles, we investigate how different national entities use language to frame responsibility, energy security, and the transition to a low-carbon future.

---

## 🔗 Quick Links

* **[Dataset](https://github.com/Owen-1234/SOSC314_Shengjie_Shilin_Haowen/tree/main/Data)**: 7,000+ processed articles and Weighted Frequency results
* **[Code](https://github.com/Owen-1234/SOSC314_Shengjie_Shilin_Haowen/tree/main/Code)**: Scripts for Context Extraction (Sliding Window), Data Cleaning, and **STM Modeling (R)**.
* **[Visualizations](https://github.com/Owen-1234/SOSC314_Shengjie_Shilin_Haowen/tree/main/Image)**: High-res narrative comparison charts and Word Clouds.

---

## 📊 Narrative Frequency Analysis & Measurement

To ensure a fair comparison between the Chinese corpus (5,000 articles) and the Western corpus (2,000 articles), we implemented a Weighted Measurement Strategy.

Instead of raw counts, we calculate the density of a concept per 1,000 articles:

### Context Extraction (Sliding Window)

We developed a Python-based **Context Extraction** script that captures all tokens within a 20-word radius of our core seed terms (*Energy Transition*, *Carbon Neutrality*, *Climate Policy*). This allows us to filter out general news noise and focus exclusively on the conceptual vocabulary surrounding energy topics.

---

##  Dirichlet Multinomial Regression & Comparative Analysis

In the final phase of our analysis, we implemented a **DMR (Dirichlet Multinomial Regression)** model to quantify the narrative divergence. After testing , we determined **** to be the optimal granularity, providing the best balance between statistical fit (Log-Likelihood) and semantic distinctness.

### 🤖 Structural Topic Modeling (STM) Implementation

In addition to DMR, we utilized an **R-based STM pipeline** to further investigate how metadata influences topic prevalence.

* **Model Configuration**: We fitted an STM with **K=20** topics using **Spectral initialization**.
* **Prevalence Covariates**: The model estimates topic proportions based on:
`Prevalence ~ media + source + keyword + s(year)`
*The inclusion of `s(year)` (a spline function) allows us to capture the non-linear evolution of energy narratives over the 2020-2026 period.*
* **Statistical Outputs**: We exported the **Theta matrix** to calculate the mean topic proportions across different media systems, enabling a rigorous comparative analysis.

### Advanced Quantified Visualizations

We decoded the energy discourse using two specialized computational social science visualizations:

#### 1. Topic Correlation Network (`topic_network_map.png`)

This graph visualizes the "Narrative Web" by calculating the semantic connectivity (keyword overlap) between topics.

* **Key Finding:** It reveals how *Renewable Energy* is structurally tied to *National Innovation* in the merged global discourse, forming a central narrative hub.

#### 2. Region-Specific Mirror Analysis (`region_specific_mirror_plot.png`)

Using a **Lexical Exclusivity Score**, this "Tornado Plot" identifies topics and keywords that are unique to each media group.

* **China-Specific:** High exclusivity in topics involving `cpc, committee, modernization`, indicating a **State-led/Institutionalized** narrative.
* **UK-Specific:** High exclusivity in topics involving `trump, biden, court, labor`, indicating a **Party-politics/Politicized** narrative.

---

## Methodology & Tech Stack

1. **Automated Collection:** Using `gdeltdoc` and `newspaper3k`.
2. **Standardized Measurement:** Weighted frequency normalization to balance corpus sizes.
3. **Context Mining:** Proximity-based extraction (20-word window) for narrative precision.
4. **Topic Modeling:** Combined **DMR** (Python) and **Structural Topic Modeling** (R, `stm` package) for cross-verifying topic prevalence.
5. **Visualization:** Matplotlib, Seaborn, NetworkX, and R's `ggplot2` for quantitative plotting.

---

##  Repository Structure

```text
├── Data/
│   ├── energy_narrative_C_cleaned.csv              # Cleaned Chinese data
│   ├── energy_narrative_W_cleaned.csv              # Cleaned Western data
│   ├── Frequency.csv                               # Word density results
│   └── STM_topic_comparison.csv                    # Topic keywords for K=10, 20, 30
├── Code/
│   ├── 01_DataGathering.ipynb
│   ├── 02_DataCleaning.ipynb
│   ├── 03_ContextExtraction.ipynb                  # Context-aware keyword mining
│   ├── 04_Frequency_Visualization.ipynb            # Standardized bar charts
│   ├── 05_DMR_Modeling.py                          # DMR Model training logic
│   ├── 06_DMR_Advanced_Visualization.py            # Network & Mirror plot scripts
│   └── 07_STM.Rmd                                  # STM implementation in R (K=20)
├── stm_outputs_R_K20/                              # Generated by R script
│   ├── K20_top_words.txt                           # Topic words & labels
│   ├── K20_theta.csv                               # Document-topic distribution
│   └── K20_mean_theta_by_media.csv                 # Regional mean proportions
├── Image/
│   ├── WordCloud.png
│   ├── Frequency.png                               # Standardized comparison chart
│   ├── topic_network_map.png                       # Topic correlation graph
│   └── region_specific_mirror_plot.png             # Regional exclusivity comparison
└── README.md

```
