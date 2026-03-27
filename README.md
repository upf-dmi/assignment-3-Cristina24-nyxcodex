# Hands-on III – Machine Learning for COVID-19 Severity Prediction

This repository contains the advanced computational analysis for Hands-on III. The project focuses on building, validating, and interpreting a Random Forest classification model to distinguish between non-Severe and Severe COVID-19 patients based on high-dimensional proteomic profiles.

The analysis follows the methodology of the seminal publication:

Proteomic and Metabolomic Characterization of COVID-19 Patient Sera

Shen et al., Cell (2020)

## Report Summary

The full analysis report is available here:

➡ Hands_on_III.html

The report details a complete machine learning workflow:

### 1. Model Development & Validation

```         
Data Preparation: Cleaning the protein matrix, performing log2 normalization, and implementing Minimum Value Imputation (MVI) to handle proteins below the detection limit.

Training: Implementing a Random Forest model using 10-fold cross-validation optimized for the Area Under the ROC Curve (AUC).

Performance: The model achieved a robust AUC of 0.953 on the training cohort.

Overfitting Check: A Label Permutation Test (shuffling group labels) confirmed the model's predictive power is derived from genuine biological signals rather than random noise, as the permuted AUC dropped to ~0.558.
```

### 2. Feature Importance & Biological Interpretation

The analysis identified the top 25 protein biomarkers driving the classification:

```         
Top Features: Dominated by inflammatory and acute-phase reactants such as Albumin (ALB), SAA1, SAA2, and CRP.

Vascular Markers: Significant contribution from markers of coagulation stress like Coagulation Factor V.

Validation: 14 of the top 25 features overlapped with the authors' original biomarkers in Supplementary Table 5, confirming a highly stable biological signature.
```

3.  External Prediction (Independent Cohort)

The model was tested on an independent cohort (n=10) to assess generalizability:

```         
Performance: Achieved an AUC of 0.792, maintaining meaningful discriminatory power.

Challenges: Strict classification accuracy was low (0.40) due to systematic baseline shifts between cohorts, highlighting the critical need for cross-cohort normalization in clinical settings.
```

## Reproduce the Analysis

To reproduce the Random Forest model and performance metrics, follow these steps:

```         
Open the R Project: Launch Hands_on_III.Rmd in RStudio.

Required Data: Ensure the following files are in the data/ folder:

    patient_metadata_exported.rds

    raw_data/Protein_matrix.xlsx

    raw_data/table_s4.xlsx (Independent test cohort)

    raw_data/table_s5.xlsx (Author biomarkers)

Run All Chunks: The script will automatically perform data cleaning, training, and evaluation.
```

## Authors

Cristina Torredemer Ortega ([cristina.torredemer01\@estudiant.upf.edu](mailto:cristina.torredemer01@estudiant.upf.edu){.email})
