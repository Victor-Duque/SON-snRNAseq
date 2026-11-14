# snRNA-seq of the rat supraoptic nucleus after water deprivation

Analysis code for the single-nucleus RNA-seq study of the rat supraoptic nucleus (SON) in control and water-deprived (WD) animals (n = 5 per group).

## Contents

- `SON_snRNAseq_analysis.qmd`: full analysis, from alignment and QC to every figure and supplementary table.
- `sessionInfo.txt`: R and package versions used.

## Pipeline

1. Alignment with Cell Ranger 10.1.0 (mRatBN7.2) and ambient RNA removal with CellBender 0.3.2 (bash chunks at the top of the script).
2. QC, integration (RPCA) and clustering in Seurat 5, followed by MCN subclustering.
3. Markers and WD effect (MAST, with pseudobulk edgeR confirmation), enrichment (clusterProfiler, ReactomePA), cell type proportions (propeller).
4. Cell–cell communication (CellChat), co-expression networks (hdWGCNA), predicted neuronal activity (NEUROeSTIMator) and trajectories (monocle3).

## Running

Open the project folder as the working directory and run the chunks in order. The script expects this layout:

```
CellBender/   Son_1_filtered.h5 ... Son_10_filtered.h5
Data/         IUPHAR.xlsx (IUPHAR/BPS target classes plus transcription factors)
Fisiologico/  degs.xlsx (bulk RNA-seq of the SON, Pauža et al. 2021)
Excel/        BulkProteomics.xlsx (SON proteome and phosphoproteome, Bárez-López et al. 2023)
```

`RDS/`, `Excel/` and `Figures/` are filled by the script. NEUROeSTIMator runs in a separate conda environment through WSL (see the NeuroEstimator chunks).

## Data

Raw data and the processed Seurat objects are available at GEO (accession to be added).

## Citation

Duque VJ et al. Single-nucleus transcriptomics of the supraoptic nucleus reveals magnocellular neuron subtypes and a Giot1-centred response to water deprivation (in preparation).
