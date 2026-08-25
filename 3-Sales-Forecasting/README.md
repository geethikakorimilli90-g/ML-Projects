# 📈 Sales Forecasting Using Machine Learning

## 📝 Project Overview

Sales forecasting is an important business application of Machine Learning and time-series analysis. Accurate sales predictions can help organizations make better decisions related to inventory planning, resource allocation, financial forecasting, and business strategy.

This project develops an end-to-end **Machine Learning-based Sales Forecasting system** that analyzes historical daily sales data and predicts future sales.

The project follows a complete data science workflow:

* Data creation and loading
* Data understanding
* Data cleaning
* Exploratory Data Analysis (EDA)
* Feature engineering
* Time-series train-test splitting
* Training multiple Machine Learning models
* Model evaluation and comparison
* Best model selection
* Future sales forecasting
* Feature importance analysis
* Business insight generation
* Model and forecast result saving

The final system generates a **30-day future sales forecast** using the best-performing Machine Learning model.

---

# 🎯 Project Objective

The primary objective of this project is to predict future daily sales using historical sales information.

The project aims to:

* Analyze historical sales patterns.
* Identify sales trends and seasonal fluctuations.
* Transform date information into useful Machine Learning features.
* Create lag-based features using previous sales values.
* Create rolling average features to capture recent sales behavior.
* Train and compare multiple Machine Learning models.
* Evaluate model performance using regression metrics.
* Select the best-performing model.
* Predict sales for the next 30 days.
* Generate useful insights for business decision-making.

---

# 📊 Dataset Description

For this project, a daily sales dataset was created using Python.

The dataset covers the period from:

**January 1, 2022 to December 31, 2024**

The dataset contains:

| Column  | Description              |
| ------- | ------------------------ |
| `Date`  | Date of the sales record |
| `Sales` | Daily sales value        |

The sales data was generated using a combination of:

* Base sales values
* A gradual long-term trend
* Seasonal patterns
* Random variation

This allows the dataset to simulate realistic sales behavior for Machine Learning experimentation.

---

# 🛠️ Technologies Used

The following technologies and libraries were used in this project:

### Programming Language

* Python

### Data Analysis

* Pandas
* NumPy

### Data Visualization

* Matplotlib
* Seaborn

### Machine Learning

* Scikit-learn
* XGBoost

### Model Saving

* Joblib

### Development Environment

* Google Colab

### Version Control

* GitHub

---

# 🔄 Project Workflow

```text
Historical Sales Data
        ↓
Data Understanding
        ↓
Data Cleaning
        ↓
Exploratory Data Analysis
        ↓
Feature Engineering
        ↓
Time-Based Train-Test Split
        ↓
Machine Learning Model Training
        ↓
Model Evaluation and Comparison
        ↓
Best Model Selection
        ↓
30-Day Future Sales Forecast
        ↓
Feature Importance Analysis
        ↓
Business Insights
        ↓
Save Model and Forecast Results
```

---

# 🔍 Exploratory Data Analysis (EDA)

Exploratory Data Analysis was performed to understand the behavior of the sales data before training Machine Learning models.

The following analyses were included:

## 1. Daily Sales Trend

A line graph was created to visualize daily sales over time.

This analysis helps identify:

* Overall sales trends
* Seasonal patterns
* Sales fluctuations
* High-sales periods
* Low-sales periods

---

## 2. Monthly Sales Comparison

Sales were grouped by month and year to compare sales performance across different periods.

This analysis helps understand:

* Monthly sales differences
* Seasonal changes
* Year-over-year patterns

---

## 3. Sales Distribution

A histogram was created to understand the distribution of sales values.

This helps analyze:

* The most common sales range
* Sales variability
* Extreme values
* Overall distribution patterns

---

## 4. Monthly Average Sales

Average sales were calculated for each month.

This analysis can help identify months with:

* Higher average demand
* Lower average demand
* Possible seasonal effects

---

# ⚙️ Feature Engineering

Feature engineering is one of the most important parts of this project.

Raw date and sales data were transformed into useful Machine Learning features.

---

## 📅 Date-Based Features

The following date features were created:

| Feature      | Description              |
| ------------ | ------------------------ |
| `Year`       | Year of the sales record |
| `Month`      | Month number             |
| `Day`        | Day of the month         |
| `DayOfWeek`  | Day of the week          |
| `WeekOfYear` | Week number in the year  |
| `Quarter`    | Business quarter         |

These features help the Machine Learning models identify:

* Monthly patterns
* Weekly patterns
* Seasonal trends
* Long-term changes

---

# ⏮️ Lag Features

Lag features represent previous sales values.

The following lag features were created:

| Feature  | Description                 |
| -------- | --------------------------- |
| `Lag_1`  | Sales from the previous day |
| `Lag_7`  | Sales from 7 days earlier   |
| `Lag_30` | Sales from 30 days earlier  |

Lag features are important because future sales often depend on historical sales patterns.

For example:

```text
Today's Sales Prediction
        ↓
Previous Day Sales
        ↓
Previous Week Sales
        ↓
Previous Month Sales
```

These features allow the model to learn relationships between historical sales and future sales.

---

# 📉 Rolling Average Features

Rolling averages were also created to capture recent sales trends.

The following features were used:

| Feature           | Description                             |
| ----------------- | --------------------------------------- |
| `Rolling_Mean_7`  | Average sales from the previous 7 days  |
| `Rolling_Mean_30` | Average sales from the previous 30 days |

Rolling averages help reduce the effect of daily fluctuations and provide information about recent sales behavior.

---

# 🚫 Data Leakage Prevention

An important consideration in forecasting is preventing data leakage.

Rolling average features were created using:

```python
shift(1)
```

This ensures that only previous sales data is used to predict the current or future sales value.

The model does not use the actual sales value of the day being predicted.

This is important because using future information during training would produce unrealistic model performance.

---

# ✂️ Time-Based Train-Test Split

The dataset was divided into:

* **80% Training Data**
* **20% Testing Data**

Unlike standard Machine Learning problems, the data was not randomly shuffled.

The split was performed based on chronological order.

```text
2022 ─────────────── 2024

|-------- Training Data --------|--- Testing Data ---|
             80%                       20%

Past Sales                         Future Sales
```

This approach ensures that:

* The model learns from historical data.
* The model is evaluated on unseen future data.
* The forecasting scenario remains realistic.

---

# 🤖 Machine Learning Models

Three regression models were trained and compared.

---

## 1️⃣ Linear Regression

Linear Regression was used as a baseline model.

It attempts to learn a linear relationship between the input features and sales.

Advantages:

* Simple and easy to interpret
* Fast training
* Useful as a baseline model

---

## 2️⃣ Random Forest Regressor

Random Forest is an ensemble Machine Learning algorithm.

It uses multiple decision trees and combines their predictions.

Advantages:

* Can capture complex relationships
* Handles non-linear patterns
* Reduces overfitting through ensemble learning
* Works effectively with engineered features

---

## 3️⃣ XGBoost Regressor

XGBoost is a gradient boosting algorithm.

It builds models sequentially, where new trees focus on improving previous prediction errors.

Advantages:

* High predictive performance
* Captures complex relationships
* Effective for tabular data
* Commonly used in real-world Machine Learning applications

---

# 📏 Model Evaluation

The models were evaluated using three regression metrics.

---

## Mean Absolute Error (MAE)

MAE measures the average absolute difference between actual and predicted sales.

```text
Lower MAE = Better Model
```

A lower MAE means the predictions are closer to the actual values on average.

---

## Root Mean Squared Error (RMSE)

RMSE measures prediction error while giving more importance to larger errors.

```text
Lower RMSE = Better Model
```

RMSE was used as the primary metric for selecting the best-performing model.

---

## R² Score

The R² score measures how much variation in sales is explained by the model.

```text
Higher R² Score = Better Model
```

A higher value generally indicates that the model explains more of the variation in the target variable.

---

# 🏆 Model Comparison

The following models were compared:

| Model             |                         MAE |                        RMSE |                    R² Score |
| ----------------- | --------------------------: | --------------------------: | --------------------------: |
| Linear Regression | Calculated during execution | Calculated during execution | Calculated during execution |
| Random Forest     | Calculated during execution | Calculated during execution | Calculated during execution |
| XGBoost           | Calculated during execution | Calculated during execution | Calculated during execution |

The best model is selected based on the lowest RMSE value.

```text
Model Evaluation
       ↓
Compare MAE
       ↓
Compare RMSE
       ↓
Compare R² Score
       ↓
Select Best Model
```

> **Note:** Model performance values depend on the generated dataset and the environment in which the notebook is executed.

---

# 🔮 Future Sales Forecasting

After selecting the best-performing model, the system predicts sales for the next 30 days.

The forecasting process works recursively.

```text
Historical Sales Data
        ↓
Predict Day 1
        ↓
Use Prediction as Historical Input
        ↓
Predict Day 2
        ↓
Continue Sequentially
        ↓
Generate 30-Day Forecast
```

For each future day:

1. The next date is generated.
2. Date-based features are created.
3. Lag features are calculated using historical values.
4. Rolling average features are calculated.
5. The Machine Learning model generates a prediction.
6. The predicted value is added to the historical sequence.
7. The process continues until all 30 days are predicted.

---

# 📈 Forecast Analysis

The future forecast provides the following information:

* Total expected sales for the next 30 days
* Average predicted daily sales
* Highest predicted sales value
* Lowest predicted sales value
* Highest expected sales day
* Lowest expected sales day

These predictions can help businesses prepare for future demand.

---

# 📊 Feature Importance Analysis

Feature importance analysis was performed to understand which variables have the greatest influence on the sales predictions.

Depending on the selected model:

* Linear Regression uses coefficient magnitude.
* Random Forest uses feature importance scores.
* XGBoost uses feature importance scores.

The analysis helps identify whether factors such as:

* Previous day sales
* Previous week sales
* Previous month sales
* Recent sales averages
* Monthly patterns
* Day-of-week patterns

have a strong influence on the forecast.

---

# 💼 Business Insights

The forecasting system provides several useful business insights.

## 📦 Inventory Planning

Predicted future demand can help businesses maintain appropriate inventory levels.

Higher predicted sales may indicate a need for increased stock.

Lower predicted sales may indicate a need to reduce unnecessary inventory.

---

## 📈 Demand Identification

The forecast can identify:

* High-demand periods
* Low-demand periods
* Expected sales fluctuations

This can help businesses prepare in advance.

---

## 💰 Financial Planning

Future sales predictions can support:

* Revenue planning
* Budget preparation
* Financial forecasting

---

## 🎯 Business Decision-Making

Sales forecasting can help decision-makers make data-driven decisions rather than relying only on intuition.

---

# 📁 Project Structure

```text
3-Sales-Forecasting/
│
├── sales_forecasting.ipynb
│
├── best_sales_forecasting_model.pkl
│
├── future_sales_forecast.csv
│
└── README.md
```

### File Description

| File                               | Description                                  |
| ---------------------------------- | -------------------------------------------- |
| `sales_forecasting.ipynb`          | Complete Machine Learning project notebook   |
| `best_sales_forecasting_model.pkl` | Saved best-performing Machine Learning model |
| `future_sales_forecast.csv`        | Predicted sales for the next 30 days         |
| `README.md`                        | Complete project documentation               |

---

# 🚀 How to Run the Project

## Step 1: Clone the Repository

```bash
git clone https://github.com/divyasreesompalli23/ML-Projects.git
```

---

## Step 2: Navigate to the Project Folder

```bash
cd ML-Projects/3-Sales-Forecasting
```

---

## Step 3: Install Required Libraries

```bash
pip install pandas numpy matplotlib seaborn scikit-learn xgboost joblib
```

---

## Step 4: Open the Notebook

Open:

```text
sales_forecasting.ipynb
```

You can run the notebook using:

* Google Colab
* Jupyter Notebook
* JupyterLab

---

## Step 5: Run the Notebook

Run all cells sequentially.

The project will:

1. Create the sales dataset.
2. Perform data cleaning.
3. Perform exploratory data analysis.
4. Create forecasting features.
5. Split data chronologically.
6. Train multiple Machine Learning models.
7. Compare model performance.
8. Select the best model.
9. Generate a 30-day sales forecast.
10. Save the trained model and forecast results.

---

# 💡 Key Learnings

This project demonstrates several important Machine Learning and forecasting concepts.

### Data Analysis

Understanding data before building a model.

### Feature Engineering

Creating useful features from raw date and sales information.

### Time-Series Thinking

Preserving chronological order while training and testing models.

### Lag Features

Using previous observations to predict future values.

### Rolling Features

Using recent averages to capture sales behavior.

### Model Comparison

Training multiple algorithms instead of depending on a single model.

### Regression Evaluation

Using MAE, RMSE, and R² Score to evaluate performance.

### Future Forecasting

Using historical information to generate future predictions.

### Business Analytics

Converting Machine Learning predictions into actionable insights.

---

# 🔮 Future Improvements

The project can be extended further by adding:

* Real-world sales datasets
* Product-level forecasting
* Store-level forecasting
* Holiday features
* Promotion and discount information
* Weather information
* External economic indicators
* Hyperparameter tuning
* TimeSeriesSplit cross-validation
* Prophet forecasting
* ARIMA or SARIMA models
* Deep Learning models such as LSTM
* Streamlit interactive dashboard
* Real-time sales data integration
* Cloud deployment

---

# ⚠️ Project Limitations

The current project uses a synthetic dataset designed for Machine Learning practice.

Therefore:

* The predictions do not represent the sales of a real business.
* Real-world forecasting may require additional features.
* Recursive multi-day forecasting can accumulate prediction errors over longer forecast periods.
* Performance depends on the quality and availability of historical data.

Despite these limitations, the project demonstrates a complete end-to-end workflow for Machine Learning-based sales forecasting.

---

# 🏁 Conclusion

This project successfully develops a complete **Machine Learning-based Sales Forecasting system** using historical sales data.

The project demonstrates an end-to-end workflow involving:

* Data preparation
* Data cleaning
* Exploratory Data Analysis
* Feature engineering
* Lag and rolling features
* Time-based train-test splitting
* Multiple Machine Learning models
* Model evaluation
* Best model selection
* 30-day future sales forecasting
* Feature importance analysis
* Business insights

The system compares **Linear Regression, Random Forest, and XGBoost** to identify the most suitable model based on predictive performance.

The selected model is then used to forecast future sales and generate insights that can support:

* Inventory planning
* Demand forecasting
* Financial planning
* Business strategy
* Data-driven decision-making

Overall, this project demonstrates how Machine Learning can transform historical sales data into meaningful future predictions and actionable business insights.

---

# 👩‍💻 Author

**Geethika**

Machine Learning Enthusiast | Aspiring Data Professional

---

## ⭐ If you found this project useful, consider giving the repository a star!

