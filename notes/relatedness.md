# Part 3: Relatedness Analysis (KING)

## What is relatedness?

Relatedness means how genetically similar two individuals are. Two unrelated people may share some DNA by chance, but closely related individuals share a much larger portion of their genome because they inherited DNA from common ancestors.

---

## Why is relatedness important in GWAS?

GWAS assumes that each individual contributes **independent genetic information**.

If closely related individuals are included in the study:

* Their shared DNA can make some SNPs appear falsely associated with the disease.
* P-values may become artificially significant.
* The study may report **false-positive associations**.

Therefore, related individuals are usually identified and one individual from each closely related pair is removed.

---

## Founder and non-founder

A **founder** is an individual whose parents are not listed in the dataset.

A **non-founder** is an individual whose parents are listed in the dataset, meaning they are offspring within the study.

Before relatedness analysis, researchers often keep only founders because they are more likely to represent independent ancestral samples.

---

## What is the KING algorithm?

KING is a method used to estimate **genetic relatedness** between individuals.

It compares pairs of individuals and calculates a **kinship coefficient**, which measures how closely they are related.

PLINK2 commonly uses KING for relatedness analysis instead of the older PI-HAT method used in some PLINK1.9 workflows.

---

## What is a kinship coefficient?

The **kinship coefficient** tells us the degree of genetic relationship between two individuals.

| Kinship value | Relationship                                      |
| ------------- | ------------------------------------------------- |
| Close to 0    | Unrelated individuals                             |
| Around 0.044  | Third-degree relatives                            |
| Around 0.088  | Second-degree relatives                           |
| Around 0.177  | First-degree relatives (siblings or parent-child) |
| Around 0.354  | Duplicate samples or identical twins              |

---

## How do we interpret kinship values?

* A value **close to 0** suggests that two individuals are likely unrelated.
* A value around **0.177** suggests a first-degree relationship.
* A value above **0.177** indicates that the individuals are likely closely related.
* A value around **0.354** may indicate duplicate samples or identical twins.

---


## Why remove related individuals?

Removing closely related individuals helps ensure that:

* Each sample contributes independent genetic information.
* Association results are not biased by shared family DNA.
* P-values are more reliable.
* The final GWAS results are more trustworthy.

