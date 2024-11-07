#Bitcoin_Price_Prediction

```markdown
# Bitcoin Price Prediction

This project uses historical Bitcoin price data to predict future prices using a machine learning model, specifically the CatBoostRegressor. It leverages yfinance for data retrieval and CatBoost for model training. The model predicts the closing price of Bitcoin for the next day based on past values and provides predictions for today's price.



## Requirements

- Python 3.7+
- Required Libraries:
  - yfinance
  - pandas
  - numpy
  - catboost
  - scikit-learn
  - matplotlib

## Installation

Install Dependencies
   ```bash
   pip install -r requirements.txt
   ```

## Usage

Run the script to fetch historical Bitcoin data, train the CatBoost model, make predictions, and visualize the results.

```bash
python bitcoin_price_prediction.py
```

## Project Workflow

1. **Fetch Bitcoin Price Data**  
   Use yfinance to download historical Bitcoin data from January 2005 to October 2024.

2. **Data Preprocessing**  
   - Calculate daily returns (`Return`) for Bitcoin.
   - Set the prediction target as the next day’s closing price (Target).
   - Drop rows with missing values.

3. **Feature Selection**  
   Features include:
   - Open, High, Low, Close prices
   - Volume
   - Daily returns (`Return`)

4. **Train-Test Split**  
   Split the data into training and test sets using an 80-20 ratio.

5. **Model Training**  
   Train a CatBoostRegressor`model using the specified features.

6. **Predictions**  
   Use the trained model to predict test set values and compute mean squared error (MSE).

7. **Fetch Today’s Price**  
   Retrieve real-time Bitcoin data to fetch today’s actual price and make a prediction for today.

## Model Evaluation

The model's performance is evaluated using Mean Squared Error (MSE), a common metric for regression models.

```plaintext
Mean Squared Error: [MSE Value]
```

## Visualization

The script plots both the actual and predicted Bitcoin prices on the test set to illustrate the model's performance.

- **Blue Line**: Actual Prices
- **Red Line**: Predicted Prices

## Future Scope

Potential improvements include:
- Hyperparameter tuning for `CatBoostRegressor` using techniques like `GridSearchCV`.
- Incorporating additional features such as moving averages, sentiment analysis, or other technical indicators.
- Using other algorithms for performance comparison.

