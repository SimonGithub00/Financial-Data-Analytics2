# S&P 500 Financial Data Analysis

A comprehensive financial data analysis project examining stock behavior and risk contributions during market turbulence (2020-2021), using advanced quantitative methods including the Fama-French 3-Factor model.

## 📊 Project Overview

This analysis explores:
- **Stock Performance Analysis**: Daily returns of S&P 500 constituents during the 2020-2021 period
- **Risk Contribution Analysis**: Identifying high-risk vs. low-risk portfolio stocks based on covariance structure
- **Factor Model Analysis**: Fama-French 3-Factor (FF3) exposure for systematic risk quantification
- **Market Periods**: Comparative analysis during normal market conditions and the COVID-19 market shock

## 🔍 Key Findings

### 1. **Risk Contribution Distribution**
- High-risk portfolio (top 10): Average risk contribution of **0.111**
- Low-risk portfolio (bottom 10): Average risk contribution of **0.021**
- **5.4x difference** in systematic risk between portfolios

### 2. **Portfolio Performance Divergence**
- High-risk portfolio experienced **severe losses** during COVID-19 crash
- Low-risk portfolio showed **significant resilience** during the same period
- Defensive stocks (Consumer Defensive, Communication Services) significantly outperformed Financial Services sector

### 3. **Factor Exposure Insights**
- **Market Risk (Mkt-RF)**:
  - High-risk portfolio: 1.32 average beta
  - Low-risk portfolio: 0.71 average beta
  - High-risk equities move 2x faster with market movements

- **Size Factor (SMB)**:
  - High-risk portfolio: 0.16 average beta (small-cap behavior)
  - Low-risk portfolio: -0.02 average beta (large-cap behavior)

- **Value Factor (HML)**:
  - High-risk portfolio: 1.37 average beta (strong value exposure)
  - Low-risk portfolio: -0.13 average beta (growth-oriented behavior)

### 4. **Correlation & Systematic Factors**
- FF3 model captures **~95% of co-movements** in portfolio returns
- Residuals between high-risk and low-risk portfolios show minimal correlation
- Clear evidence of three-factor sufficiency for risk explanation

### 5. **Walmart Case Study**
- Defensive characteristics: Beta(Mkt)=0.66, Beta(SMB)=-0.45, Beta(HML)=-0.19
- Price movements strongly correlated with factor regimes
- Exemplifies low-risk, large-cap, growth-oriented stock behavior

## 💻 Tech Stack

| Technology | Purpose |
|-----------|---------|
| ![Python](https://img.shields.io/badge/Python-3.8+-blue?logo=python&logoColor=white) | Core analysis language |
| ![Pandas](https://img.shields.io/badge/Pandas-2.0+-darkblue?logo=pandas&logoColor=white) | Data manipulation & analysis |
| ![NumPy](https://img.shields.io/badge/NumPy-1.20+-013243?logo=numpy&logoColor=white) | Numerical computations |
| ![Matplotlib](https://img.shields.io/badge/Matplotlib-3.0+-blueviolet?logo=matplotlib&logoColor=white) | Statistical visualization |
| ![Seaborn](https://img.shields.io/badge/Seaborn-0.12+-skyblue) | Advanced statistical plotting |
| ![Statsmodels](https://img.shields.io/badge/Statsmodels-0.13+-brown) | Regression & factor models |
| ![Scikit-learn](https://img.shields.io/badge/Scikit--learn-1.0+-FFA500?logo=scikit-learn&logoColor=white) | Machine learning (K-means) |
| ![YFinance](https://img.shields.io/badge/YFinance-market--data-green) | Real-time market data |

## 📈 Key Visualizations

### 1. Correlation Analysis - Full Period
![Correlation Heatmap](images/01_correlation_full_period.png)
**Description**: Heatmap showing pairwise correlations between S&P 500 constituents during the entire analysis period (Jan 2020 - Dec 2021). Lighter colors indicate weak correlations; darker colors indicate stronger correlations between stocks.

### 2. Correlation Analysis - COVID Crisis
![Crisis Correlation](images/02_correlation_crisis_period.png)
**Description**: Correlation heatmap during the acute COVID-19 market shock (Feb-Apr 2020). Noticeably darker than the full period, indicating systematic increase in correlations as markets moved in lockstep during the crisis.

### 3. Portfolio Returns Comparison
![Returns Comparison](images/03_portfolio_returns_comparison.png)
**Description**: Cumulative returns of high-risk vs. low-risk portfolios. The high-risk portfolio shows sharp decline during Feb-Apr 2020, while the low-risk portfolio maintains relative stability, highlighting the protective nature of defensive stocks.

### 4. Fama-French Beta Distribution
![Beta Distribution](images/04_ff3_beta_distribution.png)
**Description**: Histograms comparing Factor exposures (Market, SMB, HML) between high-risk (top row) and low-risk (bottom row) portfolios. High-risk portfolio shows stronger positive skew in all factors, particularly in HML, indicating value-stock behavior.

### 5. 3D Factor Space Visualization
![3D Factors](images/05_3d_factor_space.png)
**Description**: 3D scatter plot of stocks plotted by their three Fama-French factor exposures (Market-RF, SMB, HML). Clear separation between high-risk cluster (right/upper) and low-risk cluster (left/lower) visible.

### 6. Walmart Analysis - Price & Market Factor
![Walmart MKT](images/06_walmart_price_vs_mkt.png)
**Description**: Walmart stock price evolution with gray shading indicating periods of positive/negative market factor (Mkt-RF). The shading pattern closely follows price movements, demonstrating systematic market factor exposure.

### 7. Walmart Analysis - Returns & Market Factor
![Walmart Returns](images/07_walmart_returns_vs_mkt.png)
**Description**: Walmart daily returns visualization with market factor periods highlighted. Clear synchronization between factor regime changes and return patterns illustrates the importance of systematic risk in portfolio construction.

## 🚀 Getting Started

### Prerequisites
```bash
pip install pandas numpy matplotlib seaborn statsmodels scikit-learn yfinance yellowbrick
```

### Running the Analysis
1. Open `FDA2.ipynb` in Jupyter Notebook or Jupyter Lab
2. Execute cells sequentially to reproduce the analysis
3. All data is fetched directly from Yahoo Finance API (no external file downloads required)

### Data Sources
- **Stock Prices**: Yahoo Finance (S&P 500 constituents)
- **Fama-French Factors**: Kenneth French Data Library (daily factors, 1998-present)
- **Time Period**: Analysis focuses on 2020-2021, with additional context using 1998-2022 data for Walmart

## 📋 Methodology

### 1. Risk Contribution Calculation
```
Risk Contribution = Σ(Covariance Matrix Row)
```
Higher values indicate stocks with greater systematic covariance with the portfolio.

### 2. Fama-French 3-Factor Model
```
R_i - R_f = α + β_m(R_m - R_f) + β_s(SMB) + β_h(HML) + ε
```
Where:
- **Mkt-RF**: Market risk premium
- **SMB**: Small Minus Big (size factor)
- **HML**: High Minus Low (value factor)

### 3. Portfolio Construction
- **High-risk portfolio**: Top 10 stocks by risk contribution
- **Low-risk portfolio**: Bottom 10 stocks by risk contribution
- Portfolio returns calculated as equally-weighted averages

## 📁 Project Structure
```
├── FDA2.ipynb                 # Main analysis notebook
├── README.md                  # This file
├── images/                    # Chart visualizations
│   ├── 01_correlation_full_period.png
│   ├── 02_correlation_crisis_period.png
│   ├── 03_portfolio_returns_comparison.png
│   ├── 04_ff3_beta_distribution.png
│   ├── 05_3d_factor_space.png
│   ├── 06_walmart_price_vs_mkt.png
│   └── 07_walmart_returns_vs_mkt.png
└── Data Sources
    ├── Yahoo Finance API      # Real-time market data
    └── Kenneth French Library # Fama-French factors
```

## 🔬 Statistical Significance

- **Timeline**: 504 trading days (Jan 1, 2020 - Dec 31, 2021)
- **Crisis Period**: 55 trading days (Feb 1 - Apr 30, 2020)
- **Sample Size**: Analysis covers all S&P 500 constituents
- **Data Quality**: Removed stocks with >1 missing values

## 💡 Applications

This analysis framework can be applied to:
- Portfolio risk assessment and optimization
- Sector rotation strategies
- Crisis period identification and analysis
- Factor-based investment strategies
- Systematic risk decomposition
- Stress testing during market downturns

## 📚 References

- Fama, E. F., & French, K. R. (1993). "Common risk factors in the returns on stocks and bonds."
- Kenneth French Data Library: https://mba.tuck.dartmouth.edu/pages/faculty/ken.french/
- Yahoo Finance: https://finance.yahoo.com

## 📝 License

This project is provided as-is for educational and research purposes.

## ✨ Acknowledgments

- Data sourced from Yahoo Finance and Kenneth French Data Library
- Analysis conducted using industry-standard Python scientific libraries
- Methodology based on established quantitative finance practices

---

**Last Updated**: April 2026  
**Python Version**: 3.8+  
**Status**: Complete Analysis
