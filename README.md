# QSPR Solubility Predictor

A computational chemistry project to predict the aqueous solubility ($logS$) of molecules directly from their SMILES strings using machine learning and cheminformatics.

## Project Overview
Instead of using a pre-calculated dataset, I built a feature extraction workflow from scratch. The code takes raw SMILES representations from the Delaney dataset and uses **RDKit** to calculate six key molecular descriptors:
* LogP (Octanol-Water Partition Coefficient)
* Molecular Weight
* Number of H-Donors
* Number of H-Acceptors
* Number of Rotatable Bonds
* Ring Counts

After extracting the features, I trained a regression model to map these structural properties to their experimental solubility values.

## Key Findings
Chemical thermodynamics holds up in the data: **LogP** completely dominates the prediction accuracy. The hydrophobicity/lipophilicity ratio is the primary barrier to a molecule dissolving in water. Molecular size (weight) comes in second, while the other descriptors act as minor fine-tuning parameters for the model.

## Repository Files
* solubility.ipynb: The main notebook containing the complete workflow (data fetching -> RDKit extraction -> model training).
* solubility_rf_model.pkl: The saved predictive model.

## Future Plans
Currently, the model relies purely on 2D structural descriptors. I plan to incorporate parameters derived from **Density Functional Theory (DFT)** and **Molecular Docking** later to capture deeper electronic and binding effects.
