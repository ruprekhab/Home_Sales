# Home Sales Analysis with SparkSQL
## Overview
This project leverages SparkSQL to analyze home sales data and extract key insights. Using PySpark, we process and query large datasets efficiently, exploring various metrics related to home prices based on factors like bedrooms, bathrooms, square footage, and view ratings.

## Setup and Data Import

* Imported the necessary PySpark SQL functions for data processing.

* Read home_sales_revised.csv from the provided AWS S3 bucket into a PySpark DataFrame.

* Created a temporary table named home_sales.

## Data Analysis with SparkSQL
<p>Run the following queries using SparkSQL:

**Key Metrics**
1. Average price of four-bedroom houses sold per year (rounded to two decimal places).

2. Average price of homes built each year with three bedrooms and three bathrooms (rounded to two decimal places).

3. Average price of homes built each year with:

* Three bedrooms

* Three bathrooms

* Two floors

* Square footage >= 2,000

* (Rounded to two decimal places)

4. Average price of a home per "view" rating where the average price is >= $350,000. Also, determine the runtime.

## Performance Optimization

* Cache the home_sales table.

* Check if the table is cached.

* Re-run the last query using the cached table and compare runtime with the uncached version.

## Data Partitioning and Parquet Format

* Partition the dataset by the date_built field and save it in Parquet format.

* Create a temporary table from the Parquet data.

* Re-run the last query and compare runtime with the uncached version.

## Cleanup

* Uncache the home_sales temporary table.

* Verify that the table is uncached using PySpark.

## Observation Summary:
* Caching (0.44s) was the fastest, as Spark retrieved data from memory.
* Partitioning (0.87s) was slower than caching but still improved over the uncached query (1.18s) due to efficient data pruning.
* Partitioning did not outperform caching because caching keeps frequently accessed data in memory, while partitioning still requires disk access.
<p>**Conclusion:** While partitioning improved query efficiency by reducing scanned data, caching is more effective when running repeated queries on the same dataset.


## Technologies Used
* Apache Spark (PySpark)

* SparkSQL

* Parquet (for optimized data storage and retrieval)

* Jupyter Notebook



