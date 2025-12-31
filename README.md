## US Recession Early-Warning Model

This project develops a probabilistic early-warning system for US recessions using
macroeconomic and financial indicators from FRED.

### Objective
Estimate the probability that the US economy will enter an NBER-defined recession
within the next six months, focusing on interpretability and early-warning signals
rather than precise point prediction.

### Data
Monthly US macroeconomic data from FRED, including:
- Treasury yield curve slopes (10Y–2Y, 10Y–3M)
- Credit spread proxy
- Unemployment rate and short- and medium-term changes
- CPI inflation (year-over-year)
- Industrial production growth
- Federal funds rate
- NBER recession indicator

### Methodology
- Feature engineering using economically motivated transformations
- Logistic regression with standardized inputs for interpretability
- Time-based train/test split to mimic real-time forecasting
- Evaluation using ROC/AUC and threshold analysis appropriate for rare events

### Key Results
- An earlier exploratory specification achieved an out-of-sample AUC of approximately 0.57
- Incorporating additional financial indicators, particularly yield curve slopes and
  credit spreads, improves out-of-sample AUC to approximately 0.59
- Financial conditions increase model sensitivity to emerging downturns, improving
  recession detection at the cost of higher false positives
- Lower probability thresholds (approximately 20 to 25 percent) provide earlier
  recession warnings, consistent with the goals of macroeconomic risk monitoring

### Interpretation
The model captures meaningful increases in recession risk ahead of several major
US downturns, particularly during periods of yield curve inversion and tightening
financial conditions. While higher sensitivity leads to more false alarms during
some late-expansion periods, this tradeoff reflects the intended use of the model
as an early-warning and risk-monitoring tool rather than a precise timing device.

### Tools
Python, pandas, scikit-learn, matplotlib, pandas-datareader

### How to Run
1. Install dependencies listed in `requirements.txt`
2. Run the Jupyter notebook to download data from FRED and reproduce results
3. Figures and evaluation metrics are generated within the notebook