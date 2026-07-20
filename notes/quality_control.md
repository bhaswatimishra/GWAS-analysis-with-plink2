# Part 2: Quality Control (QC)

## What is Quality Control?

Quality Control (QC) is the process of removing poor-quality samples and unreliable SNPs before performing GWAS.

In simple words, QC helps us clean the genetic data so that the final association results are more trustworthy.

---

## Why is QC important?

If poor-quality data is included in GWAS, it can create false associations.

QC helps to:

* Remove samples with too much missing data.
* Remove SNPs with too many missing genotypes.
* Remove very rare variants that may give unstable results.
* Remove SNPs that may have genotyping errors.
* Improve the reliability of GWAS results.

---

## Sample Missingness (--mind)

Some individuals may have many missing genotype calls.

Example:

* Sample A has 1% missing data → usually acceptable.
* Sample B has 10% missing data → may be removed.

A common threshold is:

* **--mind 0.02** → remove individuals with more than **2% missing genotype data**.

---

## SNP Missingness (--geno)

Some SNPs may be missing in many individuals.

Example:

* SNP1 is missing in 0.5% of samples → acceptable.
* SNP2 is missing in 15% of samples → may be removed.

A common threshold is:

* **--geno 0.02** → remove SNPs missing in more than **2% of individuals**.

---

## Minor Allele Frequency (MAF)

MAF means the frequency of the less common allele in a population.

Example:

* A allele frequency = 95%
* G allele frequency = 5%

Here, **MAF = 5%**.

Why filter rare variants?

Very rare variants may give unstable statistical results, especially when the sample size is small.

A common threshold is:

* **--maf 0.05** → keep SNPs with MAF greater than **5%**.

---

## Hardy-Weinberg Equilibrium (HWE)

HWE is a genetic principle that checks whether genotype frequencies are as expected in a population.

If a SNP strongly deviates from HWE, it may indicate:

* Genotyping error.
* Poor-quality SNP.
* Population structure.
* Selection.

A common threshold is:

* **--hwe 1e-6**

Usually, HWE filtering is applied mainly to **control samples**, because disease-associated SNPs in cases may naturally deviate from HWE.

---

## Heterozygosity Check

Heterozygosity measures how many heterozygous genotypes (like AG) an individual has.

* **Very high heterozygosity** may suggest contamination.
* **Very low heterozygosity** may suggest poor DNA quality or inbreeding.

Individuals with extreme heterozygosity values may be removed from the dataset.

---

## Sex Check

The sex check compares:

* The recorded sex of the individual.
* The genetic sex inferred from X chromosome data.

If they do not match, it may indicate:

* Sample mix-up.
* Incorrect sample annotation.
* Data quality issue.

---

## Relatedness Check

GWAS assumes that individuals are mostly **unrelated**.

Closely related individuals (siblings, parent-offspring, duplicates) can bias the results because their genotypes are not independent.

In PLINK2, relatedness is commonly checked using the **KING algorithm**.

---

## Typical QC Workflow

The usual QC order is:

1. Remove individuals with high missingness.
2. Remove SNPs with high missingness.
3. Remove rare SNPs using MAF filtering.
4. Remove SNPs failing HWE.
5. Check heterozygosity.
6. Check sex mismatch.
7. Remove closely related individuals.

---

