# House Price Prediction

A machine learning project that predicts house sale prices from property features (Ames, Iowa housing data). It compares three regression models: Support Vector Regression, Random Forest, and Linear Regression.

## Project Structure

```
House_Price_Prediction/
├── House_Price_Prediction.ipynb   # Main notebook (EDA, preprocessing, modeling)
├── HousePricePrediction.xlsx      # Dataset (add this file yourself)
└── README.md
```

## Dataset

`HousePricePrediction.xlsx` has 2,919 rows and 13 columns.

| Type | Columns |
|---|---|
| Categorical | `MSZoning`, `LotConfig`, `BldgType`, `Exterior1st` |
| Integer | `MSSubClass`, `LotArea`, `OverallCond`, `YearBuilt`, `YearRemodAdd`, `Id` |
| Float | `BsmtFinSF2`, `TotalBsmtSF`, `SalePrice` |

The target variable is `SalePrice`.

## Workflow

1. **Exploratory data analysis**
   - Count the categorical, integer and float columns
   - Plot a correlation heatmap of the numerical features
   - Plot the number of unique values and the distribution of each categorical feature
2. **Preprocessing**
   - Drop the `Id` column
   - Fill missing `SalePrice` values with the mean
   - Drop any remaining rows with null values
   - One-hot encode the categorical features with `OneHotEncoder`
3. **Train/validation split**
   - 80% training, 20% validation (`random_state=0`)
4. **Modeling and evaluation**
   - Train each model and score it with Mean Absolute Percentage Error (MAPE)

## Results

| Model | MAPE |
|---|---|
| Random Forest (`n_estimators=10`) | ~18.6% |
| Linear Regression | ~18.7% |
| Support Vector Regression | ~18.7% |

## Requirements

- Python 3.8+
- pandas
- numpy
- matplotlib
- seaborn
- scikit-learn
- openpyxl (needed by pandas to read `.xlsx` files)
- jupyter

Install everything with:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn openpyxl jupyter
```

## How to Run

1. Clone or download this repository.
2. Place `HousePricePrediction.xlsx` in the same folder as the notebook.
3. Start Jupyter:
   ```bash
   jupyter notebook House_Price_Prediction.ipynb
   ```
4. Run all cells in order.

## Known Limitations and Future Work

- Missing `SalePrice` values are filled with the mean. This makes many target values identical, which can distort training and the evaluation scores. Using only the rows that have real prices would give more reliable results.
- SVR is trained without feature scaling. Adding `StandardScaler` should improve it.
- The Random Forest uses only 10 trees, and no hyperparameter tuning is done.
- Only 12 features are used. Adding more features would likely improve accuracy.
- Ideas for improvement:
  - Cross-validation
  - Log-transforming `SalePrice`
  - Gradient boosting models (XGBoost, LightGBM)
  - Fitting the encoder on the training data only

## License

Add a license of your choice (for example, MIT).
