# Pair Trading Strategy using Mean Reversion

This project implements a pair trading strategy based on the principle of mean reversion. The strategy involves selecting two historically correlated stocks—KOTAKBANK and HDFCBANK—and generating long and short positions based on the deviation of their price spread from its moving average.

## Objective

To exploit temporary price divergences between two correlated stocks by taking opposing positions, with the expectation that their spread will revert to the mean over time. This is a widely-used market-neutral strategy in algorithmic trading.

## Methodology

1. **Data Collection**  
   Historical daily closing prices for KOTAKBANK and HDFCBANK are downloaded using the `yfinance` API.

2. **Spread Calculation**  
   The spread is calculated as the difference between the two stock prices after aligning them.

3. **Mean Reversion Logic**  
   - A rolling moving average and rolling standard deviation of the spread are calculated over a defined window (e.g., 30 days).
   - Upper and lower bands are created using the moving average ± standard deviation multiplier.
   - A long position is initiated when the spread falls below the lower band and exited when it reverts to the mean.
   - A short position is initiated when the spread exceeds the upper band and exited when it reverts to the mean.

4. **Signal Generation and Position Tracking**  
   The notebook generates binary signals for entering/exiting long and short positions and maintains a combined position column based on the strategy.

5. **Performance Metrics**  
   The strategy is evaluated using key metrics such as cumulative returns, Sharpe ratio, and maximum drawdown.

## Important Note on Data Source

This project uses the `yfinance` library to fetch historical stock data from Yahoo Finance. Occasionally, Yahoo Finance may temporarily block requests from your IP due to rate limiting. If you face repeated download failures, it is recommended to run this notebook on **Google Colab**, which typically avoids these issues by using a fresh server-side IP.

## Technologies Used

- Python
- pandas
- numpy
- matplotlib
- yfinance

## How to Use

1. Clone the repository or download the notebook file.
2. Install required libraries [yfinance==0.2.54 , pandas , numpy , matplotlib].
3. Run the Jupyter Notebook `pair_trading.ipynb` in your preferred environment (Jupyter Lab, VS Code, or Google Colab).
4. Review the plots and performance metrics at the end of the notebook.

## Notes

- The strategy assumes no transaction costs or slippage.
- It is intended for educational purposes and should not be considered financial advice.

