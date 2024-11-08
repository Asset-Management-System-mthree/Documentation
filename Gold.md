
# Gold Price Prediction Using Random Forest
 
This project predicts the next day's gold price using a Random Forest Regressor trained on historical gold price data from Yahoo Finance. The project also includes feature engineering techniques such as moving averages, exponential moving averages, and lagged prices to enhance the model's predictive power.


## Requirements

- Python 3.7+
- Required Libraries:
  - yfinance
  - pandas
  - numpy
  - scikit-learn
  - matplotlib

## Installation

 **Install Dependencies**
   ```bash
   pip install -r requirements.txt
   ```

## Usage

Run the script to fetch historical gold price data, train the Random Forest model, make predictions, and visualize the results.

```bash
python gold_price_prediction_rf.ipynb
```

## Project Workflow

1. **Fetch Gold Price Data**  
   Use yfinance to download historical gold price data from January 2005 to October 2024.

2. **Data Preprocessing and Feature Engineering**  
   - Calculate daily returns (Return) and set the prediction target as the next day’s closing price.
   - Create additional features:
     - Moving Averages (5, 10, and 20 days)
     - Exponential Moving Averages (5 and 10 days)
     - Lagged Prices (1-day and 2-day lags)
   - Drop rows with missing values.

3. **Feature Selection**  
   Selected features include:
   - Open, High, Low, Close, Volume, Return, moving averages, exponential moving averages, and lagged prices.

4. **Train-Test Split**  
   Split the data into training and test sets using an 80-20 ratio.

5. **Model Training**  
   Train a RandomForestRegressor model with 100 estimators using the training data.

6. **Feature Importance Evaluation**  
   - Compute feature importance values from the model to understand which features are most relevant for predicting gold prices.

7. **Making Predictions**  
   - Use the trained model to predict test set values and evaluate the model using Mean Squared Error (MSE).

8. **Predicting Tomorrow's Price**  
   - Use the most recent row of data to predict the gold price for tomorrow.

## Model Evaluation

The model's performance is evaluated using Mean Squared Error (MSE), which is printed in the output.

```plaintext
Mean Squared Error: [MSE Value]
```

## Visualization

The script generates a plot comparing the actual and predicted gold prices.

- **Blue Line**: Actual Prices
- **Red Line**: Predicted Prices

## Future Scope

Potential improvements include:
- Hyperparameter tuning for RandomForestRegressor using techniques like GridSearchCV.
- Adding more features, such as technical indicators or sentiment analysis.
- Trying other regression algorithms, such as XGBoost, CatBoost, or deep learning models, to compare performances.
