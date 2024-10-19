### Summary of the Project: Monte Carlo Simulation and Risk Management for Portfolio Optimization

#### **1. Data Collection and Preparation**
- **Goal**: Fetch historical price data for Nifty 50 stocks.
- **Method**:  Used Yahoo Finance (`yfinance`) to gather adjusted closing prices for all Nifty 50 stocks.
- **Steps**:
  - Fetch historical prices and clean the dataset.
  - Calculate **daily returns**, **mean returns**, **standard deviations**, and the **covariance matrix** of the returns.

#### **2. Mean Returns, Standard Deviation, and Covariance Matrix Calculation**
- **Goal**: Compute essential statistics to assess the performance and risk of each stock.
- **Definitions**:
  - **Mean Return**: Average return of each stock over the chosen time horizon.
  - **Standard Deviation (Volatility)**: Measure of risk, indicating how much the stock’s returns fluctuate.
  - **Covariance Matrix**: Shows how different stocks move in relation to each other, crucial for understanding portfolio diversification.
- **Formulae**:
  \[
  \text{Mean Return} = \frac{\sum (R_i)}{N}, \quad \text{Standard Deviation} = \sqrt{\frac{\sum (R_i - \bar{R})^2}{N-1}}
  \]
  Where \(R_i\) represents returns and \( \bar{R} \) is the mean return.

#### **3. Monte Carlo Simulation for Portfolio Optimization**
- **Goal**: Generate different portfolio combinations to evaluate return, risk, and Sharpe ratio.
- **Method**: Monte Carlo simulation randomly generates thousands of portfolios by assigning random weights to the selected stocks and computing portfolio return and risk.
- **Steps**:
  - Randomly assign portfolio weights (ensuring the sum equals 1).
  - Calculate **Portfolio Return**:
    \[
    \text{Portfolio Return} = \sum w_i \cdot \mu_i
    \]
    Where \(w_i\) are the weights, and \( \mu_i \) are the mean returns.
  - Calculate **Portfolio Volatility** (Risk):
    \[
    \sigma_p = \sqrt{W^T \cdot Cov \cdot W}
    \]
    Where \(W\) is the vector of weights, and \(Cov\) is the covariance matrix.
  - Calculate **Sharpe Ratio**:
    \[
    \text{Sharpe Ratio} = \frac{R_p - R_f}{\sigma_p}
    \]
    Where \(R_p\) is the portfolio return, \(R_f\) is the risk-free rate, and \( \sigma_p \) is portfolio volatility.

#### **4. Selection of Optimal Portfolio**
- **Goal**: Identify the portfolios with the **Maximum Sharpe Ratio** (best risk-adjusted return) and **Minimum Volatility**.
- **Steps**:
  - Simulate thousands of portfolios.
  - Extract the portfolios with the **highest Sharpe ratio** and **lowest volatility**.
  - Visualize the results using a bar chart for portfolio weights and a plot of the **Efficient Frontier** (risk-return trade-off).

#### **5. Risk Management: VaR and CVaR Calculation**
- **Goal**: Evaluate downside risk through **Value at Risk (VaR)** and **Conditional Value at Risk (CVaR)**.
- **Definitions**:
  - **VaR**: The maximum loss expected over a given time horizon at a specified confidence level (e.g., 95%).
  - **CVaR**: The average loss in the worst-case scenarios where the loss exceeds the VaR threshold.
  
- **Steps**:
  - Simulate the portfolio returns using Monte Carlo simulations.
  - Sort the returns in ascending order.
  - **VaR**: Calculate the return at the \(1-\alpha\) percentile, where \( \alpha \) is the confidence level.
    \[
    VaR = \text{Return at the } (1-\alpha) \text{ percentile of simulated returns}
    \]
  - **CVaR**: Calculate the average of the losses beyond the VaR threshold:
    \[
    CVaR = E[\text{Loss} | \text{Loss} > VaR]
    \]
  
#### **6. Interpretation of VaR and CVaR**
- **VaR**: Informs the potential maximum loss in 95% of cases over a given period (e.g., a VaR of $10,000 means there's a 5% chance the portfolio could lose more than $10,000).
- **CVaR**: Provides the average loss in the worst 5% of cases, giving deeper insight into tail risks.

### Overall Process Summary:
1. **Data Collection**: Fetch historical data for Nifty 50 stocks.
2. **Return and Risk Calculation**: Compute returns, volatility, and correlations between stocks.
3. **Monte Carlo Simulation**: Randomly generate portfolios, calculate risk and return metrics for each.
4. **Portfolio Optimization**: Identify the optimal portfolios with maximum Sharpe ratio and minimum volatility.
5. **Risk Assessment**: Calculate VaR and CVaR to quantify potential losses in normal and extreme market conditions.

These steps provided a comprehensive way to evaluate and optimize a portfolio based on historical performance and risk metrics.
