# Association Analysis – Conceptual Notes

## Purpose

This document summarizes the concepts of GWAS association analysis that I studied while learning the overall GWAS workflow. The commands mentioned in this section are included for understanding the standard analysis pipeline and should not be interpreted as completed execution steps.

---

## Basic Association Test

In GWAS, the simplest association test compares allele frequencies between **cases** and **controls** for each SNP.

### Example Command

```bash
plink --bfile dataset --assoc --out assoc_results
```

### What I understood

* This command performs a basic SNP-wise association test.
* It compares allele frequencies between affected and unaffected individuals.
* It generates a p-value for each SNP.
* However, it does **not** adjust for population stratification or other covariates.

---

## Logistic Regression

For binary traits (case/control studies), logistic regression is commonly used because it can include covariates such as PCA or MDS components.

### Example Command

```bash
plink --bfile dataset --covar covar_mds.txt --logistic --hide-covar --out logistic_results
```

### What I understood

* Logistic regression tests whether a SNP is associated with disease status.
* Covariates help adjust for population stratification.
* The `--hide-covar` option hides the covariate results and displays only SNP association results.

---

## Odds Ratio (OR)

The Odds Ratio indicates whether an allele increases or decreases disease risk.

* **OR > 1** → The allele may increase disease risk.
* **OR < 1** → The allele may be protective.
* **OR = 1** → No association with disease risk.

### Example

If a SNP has **OR = 0.42**, it suggests that the allele may have a protective effect against the disease.

---

## P-value and Sample Size

I understood that the p-value depends on:

* The difference in allele frequencies between cases and controls.
* The sample size of the study.

A very small difference may become statistically significant if the sample size is very large, while a larger difference may not be significant in a very small dataset.

---

## Multiple Testing Correction

GWAS tests a very large number of SNPs simultaneously. If a normal threshold of **p < 0.05** is used, many false-positive results may occur by chance.

### Bonferroni Correction

The Bonferroni threshold is calculated as:

```text
0.05 / number of SNPs tested
```

For approximately **1,000,000 SNPs**, the commonly used genome-wide significance threshold is:

```text
5 × 10⁻⁸
```

---

## Manhattan Plot

A Manhattan plot visualizes GWAS association results across the genome.

### What I understood

* **X-axis** represents chromosome number and genomic position.
* **Y-axis** represents `-log10(p-value)`.
* Each dot represents a single SNP.
* Higher dots indicate smaller p-values and stronger evidence of association.

I also understood that a Manhattan plot peak usually represents an **associated genomic region (locus)**, not necessarily the exact causal SNP, because nearby SNPs may be in **linkage disequilibrium (LD)**.

---

## QQ Plot

A QQ plot compares the **expected** p-value distribution with the **observed** p-value distribution.

### What I understood

* If most points lie on the diagonal line, the GWAS results are generally well calibrated.
* If only the last few points deviate upward, it may indicate genuine associated SNPs.
* If the entire curve deviates upward, it may indicate population stratification, relatedness, or other confounding factors.

---

## Important Insight

A statistically significant association does **not** prove that a SNP is the causal variant. GWAS identifies **associated loci**, and further biological validation is required to determine the true causal gene or variant.

---

## My Learning Summary

From this step, I understood:

* The difference between a basic association test and logistic regression.
* The meaning of Odds Ratio (OR).
* How p-values are interpreted in GWAS.
* Why multiple testing correction is necessary.
* How Manhattan and QQ plots are interpreted.
* Why association does not always mean causation.
