# Relatedness Analysis

## Objective

The objective of this step was to identify individuals in the dataset who were genetically related. In a Genome-Wide Association Study (GWAS), closely related individuals can bias association results because their genotypes are not independent.

---

## Why is Relatedness Analysis Important?

Related individuals may share large portions of their genome. If they are included in a case-control GWAS without correction, they can create false-positive associations or inflate the significance of results.

---

## Command 1: Keep Founder Samples

```bash
plink2 --bfile hardy_filtered_step1 --keep-founders --make-bed --out founder_filtered_step5
```

### Why did I run this command?

I ran this command to remove non-founder individuals (such as offspring) from the dataset. This helped simplify the relatedness analysis by focusing only on founder samples.

### What does this command do?

* Reads the input dataset: `hardy_filtered_step1`
* Keeps only founder individuals
* Creates a new filtered dataset in PLINK binary format

### Output Generated

* `founder_filtered_step5.bed`
* `founder_filtered_step5.bim`
* `founder_filtered_step5.fam`

### What I learned

Founder filtering removes individuals who have parents listed in the `.fam` file. In my dataset, this reduced the number of samples before performing relatedness analysis.

---

## Command 2: Calculate Relatedness Using KING

```bash
plink2 --bfile founder_filtered_step5 --make-king-table --out king_founders
```

### Why did I run this command?

I ran this command to calculate the genetic relatedness between all pairs of founder individuals in the dataset.

### What does this command do?

* Uses the KING algorithm to estimate kinship coefficients
* Compares each individual with every other individual
* Generates a table showing the degree of relatedness

### Output Generated

* `king_founders.kin0`

### Important Column

The most important column in the output file was:

* `KINSHIP`: indicates how closely two individuals are genetically related.

### What I learned

* A kinship value close to **0** indicates unrelated individuals.
* Higher kinship values suggest relatedness, such as siblings or parent-offspring relationships.
* The KING method is commonly used in PLINK2 for relatedness analysis.

---

## Command 3: Sort Kinship Results

```bash
sort -k8,8gr king_founders.kin0 | head
```

### Why did I run this command?

I ran this command to display the pairs of individuals with the highest kinship values first.

### What does this command do?

* `sort`: sorts the file
* `-k8,8`: sorts using the 8th column (`KINSHIP`)
* `g`: sorts numerically
* `r`: sorts in reverse order (highest to lowest)
* `head`: displays the top 10 results

### What I learned

This command helped me quickly identify the most closely related sample pairs in the dataset.
---

## Key Learning

* Relatedness analysis is essential to identify genetically related individuals.
* Founder filtering should be performed before relatedness analysis when appropriate.
* PLINK2 uses the KING algorithm instead of the older `--genome` command.
* The `KINSHIP` value helps determine whether individuals are unrelated or closely related.

---

## Conclusion

In this step, I successfully performed relatedness analysis using the KING algorithm in PLINK2. I also learned how to identify related sample pairs and how to adapt an older PLINK1.9 tutorial workflow to PLINK2.
