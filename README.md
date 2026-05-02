#######scRNA-seq Analysis of GSE253865###########

Key Inferences from GSE147766 Neuroblastoma scRNA-seq Analysis

::Dataset Overview::
19 neuroblastoma tumor samples processed successfully
86,280 cells analyzed after quality filtering
Comprehensive pipeline: QC → normalization → PCA → UMAP → clustering → marker genes

::Quality Control Insights::
Cells filtered to ensure: 500-6,000 genes/cell, >1,000 total counts, <10% mitochondrial content
Data quality appears robust with expected distributions for high-quality scRNA-seq

::Cellular Heterogeneity Revealed::
Multiple distinct cell clusters identified via Leiden clustering
UMAP visualization shows clear separation of cell populations
Suggests neuroblastoma tumors contain diverse cell types/states beyond just malignant cells

::Sample-Specific Patterns::
PCA and UMAP by sample reveal both shared and unique cellular compositions across tumors
Some samples cluster together, others show distinct profiles
Indicates inter-tumor heterogeneity typical of cancer

::Biological Significance::
Marker gene analysis identifies cluster-specific signatures
Heatmap and dot plots show differentially expressed genes defining each cluster
Potential identification of: malignant neuroblastoma cells, stromal cells, immune infiltrates, 
endothelial cells.

::Clinical/Research Implications::
Tumor heterogeneity confirmed at single-cell level
Foundation for identifying therapeutic targets and biomarkers
Basis for understanding treatment resistance and disease progression
Data supports personalized medicine approaches for neuroblastoma

::Technical Success::
Pipeline successfully integrated 19 samples without major batch effects
All major scRNA-seq analysis steps completed: QC, clustering, visualization, DE analysis
Results provide comprehensive cellular atlas of neuroblastoma tumors

::Overall::
This analysis demonstrates the power of scRNA-seq to dissect tumor complexity, 
revealing that neuroblastoma is not a monolithic disease but comprises multiple cellular components 
that vary between patients.
This has direct implications for precision oncology and understanding tumor biology.
#################################################

This repository contains a complete, publication-ready single-cell RNA-seq workflow for GEO dataset GSE253865, 
adapted from the NBAtlas analytical framework.

## Contents
- Reproducible R pipeline for QC, integration, clustering, annotation, and visualization
- NBAtlas-style Figure Panels A–D
- Canonical marker dot plot across annotated cell types
- Output directory structure for downstream analyses
- Documentation for reproducibility and GitHub sharing

## Key Outputs
- Sample summary and QC metrics
- UMAP visualizations (dataset, assay, sample, cell type)
- Cell-type annotation tables
- Canonical marker dot plot
- Annotated Seurat object
- Cell-level metadata

## Citation
Please cite the original reference:
Cell Reports (2024), S2211-1247(24)01155-0.


================Data, Methods & Parameters=========
   
    
    Samples downloaded: KDP02, KDP06 (scRNA-seq); NBO001, NBO002, NBO004, NBO006 (snRNA-seq)
   
    
    Total raw barcodes: 72,652 across 6 samples
   
    
    QC thresholds: nFeature 500–6000, nCount 1000–50000, percent.mt < 10%
  
    
    After QC: 52,342 cells (72% retention)
   
    
    After downsampling: 21,000 cells (3500/sample)
 
    
    Normalization: LogNormalize, 2000 HVGs
 
    
    Dimensionality: PCA 30 PCs, UMAP dims 1:20

    
    Clustering: FindNeighbors + FindClusters, res=0.5 (21 clusters), res=0.8 (28 clusters)
 
    
    Annotation: AddModuleScore with NBAtlas 3-gene marker panels per cell type
  
    
    Seurat version: 5.5.0 (pipeline written for v4, minor compatibility fixes applied)
  
    
    UMAP: R-native UWOT (not Python umap-learn)


=======================

GSE253865_NBAtlas_scRNAseq/

├── README.md

├── LICENSE

├── CITATION.cff

├── acknowledgment.md

├── requirements/

│   ├── R_sessionInfo.txt

│   ├── conda_environment.yml

│   └── package_versions.md

├── input/

│   ├── GEO_GSE253865/   
                                        # raw 10x matrices or links
│   └── metadata/  
                                        # sample sheet, if any
├── code/

│   ├── 01_run_pipeline.R

│   ├── 02_make_figures.R

│   └── 03_export_pdf.R

├── output/

│   ├── figures/

│   ├── tables/

│   └── seurat_object/

└── docs/
    ├── study_description.md
    
    └── workflow_overview.md
   
    
====================
