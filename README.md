# TCGA-CESC Survival Analysis

Survival analysis of cervical cancer (TCGA-CESC) using gene expression data 
and the Cox Proportional Hazards model.

## Overview
Analyzed RNA-seq gene expression from 292 TCGA cervical cancer patients 
(matched with curated survival outcomes) to identify genes associated with 
overall survival.

## Methods
- **Data**: UCSC Xena (TCGA-CESC gene expression, n=308) + cBioPortal 
  curated clinical/survival data (TCGA PanCancer Atlas, n=297)
- **Genes analyzed**: TP53, PIK3CA, EGFR, VEGFA, MKI67 (selected from 
  cervical cancer literature)
- **Methods**: Kaplan-Meier survival curves with log-rank tests; 
  multivariate Cox Proportional Hazards regression (lifelines library)

## Key Results
- **VEGFA expression significantly predicts survival** (log-rank p=0.008; 
  Cox HR=1.54, 95% CI 1.19–2.01, p<0.005) — higher VEGFA expression is 
  associated with worse overall survival, consistent with its known role 
  in tumor angiogenesis.
- EGFR showed a borderline association (Cox HR=1.21, p=0.05).
- TP53, PIK3CA, and MKI67 were not significantly associated with survival 
  in this cohort.
- Full 5-gene Cox model: concordance index = 0.65, log-likelihood ratio 
  test p<0.005 — the model has meaningful predictive value over chance.

![VEGFA KM Plot](VEGFA_km_plot.png)
![Cox Forest Plot](cox_forest_plot.png)

## How to run
Open `cesc_survival_analysis.ipynb` in Google Colab and run all cells.
Requires the `lifelines` package: `!pip install lifelines`

## Data sources
- Gene expression: [UCSC Xena TCGA-CESC](https://xenabrowser.net/datapages/?dataset=TCGA.CESC.sampleMap%2FHiSeqV2&host=https%3A%2F%2Ftcga.xenahubs.net)
- Survival data: [cBioPortal - Cervical Squamous Cell Carcinoma (TCGA, PanCancer Atlas)](https://www.cbioportal.org/study/summary?id=cesc_tcga_pan_can_atlas_2018)
