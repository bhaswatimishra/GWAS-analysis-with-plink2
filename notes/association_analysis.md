# Part 5: Association Analysis, p-value, and Odds Ratio

## What is association analysis?

Association analysis is the main step of GWAS where we test whether a SNP is associated with a disease or trait.

It compares the allele frequencies between:

* Cases = people with the disease
* Controls = people without the disease

If an allele is much more common in cases than in controls, it may be associated with the disease.

---

## What is a p-value?

A p-value tells us how likely it is to observe the result by chance if there is actually no real association between the SNP and the disease.

### Simple meaning

* A small p-value means the result is unlikely to be due to chance.
* A large p-value means the result could easily happen by chance.

### Important point

A small p-value does not prove that the SNP causes the disease. It only suggests that the SNP is statistically associated with the disease.

---

## What is an Odds Ratio (OR)?

The Odds Ratio tells us whether an allele increases or decreases disease risk.

| OR value | Meaning                              |
| -------- | ------------------------------------ |
| OR > 1   | The allele may increase disease risk |
| OR < 1   | The allele may be protective         |
| OR = 1   | No association with disease risk     |

### Example

* OR = 2 → about 2 times higher odds of disease.
* OR = 0.5 → about 50% lower odds of disease.
* OR = 1 → no effect on disease risk.

---

## Difference between p-value and OR

| p-value                                                    | Odds Ratio (OR)                                     |
| ---------------------------------------------------------- | --------------------------------------------------- |
| Shows whether the association is statistically significant | Shows the direction and strength of the association |
| Small p-value = stronger evidence                          | OR > 1 = risk, OR < 1 = protection                  |

---

## What is logistic regression?

Logistic regression is used in GWAS for binary traits, such as case/control studies.

It tests whether a SNP is associated with disease status while adjusting for other factors called covariates.

---

## Why are covariates important?

Covariates help correct for confounding factors such as:

* Population stratification
* Sex
* Age
* Batch effects

In GWAS, PCA/MDS components are often used as covariates to adjust for ancestry differences.

