README.md – Sales Summary & Visualization using SQLite + Python

📌 Objective
The goal of this task was to:
Create and populate a SQLite sales database.
Use SQL queries inside Python to retrieve summarized sales information (total quantity, total revenue).
Display the results using Pandas.
Create multiple visualizations using Matplotlib.
Handle common errors encountered during database operations.

🛠️ Tools & Libraries Used
Python (v3.x)
SQLite3 (built-in Python library)
Pandas (for data handling)
Matplotlib (for visualizations)

📂 Steps Performed
1. Database Creation & Table Setup
Connected to SQLite using:
import sqlite3
conn = sqlite3.connect("sales_data.db")
Created a sales table with the following columns:
id (Primary Key)
product (TEXT)
quantity (INTEGER)
price (REAL)
sale_date (TEXT)
region (TEXT)
Inserted sample sales records for multiple products, dates, and regions.

2. SQL Query to Get Sales Summary
Ran the query:
SELECT 
    product, 
    SUM(quantity) AS total_qty, 
    SUM(quantity * price) AS revenue
FROM sales
GROUP BY product;
Loaded the query results into a Pandas DataFrame for further analysis.

3. Visualizations Created
Revenue by Product – Bar chart.
Quantity Sold by Product – Bar chart.
Revenue Share by Product – Pie chart.
Revenue & Quantity Combined – Dual-axis chart.
Enhancements included:
Custom colors.
Value labels.
Gridlines.
Bold titles.
High-resolution images using:
plt.savefig("chart_name.png", dpi=300, bbox_inches="tight")

⚠️ Errors Faced & Fixes
OperationalError: table sales has no column named sale_date
Cause: Attempted to insert data with sale_date & region columns into an existing table that did not have these columns.
Fix: Dropped the old table and recreated it with the correct schema using:
cursor.execute("DROP TABLE IF EXISTS sales")

ProgrammingError: Cannot operate on a closed database
Cause: Tried running queries on a connection that had already been closed with conn.close().

Fix: Ensured all queries were run before closing the connection or reconnected before querying:
conn = sqlite3.connect("sales_data.db")
need to perform closed on closed connection
Cause: Attempted to close a database connection twice.
Fix: Added checks to only close once at the end of the process.

📊 Final Output
Sales summary table printed in the console.
Four different visualizations saved as .png images:
revenue_by_product.png
quantity_by_product.png
revenue_share_pie.png
revenue_quantity_combined.png

📎 How to Run the Script
Install dependencies:
pip install pandas matplotlib

Run the Python script:
python sales_analysis.py
Check the console for the sales summary.
Check the working directory for saved chart images.

✅ Deliverables Submitted
sales_analysis.py – Python script with all steps.
Chart images – .png files for each visualization.
README.md – Documentation of the process.