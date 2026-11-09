# Spanish Wine Quality Dataset – Regression

**Applied Machine Learning | Sheffield Hallam University**  
**Author:** Ifeanyi Jordan Nnamani

## Project overview

This academic Python project explores the **Spanish wine dataset** and investigates two regression problems:

1. Predicting **wine price** from numeric features using a scaled **Linear Regression** pipeline.
2. Predicting **wine rating** using **Random Forest Regression**, including a comparison with a tuned forest.

The original assessment notebook is included, with its saved code, figures, and outputs preserved. This repository documents the work rather than claiming independent reproduction.

## Dataset

The notebook reads `wines_SPA.csv` from the same directory. Its recorded output shows **7,500 rows and 11 columns**:

`winery`, `wine`, `year`, `rating`, `num_reviews`, `country`, `region`, `price`, `type`, `body`, `acidity`.

**Dataset not included:** Add `wines_SPA.csv` only if its source licence allows redistribution. Otherwise, obtain it from the original authorised source and place it alongside the notebook. The data shown here concerns wine attributes and reviews, **not laboratory chemical measurements**.

## Technologies

- Python and Jupyter Notebook
- Pandas and NumPy
- Matplotlib and Seaborn
- scikit-learn: `LinearRegression`, `RandomForestRegressor`, `StandardScaler`, `Pipeline`, `train_test_split`, `KFold`, `cross_val_score`

## Methods

1. Load and inspect the dataset, columns, and missingness.
2. Explore rating versus price and other numeric relationships with plots.
3. Examine the highly concentrated wine-rating distribution.
4. Prepare numeric features, impute missing numeric values, and split data into 80% training / 20% testing.
5. Fit a standardised Linear Regression pipeline for price prediction.
6. Fit a Random Forest regression model for rating prediction.
7. Compare training and test results, adjust forest complexity, and conduct five-fold cross-validation and feature-importance analysis.

The models **exclude price and rating from the input features**. Categorical columns such as winery and region were not encoded in the implemented models, potentially limiting performance.

## Recorded results

These figures were read from the **saved notebook outputs** and have **not been independently rerun**.

| Task / model | Test RMSE | Test MAE | Test R² |
|---|---:|---:|---:|
| Price – Linear Regression | 165.573 | 55.756 | 0.0317 |
| Rating – Random Forest | 0.0822 | 0.0358 | 0.5550 |
| Rating – tuned Random Forest | Not reported | Not reported | 0.6167 |

### Five-fold cross-validation (saved outputs)

| Model | Mean CV R² ± SD | Mean CV RMSE ± SD |
|---|---|---|
| Price – Linear Regression | 0.0255 ± 0.0100 | 146.789 ± 21.184 |
| Rating – Random Forest | 0.5763 ± 0.0290 | 0.077 ± 0.005 |

**Interpretation:** Price prediction performed weakly with the selected numeric features. Rating prediction performed better, though the train/test R² difference (0.7820 vs 0.5550) indicates a generalisation gap. The tuned forest's saved test R² was 0.6167, but this is an exploratory tuning result, not independently validated on a fresh holdout set.

**Rating imbalance:** The saved rating histogram/counts show that 5,679 of 7,500 wines have a rating of 4.2. This concentration complicates evaluation, especially for high-rated wines.

## Visualisations

The notebook contains:
- Rating vs price scatterplot
- Numeric-variable exploratory chart
- Rating distribution histogram
- Predicted vs actual charts and residual histograms for both regression tasks
- Random Forest feature-importance chart
- Numeric-feature correlation heatmap

Open the `.ipynb` file on GitHub to inspect its stored outputs and plots.

## How to run

1. Install Python 3 and Jupyter.
2. Clone or download this repository.
3. Place an authorised copy of `wines_SPA.csv` alongside `Spanish_Wine_Quality_Regression.ipynb`.
4. Install packages:

   ```bash
   python -m pip install -r requirements.txt
   ```

5. Launch Jupyter:

   ```bash
   jupyter notebook Spanish_Wine_Quality_Regression.ipynb
   ```

6. Run cells from top to bottom. Results may vary with software versions.

## Limitations and future improvements

- The dataset file is not currently bundled, so full reproducibility requires obtaining it.
- Most categorical predictors were not used; encoding wine type, winery, or region could improve model quality.
- Median imputation occurs before splitting in the original notebook; fitting preprocessing **inside a training-only pipeline** would avoid data leakage.
- The tuned forest was assessed using the same test split during exploration; future model selection should use cross-validation with a separate final holdout set.
- Investigate repeated wines, rating imbalance, skewed prices, and stronger baselines before drawing practical conclusions.
- The notebook's final text mentions chemical features such as alcohol and density, but **those columns are not present in the displayed dataset**. Treat that wording as a template mismatch, not a finding.

## Repository files

```text
Spanish-Wine-Quality-Regression/
├── Spanish_Wine_Quality_Regression.ipynb
├── requirements.txt
├── .gitignore
└── README.md
```

## Author

**Ifeanyi Jordan Nnamani**  
MSc Computer Science and Data Analytics Candidate, Sheffield Hallam University.

*Academic portfolio project. Model performance is reported from the author's original notebook outputs, not a deployed service.*
