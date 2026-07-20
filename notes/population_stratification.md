# Part 4: Population Stratification

## What is population stratification?

Population stratification happens when individuals in a GWAS study come from different ancestral populations.

Different populations may naturally have different allele frequencies, even if the alleles are not related to the disease.

---

## Why is it a problem in GWAS?

GWAS compares allele frequencies between **cases** and **controls**.

If cases and controls belong to different ancestral groups, a SNP may appear associated with the disease simply because it is more common in one population.

This creates a **false-positive association**.

---

## Simple example

Imagine:

* Most cases are from Population A.
* Most controls are from Population B.
* A particular allele is naturally more common in Population A.

GWAS may incorrectly conclude that this allele is associated with the disease, when it is actually associated with **ancestry**, not the disease itself.

---

## What is the solution?

The main solution is to identify ancestry differences and correct for them using **PCA (Principal Component Analysis)** or **MDS (Multidimensional Scaling)**.

These methods summarize genetic variation into a few components that represent ancestry patterns.

---

## What is PCA/MDS?

PCA and MDS reduce large genetic datasets into a small number of dimensions.

Each individual gets coordinates such as:

* PC1 / C1
* PC2 / C2
* PC3 / C3

Individuals with similar ancestry cluster together in a PCA or MDS plot.

---

## What do the plots show?

* Individuals from the same ancestral group appear close together.
* Individuals from different populations appear in separate clusters.
* Outliers may represent individuals with different ancestry.

---

## What are covariates?

The PCA/MDS components are used as **covariates** in logistic regression.

They help adjust for ancestry differences between individuals.

For example, PC1, PC2, PC3, etc., can be included in the GWAS model.

---

## Why are covariates important?

Without covariates:

* Population differences can inflate p-values.
* False-positive associations may occur.
* GWAS results may be misleading.

With covariates:

* Ancestry effects are reduced.
* Association results become more reliable.
* The analysis focuses more on the SNP’s relationship with the disease.

---

## 1000 Genomes reference panel

The **1000 Genomes Project** contains genetic data from individuals belonging to different populations around the world.

It is commonly used as a **reference panel** to compare the ancestry of study samples.

Common population groups include:

* AFR = African
* EUR = European
* ASN = Asian
* AMR = American

---

## Key takeaway

Population stratification is one of the most important confounding factors in GWAS.

A SNP may appear disease-associated simply because of ancestry differences.

PCA/MDS and covariates help correct this problem, making GWAS results more accurate and trustworthy.
