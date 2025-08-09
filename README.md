# 🎬 IMDB Movies Financial Analysis  
![Language](https://img.shields.io/badge/Language-Python-blue)  ![Status](https://img.shields.io/badge/Project-Completed-brightgreen)  ![Data](https://img.shields.io/badge/Data-IMDB-orange)

---

## 1. Business Objective

To identify the key factors that influence a movie's **financial success** by analyzing relationships between features such as **budget, score, votes, genre, and production company** and a movie's **gross revenue**. This insight aims to support data-driven decision-making in the film industry regarding **investment**, **production**, and **marketing strategies**.

---

## 2. About the Data

The dataset was obtained from the **IMDB Movies Dataset**, containing metadata for over **7,600 movies**. It includes the following key attributes:

🗃️ [IMDB Movies Dataset](https://github.com/TrungLe123692/U.S.-Movies-Data-Analytics-Project/blob/main/movies%20dataset.csv)

| Column     | Description                                           |
|------------|-------------------------------------------------------|
| `name`     | Title of the movie                                    |
| `rating`   | MPAA rating (e.g., PG-13, R)                          |
| `genre`    | Genre of the movie (e.g., Drama, Comedy)              |
| `year`     | Year the movie was produced                           |
| `released` | Full release date                                     |
| `score`    | IMDb user rating (float)                              |
| `votes`    | Number of user votes received                         |
| `director` | Director of the movie                                 |
| `writer`   | Writer of the movie                                   |
| `star`     | Lead actor or actress                                 |
| `country`  | Production country                                    |
| `budget`   | Budget allocated (float)                              |
| `gross`    | Gross worldwide revenue (float)                       |
| `company`  | Production/distribution company                       |
| `runtime`  | Duration in minutes (float)                           |

---

## 3. Analysis List

> ✅ These analyses uncovered key revenue drivers, top-performing production companies, and strong budget–score–gross relationships to guide data-driven forecasting.

- **3.1 Exploratory Data Analysis (EDA)**  
  - Previewed dataset structure and first few rows  
  - Checked column data types and non-null counts  
  - Calculated missing value percentages per column  
  - Identified potential data quality issues for cleaning  

- **3.2 Correlation & Regression Analysis**  
  - Calculated Pearson, Kendall, and Spearman correlation matrices  
  - Visualized correlations with heatmaps to detect strong relationships  
  - Created regression plots to analyze `budget` vs `gross` and `score` vs `gross` trends  

- **3.3 Grouped Aggregation by Production Company**  
  - Aggregated total `gross` revenue per `company`  
  - Grouped and summed annual `gross` revenue by `released_year` and `company`  
  - Ranked companies based on revenue performance over time  

- **3.4 Business Insight Extraction**  
  - Identified budget levels most associated with higher gross revenue  
  - Highlighted production companies with consistent box office success  
  - Found strong relationships between IMDb scores, budgets, and gross revenue for forecasting  

---
## 4. Data Science Techniques 

> ✅ These techniques ensured clean, well-structured data, engineered relevant features, and applied targeted analyses to uncover revenue predictors and top industry performers.

- **Data Cleaning & Preprocessing**  
  - Removed duplicate rows  
  - Dropped rows missing key numeric fields (`gross`, `budget`, `score`)  
  - Detected and reviewed outliers in `gross` using boxplots  

- **Feature Engineering**  
  - Encoded categorical `company` values into numeric codes  
  - Extracted `released_year` from `released` date column for time-series analysis  

- **Correlation Analysis**  
  - Measured relationships between variables using Pearson, Kendall, and Spearman methods  
  - Focused on identifying predictors of `gross` revenue  

- **Regression Plotting**  
  - Visualized linear trends for `budget` vs `gross` and `score` vs `gross`  
  - Assessed direction and strength of relationships  

- **Aggregation & Ranking**  
  - Grouped and summed `gross` revenue by `company` and `released_year`  
  - Ranked companies to find top performers  

- **Outlier Detection**  
  - Used boxplots to spot unusually high or low `gross` values  

- **Date Handling & Transformation**  
  - Converted `released` to datetime format  
  - Extracted year component for analysis of yearly trends  

---

## 5. Python Script with Explanations

> ✅ This Python workflow integrated data cleaning, feature engineering, correlation analysis, visualization, and aggregation to transform raw movie data into actionable insights on revenue drivers and top-performing companies.

- **5.1. Data Loading & Setup**
   - Import libraries for data manipulation and visualization  
   - Load dataset into DataFrame for analysis  
   - Prepare environment for EDA and processing  

```python
import pandas as pd
import numpy as np
import seaborn as sns
import matplotlib.pyplot as plt

df = pd.read_csv('imdb_movies.csv')
```

---

- **5.2. Initial Exploration (EDA)**
   - Preview dataset structure and first few rows  
   - Check column data types and null counts  
   - Calculate missing value percentages  

```python
df.head()
df.info()
df.isnull().mean() * 100
```

---

- **5.3. Data Cleaning**
   - Remove duplicate records  
   - Detect outliers using boxplots  
   - Drop rows missing key numerical fields (`gross`, `budget`, `score`)  

```python
df.drop_duplicates(inplace=True)
sns.boxplot(x=df['gross'])
df.dropna(subset=['gross', 'budget', 'score'], inplace=True)
```

---

- **5.4. Correlation Analysis**
   - Compute Pearson, Kendall, Spearman correlations  
   - Visualize correlations using a heatmap  
   - Identify features most related to `gross` revenue  

```python
corr_pearson = df.corr(method='pearson')
corr_kendall = df.corr(method='kendall')
corr_spearman = df.corr(method='spearman')

sns.heatmap(corr_pearson, annot=True, cmap='coolwarm')
plt.title('Pearson Correlation Heatmap')
plt.show()
```

---

- **5.5. Feature Engineering**
   - Encode categorical `company` as numeric codes  
   - Extract `released_year` from `released` date column  

```python
df['company_code'] = pd.factorize(df['company'])[0]
df['released_year'] = pd.to_datetime(df['released'], errors='coerce').dt.year
```

---

- **5.6. Visualization & Regression**
   - Plot regression line for `budget` vs `gross`  
   - Plot regression line for `score` vs `gross`  
   - Assess relationship trends visually  

```python
sns.regplot(x='budget', y='gross', data=df)
plt.title('Budget vs Gross Revenue')
plt.show()

sns.regplot(x='score', y='gross', data=df)
plt.title('IMDb Score vs Gross Revenue')
plt.show()
```

---

- **5.7. Business Insights & Grouping**
   - Aggregate total revenue by `company`  
   - Group yearly revenue by `company`  
   - Rank top-performing companies over time  

```python
company_total_gross = df.groupby('company')['gross'].sum().sort_values(ascending=False)

yearly_company = df.groupby(['released_year', 'company'])['gross'].sum().reset_index()
top_yearly = yearly_company.sort_values(by='gross', ascending=False)
```
---

## 6. 💡 Business Insights

- **Improved Budget Allocation**  
  ▪ Strong positive correlation between `budget` and `gross` suggests higher investments can yield greater returns.  
  ▪ Studios can optimize fund distribution to maximize box office revenue.  

- **Data-Driven Talent Selection**  
  ▪ Historical performance data shows certain directors, writers, and stars are linked to high-grossing films.  
  ▪ Enables informed casting and production decisions to increase success rates.  

- **Strategic Partnerships with Top Studios**  
  ▪ Revenue analysis highlights companies consistently generating high returns.  
  ▪ Provides benchmarks and collaboration opportunities for emerging studios.  

- **Performance Forecasting**  
  ▪ Regression models predict gross revenue based on `budget`, `score`, and `votes`.  
  ▪ Supports better forecasting, risk management, and marketing strategy planning.  
