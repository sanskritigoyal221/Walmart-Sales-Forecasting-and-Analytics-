# Walmart Sales Forecasting & Causal Analysis

## Overview
This project presents an **end-to-end data science workflow** to analyze and forecast weekly sales for **45 Walmart stores at the department level**. The analysis leverages **historical sales data** and **external economic factors** to build a high-performance predictive model.  

Beyond forecasting, this project also includes an **advanced causal impact analysis** to measure the true financial effect of specific promotional markdown events, providing **actionable insights into marketing effectiveness**.



## Key Findings & Business Insights
The analysis yielded several critical insights into the drivers of retail sales:

- **Dominant Seasonal Patterns**  
  Sales are heavily influenced by a strong yearly seasonality, with a massive, predictable spike in the final weeks of the year corresponding to the **Thanksgiving and Christmas holiday season**.

- **Recent Performance is King**  
  The most powerful predictor of a department's sales is its **performance in the immediately preceding weeks**.  
  The feature `sales_lag_1` (sales from one week ago) was consistently ranked as the most important by the final model.

- **Store & Department Identity are Crucial**  
  Store characteristics are a primary driver of sales volume. **Type 'A' stores consistently outperform Type 'B' and 'C' stores.**  
  The model's reliance on target-encoded Store and Dept features confirms that a store's identity is fundamental to its sales potential.

- **Quantifiable Promotion Impact**  
  A causal impact analysis on a **MarkDown1 promotion for Store 1** estimated that the event generated **~$155,658 in additional sales**, demonstrating a **positive but modest uplift of 0.19%**.



## Technical Workflow & Project Structure
The project is organized into a series of modular **Jupyter Notebooks** for clarity and reproducibility:

1. **01_Data_Cleaning_and_EDA.ipynb**  
   Handles the initial data loading, merging of all data sources, cleaning of missing values, and a comprehensive exploratory data analysis (EDA) to uncover underlying patterns and trends.

2. **02_Feature_Engineering.ipynb**  
   Creates a rich set of time-series features, including **lags, rolling window statistics (mean, standard deviation), and interaction terms.**  
   The final feature-rich dataset is saved for modeling.

3. **03_Modeling_ARIMA.ipynb**  
   Develops and evaluates **classical and modern time-series model (SARIMA)** on the aggregated sales data to establish performance benchmarks.

4. **04_Modeling_XGBoost.ipynb**  
   Implements a **professional-grade machine learning pipeline**. This includes a **time-series aware data split**, **advanced categorical encoding (Target Encoding)**, and the training and evaluation of a **high-performance XGBoost model** on the granular store-department level data.

5. **05_Causal_Impact_Analysis.ipynb**  
   Conducts a **quasi-experimental analysis** using an **XGBoost-based causal model** to isolate and measure the sales impact of a specific promotional event.


## Final Model Performance
A variety of models were evaluated, but the **XGBoost model was the champion**, providing the most accurate and granular forecasts.

- **Model:** XGBoost Regressor  
- **Prediction Level:** Store-Department  
- **Validation MAE:** $1,421.28  

This result indicates that, on average, the model's forecast for a specific department's weekly sales was **off by approximately $1,421**.



## Technologies Used
- **Data Manipulation & Analysis:** Python, Pandas, NumPy  
- **Data Visualization:** Matplotlib, Seaborn  
- **Machine Learning & Modeling:** Scikit-learn, XGBoost, Statsmodels (SARIMA)
- **Causal Inference:** CausalImpact (via a custom XGBoost implementation)  
- **Environment Management:** Conda  

---

## Future Enhancements (Path to Production)
This project serves as a **robust proof-of-concept**. The next steps to productionalize this pipeline would involve:

1. **Cloud Migration**  
   Moving the data pipeline to a cloud platform like **AWS**.  

2. **Automation**  
   Using **AWS S3** for data storage, **AWS Glue** for scheduled ETL and feature engineering, and **Amazon SageMaker** for automated model training and deployment.  

3. **Deployment**  
   Deploying the final **XGBoost model** as a **real-time API endpoint** for on-demand forecasting.  

---
