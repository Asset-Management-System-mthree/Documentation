 
# Stock Price Prediction Using LSTM

This project utilizes a Long Short-Term Memory (LSTM) model to predict the next day's stock closing price. The model is trained on historical stock data fetched from Yahoo Finance (yfinance), with `AAPL` (Apple Inc.) as the default stock. The project leverages `MinMaxScaler` for feature scaling, LSTM layers for sequence learning, and dropout layers to prevent overfitting.



## Requirements

- Python 3.7+
- Required Libraries:
  - yfinance
  - pandas
  - numpy
  - scikit-learn
  - tensorflow
  - matplotlib

## Installation

 **Install Dependencies**
   ```bash
   pip install -r requirements.txt
   ```

## Usage

Run the script to fetch historical stock data, train the LSTM model, make predictions, and visualize the results.

```bash
python stock_price_prediction_lstm.ipynb
```

## Project Workflow

1. **Fetch Stock Price Data**  
   Use yfinance to download historical stock data, starting from January 2005.

2. **Data Preprocessing**  
   - Calculate daily returns and define the prediction target as the next day’s closing price.
   - Use MinMaxScaler to scale features between 0 and 1.
   - Define a window size to create sequences for LSTM training. The default window size is set to 60 days.

3. **Sequence Creation and Reshaping**  
   - Create input (X) sequences and corresponding target (y) values based on the defined window size.

4. **Train-Test Split**  
   Split the data into training and testing sets based on a specified ratio (default is 80-20).

5. **Model Building and Training**  
   - Define a sequential LSTM model:
     - Two LSTM layers with 50 units each and dropout for regularization.
     - A dense layer to output the next day’s closing price.
   - Compile and train the model on training data, using Mean Squared Error (MSE) as the loss function.

6. **Making Predictions**  
   - Make predictions on the test set and inverse transform the scaled values back to original prices.

7. **Evaluate Model Performance**  
   Compute the Mean Squared Error (MSE) to evaluate the model.

8. **Visualize Results**  
   Plot the actual vs. predicted stock prices for the test set.

## Model Evaluation

The model's performance is evaluated using Mean Squared Error (MSE), a common metric for regression models.

```plaintext
Mean Squared Error: [MSE Value]
```

## Visualization

The script generates a plot to visualize the actual and predicted stock prices.

- **Blue Line**: Actual Prices
- **Red Line**: Predicted Prices

## Future Scope

Potential improvements include:
- Hyperparameter tuning (e.g., number of LSTM units, window size) to improve model performance.
- Experimenting with additional features, such as technical indicators, news sentiment, or social media sentiment.
- Using alternative deep learning architectures, like GRU or Transformers, for time-series predictions.
