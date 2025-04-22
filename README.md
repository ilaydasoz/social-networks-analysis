# Social Network Analysis: Author Success Prediction

### Files

- `soc_net_analysis.ipynb`: Jupyter Notebook containing the full implementation of network analysis and predictive modeling.
- `sna_report.pdf`: Final report detailing the methodology, experimental design, and results.

### Overview

This project investigates the relationship between a researcher's **position in a coauthorship network** and their **likelihood of publishing in top-tier venues**. It is inspired by the study by Sarıgöl et al. (2014), which used citation counts to predict academic success through social network features. This project redefines success based on publication venue prestige.

## Objectives

- Construct a **time-evolving coauthorship graph** from the DBLP dataset (2019–2025).
- Define a binary **success label**: papers published in top-tier venues (e.g., ICLR, NeurIPS, CVPR) are marked as successful.
- Extract **author-level network features** (Betweenness Centrality, K-Core Number) using the Networkit library.
- Aggregate features at the **paper level** and train machine learning models to predict publication success.


### Methods

#### 1) Network Construction
- Nodes represent authors, and edges represent coauthorship.
- Networks are created using **2-year sliding windows** to capture temporal evolution.
- Isolated nodes and self-loops are removed; the largest connected component is retained for analysis.

#### 2) Feature Extraction
- Centrality metrics are computed per author and aggregated per paper (e.g., maximum betweenness among coauthors).
- Features used:
  - Betweenness Centrality
  - K-Core Number

#### 3) ML Models
- **Random Forest Classifier**: Robust to small datasets, serves as a baseline.
- **Multi-Layer Perceptron (MLP)**: Includes feature scaling and **SMOTE oversampling** to address class imbalance.

Models are trained and tested on datasets of increasing size: 100K, 200K, 500K, and 1M papers.

### References

- Sarıgöl, E., et al. *Predicting Scientific Success Based on Coauthorship Networks*. EPJ Data Science, 2014.
