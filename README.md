# ImmunoWES: An Integrated Pipeline for Somatic Mutation and HLA Analysis in Precision Oncology 

## Overview
This repository provides a comprehensive analysis workflow that integrates whole-exome sequencing (WES) data with HLA genotyping information. The aim is to explore how somatic mutations interact with the human leukocyte antigen (HLA) system to influence immune-mediated disease progression and clinical outcomes.

Unlike traditional WES analyses that focus solely on mutation detection, our pipeline adds immunogenetic context by incorporating HLA class I and II alleles, mutation–HLA binding affinity prediction, HLA evolutionary divergence (HED) scoring, and survival analysis.

**Note: File paths in scripts are environment-specific. Please modify them according to your local server configuration.**

## Workflow Structure
The project includes the following key modules:

### 1. /scripts/Exome_upstream_analysis/
Performs quality control, alignment, duplicate removal, BQSR, and variant calling.

Outputs somatic variant VCF files.

Key tools: FastQC (v0.12.1), MultiQC (v1.19), BWA-MEM (v0.7.17), SAMtools (v1.9), Picard (v2.18.23), GATK (v4.0.4.0)

### 2. /scripts/HLA_analysis/
HLA typing using HLA-HD (v1.7.0) from FASTQ files.

Extracts mutation-derived peptides.

Predicts binding affinities using MixMHC2pred for HLA-II alleles.

### 3. /scripts/HLA_HED/
Calculates HLA evolutionary divergence (HED) scores.

Quantifies the sequence divergence between HLA alleles per individual.

### 4. /scripts/Mutation_analysis/
Converts VCF to MAF format using Annovar + maftools.

Calculates tumor mutation burden (TMB).

Performs GO and KEGG pathway enrichment based on mutated genes.

### 5. /scripts/cox/
Integrates mutation immunogenicity scores, binding affinities, and HED.

## Dataset
Project Accession: [SRP043661](https://www.ncbi.nlm.nih.gov/sra/?term=SRP043661)


## Abstract
Whole-exome sequencing (WES), owing to its efficiency in identifying mutations within protein-coding regions, has emerged as a powerful tool for elucidating the molecular mechanisms underlying immune-mediated diseases and related conditions. Nevertheless, most current studies primarily focus on the mutation profiling of WES data, often neglecting the potential influence of the human leukocyte antigen (HLA) system—a central component of immune regulation. The interaction between somatic mutations and HLA genotypes remains insufficiently characterized, limiting our understanding of immune-driven disease processes and clinical outcomes.

To refine this understanding, we propose a comprehensive integrative analytical framework that combines WES data with high-resolution HLA typing derived from raw FASTQ sequences. This pipeline includes upstream WES processing, somatic mutation detection, HLA genotyping, prediction of mutation–HLA binding affinity, assessment of HLA evolutionary divergence, and correlation with clinical prognosis. Kaplan–Meier survival analysis demonstrates that incorporating mutation–HLA binding affinity provides additional insights into immune-mediated disease progression and prognostic evaluation.

We anticipate that this framework will support researchers in identifying immune-related mutations that are potentially associated with immune-mediated disease outcomes.

## Dependencies
The pipeline requires the following software versions:

FastQC v0.12.1

MultiQC v1.19

BWA-MEM v0.7.17

SAMtools v1.9

Picard v2.18.23

GATK v4.0.4.0

HLA-HD v1.7.0

Annovar

maftools(2.20.0)

clusterProfiler

MixMHC2pred

MHCflurry

R 4.1+ with required packages (org.Hs.eg.db, enrichplot, etc.)

## Contact
For questions or contributions, please contact:

Name: [Qingzhen Hou]

Email: [houqingzhen@sdu.edu.cn]

Institution: [Department of Biostatistics, School of Public Health, Cheeloo College of Medicine,
 Shandong University, Jinan, 250012, Shandong, China.]
