# AI Data Quality Pipeline

## Project Overview

This project demonstrates a modern data engineering pipeline for an e-commerce application. The pipeline uses Apache Spark and Delta Lake to ingest, validate, clean, store, and analyze e-commerce order data.

## Problem Description

E-commerce data may contain missing values, duplicate orders, invalid quantities, invalid prices, and invalid order statuses.

The goal of this project is to build a data quality pipeline that identifies invalid records, separates trusted data from failed records, and produces useful business analytics from the clean data.

## Data Source

The project uses a small synthetic e-commerce dataset created specifically for data quality testing.

The dataset contains order information including:

- Order ID
- Customer ID
- Product ID
- Order Date
- Quantity
- Unit Price
- Order Status
- Customer City
- Payment Method

The raw data is stored as a CSV file and ingested using Apache Spark.

## Workflow / Architecture

The pipeline follows these steps:

1. Data Source
2. Data Ingestion
3. Apache Spark Processing
4. Data Quality Checks
5. PASS / FAIL Quality Gate
6. Clean Data or Quarantine
7. Delta Lake Storage
8. Analytics and Business Insights

The architecture diagram is available in:

`architecture.png`

## Data Quality Checks

The pipeline implements several data quality checks:

### 1. Completeness

Checks for missing required values, including missing quantity.

### 2. Uniqueness

Checks for duplicate `order_id` values.

### 3. Validity

Checks that:

- Quantity is greater than zero.
- Unit price is greater than zero.
- Order status belongs to the accepted status values.

Valid statuses include:

- Completed
- Pending
- Returned
- Cancelled

### Quality Gate

Records that pass all quality checks are marked:

`PASS`

Records that fail one or more checks are marked:

`FAIL`

PASS records continue to the trusted data layer.

FAIL records are sent to the Quarantine area together with the reason for failure.

## Analytics Output

The clean data is used to produce business analytics including:

- Total Sales
- Total Valid Orders
- Average Order Value
- Sales by City
- Sales by Product

The project also includes bar charts for sales by city and sales by product.

## Results

The pipeline processed 20 total records.

The quality gate identified:

- 14 passed records
- 6 failed records

The total sales from the trusted data were:

`5,346 SAR`

The average order value was calculated from the trusted records.

The pipeline also generated sales summaries by customer city and product.

## Technologies Used

- Python
- Apache Spark
- PySpark
- Delta Lake
- Pandas
- Matplotlib
- Google Colab
- GitHub

## How to Run the Project

1. Open `AI_Data_Quality_Pipeline.ipynb` in Google Colab.
2. Run the notebook cells from top to bottom.
3. The notebook installs the required PySpark and Delta Lake packages.
4. The pipeline creates the required data directories.
5. The synthetic dataset is generated and saved as CSV.
6. Apache Spark loads and processes the data.
7. Data quality checks are applied.
8. Valid records are stored in Delta Lake.
9. Failed records are stored in the Quarantine area.
10. Analytics and visualizations are generated.

## Future Improvements

Possible future improvements include:

- Using a larger real-world dataset.
- Adding automated data quality monitoring.
- Adding more business validation rules.
- Using cloud storage such as AWS S3 or Azure Data Lake.
- Adding pipeline scheduling and monitoring.
- Adding machine learning or RAG capabilities for advanced use cases.

## Project Files

- `AI_Data_Quality_Pipeline.ipynb` — Complete project notebook.
- `architecture.png` — Project workflow and architecture diagram.
- `README.md` — Project documentation.
