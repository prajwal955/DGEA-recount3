# DGEA-recount3

# RNA-seq Differential Expression & Functional Enrichment Pipeline

An end-to-end bulk RNA-seq analysis workflow in R, starting from public data on **recount3**, through differential expression testing with **DESeq2**, quality control, visualization, and functional enrichment.

**Dataset:** recount3 project `SRP095512` (human, GENCODE v26)
**Comparison:** Control vs. Patient (`Ctrl` vs `Pat`)

## What this script does

1. Pulls raw coverage data from recount3 and converts it to read counts
2. Builds a DESeq2 dataset and filters low-count genes
3. Runs differential expression testing (Wald test) with `apeglm` LFC shrinkage
4. QC via PCA to confirm sample clustering by condition
5. Annotates ENSEMBL IDs with gene symbols
6. Visualizes results: MA plots, heatmaps (pheatmap + ComplexHeatmap), volcano plots (ggplot2 + EnhancedVolcano)
7. Runs GO enrichment and GSEA on the resulting gene list

## Key Results

**PCA plot** — samples cluster clearly by condition along the first principal component, confirming the Control and Patient groups are separable before trusting downstream DE results.

![PCA plot](figures/PCA.png)

**Heatmap** — expression patterns of the top significant genes across samples, clustered by both gene and sample, show consistent, condition-specific expression blocks.

![Heatmap](figures/Heatmap.png)

**Volcano plot** — combining fold change with statistical confidence reveals a clear pattern: down-regulated genes dominate, both in number and in significance, compared to a smaller, less pronounced set of up-regulated genes.

![Volcano plot](figures/Volcano-plot.png)

**GO enrichment** — functional enrichment of the significant gene set highlights the biological processes most associated with this expression signature.

![GO Analysis](figures/GO-Analysis.png)

Together, these results tell a consistent story: samples separate cleanly by condition, and the resulting differential expression signature is dominated by down-regulation, enriched for specific, interpretable biological processes.

## Files

- `rnaseq-dgea-recount3.Rmd` — full annotated analysis script
- `figures/` — exported plots referenced above

