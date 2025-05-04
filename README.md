# ASAP-polaris-blind-challenge-Ligand-ADMET-property-prediction-

## Problem Statement
Project focuses on predicting ADMET (Absorption, Distribution, Metabolism, Excretion, and Toxicity) properties of drug-like molecules. These properties play a crucial role in determining a drug’s efficacy and safety. By leveraging machine learning, we aim to enhance the prediction accuracy of pharmacokinetic properties, aiding in early-stage drug discovery.

# Data Set:
Absorption, Distribution, Metabolism, Excretion, Toxicology - or ADMET - endpoints sit in the middle of the assay cascade and can make or break preclinical candidate molecules. For this blind challenge we selected several crucial endpoints for the community to predict:

**Mouse Liver Microsomal stability (MLM, protocol)**: This is a stability assay that tests how quickly a molecule gets broken down by mouse liver microsomes. This is a useful assay that can be used as an estimate on how long a molecule will reside in the mouse body before it gets cleared.

**Human Liver Microsomal stability (HLM, protocol):** This is a stability assay that tests how quickly a molecule gets broken down by human liver microsomes. This is a useful assay that can be used as an estimate on how long a molecule will reside in the human body before it gets cleared.

**Solubility (KSOL, protocol):** solubility is essential for drug molecules: this heavily affects the pharmacokinetic and dynamics ('PKPD') of the molecule in the human body.

**LogD (protocol):** like solubility - but then in fatty tissue - LogD is a measure of a molecule's lipophilicity, or how well it dissolves in fat. LogD is calculated by comparing a molecule's solubility in octanol, a fat-like substance, to its solubility in water.

**Cell permeation (MDR1-MDCKII, protocol):** MDCKII-MDR1 is a cell line that's used to model cell permeation i.e. how well drug compounds will permeate cell layers. For coronaviruses this is a critical endpoint because there is increasing evidence that afflictions such as long-covid are caused by (remnant) virus particles in the brain, and blood-brain-barrier (BBB) permeation is critical for drug candidates to reach the brain.
![Image Alt](https://github.com/haleemiliyash/ASAP-polaris-blind-challenge-Ligand-ADMET-property-prediction-/blob/main/data%20set%20detail.png?raw=true)

## Libraries Used:

* Seaborn
* Pandas
* Numpy 
* Random forest Regression
* Json
* Sklearn

## Approach:
1. Dataset Description:

 The raw training dataset contained 434 entries and 6 columns, with CxSmiles as the only feature and five target endpoints:

  * LogD
  * MDR1-MDCKII
  * HLM (Human Liver Microsomes)
  * MLM (Mouse Liver Microsomes)
  * KSOL (Solubility)
  The dataset had several missing values (NaNs) in the target columns.

2. Missing Value Handling:
  To address missing values, Tanimoto similarity was used between RDKit fingerprints. The values for missing endpoints were filled based on the most similar compounds' fingerprints.

3. Feature Engineering:
  Initially, only one feature (CxSmiles) was available, which could limit model performance. To enhance the feature set and improve accuracy, Lipinski Descriptors were extracted using RDKit:

  * Molecular weight (MolWt)
  * Octanol-water partition coefficient (LogP)
  * Hydrogen bond donors (NumHDonors)
  * Hydrogen bond acceptors (NumHAcceptors)
  This expanded the feature set to:
  * CxSmiles
  * MolWt
  * LogP
  * NumHDonors
  * NumHAcceptors
4. Models Used for Prediction:
  The following regression models were trained and evaluated:
  * Linear Regression
  * Decision Tree Regression
  * Random Forest Regression
  * Gradient Boosting Regression
  * XGBoost Regression
5. Model Evaluation Metrics:
  The models were evaluated using:
  * R² Score (Coefficient of Determination)
  * Mean Absolute Error (MAE)
  * Mean Squared Error (MSE)
6. Best Model Performance:

  Among all models, XG Boost Regression provided the best results, achieving the highest R² score and the lowest MAE and MSE, indicating superior predictive performance.


  Overview of Model Evaluation matrix
![image](https://github.com/user-attachments/assets/0a997d7b-b5af-4495-b230-a4c71686b6eb)


