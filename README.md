# Profiling of Circular RNAs in OSCC Using a Bioinformatics Pipeline
## Project Overview
This study builds a complete bioinformatics pipeline to detect, quantify and functionally annotate circular RNAs (circRNAs) in oral squamous cell carcinoma (OSCC), using 39 paired tumor and normal tissue RNA-seq samples from the NCBI SRA database.
## Background
Oral squamous cell carcinoma (OSCC) accounts for over 90% of oral cancers and has a poor prognosis due to late detection. Circular RNAs (circRNAs) are a class of covalently closed non-coding RNAs that are highly stable and tissue-specific — making them ideal candidates as non-invasive biomarkers.This project uses CIRI2 and CIRIquant to profile circRNA expression differences between OSCC tumor and matched normal tissue.
## Objective of the study
- To identify and profile circular RNAs in OSCC.
- To construct a bioinformatics pipeline for circRNA analysis.
- To explore differential expression and potential biological function.
## Pipeline used for the analysis of circRNA
```
NCBI SRA Database
      │
39 paired RNA-seq samples
      │  
    FastQC                  ── Raw read quality control
      │
  Trim Galore             ── Adapter removal and quality trimming
      │
    CIRI2                   ── circRNA detection 
      │
  CIRIquant               ── circRNA expression quantification
      │
   edgeR                  ── Differential expression analysis
      │
      ├──► Volcano plots  ── Visualise DE circRNAs
      │
      └──► GO & KEGG      ── Functional enrichment analysis
```
 ## Methodology
- Expression profiling datasets obtained from SRA(Sequence Read Archive) (NCBI).
- Total of 39 samples were used in which 22 were OSCC(tumor) samples and 17 were of normal tissue
  samples.
- All datasets sequenced on ILLUMINA platforms and comprised of paired end reads.Samples downloaded using SRA toolkit.
- Converted to FASTQ format using fastq-dump utility for paired end reads. Quality control-
Used FastQC (v0.11.9) to evaluate raw FASTQ files.
- Removed adapter sequences and low-quality bases using Trim Galore (v0.6.10)
- Preprocessed reads used for accurate alignment and circRNA detection.
- Reference Preparation Index reference genome (hg19)using BWA.
- RNA-Seq reads were aligned to the reference genome using BWA-MEM, which is recommended for circRNA detection with CIRI2.
- CIRI2(v2.0.6)- a computational tool made to detect circular RNAs by identifying back-splice junctions.
- The resulting aligned SAM files were used as input for CIRI2 to identify circRNA candidates.
- CIRIquant was applied to quantify circRNA expression levels across OSCC and normal samples.
- Normalised circRNA expression matrix
- Differential Expression Analysis using edgeR (R/Bioconductor) comparing OSCC tumor vs matched normal tissue.
- Output- Table of significantly differentially expressed circRNAs.
- DEGs analysis identified 29circRNAs as significantly dysregulated between OSCC and normal tissues with (log2FC > 1, FDR < 0.05), of which 8 were upregulated and 21 were downregulated.
- After circRNA quantification using CIRIquant, downstream analyses were performed to interpret the biological significance of differentially expressed circRNAs.
- These differentialy expressed circRNA then used in functional enrichment analysis using GO (Gene Ontology) and KEGG (Kyoto Encyclopedia of Genes and Genomes) .Enrichment analyses were performed using Galaxy web platform.
- Volcano plots: Display DE circRNAs with significance and fold-change axes. Upregulated and downregulated circRNAs annotated

## Key findings
- Successfully detected and quantified circRNAs across 39 paired OSCC samples
- Identified differentially expressed circRNAs between tumor and normal tissue
- GO and KEGG enrichment highlighted OSCC-associated signalling pathways
- Results support the potential of specific circRNAs as OSCC biomarkers










