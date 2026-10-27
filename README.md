# Car Sales Data Analysis | Python

## Project Overview
This project analyzes a car sales dataset using Python (Pandas) to clean messy raw data and explore how car manufacturers, fuel types, models, mileage, and prices relate to each other.

The main goal is to transform a "dirty" dataset containing missing values and duplicate records into a clean one, and then extract insights about the market share of each manufacturer, price levels, fuel type preferences, and the relationship between mileage and price.

## Dataset Description
The dataset (`car_sales_data_dirty.csv`) contains **50,025 car records and 7 columns**. Each row represents one car.

| Column | Description |
|---|---|
| Manufacturer | Car manufacturer (5 companies: Ford, VW, Toyota, BMW, Porsche) |
| Model | Car model (15 models) |
| Engine size | Engine size in liters |
| Fuel type | Fuel type (Petrol, Diesel, Hybrid) |
| Year of manufacture | Year the car was made (1984 – 2022) |
| Mileage | Distance driven |
| Price | Car price |

## Tools Used
- Python
- Pandas (data cleaning and analysis)
- Jupyter Notebook

## Project Workflow

### 1. Data Understanding
- Loaded the dataset and reviewed its structure, data types, and shape.
- Checked column names and missing values using `info()` and `isnull()`.

### 2. Data Cleaning
- **Renaming columns:** `Manufacturer` was renamed to `Company`, and `Mileage` to `Mile(KM)`.
- **Removing unneeded columns:** Dropped `Engine size` (100 missing values, and not needed for this analysis).
- **Handling missing values:**

| Column | Missing values | Method |
|---|---|---|
| Model | 80 | Filled with the most frequent value (mode) |
| Fuel type | 250 | Filled with the most frequent value (mode: Petrol) |
| Mile(KM) | 200 | Filled with the mean |
| Price | 150 | Filled with the mean |

- **Removing duplicates:** Found and removed **36 duplicate rows**.
- **Final clean dataset:** **49,989 rows × 6 columns**.

### 3. Exploratory Data Analysis (EDA)

| Analysis | Method | Visualization |
|---|---|---|
| Number of cars per company | Value counts | Pie chart |
| Number of cars per fuel type | Value counts | — |
| Average price per company | Group by company | Histogram |
| Cars per fuel type in each company | Group by company and fuel type | Bar chart |
| Number of cars per model in each company | Group by company and model | Horizontal bar chart |
| Low-price cars (price under 5,000) per company | Filter and group by company | Bar chart |
| Correlation between mileage and price | Correlation coefficient | Scatter plot |

### 4. KPI Summary
Calculated key metrics for the cleaned dataset: total cars, total companies, average price, maximum and minimum price, average mileage, and the oldest and newest car year.

## Key Findings

- The cleaned dataset contains **49,989 cars** from **5 manufacturers**.
- **Ford** (14,956 cars) and **VW** (14,906) have the largest share, together making up about 60% of the dataset. They are followed by **Toyota** (12,553), **BMW** (4,965), and **Porsche** (2,609).
- **Petrol** is the most common fuel type (25,596 cars, about 51%), followed by Diesel (13,202, about 26%) and Hybrid (11,191, about 22%).
- **Toyota** is the main hybrid brand: 9,676 of its 12,553 cars (about 77%) are hybrids. BMW and Porsche have no hybrid cars in the data.
- **Porsche** has the highest average price (about 29,088), followed by **BMW** (about 24,396), **Toyota** (about 14,323), **Ford** (about 10,684), and **VW** (about 10,372).
- The overall average price is about **13,827**, while the median is **8,010**. The average is much higher than the median because a small number of expensive cars (up to 168,081) pull it up. The cheapest car is priced at 76.
- **18,596 cars (about 37%)** are priced under 5,000. VW (6,323) and Ford (6,314) have the most low-price cars, while Porsche has the fewest (451).
- Mileage and price show a **moderate negative correlation (−0.63)**: cars with higher mileage tend to have lower prices.
- The average mileage is about **112,526**, and the cars were manufactured between **1984 and 2022**.

*Note: The findings describe this dataset and should not be interpreted as facts about the real car market.*

## Limitations
- Missing `Model` values were filled with the most frequent model (Mondeo) for all manufacturers. This created about 60 invalid combinations, such as non-Ford cars labeled as Mondeo. This affects a very small share of the data (about 0.1%).
- Missing `Price` and `Mile(KM)` values were filled with the mean, which slightly reduces variation in these columns. This affects less than 0.5% of rows.
- The correlation between mileage and price shows an association only and does not establish causation. Mileage and car age are likely related, and the analysis does not separate their effects.

## Business Value

This project demonstrates how Python can be used to:

- Clean a dirty dataset by handling missing values and duplicate records.
- Compare manufacturers by market share and price level.
- Understand fuel type preferences across brands.
- Measure how mileage relates to car price, which supports pricing decisions.

## Skills Demonstrated

- Data Cleaning (missing values, duplicates, renaming, dropping columns)
- Data Analysis with Pandas (`groupby`, `value_counts`, filtering)
- Correlation Analysis
- KPI Calculation
- Data Visualization
- Insight Communication

## How to Run

1. Install the required libraries:
   ```bash
   pip install pandas matplotlib jupyter
   ```
2. Place the CSV file in the same folder as the notebook, and make sure the file name inside `pd.read_csv()` matches your CSV file name.
3. Open `Car_Sales_Analysis_ipynb.ipynb` in Jupyter Notebook and run all cells.

## Project Files

- `car_sales_data_dirty.csv` — Original dirty dataset (50,025 rows, 7 columns).
- `Car_Sales_Analysis_ipynb.ipynb` — Jupyter Notebook containing the full cleaning, analysis, and visualizations.

## Conclusion

This project demonstrates the use of Python and Pandas to clean a dirty car sales dataset, explore it, and extract clear insights about manufacturers, fuel types, prices, and the effect of mileage on price.

It highlights the importance of data cleaning before analysis and how simple group-based analysis can reveal useful patterns in sales data.
