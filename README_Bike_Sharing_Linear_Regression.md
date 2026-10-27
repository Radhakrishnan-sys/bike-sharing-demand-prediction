# Bike Sharing Demand Prediction — Linear Regression

## Project Overview
This project analyzes daily bike-sharing demand and builds a Linear Regression model to estimate the total number of bike rentals (`cnt`) using calendar, seasonal, and weather-related variables.

The work is documented in `Linear_Regression_Assignment.ipynb` and uses Python for data preparation, exploratory data analysis, visualization, feature selection, and model evaluation.

## Business Objective
Understand which factors are associated with bike-rental demand and explore whether historical calendar and weather information can help estimate daily rentals. These insights may support demand planning and bike availability decisions.

## Dataset
The notebook loads `day.csv`, containing daily bike-sharing records. The initial dataset shape recorded in the notebook is **730 rows and 16 columns**.

The target variable is:
- `cnt` — total daily bike rentals.

Features explored include:
- **Calendar:** year (`yr`), season, month, weekday, holiday, and working day.
- **Weather:** weather situation, temperature (`temp`), feels-like temperature (`atemp`), humidity (`hum`), and wind speed (`windspeed`).

The notebook removes `casual` and `registered` because they are components of the total rental count, and removes `instant` and `dteday` during preparation.

> The dataset file is not included here. Add `day.csv` to your working directory before running the notebook, and check the dataset's original source and sharing terms before publishing it.

## Tools and Libraries
- Python
- pandas and NumPy
- Matplotlib and Seaborn
- scikit-learn
- statsmodels
- Jupyter Notebook / Google Colab

## Workflow

1. **Load and inspect data** — examine dataset dimensions, column types, descriptive statistics, and null values.
2. **Clean and prepare features** — remove selected columns, inspect numeric distributions and potential outliers, and convert season, month, weekday, and weather codes into readable categories.
3. **Explore the data** — use histograms, pair plots, box plots, regression plots, and correlation heatmaps to investigate relationships with daily rentals.
4. **Encode categorical variables** — apply one-hot encoding to selected categorical features.
5. **Split the data** — use a 70/30 train-test split with `random_state=42` (511 training rows and 219 test rows in the saved notebook output).
6. **Scale numerical features** — apply MinMax scaling to selected weather variables.
7. **Select features and fit a model** — use Recursive Feature Elimination (RFE) with Linear Regression, then inspect candidate features with statsmodels and Variance Inflation Factor (VIF).
8. **Evaluate the model** — compare actual and predicted values, inspect residuals, and calculate R² on training and test data.

## Reported Model Performance

The notebook's written inference reports:
- **Training R²:** 0.818
- **Test R²:** 0.815

The test R² indicates that the model explains approximately **81.5% of the variation in rental counts** on the test split, according to the notebook's reported result. This is a model evaluation metric, not a measured improvement in business outcomes.

## Exploratory Findings Recorded in the Notebook
- Rental counts show a positive relationship with temperature.
- Higher humidity and wind speed are associated with lower rental counts in the visual exploration.
- Demand varies by season, month, year, and weather situation.
- The notebook identifies September and the fall season as periods with relatively high demand in its exploratory plots.
- The notebook's selected model features include year, spring, July, winter, September, Sunday, selected weather categories, and temperature.

These are exploratory patterns from this dataset and should not be interpreted as proof of causation.

## How to Run

1. Clone or download this repository.
2. Place `day.csv` in the notebook's working directory.
3. Install the required libraries:

   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn statsmodels jupyter
   ```

4. Open `Linear_Regression_Assignment.ipynb` in Jupyter Notebook or Google Colab.
5. Run the notebook cells in order.

The notebook includes a Google Colab file-upload cell. If running locally, skip that cell and ensure `day.csv` is available at the path used in `pd.read_csv()`.

## Validation Notes and Next Improvements

Before using this notebook as a final portfolio deliverable, rerun it from top to bottom and verify that every cell executes successfully. In particular:
- Ensure the preprocessing and scaling steps use the same feature columns in training and test data.
- Fit the final prediction model using the selected feature set rather than relying on a model trained on a different set of columns.
- Confirm the reported training and test R² values by executing the evaluation cells.
- Add MAE and RMSE to show typical prediction error in rental-count units.
- Compare against a simple baseline and document the final model formula and assumptions.
- Avoid interpreting correlation as causation.

## Repository Structure

```text
bike-sharing-demand-prediction/
├── README.md
└── Linear_Regression_Assignment.ipynb
```

## Author
**Krishna** — Data Analytics Portfolio Project
