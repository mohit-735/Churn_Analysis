# Churn_Analysis
📌 Project Description

This project focuses on analyzing customer churn data to identify patterns and key factors that influence customer retention. The analysis explores customer subscriptions, plans, contracts, complaints, escalations, satisfaction scores, churn risk, and revenue impact.

The project uses Python, Pandas, SQLite, SQL, and data visualization to generate meaningful business insights and understand the factors associated with customer churn.

🎯 Project Objectives

The main objectives of this project are:

Analyze overall customer churn.
Identify churn patterns by subscription type.
Analyze churn by plan type and contract type.
Calculate churn rates across different customer segments.
Analyze revenue associated with churned customers.
Calculate revenue at risk from churned customers.
Analyze customer complaints and escalations.
Study the relationship between escalations and churn.
Analyze customer satisfaction and churn.
Create churn risk categories based on churn scores.
Perform correlation analysis to identify relationships between important variables.
Use SQL queries and CTEs for data analysis.
🛠️ Technologies Used
Python
Pandas
NumPy
SQLite
SQL
Matplotlib
Seaborn
Jupyter Notebook
📂 Dataset Features

The dataset contains customer-related information including:

Customer ID
Customer Name
Subscription Start Date
Subscription Type
Renewal Date
Plan Type
Contract Type
Cancellation Date
Cancellation Reason
Monthly Charges
Customer Lifetime Value (CLTV)
Churn Score
Churn Flag
Country
State
Gender
Date of Birth
Complaint Date
Escalations
CSAT Score
Complaint Count
🔍 Key Analysis Performed
1. Data Cleaning and Preparation
Checked dataset structure and data types.
Handled missing values.
Removed unnecessary columns.
Renamed columns for better readability.
Converted columns into appropriate data types.
2. Customer Churn Analysis

The project analyzes churn across different customer segments:

Churn by State
Churn by Subscription Type
Churn by Plan Type
Churn by Contract Type

Example calculation:

df.groupby('plan_type')['churn_flag'].mean() * 100
3. Revenue at Risk

Revenue at risk was calculated using the monthly charges of customers who have churned.

revenue_at_risk = df.loc[
    df['churn_flag'] == 1,
    'monthly_charges'
].sum()

This helps estimate the monthly revenue associated with churned customers.

4. Customer Complaints Analysis

The analysis includes:

Total complaints.
Average complaints per customer.
Relationship between complaints and churn.

Example:

avg_complaints = (
    df['complaint_count'].sum() /
    df['customerid'].nunique()
)
5. Escalation Analysis

Customer escalations were analyzed to understand their relationship with churn.

The analysis includes:

Escalation rate.
Escalated vs non-escalated customers.
Correlation between escalation and churn.
6. Churn Risk Classification

Customers were categorized into risk groups based on their churn score:

Low Risk: Churn Score below 50
Medium Risk: Churn Score between 50 and 69
High Risk: Churn Score 70 and above
conditions = [
    df['churn_score'] < 50,
    (df['churn_score'] >= 50) & (df['churn_score'] < 70),
    df['churn_score'] >= 70
]

choices = ['Low', 'Medium', 'High']

df['churn_risk'] = np.select(
    conditions,
    choices,
    default='Unknown'
)
7. Correlation Analysis

A correlation matrix and heatmap were created to identify relationships between important variables such as:

Churn Score
Churn Flag
Escalations
Churn Risk

This helps identify factors strongly associated with customer churn.

8. SQL Analysis Using Pandas

SQLite SQL queries were executed directly from Python using Pandas.

Example:

query = """
SELECT country,
       SUM(budget) AS total_budget
FROM users
GROUP BY country
"""

df_results = pd.read_sql(query, conn)
9. Common Table Expressions (CTE)

CTEs were used to create readable and structured SQL queries.

Example:

WITH country_budget AS (
    SELECT
        country,
        SUM(budget) AS total_budget
    FROM users
    GROUP BY country
)

SELECT *
FROM country_budget;
📊 Key Business Insights

This analysis helps answer important business questions such as:

Which customer segments have the highest churn rate?
Which subscription plans experience higher churn?
How do escalations impact customer churn?
Are customers with more complaints more likely to churn?
Which customers represent the highest revenue risk?
How does customer satisfaction relate to churn?
Which customers should be prioritized for retention strategies?
📁 Project Structure
Customer-Churn-Analysis/
│
├── customer_churn.db
├── churn_analysis.ipynb
├── README.md
└── requirements.txt
🚀 How to Run the Project
1. Clone the repository
git clone <your-repository-url>
2. Install required libraries
pip install pandas numpy matplotlib seaborn
3. Open Jupyter Notebook
jupyter notebook
4. Run the notebook

Open:

churn_analysis.ipynb

Run all cells to perform the complete analysis.

📈 Skills Demonstrated
Data Cleaning
Exploratory Data Analysis (EDA)
Customer Churn Analysis
Feature Engineering
SQL Queries
SQLite Database
Common Table Expressions (CTEs)
Data Aggregation
Correlation Analysis
Data Visualization
Business Insight Generation
Python and Pandas
