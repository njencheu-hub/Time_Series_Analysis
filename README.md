# Time_Series_Analysis

# Handling Missing Data in Stock Price Time Series

This project explores different techniques to handle **missing values** in stock price data and evaluates their impact on time series modeling.  

---

## Objectives
- Identify and visualize missing values in time series data.  
- Apply different **imputation techniques** to fill gaps.  
- Compare imputation methods visually.  
- Use an **imputation flag** to improve predictive modeling.  

---

## Dataset
- Input file: **`Stock_price.csv`**  
- Structure:  
  - `Date`: Trading date (parsed as datetime, used as index).  
  - `Close`: Closing stock price (with missing values).  

---

## Methods for Handling Missing Data
The following imputation methods are applied to the `Close` column:

1. **Forward Fill (`ffill`)**  
   Propagates the last valid observation forward.  

2. **Backward Fill (`bfill`)**  
   Uses the next valid observation to fill missing values.  

3. **Linear Interpolation**  
   Connects missing values using a straight-line estimate between neighbors.  

4. **Global Mean**  
   Replaces missing values with the overall mean closing price.  

5. **Rolling Mean**  
   Uses the moving average of the past 3 trading days.  

Additionally, an **`imputed_flag`** column is created to mark whether a value was originally missing (1) or observed (0).  

---

## Visualizations
1. **Original Data with Missing Gaps**  
   - Missing points highlighted in red.  

2. **Comparison of Imputation Methods**  
   - Overlay of forward fill, backward fill, linear interpolation, global mean, and rolling mean.  

3. **Zoomed-In Analysis (Jan 10–20, 2024)**  
   - Detailed view of how each method performs near missing values.  

---

## Predictive Modeling
To test the impact of imputation strategies, a **linear regression model** is applied:  

- **Target**: Next-day closing price (`target`).  
- **Features**:  
  - Model A: `Close_imputed` (imputed stock price).  
  - Model B: `Close_imputed` + `imputed_flag`.  

### Results
- **Model A** (no flag): Treats imputed data as fully reliable, leading to biased predictions.  
- **Model B** (with flag): Adjusts around imputed points, providing more robust predictions.  

---

## Key Takeaway
Missing data is not just a nuisance—it’s a signal.
By combining imputation techniques with an imputation flag, we can improve predictive performance and ensure models remain robust in the presence of gaps.

License
This project is for educational and research purposes.