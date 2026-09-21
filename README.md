# Wine Dataset — Unsupervised Clustering Analysis

Comprehensive unsupervised learning analysis of the UCI Wine dataset, applying and comparing multiple clustering techniques to identify natural groupings among 178 wine samples described by 13 physicochemical properties.

## Techniques covered

| Method | Family | Key result |
|---|---|---|
| Hierarchical clustering (Ward, Average, Agnes) | Hierarchical | 3 clusters confirmed |
| K-Means | Partition | K=3 optimal (WSS + Silhouette) |
| K-Means on PCA components | Dimensionality reduction + partition | 66% variance with 3 PCs |
| DBSCAN / HDBSCAN | Density-based | 1 dense cluster + noise points |
| OPTICS | Density-based | Confirms DBSCAN findings |
| Gaussian Mixture Models (mclust) | Probabilistic | VVE model, G=3 |
| FlexMix | Probabilistic | Consistent with GMM |

## Dataset

[Wine — UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/109/wine)

178 observations · 13 numeric features · 3 wine cultivars (Type 1, 2, 3)

The `wine.csv` file is included in this repository. Original source: Forina, M. et al., PARVUS (1991).

## Key findings

- **23 out of 29 methods** (`parameters::n_clusters`: NbClust indices, silhouette, gap statistic and mclust mixtures) agree that K=3 is the optimal number of clusters, aligning perfectly with the 3 known wine types.
- **DBSCAN and OPTICS** consistently detect a single dense cluster with noise points, suggesting the wine groups overlap in density-based space — a meaningful contrast to partition methods.
- **PCA** with 3 components explains ~66% of variance; clustering on reduced dimensions yields results consistent with full-feature clustering.
- **GMM (VVE model)** confirms 3 probabilistic clusters with 6 observations showing >50% uncertainty between two groups.

## Repository structure

```
wine-clustering-analysis/
├── wine_clustering_analysis.Rmd   # Full analysis source
├── wine.csv                       # Dataset (UCI, public domain)
└── README.md
```

## How to run

1. Clone the repository
2. Open `wine_clustering_analysis.Rmd` in RStudio
3. Install dependencies — the script uses `pacman::p_load()` to handle this automatically on first run
4. Click **Knit → PDF** (requires a LaTeX installation, e.g. TinyTeX: `install.packages("tinytex"); tinytex::install_tinytex()`)

### R environment

Developed and tested under:

```
R version 4.5.3 (2026-03-11)
Platform: x86_64-w64-mingw32/x64 (Windows 10)
```

Key packages: `tidymodels 1.4.1` · `factoextra 1.0.7` · `FactoMineR 2.12` · `dbscan 1.2.4` · `ClusterR 1.3.6` · `NbClust 3.0.1` · `pvclust 2.2-0` · `plotly 4.11.0` · `igraph 2.2.1`

Full session info is included at the end of the compiled document.

## Language

The analysis report (Rmd / notebook text) is written in Spanish; this README is in English.

## Authors

Dámaso López, Alexis Aminadab · Islas Zicatl, Max Emiliano · Mares Guerra, José de Jesús · Martínez Sánchez, José Ricardo · Ramos López, Gabriela · Salazar Argáez, Miguel Angel

Statistical Methods and Mathematics for Data Science Diploma — Team 9
