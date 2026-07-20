# Population Stratification

## Objective

The objective of this step was to understand and control for **population stratification** in a Genome-Wide Association Study (GWAS). Population stratification occurs when individuals in a dataset belong to different ancestral populations, which can lead to false-positive associations.

---

## Why is Population Stratification Important?

In GWAS, allele frequencies can differ between populations due to ancestry rather than disease association. If this population structure is not corrected, a SNP may appear to be associated with a disease simply because it is more common in one ancestral group.

### Example

If most cases belong to one population and most controls belong to another population, allele frequency differences may reflect ancestry rather than the disease itself.

---

## Command 1: Download 1000 Genomes Reference Data

```bash
wget https://ftp.1000genomes.ebi.ac.uk/vol1/ftp/release/20100804/ALL.2of4intersection.20100804.genotypes.vcf.gz
```

### Why did I run this command?

I attempted to download the **1000 Genomes reference panel**, which is commonly used to compare the ancestry of study samples with known global populations.

### What does this command do?

* Downloads a large VCF file containing genotype data from individuals belonging to different ancestral populations.
* Provides a reference panel for population stratification analysis.

### Problem I Faced

The download file was approximately **60 GB**, and the estimated download time was around **19 hours**. Due to hardware and time limitations, I decided not to complete the full download.

### Decision Taken

Instead of forcing the download, I focused on understanding the **complete conceptual workflow** of population stratification.

---

## Command 2: Convert VCF to PLINK Format

```bash
plink --vcf ALL.2of4intersection.20100804.genotypes.vcf.gz --make-bed --out 1000G_data
```

### Why is this command used?

This command converts the downloaded VCF file into PLINK binary format (`.bed`, `.bim`, `.fam`) so that it can be processed using PLINK commands.

### What I learned

VCF files contain raw genotype information, while PLINK binary files are more efficient for GWAS analysis.

---

## Command 3: Extract Common SNPs

```bash
awk '{print $2}' founder_filtered_step5.bim > HapMap_SNPs.txt
plink --bfile 1000G_data --extract HapMap_SNPs.txt --make-bed --out 1000G_common
```

### Why is this command used?

This step identifies the SNPs that are present in both the study dataset and the 1000 Genomes reference dataset.

### What I learned

Only **common SNPs** can be compared or merged between two datasets.

---

## Command 4: Perform PCA/MDS

```bash
plink --bfile merged_data --cluster --mds-plot 10 --out MDS_results
```

### Why is this command used?

This command performs **Multidimensional Scaling (MDS)**, which is similar to Principal Component Analysis (PCA). It reduces the genetic data into a small number of dimensions that represent ancestry patterns.

### Output Generated

* `MDS_results.mds`

### What I learned

* Each individual receives coordinates such as **C1, C2, C3...**
* Individuals with similar ancestry cluster together in the MDS plot.
* The first few components can be used as **covariates** in logistic regression.

---

## Covariates File

The MDS coordinates are converted into a covariate file:

```bash
awk '{print $1, $2, $4, $5, $6, $7, $8, $9, $10, $11, $12, $13}' MDS_results.mds > covar_mds.txt
```

### Why is this file important?

The file `covar_mds.txt` stores the ancestry-related components (C1–C10). These components are included in logistic regression to adjust for population structure.

### What I learned

Without covariates, population differences could create **false disease associations**. Including MDS/PCA covariates helps ensure that the association test focuses on the SNP’s effect rather than ancestry differences.

---

## Key Concepts Learned

* Population stratification can bias GWAS results.
* The 1000 Genomes Project provides a reference panel for ancestry comparison.
* PCA/MDS identifies ancestry clusters in genetic data.
* Covariates derived from PCA/MDS are included in logistic regression to reduce false positives.
* Population stratification correction is an essential step before association analysis.

---

## Practical Note

In this project, I **did not complete the full 1000 Genomes download and PCA execution** due to computational limitations. However, I studied and documented the complete workflow, including data conversion, SNP matching, dataset merging, PCA/MDS generation, and covariate creation.

---

## Conclusion

This step helped me understand how ancestry differences can affect GWAS results and how PCA/MDS-based covariates are used to correct for population stratification before performing association analysis.
