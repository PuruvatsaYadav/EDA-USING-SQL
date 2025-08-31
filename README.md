Project: EDA using SQL on Electronics Data

I started by creating a database and loading the CSV file into a table using `LOAD DATA INFILE`. Then I checked the structure with `DESCRIBE` to understand the columns.

Next, I focused on data cleaning:

* Cleaned the **Price** column by removing “\$” and “,” with `REPLACE()` and handled ranges (like “1000 through 2000”) using `SUBSTRING_INDEX()`.
* Standardized the **Discount** column by creating a new flag (`discount_given`) with `CASE WHEN`, and calculated **MRP** with logic inside `CASE`.
* Extracted **ratings** and **review counts** from text using `REGEXP_SUBSTR()`, then stored them in new columns using `ALTER TABLE` and `UPDATE`.
* Pulled out the **brand name** from the product title using `SUBSTRING_INDEX()` and then cleaned inconsistencies with `UPDATE`.
* Dropped unnecessary columns like `Currency` with `ALTER TABLE DROP COLUMN`.

After cleaning, I moved to **EDA**:

* Ran summary stats on Price with `MIN()`, `MAX()`, `AVG()`, `STDDEV()`.
* Checked null values with `COUNT()`.
* Used `PERCENT_RANK()` in a stored procedure to calculate percentiles.
* Grouped data with `GROUP BY` to get brand-level and category-level insights.
* Built price **buckets** using `CASE` statements to see distribution patterns.
  
* Explored relationships:
   * Between **average\_rating** and **reviews\_count** using covariance and correlation formulas.
   * Between **Price** and **MRP** with a regression slope formula in SQL.
* Created contingency tables with `COUNT(DISTINCT ...)` to check which brands cover multiple subcategories.

By the end, I had a clean dataset and insights like: how discounts affect MRP
which brands are more consistent in pricing, distribution of products by sub-category, and the weak but positive relation between reviews and ratings.
