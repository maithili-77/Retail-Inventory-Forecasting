# Retail-Inventory-Forecasting
Retail businesses often suffer revenue loss due to stock-outs (products running out of inventory).
This project builds an end-to-end data science solution that forecasts daily product demand and predicts stock-out risk using historical sales data.

**The system helps answer:**

 1)How many units will sell daily?
2) How many days before inventory runs out?
3) Which products are at high risk of stock-out

# Business Problem
Retail demand fluctuates due to seasonality, weekdays, and trends
Inventory data is often unavailable or delayed
Poor forecasting leads to lost sales or overstocking
Solution

**Use time-series feature engineering + machine learning to:**

Predict daily demand
Estimate inventory coverage
Flag high-risk products before stock-out

#Dataset Description

Transaction-level retail sales data.

Column	Description
transaction_id	Unique transaction ID
date	Transaction date
customer_id	Customer identifier
product_category	Product category
quantity	Units sold
price_per_unit	Unit price
total_amount	Total transaction value

Feature Engineering
Time-Based Features
day_of_week
month
week_of_year
is_weekend
Lag Features (Demand Memory)
sales_lag_1
sales_lag_7
sales_lag_14
Rolling Statistics
rolling_mean_7
rolling_mean_14

These features allow the model to learn seasonality, trends, and past demand behavior.

# Model Used

Random Forest Regressor

Handles non-linear demand patterns
Robust for tabular retail data
Minimal feature scaling required
 Train–Test Strategy
Time-based split (shuffle=False)
Prevents data leakage
Mimics real forecasting conditions
 Inventory Estimation Logic

Since inventory data was unavailable, inventory was estimated using business assumptions:

Estimated Inventory = Predicted Daily Demand × 14 days

 This reflects real retail practice where stores maintain 1–2 weeks of stock.

*#Stock-Out Risk Calculation#
Days to Stock-Out = Inventory / Predicted Daily Demand
Risk Classification
Condition	Risk
Days ≤ Supplier Lead Time (7 days)	🚨 HIGH RISK
Days > Lead Time	
# Final Output

The model produces actionable insights:

Product Category	Inventory	Predicted Daily Demand	Days to Stock-Out	Risk
Electronics	140	22	6	HIGH RISK
Clothing	280	10	28	SAFE

**Tech Stack**:
Python
Pandas, NumPy
Scikit-learn
Matplotlib / Seaborn

**Key Learnings**:
Time-series feature engineering
Real-world data limitations handling
Demand forecasting with ML
Inventory planning logic
Business-driven model evaluation

# Author

Maithili Mahajan
Aspiring Data Scientist | Business & Data Analytics
