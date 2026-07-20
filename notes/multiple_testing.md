# Part 6: Multiple Testing, Manhattan Plot, QQ Plot, and LD

## Why is multiple testing a problem?

In GWAS, we test **hundreds of thousands to millions of SNPs** at the same time.

If we use the normal significance threshold of **0.05**, many SNPs may appear significant just by chance, even when they are not truly associated with the disease.

This is called a **false-positive association**.

---

## Bonferroni correction

Bonferroni correction makes the p-value threshold much stricter to reduce false positives.

### Formula

```text
Corrected threshold = 0.05 / number of SNPs tested
```

### Example

If **1,000,000 SNPs** are tested:

```text
0.05 / 1,000,000 = 5 × 10⁻⁸
```

So, in GWAS, a SNP is usually considered **genome-wide significant** if:

```text
p < 5 × 10⁻⁸
```

---

## What is a Manhattan plot?

A Manhattan plot is a graph used to visualize GWAS results across the genome.

### What does it show?

* **X-axis:** chromosome number and genomic position.
* **Y-axis:** `-log10(p-value)`.

Each dot represents one SNP.

### Why use -log10(p-value)?

Very small p-values are difficult to visualize directly. Converting them to **-log10(p-value)** makes significant SNPs appear as high peaks.

Example:

| p-value  | -log10(p-value) |
| -------- | --------------- |
| 0.01     | 2               |
| 0.001    | 3               |
| 5 × 10⁻⁸ | ~7.3            |

---

## How to interpret a Manhattan plot

* Higher dots mean **smaller p-values** and stronger evidence of association.
* A horizontal line around **7.3** represents the genome-wide significance threshold (`5 × 10⁻⁸`).
* A cluster of high dots forms a **peak**, which represents an associated genomic region (locus).

### Important point

A Manhattan plot peak does **not** prove that the highest SNP is the causal variant. It only shows that the region is associated with the disease.

---

## What is a QQ plot?

QQ (Quantile-Quantile) plot compares the **expected p-value distribution** with the **observed p-value distribution**.

### How to interpret it

* If most points lie on the diagonal line, the GWAS results are well calibrated.
* If only the last few points rise above the line, it may indicate genuine associated SNPs.
* If the whole curve rises above the line, it may indicate population stratification, relatedness, or other confounding factors.

---

## What is genomic inflation?

Genomic inflation means that p-values are systematically smaller than expected, often due to confounding factors.

It is measured using the **Genomic Inflation Factor (λGC)**.

* **λGC ≈ 1:** well-calibrated GWAS results.
* **λGC > 1:** possible inflation due to population structure or relatedness.

---

## What is Linkage Disequilibrium (LD)?

Linkage Disequilibrium means that nearby SNPs are often inherited together.

If one SNP is truly associated with a disease, nearby SNPs in the same LD block may also appear significant, even if they are not the causal variant.

### Why is LD important?

LD explains why a Manhattan plot often shows a **cluster of significant SNPs** instead of just one single SNP.

---

## Association vs causation

This is one of the most important concepts in GWAS.

* **Association:** a SNP is statistically linked to the disease.
* **Causation:** a SNP directly causes the disease.

GWAS usually identifies **associated loci**, not the exact causal gene or variant.

Further biological experiments are needed to prove causation.

---

