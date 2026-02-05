# RNASeq-Differential-Expression in SARS-CoV-2
This repository contains a complete analysis pipeline for RNA-Seq data using **R** and **Bioconductor**. The project focuses on identifying differentially expressed genes (DEGs) in blood samples from SARS-CoV-2 patients to discover biomarkers and biological pathways.

## Project Summary and goal
The main goal of this analysis is to process transcriptomic data to understand the host response to viral infection, in comparison with other common respiratory infections such as bacteria neumonia. The workflow covers everything from raw count processing to functional interpretation.

## Key Steps
* **Data Preprocessing:** quality control, filtering of low-count genes and normalization.
* **Exploratory Data Analysis:** Visualizing sample clustering through PCA and heatmaps to possibly discover atypical points and ensure data consistency.
* **Differential Expression:** Statistical modeling to identify significant DEGs.
* **Functional Enrichment:** Pathway analysis using Gene Ontology (GO) and KEGG to provide biological context to the findings.

## Software & Libraries
* **Language:** R
* **Bioinformatics:** Bioconductor (`DESeq2`, `clusterProfiler`, `limma`)
* **Visualization:** `ggplot2`, `pheatmap`, `EnhancedVolcano`

## Repository Structure
* This data comes from a published study: McClain M. T., *Nat Comm.*, 2021. **GSE161731**. 
* `analysis_script.R`: Full documented R script for the analysis.
* `plots/`: Directory containing key visualizations (Volcano Plots, PCA, Heatmaps).
* `executive_summary.pdf` : a structured summary of all the procedures, results and conclusions. 

---
*Developed as part of my technical portfolio in Biostatistics and Genomic Data Science.*
