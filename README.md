## US Recession Early-Warning Model

This project develops a probabilistic early-warning system for U.S. recessions using
macroeconomic and financial indicators from the Federal Reserve Economic Data (FRED).

### Objective

Estimate the probability that the U.S. economy will enter an NBER-defined recession
within the next six months. The analysis emphasizes interpretability, proper
time-series evaluation, and early-warning signals rather than precise point forecasts
of economic activity.

### Data

Monthly U.S. macroeconomic and financial data from FRED, including:
- Treasury yield curve slopes (10Y–2Y, 10Y–3M)
- Credit spread proxy (Baa corporate yield minus Treasury yield)
- Unemployment rate and short- and medium-term changes
- CPI inflation (year-over-year)
- Industrial production growth (year-over-year)
- Federal funds rate
- NBER recession indicator

All series are transformed to a monthly frequency and aligned to avoid look-ahead bias.

### Methodology

- Feature engineering using economically motivated transformations
- Logistic regression with standardized inputs to support coefficient interpretability
- Time-based train/test split to mimic real-time forecasting conditions
- Evaluation using ROC/AUC and threshold analysis appropriate for rare events
- Explicit examination of the tradeoff between early detection and false positives

### Key Results

- An earlier exploratory specification achieved an out-of-sample ROC–AUC of approximately 0.57
- Incorporating additional financial indicators, particularly yield curve slopes and
  credit spread proxies, improves out-of-sample ROC–AUC to approximately 0.59
- Financial conditions increase model sensitivity to emerging downturns, improving
  recession detection at the cost of higher false positives
- Lower probability thresholds (approximately 20 to 25 percent) provide earlier
  recession warnings and are more appropriate for macroeconomic risk monitoring
  than a conventional 50 percent classification cutoff

### Interpretation

The model captures economically meaningful increases in recession risk ahead of
several major U.S. downturns, particularly during periods of yield curve inversion,
tightening financial conditions, and weakening labor market dynamics. While increased
sensitivity leads to false alarms during some late-expansion periods, this tradeoff
reflects the intended use of the model as an early-warning and risk-monitoring tool
rather than a precise recession-timing device.

### Limitations

- Recessions are rare events, which inherently limits predictive performance and leads
  to imbalanced classification outcomes
- The analysis relies on revised historical data rather than real-time data vintages
- Structural shocks such as the COVID-19 recession may distort estimates
- The logistic regression framework is linear and may not capture nonlinear dynamics

### Tools

Python, pandas, scikit-learn, matplotlib, pandas-datareader

### How to Run

1. Install dependencies listed in `requirements.txt`
2. Run the Jupyter notebook to download data from FRED and reproduce results
3. Figures, coefficient plots, and evaluation metrics are generated within the notebook
