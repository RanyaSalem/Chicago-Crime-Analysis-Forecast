# Chicago Crime Analysis & Forecasting (2001–2022)

This notebook explores over two decades of Chicago crime data and builds time series forecasts to support a 6-month resource-allocation recommendation for law enforcement.

Every code cell is preceded by a short markdown explanation of what it does, so the notebook can be read top to bottom without running it.

## Data

- **Source:** `Chicago_Crime_2001-2022.zip` — a ZIP archive containing multiple yearly CSV files of Chicago crime records.
- The notebook reads every CSV inside the ZIP and concatenates them into a single DataFrame (`df`), then parses and cleans the `Date` column and sets it as a sorted datetime index.
## Requirements
```
pandas
numpy
matplotlib
statsmodels
scikit-learn
pmdarima
```
## Notebook Structure

1. **Setup & Data Loading**
   Import libraries, load and combine the CSV files from the ZIP, parse dates, clean, and index the data.

2. **Crime Trends Over the Years**
   - Total crimes per year (2001–2022) and their overall trend.
   - Trend slope per crime type, to find which specific crime types are moving *against* the overall trend.

3. **AM vs. PM Rush Hour Comparison**
   - Total crime volume during AM (7–10) vs. PM (16–19) rush hours.
   - Top 5 crime types in each window.
   - A focused comparison for Motor Vehicle Theft specifically.

4. **Seasonality & Cycles**
   - Daily and monthly crime counts.
   - Weekly seasonal decomposition (7-day period) and annual seasonal decomposition (12-month period).
   - Identification of the highest- and lowest-crime calendar months.

5. **Deep Dive: Theft & Narcotics**
   - Monthly time series for `THEFT` and `NARCOTICS`.
   - Stationarity testing (Augmented Dickey-Fuller) and seasonal/regular differencing.
   - ACF/PACF plots to guide ARIMA parameter selection.

6. **Forecasting**
   - Manual SARIMA models for Theft and Narcotics, evaluated on a held-out 6-month test set (MAE, RMSE, MAPE).
   - Automated model selection with `pmdarima.auto_arima`, evaluated the same way.
   - Final models refit on the full history and used to forecast the **next 6 months** of Theft and Narcotics crime counts.
   - Net change and percent change in forecasted volume, plotted together to support resource-allocation planning.
   - 
## Output
The final section produces a 6-month-ahead forecast for Theft and Narcotics crime counts, along with the expected net and percent change over that period — intended to inform where Chicago law enforcement resources should be allocated going forward.

# Chicago Crime Dashboard 2008

An interactive Tableau dashboard exploring crime data in Chicago for 2008, including crime types, locations, timing patterns, and overall trends.

## Dashboard Preview

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/09a7d232-bdcd-4459-ae48-263f649e2be2" />

## Live Dashboard

View the interactive dashboard on Tableau Public:

[Chicago Crime Dashboard 2008 — Tableau Public](https://public.tableau.com/app/profile/rania.salem3243/viz/Book2_17884685984470/CrimeDetails?publish=yes)

## About

This project visualizes 2008 Chicago crime data, including:
- Total crime counts
- Top 10 crime types
- Crimes by month
- Crimes by hour
- Top 10 crime locations





