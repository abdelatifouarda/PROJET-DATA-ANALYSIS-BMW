# BMW Sales & Marketing Performance Analysis

## Executive Summary
This project analyzes a ~1,000-record BMW vehicle sales dataset to understand how pricing, marketing spend, and dealership presence relate to sales performance across three vehicle segments (Electric, SUV, Sedan). Beyond exploratory analysis, the project tests multiple machine learning approaches (classification, regression, and unsupervised methods) and — just as importantly — demonstrates the judgment to identify which techniques actually add business value and which do not.

## Business Problem
Understanding what drives vehicle sales and marketing efficiency across product segments is essential for allocating marketing budget effectively and setting pricing strategy. This project explores whether sales volume can be explained and predicted from pricing, marketing investment, and distribution (dealership count), and whether vehicle segment itself can be inferred from sales behavior.

## Business Objectives
- Analyze price, revenue, and marketing-efficiency trends across vehicle segments and over time.
- Identify which factors most strongly explain sales volume.
- Test whether vehicle segment can be predicted from sales and distribution data.
- Apply and honestly evaluate dimensionality-reduction and clustering techniques for exploratory value.

## Dataset
A structured dataset of 1,000 records covering BMW vehicle sales across 3 segments (Electric, SUV, Sedan), 4 engine types, and 10 countries, with fields including price, units sold, marketing spend, dealership count, and macroeconomic indicators (fuel price, GDP growth, interest rate, competition index). No missing values were found in any column. The balanced distribution across categories is consistent with a structured/simulated dataset used for analytical practice.

## Project Workflow
1. **Data Cleaning** — Verified data types and confirmed no missing values; created derived columns (revenue, marketing spend per car, scaled units for readability).
2. **Exploratory Data Analysis** — Examined sales trends by segment over time, revenue by segment, pricing by segment, and marketing spend efficiency by segment and year.
3. **Feature Engineering** — Built aggregated views (by year/segment, and by country/segment/engine type/model) to support comparison metrics and marketing-efficiency indicators.
4. **Predictive Modeling**:
   - **Classification** — Tested Decision Tree, Random Forest, SVM, and KNN to predict vehicle segment from sales and dealership data.
   - **Regression** — Used Ridge, Lasso, and ElasticNet to predict units sold from price, marketing spend, and dealership count; used Gradient Boosting (with hyperparameter tuning) to predict dealership count from price, units sold, and marketing spend.
5. **Unsupervised Exploration** — Applied PCA and K-Means clustering as an exploratory exercise to test whether natural groupings exist in the data.

## Technologies Used
- **Python**, **Pandas**, **NumPy**
- **Scikit-learn** (Ridge, Lasso, ElasticNet, Gradient Boosting, Decision Tree, Random Forest, SVM, KNN, PCA, K-Means, GridSearchCV)
- **Matplotlib**, **Seaborn**, **Plotly**

## Results
- **Regression (strongest result)**: Predicting units sold from price, marketing spend, and dealership count achieved **R² ≈ 0.76** with Ridge and Lasso regression (RMSE ≈ 128 units), showing these three factors explain the large majority of sales variance.
- **Gradient Boosting** (predicting dealership count): cross-validated R² ≈ 0.75 after hyperparameter tuning. *(Final test-set R²/RMSE/MAE should be re-verified — the current notebook cell references an undefined variable when printing these values and needs a small fix before the exact test numbers are considered final.)*
- **Classification**: None of the tested models (Decision Tree, Random Forest, SVM, KNN) reliably predicted vehicle segment from units sold and dealership count alone — the best result was KNN at 42% accuracy, only modestly above the ~33% baseline for a 3-class problem. This is a clear, evidence-based conclusion that these two features do not carry enough signal to distinguish segments — not a failure of the modeling process.
- **PCA / K-Means**: Applied as an exploratory exercise; the resulting components and clusters showed substantial overlap between segments, consistent with — and reinforcing — the classification result above. These methods were correctly not used for business decision-making given the weak separation found.

## Business Insights
- Sales volume is strongly and predictably related to price, marketing spend, and dealership presence (R² ≈ 0.76), making these three levers the most actionable for forecasting and planning.
- Vehicle segment cannot be reliably inferred from sales volume and dealership count alone, indicating that segment-level performance differences are driven by factors beyond these two variables (e.g., pricing strategy or marketing approach itself, which show clearer segment-level patterns in the EDA).
- Electric vehicle marketing spend per car is lower than SUV and Sedan, while EV sales have grown — suggesting a more efficient marketing/distribution model for this segment worth studying further.

## Business Recommendations
- Use the price/marketing-spend/dealership-count regression model as a starting point for sales forecasting and marketing-budget planning, given its strong explanatory power.
- Investigate what makes Electric vehicle marketing more capital-efficient (lower spend per car) and evaluate whether elements of that approach transfer to SUV and Sedan marketing.
- Avoid relying on PCA/clustering-based segment groupings for this dataset in its current form — the data does not currently support them; prioritize collecting more segment-differentiating features (e.g., customer demographics, region-specific marketing channels) if segment-level modeling is a future goal.


## Author
Junior Data Analyst — Data Analysis & Machine Learning.
