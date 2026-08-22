# Chicago-Crime-Data-2008-Exploratory-Time-Series-Analysis

# Chicago Crime Data (2008) — Exploratory & Time Series Analysis

This project explores the City of Chicago's 2008 crime dataset from the Chicago Data Portal, focusing on temporal patterns: holiday effects, monthly trends, rush-hour comparisons, and weekly seasonality.

## Dataset

**Source:** Chicago Data Portal — Crimes 2008

**Fields include:** crime type, exact date/time, latitude/longitude, district/ward, and whether an arrest was made.


## Stakeholder Questions Answered

1. **Holiday effects** — Which holidays saw the highest crime volume in 2008, and what crime types dominated on those days?
2. **Monthly trends** — How did overall crime volume, and volume for specific crime types (theft, battery, burglary, motor vehicle theft, homicide), change across the months of 2008?
3. **Rush hour comparison** — How does crime activity during morning rush hour (7–10 AM) compare to evening rush hour (4–7 PM)?
4. **Seasonality** — Is there a recurring weekly cycle in daily crime counts, and how large is its effect?

## Methodology

- **Data preparation:** Parsed the `Date` column to datetime, set it as the index, and resampled to a daily frequency.
- **Feature engineering:** Added year, month, day, day-of-week, weekend flag, and US/Illinois holiday flags (via the `holidays` library).
- **Holiday analysis:** Aggregated daily crime totals by holiday and identified the top crime types on the highest-volume holidays.
- **Monthly analysis:** Compared overall monthly crime volume against trends for major individual crime types.
- **Rush hour analysis:** Filtered incidents into AM (7–9 AM) and PM (4–6 PM) windows and compared total volume and crime-type breakdowns.
- **Seasonality:** Applied `statsmodels`' `seasonal_decompose` (additive model, 7-day period) to the daily crime series to isolate a weekly seasonal component and measure its magnitude.

## Key Findings

- **Top 3 holidays by crime volume:** New Year's Day (1,827 incidents), Labor Day (1,469), and Memorial Day (1,193). Across all three, the dominant crime types were Theft, Battery, Other Offense, Criminal Damage, and Deceptive Practice.
- **Monthly trend:** No consistent increasing or decreasing trend across 2008 — crime dropped sharply from January to February, rose steadily to a peak around August–September, then declined through December. No individual crime type consistently moved opposite the overall trend.
- **Rush hour:** PM rush hour (4–7 PM) saw substantially more crime (~64,000 incidents) than AM rush hour (7–10 AM) (~42,000 incidents) — over 50% higher.
- **Weekly seasonality:** A clear 7-day cycle emerged, with crime spiking on weekends and dipping midweek. The seasonal swing spans about 150 crimes/day (roughly +75 above baseline at the peak to -75 below baseline at the trough).



