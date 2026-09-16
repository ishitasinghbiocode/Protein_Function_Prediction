# Dataset Information

## Data Source

Protein sequences were obtained from the UniProtKB/Swiss-Prot reviewed protein database using the UniProt REST API.

## Dataset Construction

The dataset was constructed using reviewed protein entries belonging to four top-level Enzyme Commission (EC) functional classes:

- EC1: Oxidoreductases
- EC2: Transferases
- EC3: Hydrolases
- EC4: Lyases

Proteins were restricted to sequences with lengths between 100 and 500 amino acids.

## Final Dataset

After quality control and removal of duplicate entries and one sequence containing the non-standard amino acid residue U (selenocysteine), the final dataset contained:

- 192 protein sequences
- 4 functional classes

### Class Distribution

| Functional Class | Number of Proteins |
|---|---:|
| Oxidoreductases | 49 |
| Lyases | 49 |
| Transferases | 47 |
| Hydrolases | 47 |

## Feature Representation

Two feature representations were evaluated.

### Baseline Features

The baseline representation contained:

- 20 amino-acid composition features
- 5 physicochemical properties

Total: **25 features**

### Dipeptide Representation

The second representation additionally included:

- 400 possible dipeptide composition features

Total: **425 features**

## Data Quality Control

The following checks were performed:

1. Missing-value inspection
2. Duplicate protein-entry inspection
3. Duplicate sequence inspection
4. Amino-acid sequence validation
5. Removal of one sequence containing U (selenocysteine)

## Important Scope

This project represents a simplified four-class enzyme functional classification problem. It is not intended to represent the complete multi-label protein-function prediction problem involving Gene Ontology annotations.

The dataset is relatively small and the resulting models should therefore be interpreted as a computational proof-of-concept.
