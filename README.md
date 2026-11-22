# Bacterial DNA Classification Using Machine Learning

**An Exploratory Bioinformatics and Machine Learning Project**

## Project Overview

This project explores the application of machine learning algorithms to classify bacterial DNA fragments based on genomic sequence composition.

Four bacterial species were selected, and their reference genomes were processed to extract normalized 3-mer (trinucleotide) frequency features. These features were subsequently used to train and evaluate machine learning classification models.

The project combines computational genomics, sequence feature extraction, exploratory data analysis, and supervised machine learning.

## Objectives

- Perform genomic data preprocessing and quality control.
- Extract fixed-length DNA fragments from bacterial reference chromosomes.
- Calculate normalized 3-mer frequency features.
- Explore genomic composition using statistical analysis and Principal Component Analysis (PCA).
- Train and compare multiple machine learning classifiers.
- Evaluate classification performance using accuracy, macro F1-score, and confusion matrices.

## Dataset

The study includes four bacterial species represented by one reference genome per species.

| Bacterial Species | Reference Strain | RefSeq Assembly |
|---|---|---|
| *Escherichia coli* | K-12 MG1655 | GCF_000005845.2 |
| *Salmonella enterica* | LT2 | GCF_000006945.2 |
| *Klebsiella pneumoniae* | MGH 78578 | GCF_000016305.1 |
| *Pseudomonas aeruginosa* | PAO1 | GCF_000006765.1 |

Reference genome data were obtained from the NCBI RefSeq database.

## ⚙️ Methodology

### 1. Genome Quality Control
Genome sequences were examined for:
- Genome length
- GC content
- AT content
- Ambiguous nucleotide counts
- Other unexpected nucleotide symbols

### 2. DNA Fragmentation
- Fragment length: 1,000 bp
- Step size: 1,000 bp
- Overlapping fragments: No
- Incomplete terminal fragments shorter than 1,000 bp were excluded.

### 3. Feature Extraction

Normalized trinucleotide (3-mer) frequencies were extracted from each DNA fragment.

- k-mer size: 3
- Possible features: 64
- Normalization: Frequency-based normalization

### 4. Exploratory Data Analysis

The analysis included:
- GC-content distribution.
- 3-mer frequency analysis.
- Feature variance and correlation analysis.
- Principal Component Analysis (PCA).
- Exploration of relationships between GC content and sequence composition.

### 5. Machine Learning

Three classification algorithms were evaluated:

- Logistic Regression
- Random Forest
- Support Vector Machine (SVM) with RBF kernel

Three feature configurations were compared:

1. GC-content only
2. 3-mer features only
3. Combined GC-content and 3-mer features

### 6. Model Evaluation

The dataset was divided using a stratified random fragment-level split:

- Training set: 80%
- Testing set: 20%
- Random state: 42

Performance was evaluated using accuracy and macro-averaged F1-score.

##  Dataset Summary

| Metric | Value |
|---|---:|
| Number of bacterial species | 4 |
| Total genome length | 21,078,626 bp |
| Total DNA fragments | 21,077 |
| Fragment length | 1,000 bp |
| Number of 3-mer features | 64 |
| Total feature columns | 72 |

##  Machine Learning Results

The best-performing configuration was Support Vector Machine (SVM) using combined GC-content and 3-mer features.

| Model | Feature Set | Accuracy | Macro F1-score |
|---|---|---:|---:|
| SVM | Combined | 83.59% | 82.46% |
| SVM | 3-mer only | 83.49% | 82.36% |
| Logistic Regression | 3-mer only | 82.19% | 80.98% |
| Logistic Regression | Combined | 82.16% | 80.95% |
| Random Forest | 3-mer only | 79.72% | 78.57% |
| Random Forest | Combined | 79.60% | 78.50% |

GC-content-only models achieved lower classification performance than models using 3-mer features.

The performance difference between SVM with combined features and SVM with 3-mer features was small.

##  Technologies and Libraries

- Python 3.11
- Jupyter Notebook
- Biopython
- NumPy
- Pandas
- Scikit-learn
- Matplotlib
- Seaborn

## 📁 Repository Structure

```text
bacterial-dna-classification-ml/
│
├── README.md
├── .gitignore
├── ML1.ipynb
│
├── data/
│   └── processed/
│       ├── all_species_dna_fragments.csv
│       ├── all_species_kmer_features.csv
│       └── genome_quality_control.csv
│
└── results/
    └── figures/
        └── figure_name.png
```

##  How to Run

1. Clone the repository:

```bash
git clone https://github.com/engabubakerib-dot/bacterial-dna-classification-ml.git
```

2. Navigate to the project directory:

```bash
cd bacterial-dna-classification-ml
```

3. Install the required libraries:

```bash
pip install biopython numpy pandas scikit-learn matplotlib seaborn jupyter
```

4. Launch Jupyter Notebook:

```bash
jupyter notebook
```

5. Open `ML1.ipynb` and execute the notebook cells.

**Note:** The repository includes processed datasets. Original genome files are not included; refer to the NCBI RefSeq assembly accessions listed above for the source data.

## ⚠️ Limitations

This project is an exploratory computational study based on four reference genomes, with one genome representing each bacterial species.

The train-test split was performed at the DNA fragment level. Therefore, fragments from the same reference genome may occur in both training and testing sets.

Consequently, the reported performance does not establish generalization to independent genomes, unseen strains, or broader bacterial populations.

The results should be interpreted within the scope of this dataset and validation strategy.

##  Future Directions

- Validate classification performance using independent genomes and additional strains.
- Investigate genome-level and strain-level generalization.
- Explore alternative sequence representations and feature extraction methods.
- Evaluate additional machine learning and deep learning approaches.
- Improve validation strategies to assess robustness across independent genomic datasets.

##  Author

**Abubaker Izzeldeen Babelkhair**

Bioinformatics | Computational Biology | Machine Learning

## 📄 License

This project is licensed under the **MIT License**.

You are free to use, modify, and distribute the project's code, subject to the conditions specified in the license.

See the [LICENSE](LICENSE) file for the full license text.

**Copyright © 2026 Abubaker Izzeldeen Babelkhair.**

---

**Keywords:** Bioinformatics, Bacterial DNA Classification, Machine Learning, Genomics, k-mer Analysis, 3-mer Frequencies, GC Content, PCA, Logistic Regression, Random Forest, Support Vector Machine.
