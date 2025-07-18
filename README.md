# Business Objective 
To identify the key factors that influence a movie's financial success by analyzing the relationships between features such as budget, score, votes, genre, and production company and the movie's gross revenue. This insight aims to support data-driven decision-making in the film industry regarding investment, production, and marketing strategies.

# About the Data 
The dataset was obtained from [IMDP Movies Dataset](https://github.com/TrungLe123692/U.S.-Movies-Data-Analytics-Project) and contains metadata for over 7,600 movies. It includes attributes such as genre, release year, rating, budget, gross revenue, and information about the cast and crew:   

<img width="1030" height="705" alt="hehe" src="https://github.com/user-attachments/assets/8beba694-d036-493c-bf75-3c1c9e80431d" />

## Analysis List 
1. Exploratory Data Analysis (EDA): Performed initial inspection, missing value checks, outlier detection, and data cleaning to understand the structure and quality of the dataset.
2. Correlation & Regression Analysis: Used Pearson, Kendall, and Spearman correlation matrices, as well as regression plots, to uncover relationships between key variables such as budget, score, and gross revenue.
3. Grouped Aggregation Analysis: Aggregated and ranked total and yearly gross revenues by production companies to identify industry leaders and performance trends over time.

## Python Script
1. Data Loading & Setup: Imported libraries (`pandas`, `numpy`, `seaborn`, `matplotlib`) and loaded the movie dataset using `pd.read_csv().`
2. Initial Exploration: Displayed the dataset, reviewed column data types, and calculated missing value percentages to understand data quality.
3. Data Cleaning: Removed duplicate records, visualized outliers in gross using boxplots, and handled missing values.
4. Correlation Analysis: Calculated Pearson, Kendall, and Spearman correlation matrices and visualized them using heatmaps to find key relationships between variables.
5. Feature Engineering: Applied label encoding (factorization) to convert categorical variables to numeric and extracted release year from the `released` column.
6. Visualization & Regression: Created scatter and regression plots to examine the relationships between `budget`, `score`, and `gross earnings.`
7. Business Insights & Grouping: Grouped and ranked production companies by total and annual gross revenue to identify top performers.

## Key Business Impacts
1. Improved Busget Allocation: By identifying a strong positive correlation between budget and gross revenue, studios can make data-driven decisions when allocating funds to maximize return on investment.
2. Data-Driven Talent Selection: The correlation between directors, writers, and stars with high-grossing films highlights the potential of using historical performance data to guide casting and production decisions.
3. Strategic Partnership with Top Studies: Analyzing which production companies consistently generate the highest revenue supports strategic collaboration and benchmarking for emerging studios.
4. Performance Forecasting: Regression and correlation models allow stakeholders to predict box office performance based on measurable features like score, budget, and votes—enabling better forecasting and risk management.

