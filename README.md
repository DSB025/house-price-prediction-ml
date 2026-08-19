# Bengaluru House Price Prediction

An end-to-end machine learning project that predicts residential property prices in Bengaluru using property characteristics and Linear Regression.

## Project Overview

The project starts with raw Bengaluru housing data and applies data cleaning, feature engineering, location preprocessing, domain-specific outlier removal, categorical encoding, model training, and cross-validation before generating price predictions for new properties.

## Workflow

```text
Raw Dataset
    ↓
Data Cleaning
    ↓
Missing Value Handling
    ↓
Feature Engineering
    ↓
Location Preprocessing
    ↓
Outlier Removal
    ↓
One-Hot Encoding
    ↓
Train/Test Split
    ↓
Linear Regression
    ↓
Cross-Validation
    ↓
Price Prediction
```

## Dataset

The notebook expects:

```text
Bengaluru_House_Data.csv
```

Place the CSV in the project root, next to the notebook.

The original dataset contains property attributes including area type, availability, location, size, society, total square feet, bathrooms, balcony, and price.

## Features Used

The final model uses:

- `total_sqft`
- `bath`
- `bhk`
- One-hot encoded location features

The target variable is:

- `price` — house price in lakh Indian rupees

## Data Preprocessing

The project:

1. Removes unused columns.
2. Removes rows with missing values.
3. Converts `size` into a numeric BHK feature.
4. Converts square-footage ranges such as `2100-2850` into their average.
5. Creates `price_per_sqft` for outlier analysis.
6. Groups low-frequency locations into `other`.
7. Removes properties with unusually low area per BHK.
8. Removes location-level price-per-square-foot outliers.
9. Removes BHK-related outliers.
10. Filters unusually high bathroom counts.
11. One-hot encodes location.

## Model

The project uses:

**Linear Regression**

Model evaluation includes:

- Test-set R² score
- 5-fold-style ShuffleSplit cross-validation

The notebook prints the actual scores when executed, rather than hard-coding a result.

## Example Prediction

The notebook includes a reusable:

```python
predict_price(location, sqft, bath, bhk)
```

function for predicting the price of a new property.

## Technologies

- Python
- NumPy
- Pandas
- Matplotlib
- Scikit-learn
- Jupyter Notebook / Google Colab

## Project Structure

```text
Bengaluru-House-Price-Prediction/
│
├── HousePricePrediction_GitHub.ipynb
├── Bengaluru_House_Data.csv
├── README.md
├── requirements.txt
├── .gitignore
└── images/
```

## How to Run

### Option 1: Google Colab

1. Upload the notebook to Google Colab.
2. Upload `Bengaluru_House_Data.csv` to the Colab session.
3. Run all cells.

### Option 2: Local Jupyter

Clone the repository:

```bash
git clone https://github.com/DSB025/house-price-prediction-ml
cd Bengaluru-House-Price-Prediction
```

Install dependencies:

```bash
pip install -r requirements.txt
```

Open the notebook:

```bash
jupyter notebook HousePricePrediction_GitHub.ipynb
```

## Future Improvements

- Compare Linear Regression with Ridge, Lasso, Random Forest, and Gradient Boosting.
- Build a scikit-learn Pipeline for reproducible preprocessing and inference.
- Add a Streamlit or Flask interface.
- Save and load the trained model.
- Expose predictions through an API.
- Add MAE and RMSE alongside R².

## Author

**Devashish Bornare**

B.Tech Computer Science Engineering
