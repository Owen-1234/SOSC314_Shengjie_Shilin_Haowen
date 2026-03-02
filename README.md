
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

In the final phase of our analysis, we implemented a **DMR (Dirichlet Multinomial Regression)** model to quantify the narrative divergence. After testing , we determined K = 20 to be the optimal granularity, providing the best balance between statistical fit (Log-Likelihood) and semantic distinctness. To address the limitations of DMR in uncovering latent thematic patterns and temporal trends, we abandoned DMR in favor of the Structural Topic Model (STM) to conduct our core narrative divergence analysis.


## 🤖 Structural Topic Modeling (STM) Implementation: Core Methodology & Analytical Findings

We employ the **Structural Topic Model (STM)** (Roberts et al., 2014) as the core analytical framework to uncover latent thematic patterns in cross-regional energy transition discourse (2020–2025), with optimal topic granularity set to **K=20** (balanced statistical robustness and interpretability).

### Key Model Design
1. **Input Features**
   - Textual: Document-Term Matrix (DTM) built from 20-word context windows around seed terms ("energy transition", "carbon neutrality", "climate policy"), with stopwords/numbers removed and no stemming (preserve semantic nuance of technical/political terminology).
   - Covariates: Categorical (media region: China/Western; source; keyword) + Continuous (publication year) to structure topic priors and capture temporal dynamics.
2. **Model Specification**
   - Non-linear temporal modeling via spline functions ($f(Year_d)$) to address event-driven volatility in climate narratives (vs. linear constraints of Dirichlet-Multinomial Regression).
   - Training: Deterministic Spectral Initialization, EM algorithm capped at 75 iterations; hyperparameter tuning across K=10/20/30 (K=10: over-broad topics; K=30: semantic noise).

### Core Findings
1. **Cross-Regional Thematic Divergence** (Statistically validated via two-sample t-tests with Bonferroni correction, p<0.01)
   - Chinese media: Emphasis on state-led implementation (Renewables & Hydrogen, Low-Carbon Policy, EVs & Batteries, CPC Governance) and international cooperation (Belt and Road, China-Africa partnerships).
   - Western media: Focus on political contestation (Activism, Australian Politics), fossil fuel transition conflicts (Coal & Emissions, Oil & Gas), and regulatory debate.
   - Shared focus: COP/Paris Talks (symbolic diplomatic significance).

2. **Temporal Dynamics (2020–2025)**
   - Group A (moderate-high baseline): Gradual trends (e.g., China-Africa Cooperation ↑, Global Macroeconomy ↓, Green Finance peaked in 2021).
   - Group B (low baseline, high variability): Sharp fluctuations aligned with policy/events (e.g., EVs & Batteries ↑ post-2022, Low-Carbon Policy peaked in 2021, COP & Paris Talks episodic spikes).
   - Overall trajectory: Early focus on energy security → mid-term policy consolidation → late emphasis on tech/industrial competition.

### Model Evaluation & Limitations
- Evaluation: Multi-dimensional validation (pre-model lexical window analysis, structural differentiation, temporal coherence) — no predictive metrics (unsupervised task), focus on interpretability/coherence of thematic structures.
- Limitations: Bag-of-words assumption (insensitive to tone/stance/causality); K=20 as a compromise (held-out likelihood ↑ with K, semantic coherence ↓ beyond K=20); corpus restricted to 4 major outlets (China Daily/People’s Daily; The Guardian/Reuters).

#### Future Work
Expand media sources (diverse national/linguistic/genre coverage), extend time series post-2025, and integrate transformer-based models (stance classifiers/framing detectors) to complement STM’s shallow semantic analysis — moving from descriptive topic tracking to explanatory analysis of narrative construction.

---

##  Repository Structure

```text
├── Code/
│   ├── DMR/                          # Scripts for Dirichlet Multinomial Regression modeling
│   ├── Processing/                    # Data cleaning and preprocessing pipelines
│   ├── STM/                           # Structural Topic Modeling implementation scripts
│   ├── Scraping/                      # Web scraping and data collection utilities
│   └── Readme.md                      # Documentation for the Code directory
├── Data/
│   ├── DMR/                           # Input/output data for the DMR model
│   ├── STM/                           # Input/output data and results for the STM model
│   ├── scraped/                       # Raw, unprocessed scraped news articles
│   └── README.md                      # Documentation for the Data directory
├── Image/
│   ├── 20-word_Media_Narrative_Comparison.png  # 20-word window media narrative comparison
│   ├── DMR_region_specific_mirror_plot.png    # DMR region-specific lexical exclusivity mirror plot
│   ├── DMR_topic_network_map.png              # DMR topic correlation network graph
│   ├── STM_China-UK_comparison.png            # STM China-UK media narrative comparison
│   ├── STM_HeatTopics.png         # STM topic heatmap visualization
│   ├── Western_media_wordclouds.png  # Word cloud for Western media corpus 
│   ├── chinese_media_wordclouds.png  # Word cloud for Chinese media corpus
│   └── topic_time_series.rar      # Compressed archive of topic time series data
├── 314Final.html                      # HTML version of the final project report
└── README.md                          # Main project documentation and overview

```
