# Heusler-Classifier
Classification of Heusler materials based on elemental descriptors
# README

The goal of this project was to use descriptors to categorise a compound as either a Heusler or not a Heusler compound.

## Dataset

The positives of Full Heusler and Half Heusler compound dataset were generated using matminer, a **Python library for data mining the properties of materials** by Hacking Materials Group. I used their `heusler_magnetic` dataset to get both Full Heusler and Half Heusler formulas. The negatives were extracted using the AFLOW API.

## Model

The classification models were developed using the **Random Forest (RF)** algorithm and evaluated using **20-fold cross-validation** to assess their predictive performance.

- Average cross-validated F1 score for Full-Heusler compounds: **0.967 ± 0.024**
- Average cross-validated F1 score for Half-Heusler compounds: **0.920 ± 0.048**

This was done using descriptors provided by the **"High-Throughput Machine-Learning-Driven Synthesis of Full-Heusler Compounds"** paper. These descriptors give information about the individual elements present in the compound and some tell us about their collective effect like total valence electron count and the difference between covalent radius of any pair of elements, etc. 

## Classification

Half Heuslers and Full Heuslers are two closely related families of intermetallic ternary compounds with remarkably versatile properties. They show phenomena like thermoelectrics, spintronics, superconductivity, shape-memory behaviour, topological insulator states, and heavy-Fermion physics, often with multiple functionalities coexisting in one compound.

They are classified based on their structure:
- **Half-Heuslers**: C1ᵦ structure (space group F̄43m, No. 216). Other configurations are also possible because of Jahn-Teller / Martensitic distortions but those were ignore.
- **Full Heuslers**: Cu₂MnAl-type L2₁ structure (space group Fm3̄m, No. 225) and D0₂₂ structure (space group I4/mmm, No. 139)

These reasons make it an interesting task to predict a compound to be Heusler or not simply based on elemental descriptors and not using structural parameters.

## Feature Importances

### Half Heuslers (ABC type)

Elements were positioned based on electronegativity, with the most electronegative being X.

| Feature | Importance |
|---------|------------|
| r_C | 0.183657 |
| t_p | 0.112389 |
| en_C | 0.106274 |
| g_C | 0.100739 |
| m_C | 0.086113 |
| m_A | 0.084922 |
| p_C | 0.048068 |
| p_A | 0.043632 |
| t_d | 0.038889 |
| r_AC | 0.035955 |
| m_B | 0.035255 |
| en_A | 0.030485 |
| p_B | 0.019330 |
| r_BC | 0.019104 |
| g_A | 0.018533 |
| t_all | 0.013821 |
| en_B | 0.007995 |
| r_AB | 0.006448 |
| r_B | 0.003544 |
| g_B | 0.002930 |
| r_A | 0.001646 |
| t_s | 0.000273 |

### Full Heuslers (AB₂C type)

| Feature | Importance |
|---------|------------|
| t_p | 0.177722 |
| r_B | 0.103108 |
| g_B | 0.090641 |
| m_C | 0.082489 |
| t_d | 0.078289 |
| m_B | 0.074284 |
| en_A | 0.067852 |
| p_C | 0.065982 |
| r_BC | 0.059979 |
| en_C | 0.042858 |
| g_C | 0.042776 |
| m_A | 0.027888 |
| en_B | 0.018426 |
| p_A | 0.016938 |
| g_A | 0.016450 |
| p_B | 0.010338 |
| r_C | 0.009090 |
| r_AB | 0.009084 |
| t_all | 0.002748 |
| r_AC | 0.002381 |
| r_A | 0.000489 |
| t_s | 0.000187 |

