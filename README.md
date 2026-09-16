# Machine Learning-Based Enzyme Function Classification from Protein Sequences

## Overview

This project investigates whether machine-learning models can classify proteins into broad enzyme functional classes using features derived from their amino-acid sequences.

The study compares conventional sequence-composition and physicochemical features with additional dipeptide composition features using three machine-learning approaches:

- Logistic Regression
- Random Forest
- Support Vector Machine (SVM)

The project was designed as a reproducible computational proof-of-concept for sequence-based enzyme function classification.

## Research Question

Can machine-learning models predict the functional class of a protein using features derived from its amino-acid sequence?

## Dataset

Protein sequences were obtained from the UniProtKB/Swiss-Prot reviewed protein database using the UniProt REST API.

Four top-level Enzyme Commission (EC) classes were studied:

| EC Class | Functional Class | Proteins |
|---|---|---:|
| EC1 | Oxidoreductases | 49 |
| EC2 | Transferases | 47 |
| EC3 | Hydrolases | 47 |
| EC4 | Lyases | 49 |
| Total | | 192 |

Protein sequences were restricted to lengths between 100 and 500 amino acids.

Detailed dataset information is available in:

data/dataset_information.md

## Computational Workflow

UniProtKB/Swiss-Prot
→ Protein sequence collection
→ Quality control
→ Feature extraction
→ Machine learning
→ 5-fold cross-validation
→ Performance comparison
→ Biological interpretation

## Feature Engineering

### Baseline Features

The baseline representation contained:

- 20 amino-acid composition features
- Molecular weight
- Aromaticity
- Instability index
- Isoelectric point
- GRAVY

Total: 25 features.

### Dipeptide Features

The second representation additionally included all 400 possible dipeptide composition features.

Total:

25 baseline features + 400 dipeptide features = 425 features.

## Machine Learning Models

Three classification algorithms were evaluated:

1. Logistic Regression
2. Random Forest
3. Support Vector Machine with an RBF kernel

## Evaluation Strategy

The final evaluation used stratified 5-fold cross-validation with shuffling and random state 42.

Performance is reported as mean accuracy ± standard deviation across the five folds.

## Final Results

| Model | Baseline Features | With Dipeptides | Change |
|---|---:|---:|---:|
| Logistic Regression | 32.83 ± 4.99% | 38.56 ± 6.57% | +5.72 pp |
| Random Forest | 40.19 ± 7.16% | 39.11 ± 9.41% | -1.08 pp |
| SVM | 36.46 ± 5.49% | 38.00 ± 2.82% | +1.54 pp |

pp = percentage points.

### Main Observation

The effect of adding dipeptide features was model-dependent.

Logistic Regression and SVM showed improved mean cross-validated accuracy after adding dipeptide features, whereas Random Forest showed a small decrease.

This indicates that additional sequence-order information does not necessarily improve every machine-learning model under the same dataset and experimental conditions.

## Results and Figures

The repository contains:

- Baseline vs. dipeptide accuracy comparison
- Model accuracy comparison
- Top 10 Random Forest feature importances
- Logistic Regression confusion matrix
- Random Forest confusion matrix
- SVM confusion matrix

## Feature Importance

Random Forest feature importance was examined to identify features that contributed most strongly to model predictions.

Feature importance should be interpreted as model-specific predictive contribution, not as evidence that an individual amino acid or physicochemical property biologically determines enzyme function.

## Project Structure

Protein_Function_Prediction/

├── Protein_Function_Prediction.ipynb

├── README.md

├── requirements.txt

├── data/

│   └── dataset_information.md

├── results/

│   ├── final_project_results.csv

│   ├── final_model_comparison.csv

│   └── feature_importance.csv

└── figures/

   ├── baseline_vs_dipeptide_accuracy.png
 
   ├── model_accuracy_comparison.png
    
   ├── top_10_feature_importance.png
    
   ├── logistic_regression_confusion_matrix.png
    
   ├── random_forest_confusion_matrix.png
    
   └── svm_confusion_matrix.png

## Reproducibility

The project was implemented in Python using:

- Python
- Pandas
- NumPy
- Biopython
- Scikit-learn
- Matplotlib
- Seaborn
- Requests

Required packages are listed in requirements.txt.

## Limitations

This study is a small computational proof-of-concept.

Key limitations include:

1. The dataset contains only 192 protein sequences.
2. Only four broad enzyme functional classes were considered.
3. Protein function is more complex than the four-class classification problem used here.
4. The feature space becomes high-dimensional when dipeptide features are included.
5. The current evaluation does not explicitly control for protein sequence homology between training and testing folds.
6. Accuracy alone does not capture every aspect of multiclass classification performance.
7. The results should not be interpreted as a general solution to protein function prediction.

## Future Extensions

Possible extensions include:

- Larger protein datasets
- Homology-aware train/test splitting
- More refined enzyme subclasses
- Gene Ontology-based functional annotation
- Additional sequence representations
- Protein embeddings from pretrained protein language models
- More comprehensive evaluation metrics
- Independent external validation

## Conclusion

This project demonstrates a reproducible machine-learning workflow for classifying enzyme functional classes from protein sequence-derived features.

The comparison between baseline sequence features and dipeptide-enriched representations demonstrates that feature representation can influence model performance differently across machine-learning algorithms.

The work provides a foundation for developing more sophisticated protein-function prediction systems using larger datasets, homology-aware evaluation, and modern protein representation learning.

## Author

Ishita Singh

B.Tech Bioinformatics
AKTU

## License

This project is intended for academic and educational research purposes.
