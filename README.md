# Cytokine/Chemokine PCA and Clustering Analysis

## Procedure Overview

This repository contains an R Markdown workflow for dimensionality reduction and clustering of cytokine expression data. The analysis demonstrates how PCA and clustering methods can be applied to distinguish biological groups based on cytokine profiles.

> **Important Note:** This analysis uses **artificially generated data** simulated with known group separation. It is intended as a methodological demonstration only and does not represent real patient or experimental data. Results should not be interpreted in a clinical or biological context.

---

## What This Analysis Does

1. **Data preparation** — generates a simulated cytokine dataset (Control vs. Sepsis groups) with 5 analytes: IL-6, TNF-α, IL-10, IFN-γ, and IL-1β. These are major inflammatory cytokines indicative of sepsis in murine species. Each cytokine concentration was generated via a form of a random normal distribution.
2. **Preprocessing** — removes non-numeric columns, checks for missing values, and z-score scales the data
3. **PCA** — runs principal component analysis, produces a scree plot, PC1/PC2 biplot with 95% confidence ellipses, and a PC1 loadings plot
4. **Hierarchical clustering** — builds a distance matrix, plots a color-labeled dendrogram, and evaluates cluster-to-group concordance
5. **K-means clustering** — fits a 2-center k-means model and overlays cluster assignments on the PCA plot
6. **Heatmap visualization** — generates annotated heatmaps using base R and `pheatmap`, with group color annotations to further characterize clusters and sepsis profiles.

---

## Important Limitations

This workflow **does not include the data cleaning steps required for raw cytokine data**. Before applying this pipeline to real experimental data, you would need to address:

- **Below detection limit (BDL) values** — common in multiplex cytokine assays; require imputation or removal strategies
- **Outlier detection and removal** — raw assay data often contains technical outliers that must be flagged
- **Batch correction** — multi-plate or multi-day assay runs introduce systematic batch effects
- **Log transformation** — cytokine concentrations are typically right-skewed and should be log-transformed before scaling
- **Quality control filtering** — samples with high CVs or failed internal controls should be excluded
- **Unit standardization** — ensure all analyte concentrations are on the same scale (e.g., pg/mL)

---

## Requirements

- R (>= 4.5.2)
- R packages: `ggplot2`, `dplyr`, `tidyverse`, `car`, `dendextend`, `pheatmap`

Package versions are managed with `renv` for proper version control. To restore the exact environment:

```r
renv::restore()
```

---

## Usage

1. Clone the repository:
```bash
git clone https://github.com/jackcleary515/Cytokine-Chemokine-Analysis-.git
cd Cytokine-Chemokine-Analysis-
```

2. Open `PCA with Cytokines.Rmd` in RStudio

3. Restore the package environment:
```r
renv::restore()
```

4. Knit the document or run chunks interactively

> To apply this workflow to your own data, replace the simulated `cytokine_df` in chunk 1 with your preprocessed cytokine dataset, ensuring column names match the analyte names used throughout the script.

---

## Repository Structure

```
.
├── PCA with Cytokines.Rmd   # Source R Markdown file
├── PCA-with-Cytokines.html  # Rendered HTML report
├── cytokine_data.csv        # Simulated cytokine dataset
├── renv.lock                # Locked package versions
├── renv/                    # renv activation scripts
├── .Rprofile                # renv auto-activation
└── .gitignore
```

---

## Author

Jack Cleary
Date of Publication: 25JUN2026
Most Recent Update: 25JUN2026
