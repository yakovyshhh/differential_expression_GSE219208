Differential Gene Expression Analysis of GSE219208
This project analyzes gene expression differences across experimental conditions using RNA-seq data from the **GSE219208** dataset. It involves data preprocessing, differential expression analysis, visualization, and functional enrichment of significantly regulated genes.

Data & Metadata

- Counts: `counts.csv` (gene expression count matrix)  
- Metadata: `metadata.txt` (sample annotations)  
- Samples are grouped by:
  - Treatment type
  - Timepoint (3 vs 6 days)

Setup

Required R packages:
pacman::p_load("here", "tidyverse", "DESeq2", "ashr", "maEndToEnd", "EnhancedVolcano",
               "pd.mogene.2.0.st", "enrichR", "gprofiler2", "pheatmap", "gt")


Workflow Overview

1. Data Import & Preprocessing
- Load count matrix and metadata
- Match samples between metadata and expression matrix
- Create `DESeqDataSet` and normalize data using DESeq2

2. Differential Expression Analysis
- Design: `~ time..days..ch1`
- Identify significantly differentially expressed genes:
  - `padj < 0.05`
  - `|log2FoldChange| > 0.27`

3. Visualization
- Volcano plot of differential expression
- PCA plot to inspect sample clustering
- Heatmap of top differentially expressed genes
- MA plot and ECDF plot of p-values

4. Functional Enrichment
- Gene Ontology (GO) analysis using:
  - `gprofiler2`
  - `enrichR` with GO Biological Process, Cellular Component, Molecular Function
- Highlighting key terms in enrichment plots

5. Time-Course Expression Plots
- Visualization of gene expression across time (day 3 vs day 6)
- Line plots for top 5–6 DE genes by treatment


Key Results
- Number of significantly differentially expressed genes (DEGs): 7
- Notable enriched GO terms: 
=> GO:0005840 — ribosome (Cellular Component), adjusted p-value = 0.0089
=> GO:0003735 — structural constituent of ribosome (Molecular Function), adjusted p-value = 0.0036
=> GO:0005198 — structural molecule activity (Molecular Function), adjusted p-value = 0.0036
- Expression changes over time visualized via `ggplot2`

Outputs
- `significant_genes1.csv` – list of significant DE genes
- GO enrichment results from `gprofiler2` and `enrichR`
- Volcano, PCA, heatmap, MA, ECDF, and time-course plots

Author
Differential expression analysis performed by Liliia Yakovyshyna, September 2024  
R version: 4.x with Bioconductor packages


