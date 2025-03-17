# California House Price Prediction

## Overview

This project aims to predict median house values in California using various regression techniques. The dataset includes information such as median income, house age, number of rooms, and ocean proximity to develop predictive models.

## Research Questions

1. How does the number of total bedrooms impact median house value across regions?
2. How does the ratio of bedrooms per room affect median house value?
3. What is the impact of ocean proximity on median house value?
4. How does the number of total rooms affect households in predicting median house value?
5. How does median income compare to housing median age in impacting median house value?

## Dataset

The dataset consists of the following features:

- **`longitude`**: The longitude of the region.
- **`latitude`**: The latitude of the region.
- **`housing_median_age`**: The median age of the houses in the region.
- **`total_rooms`**: The total number of rooms in all houses in the region.
- **`total_bedrooms`**: The total number of bedrooms in all houses in the region.
- **`population`**: The total population of the region.
- **`households`**: The total number of households in the region.
- **`median_income`**: The median income of households (in tens of thousands of dollars).
- **`median_house_value`**: The median house value for households in the location (target variable).
- **`ocean_proximity`**: The proximity of the location to the ocean (categorical feature).

## Data Cleaning and Feature Engineering

### Handling Missing Values

- The `total_bedrooms` feature had **207 missing values**, which were removed from the dataset.

### Feature Creation

- **`bedrooms_per_room`**: Ratio of bedrooms to total rooms, which showed a strong correlation with house values.
- **`rooms_per_household`**: Number of rooms per household, which was also more informative than total rooms.

### Handling Categorical Attributes

- One-hot encoding was applied to `ocean_proximity` to convert categorical data into numerical format.

## Regression Analysis

### Linear Regression

- A **multiple linear regression model** was trained, but it showed **underfitting**, indicated by:
  - **High RMSE**: ~68,231
  - **R² score**: 0.65

### Polynomial Regression

- A **quadratic polynomial regression model** performed slightly better:
  - **RMSE**: ~60,648
  - **R² score**: 0.72
- However, it still underfitted the data.

### Assumptions of Linear Regression

- **Linear Relationship**: Residual plots indicated a non-linear relationship.
- **Normality of Residuals**: The Q-Q plot showed deviations from normality.
- **Independence of Residuals**: The Durbin-Watson test suggested **no autocorrelation issues**.

## Model Evaluation

- The **linear regression model** had **high RMSE values** on both training and test sets, indicating poor performance.
- **Cross-validation** resulted in an **average RMSE** of ~72,372, confirming that a **more complex model is needed**.

## Key Interpretations

1. **Total Bedrooms**: Weakly affects median house value (**p-value: 0.056**), making it an unreliable predictor.
2. **Bedrooms per Room Ratio**: Strong positive impact, suggesting homes with more bedrooms relative to rooms tend to be **larger and more valuable**.
3. **Ocean Proximity**: Highly influential, with **inland areas seeing a significant decrease** in house values.
4. **Total Rooms**: Minimal effect on house value, suggesting other factors are more critical.
5. **Median Income**: **Strongest predictor**, with a large positive coefficient, reinforcing that **income levels drive housing prices**.

## Conclusion

- **Income levels and ocean proximity** are the primary drivers of house values in California.
- **Higher bedrooms-per-room ratios** indicate larger or more luxurious homes, leading to higher prices.
- **Linear and polynomial regression models performed poorly**, suggesting the need for more complex models like **Random Forest or Support Vector Machines**.
- **Future work** should include testing **non-linear models**, handling outliers, and adding more relevant features for improved prediction accuracy.

## Installation and Usage

### Prerequisites

- Python 3.x
- Required libraries:
  ```bash
  pip install numpy pandas matplotlib seaborn scikit-learn statsmodels
  ```
