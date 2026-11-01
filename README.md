# Customer Shopping Behavior - End-to-End Data Analytics Project

## 📌 Overview
This project presents an end-to-end data analytics workflow analyzing customer purchasing patterns, demographics, and transactional behavior. The project pipeline encompasses raw data ingestion, exploratory data analysis (EDA), data cleaning, feature engineering using Python, relational database storage and advanced SQL querying, an interactive Power BI dashboard, and an executive presentation created with Gamma.

---

## 📂 Dataset
- **Source Dataset:** `customer_shopping_behavior.csv`
- **Total Records:** 3,900 rows
- **Key Columns:** 
  - **Demographics:** `Customer ID`, `Age`, `Gender`, `Location`
  - **Item Info:** `Item Purchased`, `Category`, `Size`, `Color`, `Season`
  - **Transactions:** `Purchase Amount (USD)`, `Review Rating`, `Subscription Status`, `Shipping Type`, `Discount Applied`, `Previous Purchases`, `Payment Method`, `Frequency of Purchases`

---

## 🛠️ Tools & Tech Stack
- **Python (Pandas, SQLAlchemy):** Data ingestion, exploratory analysis, cleaning, feature engineering, and database loading.
- **PostgreSQL:** Relational database management and business intelligence querying (SQL).
- **Power BI:** Data modeling and interactive dashboard visualization.
- **Gamma:** Executive presentation design.

---

## 🚀 Steps & Workflow

### 1. Exploratory Data Analysis & Data Cleaning (Python)
- **Missing Value Imputation:** Handled missing values in `Review Rating` by imputing median ratings grouped by product `Category`.
- **Column Standardization:** Lowercased all column headers and replaced spaces with underscores (`purchase_amount_(usd)` $\rightarrow$ `purchase_amount_usd`).
- **Feature Engineering:**
  - Created `age_group` (`Young Adult`, `Adult`, `Middle Aged`, `Senior`) via quantile binning.
  - Converted textual purchase frequencies (`Weekly`, `Monthly`, `Annually`) into numerical values (`purchase_frequency_days`).
  - Removed redundant attributes (e.g., `promo_code_used`).

### 2. Database Integration & Advanced SQL Querying
Loaded the cleaned dataset into PostgreSQL (`customer_behavior` database) and executed key analytics queries:
1. **Gender Revenue Share:** Calculated total revenue contributions between Male and Female customers.
2. **High-Value Discount Users:** Identified customers using discounts who still spent above the average purchase value.
3. **Top Rated Products:** Ranked top 5 items based on average review ratings.
4. **Shipping Comparisons:** Compared average spend between `Standard` and `Express` shipping.
5. **Subscription Impact:** Analyzed total revenue and average spend between subscribers vs. non-subscribers.
6. **Discount Reliance:** Identified top 5 products with the highest percentage of discount-driven purchases.
7. **Customer Segmentation:** Segmented buyers into `New`, `Returning`, and `Loyal` based on previous order counts.
8. **Category Rankings:** Utilized SQL window functions (`ROW_NUMBER()`) to extract top 3 items in each category.
9. **Loyalty & Subscriptions:** Evaluated subscription adoption among repeat customers ($>5$ purchases).
10. **Demographic Revenue:** Identified the highest revenue-generating age brackets.

### 3. Power BI Dashboard & Reporting
- Developed an interactive Power BI dashboard (`.pbix`) tracking key KPIs: Total Revenue, Average Order Value, Customer Distribution, and Category Performance.
- Built interactive slicers for `Gender`, `Category`, `Season`, and `Subscription Status`.

---

## 📊 Dashboard Key Metrics & Results
- **Demographics:** Middle-Aged and Adult age groups contribute the highest percentage to overall store revenue.
- **Subscriptions:** Subscribers demonstrate higher overall lifetime value and order frequency compared to non-subscribers.
- **Promotions:** Discount applications significantly drive volume for specific clothing items, offering insights for margin optimization.

---

## ⚙️ How to Run Locally

### Prerequisites
- Python 3.x
- PostgreSQL Server
- Power BI Desktop

### Setup Steps
1. **Clone the Repository:**
   ```bash
   git clone https://github.com/your-username/customer-shopping-behavior-analytics.git
   cd customer-shopping-behavior-analytics
   ```

2. **Install Python Libraries:**
   ```bash
   pip install pandas sqlalchemy psycopg2-binary
   ```

3. **Run Data Pipeline Notebook:**
   Run `code.ipynb` to clean the raw data and push the processed dataset into your local PostgreSQL server.

4. **Run SQL Queries:**
   Execute `customers_data_sql_code.sql` using PostgreSQL (pgAdmin/DBeaver) to perform the analytics queries.

5. **View Dashboard:**
   Open `customer_behavior_dashboard.pbix` in **Power BI Desktop** to inspect the interactive dashboards.
