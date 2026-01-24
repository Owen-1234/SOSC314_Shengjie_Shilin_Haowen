# SOSC314: Narrative Competition in Global Energy Transition
### A Cross-National Media Analysis (2020-2026)

##  Project Overview
This project is the final capstone for **SOSC 314: Computational Social Science** at Duke Kunshan University. It explores the "narrative divide" between Western and Chinese media regarding climate policy and energy transition. By leveraging 7,000 news articles, we investigate how different national entities use language to frame responsibility, energy security, and the transition to a low-carbon future.

---

##  Quick Links
* **[Dataset](https://github.com/Owen-1234/SOSC314_Shengjie_Shilin_Haowen/tree/main/Data)**: 7,000+ processed articles and **Weighted Frequency results**.
* **[Code](https://github.com/Owen-1234/SOSC314_Shengjie_Shilin_Haowen/tree/main/Code)**: Scripts for Context Extraction (Sliding Window), Data Cleaning, and Visualization.
* **[Visualizations](https://github.com/Owen-1234/SOSC314_Shengjie_Shilin_Haowen/tree/main/Image)**: High-res narrative comparison charts and Word Clouds.

---

##  Narrative Frequency Analysis & Measurement
To ensure a fair comparison between the Chinese corpus (5,000 articles) and the Western corpus (2,000 articles), we implemented a Weighted Measurement Strategy 

Instead of raw counts, we calculate the density of a concept per 1,000 articles:

$$ \text{Weighted Frequency} = \left( \frac{\text{Raw Token Count}}{\text{Total Articles in Corpus}} \right) \times 1000 $$

### Context Extraction (Sliding Window)
We developed a Python-based Context Extractionn script that captures all tokens within a 20-word radius of our core seed terms (*Energy Transition*, *Carbon Neutrality*, *Climate Policy*). This allows us to filter out general news noise and focus exclusively on the conceptual vocabulary surrounding energy topics.



---

##  Methodology & Tech Stack
1. **Automated Collection:** Using `gdeltdoc` and `newspaper3k`.
2. **Standardized Measurement:** Weighted frequency normalization to balance corpus sizes.
3. **Context Mining:** Proximity-based extraction (20-word window) for narrative precision.
4. **Structural Topic Modeling (STM):** Analyzing topic prevalence over time.
5. **Fightin' Words:** Dirichlet-prior weighted log-odds for polarized vocabulary detection.

---

##  Repository Structure
```text
├── Data/
│   ├── raw/                    # Original datasets
│   └── processed/              # Weighted_Media_Comparison_Top25.csv
├── Code/
│   ├── 01_DataGathering.ipynb
│   ├── 02_DataCleaning.ipynb
│   ├── 03_ContextExtraction.ipynb # Context-aware keyword mining
│   └── 04_Frequency.ipynb     # High-res bar charts & WordCloud
├── Image/
│   ├── WordCloud.png
│   └── Frequency.png # Standardized comparison chart
└── README.md
