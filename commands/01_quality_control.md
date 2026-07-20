# Quality Control

## Objective

Remove low-quality samples and SNPs before GWAS.

---

## Command 1

```bash
plink2 --bfile HapMap_3_r3_1 --missing --out missingness
```

### Why did I run this?

To calculate the proportion of missing genotypes for every individual and every SNP.

### Output

- missingness.vmiss
- missingness.smiss

### What did I learn?

This command does **not remove** data.

It only calculates missing genotype statistics.

---

## Command 2

```bash
plink2 --bfile HapMap_3_r3_1 --mind 0.02 --make-bed --out step1
```

### Why?

Individuals with excessive missing genotypes may introduce unreliable results.

### What does it do?

Removes samples with more than **2% missing genotype data**.

### Output

A filtered dataset containing only higher-quality individuals.

---

## Challenges

No issues encountered.
