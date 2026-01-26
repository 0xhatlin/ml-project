# RT-IoT2022 Classification Project

## Dataset
**RT-IoT2022: A Real-Time Internet of Things Security Dataset**
- **UCI Link**: [https://archive.ics.uci.edu/dataset/942/rt-iot2022](https://archive.ics.uci.edu/dataset/942/rt-iot2022)
- **Donated on**: 2024-09-30
- **Number of instances**: 123,117
- **Number of features**: 83 numeric + 1 categorical (proto)
- **Task**: Multiclass Classification
- **Target variable**: Attack type classification (12 classes including normal traffic)

### Dataset Constraints Verification
✓ Added after 2015 (donated 2024)  
✓ Contains at least 1000 instances (123,117)  
✓ Contains at least 20 features (84 total)  
✓ Tabular format  
✓ Supports classification task

## Project Structure
```
ml-project-01/
├── main.ipynb           # Main analysis notebook
├── README.md            # This file
├── requirements.txt     # Python dependencies
└── reports/
    └── figures/         # Generated plots and visualizations
```

## Setup Instructions

1. **Create virtual environment**:
```bash
python -m venv .venv
source .venv/bin/activate  # On macOS/Linux
# .venv\Scripts\activate  # On Windows
```

2. **Install dependencies**:
```bash
pip install -r requirements.txt
```

3. **Run the notebook**:
```bash
jupyter lab main.ipynb
```

## Methodology

### 1. Data Preprocessing
- Handle missing values (placeholder "-" converted to NaN)
- Median imputation for numeric features
- Most frequent imputation for categorical features
- StandardScaler for numeric normalization
- OneHotEncoder for categorical encoding

### 2. Models
- **Baseline**: DummyClassifier (most_frequent strategy)
- **Model 1**: Logistic Regression (max_iter=2000, class_weight=balanced)
- **Model 2**: Random Forest (with hyperparameter tuning via RandomizedSearchCV)

### 3. Hyperparameter Tuning
- Method: RandomizedSearchCV
- Cross-validation: 3-fold
- Scoring metric: F1-macro
- Parameters tuned: n_estimators, max_depth, min_samples_split, max_features

### 4. Evaluation Metrics
- F1-Score (macro and weighted)
- Balanced Accuracy
- Confusion Matrix
- Precision-Recall Curves
- Classification Report

### 5. Validation Strategy
- Train/Test Split: 80/20
- Stratified sampling to preserve class distribution
- Random state: 42 (for reproducibility)

## Results Summary

| Model | F1-Macro | Balanced Accuracy |
|-------|----------|-------------------|
| Dummy Baseline | 0.072 | 0.083 |
| Logistic Regression | 0.804 | 0.950 |
| Random Forest (tuned) | 0.971 | 0.980 |

## Libraries Used
- **pandas**: Data manipulation
- **numpy**: Numerical operations
- **scikit-learn**: Machine learning models and evaluation
- **matplotlib**: Visualizations
- **ucimlrepo**: UCI dataset fetching

## Academic Integrity
This project follows all academic integrity guidelines. No deep learning libraries or AutoML tools were used as per project constraints.
