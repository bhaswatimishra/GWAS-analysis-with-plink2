# GWAS Analysis with PLINK2

A documented implementation of a Genome-Wide Association Study (GWAS) workflow using **PLINK2**.

This repository documents my learning journey while implementing a standard GWAS pipeline using publicly available educational datasets. The project focuses on understanding each stage of a typical GWAS workflow, from genotype quality control to association analysis.

---

## Project Objectives

- Understand the complete GWAS workflow.
- Learn genotype quality control using PLINK2.
- Perform relatedness analysis using the KING algorithm.
- Study population stratification and its impact on association studies.
- Perform association testing and interpret GWAS results.

---

## Workflow

```text
Raw Genotype Data
        │
        ▼
Quality Control
        │
        ▼
Relatedness Analysis (KING)
        │
        ▼
Population Stratification
        │
        ▼
Association Testing
        │
        ▼
Multiple Testing
        │
        ▼
Manhattan Plot
        │
        ▼
QQ Plot
```

---

## Repository Structure

```
GWAS-analysis-with-plink2/
│
├── commands/
├── workflow/
└── notes/
```

---

## Topics Covered

- Sample Quality Control
- SNP Quality Control
- Minor Allele Frequency (MAF)
- Hardy-Weinberg Equilibrium (HWE)
- Relatedness Analysis (KING)
- Founder Filtering
- Population Stratification
- Logistic Association Analysis
- Multiple Testing Correction
- Manhattan Plot
- QQ Plot

---

## Software

- PLINK2
- Ubuntu (WSL)
- Bash
- Git
- GitHub

---

## Skills Demonstrated

- Linux
- Bash
- PLINK2
- Bioinformatics
- GWAS
- Population Genetics
- Quality Control
- Association Analysis

---

## Challenges

- Learned the differences between PLINK 1.9 and PLINK2 workflows.
- Relatedness analysis was performed using the KING algorithm.
- The complete 1000 Genomes integration was studied conceptually because of computational limitations.

---

## Future Work

- Complete PCA using the 1000 Genomes reference panel.
- Perform Polygenic Risk Score (PRS) analysis.
- Explore larger GWAS datasets.
