# Econometrics

Lab assignments and final exam for the **Econometrics** course, implemented in Python as an alternative to Gretl. The project covers from simple/multiple linear regression to time-series models (ARIMA / SARIMAX), including residual analysis and statistical diagnostics.

## 📋 Project description

Each `PracN.py` file corresponds to a weekly lab, while `Examen.py` is the final exam. The `utilities.py` module provides a toolbox of reusable econometric helpers, and two working templates (`Plantilla_A.py`, `Plantilla_B.py`) are included as starting points for new analyses.

## 📁 Project structure

```
econometrics/
├── Prac4.py             # Lab 4
├── Prac5.py             # Lab 5
├── Prac8.py             # Lab 8
├── Prac9.py             # Lab 9
├── Prac10.py            # Lab 10
├── Prac11.py            # Lab 11
├── Prac12.py            # Lab 12
├── Examen.py            # Final exam (SARIMAX on a real series)
├── Plantilla_A.py       # Working template A
├── Plantilla_B.py       # Working template B
├── utilities.py         # Helper functions (residuals, plots, tests…)
├── __init__.py
│
├── Plots EXAMEN.pdf     # Plots generated during the final exam
│
├── MRD003.csv           # Datasets (Multiple Regression — Data)
├── MRD021a.csv
├── MRD060.csv
├── MRL016-1.csv         # Datasets (Multiple Regression — Linear)
├── MRL028tc.gdt
├── MRL151-1.gdt
├── MST007.csv           # Datasets (Multiple / Simple time series)
├── MST015.csv
├── MST050.csv
└── TASA_PARO.csv        # Unemployment rate (time series)
```

## 🛠️ Main features

### `utilities.py` — Econometrics toolbox

Shared helper functions used across labs:

- **`compute_residuals(target_var, predictors, df)`** — fits an OLS model for a target variable with a given set of predictors and returns the residuals.
- **Time-series and autocorrelation plots** — wrappers around `plot_acf` / `plot_pacf` and time-domain plots of the series.
- **White-noise check** — graphical and statistical inspection of residuals (ACF, PACF, Ljung-Box-style visualisation).
- **Residual diagnostics** — heteroskedasticity (Breusch-Pagan, White), normality (Jarque-Bera) and autocorrelation (Durbin-Watson) tests.
- **Seasonal decomposition** — `seasonal_decompose` wrapper for trend/seasonality/residual analysis.
- **Multicollinearity** — Variance Inflation Factor (VIF) helpers.
- **ADF test** — Augmented Dickey-Fuller stationarity testing.

Main libraries leveraged: `pandas`, `numpy`, `statsmodels`, `pmdarima`, `scipy`, `seaborn`, `matplotlib`.

### Lab assignments (`Prac4.py` – `Prac12.py`)

Each lab applies the theory seen in class to one of the included datasets, covering topics such as:

- Simple and multiple linear regression (OLS)
- Residual analysis and goodness-of-fit metrics
- Variable selection and multicollinearity diagnosis (VIF)
- Heteroskedasticity and autocorrelation tests
- Stationarity (ADF) and differencing
- ARIMA / SARIMAX modelling
- Forecasting and confidence intervals

### Final exam (`Examen.py`)

Contains the complete pipeline for the final exam: data loading, visual inspection, differencing, SARIMAX fitting, residual diagnostics and forecasting, with the generated plots saved in `Plots EXAMEN.pdf`.

### Templates (`Plantilla_A.py`, `Plantilla_B.py`)

Reusable skeletons that bundle typical imports and helper calls so that a new analysis can be started quickly.

## 📊 Datasets

The repository ships a collection of CSV / GDT files used across the labs:

| File | Type | Notes |
|---|---|---|
| `MRD003.csv`, `MRD021a.csv`, `MRD060.csv` | Multiple Regression — Data | Cross-section datasets |
| `MRL016-1.csv`, `MRL028tc.gdt`, `MRL151-1.gdt` | Multiple Regression — Linear | Mixed CSV / Gretl format |
| `MST007.csv`, `MST015.csv`, `MST050.csv` | Time series | Multiple / single-series |
| `TASA_PARO.csv` | Unemployment rate | Real-world macroeconomic series |

> **Note:** `.gdt` files come from Gretl and can be read with `pandas` after a light preprocessing step, or opened directly in Gretl.

## 📦 Dependencies

```
pandas         # Data manipulation
numpy          # Numerical operations
statsmodels    # Econometric models (OLS, SARIMAX, tests)
pmdarima       # Automated ARIMA model selection
scipy          # Statistical tests and distributions
matplotlib     # Visualisation
seaborn        # Statistical plotting
```

### Installation

```bash
pip install pandas numpy statsmodels pmdarima scipy matplotlib seaborn
```

## 🚀 Usage

All scripts are meant to be run from inside the `econometrics/` folder so that the relative paths to the datasets resolve correctly:

```bash
cd econometrics

# Run any of the labs
python Prac4.py
python Prac11.py

# Run the final exam pipeline
python Examen.py
```

> **Tip:** some scripts save plots to your user `Downloads` folder (via `os.path.expanduser("~")`). Adjust `save_path` at the top of the script if you prefer a different target.

## 📝 Key concepts

- **OLS (Ordinary Least Squares)** — linear regression parameter estimation.
- **Residual analysis** — checking model assumptions (linearity, homoskedasticity, normality, independence).
- **Stationarity** — prerequisite for many time-series models; inspected via ACF/PACF plots and the ADF test.
- **ARIMA / SARIMAX** — autoregressive-integrated-moving-average models, with seasonal and exogenous variants.
- **Information criteria** — AIC / BIC used to compare candidate models.
- **Multicollinearity** — detected via pairwise correlations and VIF.

## 🎯 Learning objectives

1. Build and interpret linear regression models on real data.
2. Diagnose model assumptions through residual analysis.
3. Model and forecast time series using ARIMA/SARIMAX.
4. Run and interpret classical statistical tests (Durbin-Watson, Breusch-Pagan, White, Jarque-Bera, ADF).
5. Produce clean, reproducible analyses using the pandas/statsmodels ecosystem.

## 📄 License

Academic project for educational purposes.

## 👤 Author

Developed as part of the Econometrics course.

**Author:** Oscar Jiménez Bou

---

> **Note:** several scripts include hard-coded relative paths (e.g. `"Econometria/MRD060.csv"`). You may need to tweak them to match the actual path of the dataset on your machine.
