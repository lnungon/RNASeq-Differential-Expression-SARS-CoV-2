# RNASeq-Differential-Expression in SARS-CoV-2
This repository contains a complete analysis pipeline for RNA-Seq data using **R** and **Bioconductor**. The project focuses on identifying differentially expressed genes (DEGs) in blood samples from SARS-CoV-2 patients to discover biomarkers and biological pathways.

## Project Summary and goal
The main goal of this analysis is to process transcriptomic data to understand the host response to viral infection, in comparison with other common respiratory infections such as bacteria neumonia. The workflow covers everything from raw count processing to functional interpretation.

**Dataset Highlights**: Analysis of 195 blood samples. 
**Conditions:** Comparison between COVID-19, Bacterial Pneumonia, and Healthy Controls.
**Technology:** Bulk RNA-Seq (Illumina)

## Key Steps
* **Data Preprocessing:** quality control, filtering of low-count genes and normalization.
* **Exploratory Data Analysis:** Visualizing sample clustering through PCA and heatmaps to possibly discover atypical points and ensure data consistency.
* **Differential Expression**: Statistical modeling to identify significant DEGs using the Negative Binomial distribution.
* **Functional Enrichment:** Pathway analysis using Gene Ontology (GO) to provide biological context to the findings.

## Analysis overview
The following visualizations demonstrate the robust biological signal captured from the 195 blood samples in the GSE161731 dataset.

1. **Sample Clustering via Principal Component Analysis (PCA)**
We performed unsupervised clustering using TMM-normalized log2 counts. To ensure that genes with different expression levels contributed equally to the variation, the data was centered and scaled ($scale. = TRUE$) before computing the principal components.

![PCA Plot](1.PCA plot-1.png)

>The PCA plot shows a clear separation along PC1 ($14.6%$ of variance) between bacterial pneumonia patients (red) and healthy controls (blue). However, COVID-19 patients (green) exhibit significant transcriptional overlap with the control group. This suggests that while bacterial pneumonia triggers a highly distinct systemic host response, the COVID-19 signature appears more heterogeneous or subtle, highlighting the varying nature and intensities of the host response across different respiratory pathogens.

2. **Functional Enrichment Analysis (Gene Ontology)**
To interpret the biological relevance of the Differentially Expressed Genes (DEGs), we performed over-Representation Analysis using clusterProfiler against the Gene Ontology (GO) database.

! [Functional enrichment based on biological processes (GO terms) in COVID-19 and pneumonia bacterial patients over healthy controls](plots/10.Functional enrichment by biological process-1.png)

>This dotplot illustrates the top enriched GO terms (classified by Biological Process) for upregulated genes in COVID-19 and bacterial pneumonia. Key activated pathways include "type I interferon signaling pathway" and "response to virus", which are hallmark innate immune responses to viral infection. The Gene Ratio and Adjusted P-value ($P_{adj}$) demonstrate significant over-representation, providing a biological mechanistic link to the clinical phenotype. In contrast, the bacterial infection signature is directly linked to cellular structural and degradative processes, specifically autophagy, vesicle-mediated transport, and endocytosis. These pathways likely represent the host’s attempt to internalize and degrade bacteria. 

## Software & Libraries
This pipeline is built on the Bioconductor ecosystem for genomic data science and the primary frameworks used are: 
* **Language:** R
* **Bioinformatics:** Bioconductor:
  * DESeq2: Principal statistical framework for Differential Gene Expression (DGE) analysis.
  * SummarizedExperiment: Standard S4 infrastructure for coordinated storage of assay data and clinical metadata.
  * clusterProfiler: Functional enrichment analysis (Gene Ontology & KEGG pathways).
  * edgeR: Used for TMM normalization and library size scaling.
* **Data manipulation & Visualization:** `tidiverse`(`ggplot2` and `tdyr`), `pheatmap`, `EnhancedVolcano`
  
Reproducibility Note: A comprehensive list of all loaded packages, versions, and the computational environment is provided in the Session Information section at the end of the final report.

## Repository Structure
* This data comes from a published study: McClain M. T., *Nat Comm.*, 2021. **[GSE161731](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE161731)**. 
* `analysis_script.R`: Full documented R script for the analysis.
* `analysis_script.html`: Full documented html output from the script.
* `plots/`: Directory containing key visualizations (Volcano Plots, PCA, Heatmaps).
* `executive_summary.pdf` : a structured summary of all the procedures, results and conclusions.
* `sessio_info.txt`: complete information about the used environment

---
*Developed as part of my technical portfolio in Biostatistics and Genomic Data Science.*
