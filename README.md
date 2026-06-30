# Renewable Energy Portfolio Optimization for ERCOT Market



---

## Executive Summary

This project develops a quantitative framework for optimizing renewable energy portfolios in the ERCOT (Electric Reliability Council of Texas) power market. It combines price forecasting, generation modeling, portfolio optimization, and hedging strategies to maximize risk-adjusted returns for renewable energy assets.

**Key Objectives:**
- Forecast electricity prices using advanced time series and ML models
- Model renewable generation profiles (solar & wind) with uncertainty quantification
- Optimize portfolio composition to maximize Sharpe ratio
- Develop hedging strategies to manage price and volume risk
- Backtest performance against naive strategies

---

## Problem Statement

Renewable energy producers and traders like Statkraft face unique challenges:
- **Price Volatility:** Electricity prices are highly volatile with seasonal patterns
- **Generation Uncertainty:** Solar and wind output depends on weather conditions
- **Volume Risk:** Unlike conventional generation, renewables can't control output
- **Shape Risk:** Mismatch between generation profiles and price patterns
- **Regulatory Complexity:** REC markets, curtailment rules, transmission constraints

This project addresses these challenges through quantitative modeling and optimization.

---

## Methodology

### Phase 1: Data Collection & Exploration
- ERCOT electricity prices (real-time & day-ahead)
- Weather data (solar irradiance, wind speed, temperature)
- Historical renewable generation profiles
- Natural gas prices (correlation analysis)

### Phase 2: Price Forecasting
**Statistical Models:**
- GARCH (Generalized Autoregressive Conditional Heteroskedasticity) for volatility
- ARIMA/SARIMA for time series forecasting
- Jump-diffusion models for spike detection

**Machine Learning Models:**
- XGBoost for short-term predictions
- LSTM neural networks for sequence modeling
- Feature engineering: hour-of-day, day-of-week, temperature, gas prices

**Model Evaluation:**
- RMSE, MAE, MAPE metrics
- Directional accuracy
- Out-of-sample testing

### Phase 3: Renewable Generation Modeling
**Solar Generation:**
- Clear-sky irradiance models
- Cloud cover impact
- Temperature effects on panel efficiency
- Seasonal variations

**Wind Generation:**
- Power curve modeling
- Wind speed distributions (Weibull)
- Capacity factor analysis

**Monte Carlo Simulation:**
- Generate synthetic generation scenarios
- Capture correlation between sites
- Quantify uncertainty (P10/P50/P90 levels)

### Phase 4: Portfolio Optimization
**Optimization Framework:**
- Mean-variance optimization (Markowitz)
- Risk measures: Value-at-Risk (VaR), Conditional VaR
- Constraints: capacity limits, geographical diversification, minimum holdings

**Objective Functions:**
- Maximize Sharpe ratio
- Minimize CVaR subject to return target
- Multi-objective optimization (return vs. ESG score)

**Analysis:**
- Efficient frontier visualization
- Sensitivity analysis to key parameters
- Scenario testing (high/low price, drought years, etc.)

### Phase 5: Hedging Strategy Development
**Instruments:**
- Financial forwards/futures
- Weather derivatives (potential)
- Basis hedges for location spreads

**Strategies:**
- Delta hedging: hedge expected generation
- Minimum variance hedge ratios
- Dynamic hedging adjusting to forecast updates
- Shape hedging: manage hourly profile risk

**Backtesting:**
- Historical simulation
- Transaction cost considerations
- P&L attribution
- Risk metrics (volatility reduction, maximum drawdown)

---

## Technical Skills Demonstrated

**Quantitative Finance:**
- GARCH modeling (volatility forecasting)
- Portfolio optimization theory
- VaR and risk metrics
- Option pricing concepts
- Hedging strategy design

**Machine Learning:**
- Time series forecasting (LSTM)
- Gradient boosting (XGBoost)
- Feature engineering
- Model validation and backtesting

**Programming & Software Engineering:**
- Clean, modular Python code
- Object-oriented design
- Unit testing
- Version control (Git)
- Documentation

**Domain Knowledge:**
- Power market mechanics (ERCOT)
- Renewable energy generation
- Trading and risk management
- ESG considerations

---

## Project Structure

```
renewable-portfolio-optimization/
├── README.md                          # This file
├── requirements.txt                   # Python dependencies
├── setup_instructions.md              # Detailed setup guide
├── data/
│   ├── raw/                          # Raw data files (not in git)
│   └── processed/                    # Cleaned, processed data
├── notebooks/
│   ├── 01_data_exploration.ipynb     # Initial data analysis
│   ├── 02_price_forecasting.ipynb    # Price model development
│   ├── 03_generation_modeling.ipynb  # Renewable generation models
│   ├── 04_portfolio_optimization.ipynb # Portfolio optimization
│   └── 05_hedging_strategy.ipynb     # Hedging strategy & backtest
├── src/
│   ├── __init__.py
│   ├── data_processing.py            # Data loading and cleaning
│   ├── price_models.py               # Price forecasting models
│   ├── generation_models.py          # Renewable generation models
│   ├── optimization.py               # Portfolio optimization
│   ├── hedging.py                    # Hedging strategies
│   └── visualization.py              # Plotting utilities
├── tests/
│   ├── __init__.py
│   └── test_optimization.py          # Unit tests
└── results/
    ├── figures/                      # Saved plots
    └── reports/                      # Generated reports
```

---

## Installation & Setup

### Prerequisites
- Python 3.8+ (tested on Python 3.11)
- Jupyter Notebook or JupyterLab
- 4GB RAM minimum (8GB recommended for Monte Carlo simulations)

### Installation

```bash
# Clone the repository
git clone https://github.com/YOUR-USERNAME/renewable-portfolio-optimization.git
cd renewable-portfolio-optimization

# Create virtual environment (recommended)
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Launch Jupyter
jupyter notebook
```

### Running the Analysis

Execute notebooks in order:
1. `01_data_exploration.ipynb` - Generate/load ERCOT market data
2. `02_price_forecasting.ipynb` - Build forecasting models
3. `03_generation_modeling.ipynb` - Simulate renewable generation
4. `04_portfolio_optimization.ipynb` - Calculate efficient frontier
5. `05_backtesting.ipynb` - Validate performance

**Estimated runtime:** ~15 minutes on modern laptop (Monte Carlo simulations are parallelizable)



---

## References & Data Sources

**Data:**
- [ERCOT Market Data](http://www.ercot.com/gridinfo)
- [NREL Solar Radiation Data](https://nsrdb.nrel.gov/)
- [EIA Electricity Data](https://www.eia.gov/electricity/)

**Literature:**
- Weron, R. (2014). "Electricity price forecasting: A review of the state-of-the-art"
- Conejo, A. J., et al. (2010). "Decision Making Under Uncertainty in Electricity Markets"
- Geman, H. (2005). "Commodities and Commodity Derivatives"

---

## License

This project is for educational and portfolio purposes.

---
