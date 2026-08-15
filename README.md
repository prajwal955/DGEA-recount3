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

This is a dataset containing approximate mRNA counts obtained from dermal epithelial cells of 6 healthy individuals and 4 diabetes-affected individuals.

**PCA plot** 

The PCA plot displays a clear clustering of samples based on condition (healthy (Ctrl) vs diseased (Pat)).

![PCA plot](figures/PCA.png)

**Heatmap** 

The heatmap displays that the control samples have a varied, but consistently higher gene expression than the diseased samples. These genes were the top twenty genes filtered out based on significance.

![Heatmap](figures/Heatmap.png)

**Volcano plot** 

The volcano plot displays a clear trend of down-regulation occupying the differential gene expression of this dataset with most of the significant genes leaning towards the negative log2FC quadrant.

![Volcano plot](figures/Volcano-plot.png)

**GO enrichment** 

The GO enrichment analysis of down-regulated genes shows that the majority of the significant genes are involved in skin cell growth, differentiation, and wound healing. The down-regulation of genes involved in such biological processes leads to the interpretation that the wound healing process is affected due to decreased expression of these genes, which in turn leads to the delay in healing of wounds in a diabetic patient compared to a healthy individual.

![GO Analysis](figures/GO-Analysis.png)


## Files

- `rnaseq-dgea-recount3.Rmd` — full annotated analysis script
- `figures/` — exported plots referenced above

> **Note:** This script is written for the specific dataset and comparison described above (recount3 project SRP095512, Ctrl vs Pat), but the workflow is general-purpose. Please feel free to fork and adapt it, for example, swap in a different recount3 project ID, adjust the significance thresholds, or change the comparison groups to fit your own dataset.

