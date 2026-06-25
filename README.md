# 📈 Data Pipeline with Airflow and AWS

An automated ETL data pipeline that extracts historical stock market data from Yahoo Finance, transforms it into structured CSV files, and stores the processed data in AWS S3.

The pipeline is orchestrated using **Apache Airflow** and is designed to demonstrate practical data engineering concepts such as workflow scheduling, extraction, transformation, cloud storage and pipeline automation.

---

## 📌 Overview

This project implements a financial data pipeline using:

- **Apache Airflow** for workflow orchestration
- **Yahoo Finance / yfinance** for stock market data extraction
- **Python** for ETL logic
- **AWS S3** for cloud storage
- **CSV files** as processed output datasets

The pipeline fetches historical stock prices for selected stock symbols, processes the data, and stores the results in separate CSV files before uploading them to an S3 bucket.

---

## ❗ Problem

Financial data is often needed for analysis, reporting, dashboards and machine learning models. However, manually downloading and preparing stock data is repetitive, time-consuming and error-prone.

This project solves that by automating the process of:

- Extracting stock market data
- Cleaning and formatting the data
- Saving structured output files
- Uploading processed datasets to cloud storage
- Scheduling the pipeline for repeatable execution

---

## ✅ Solution

The pipeline automates the full ETL process:

```text
Yahoo Finance
     |
     | Extract stock data using yfinance
     v
Python ETL Script
     |
     | Clean and transform data
     v
CSV Output Files
     |
     | Upload processed files
     v
AWS S3 Bucket
     |
     | Orchestrated by Apache Airflow
     v
Scheduled Data Pipeline
```

---

## 🏗️ Architecture

```text
Apache Airflow DAG
     |
     ├── Extract stock data
     |
     ├── Transform and clean data
     |
     ├── Save data as CSV files
     |
     └── Upload files to AWS S3
```

---

## ✨ Features

- Extracts historical stock prices from Yahoo Finance
- Supports multiple stock symbols
- Uses Apache Airflow DAGs for orchestration
- Saves processed data into separate CSV files
- Uploads output files to AWS S3
- Demonstrates ETL workflow automation
- Provides a foundation for financial analytics or ML pipelines

---

## 🧰 Tech Stack

- Python
- Apache Airflow
- AWS S3
- yfinance
- pandas
- CSV
- Git/GitHub

---

## 📂 Project Structure

```text
data-pipeline-with-airflow/
├── dags/                  # Airflow DAG files
├── scripts/               # ETL scripts
├── data/                  # Local output data files
├── requirements.txt       # Python dependencies
├── README.md              # Project documentation
└── .gitignore
```

Adjust this structure if your actual folders are slightly different.

---

## 🚀 How It Works

### 1. Extract

The pipeline uses the `yfinance` library to fetch historical stock data for selected stock symbols.

Example stock symbols:

```python
["AAPL", "MSFT", "GOOGL", "AMZN"]
```

### 2. Transform

The extracted data is cleaned and formatted into structured tabular data.

Typical fields include:

- Date
- Open price
- High price
- Low price
- Close price
- Adjusted close price
- Volume

### 3. Load

The transformed data is saved into CSV files and uploaded to an AWS S3 bucket.

Example output:

```text
AAPL_stock_data.csv
MSFT_stock_data.csv
GOOGL_stock_data.csv
AMZN_stock_data.csv
```

---

## ⚙️ Prerequisites

Before running the project, make sure you have:

- Python 3.8+
- Apache Airflow
- AWS account
- AWS S3 bucket
- AWS access key and secret key
- yfinance
- pandas
- boto3

Install dependencies:

```bash
pip install -r requirements.txt
```

---

## 🔐 Environment Variables

Create a `.env` file or configure these variables in your Airflow environment:

```env
AWS_ACCESS_KEY_ID=your_access_key
AWS_SECRET_ACCESS_KEY=your_secret_key
AWS_REGION=your_region
S3_BUCKET_NAME=your_bucket_name
```

Do **not** commit your `.env` file to GitHub.

---

## ▶️ Running the Pipeline

### 1. Start Airflow

```bash
airflow standalone
```

Or, if using separate services:

```bash
airflow webserver
airflow scheduler
```

### 2. Open Airflow UI

Visit:

```text
http://localhost:8080
```

### 3. Enable the DAG

Find the stock data pipeline DAG in the Airflow UI and turn it on.

### 4. Trigger the DAG

Run the pipeline manually or allow it to execute based on its schedule.

---

## 📊 Example Output

After the pipeline runs successfully, processed stock data files are generated and uploaded to S3.

Example local or S3 output:

```text
s3://your-bucket-name/stock-data/AAPL_stock_data.csv
s3://your-bucket-name/stock-data/MSFT_stock_data.csv
s3://your-bucket-name/stock-data/GOOGL_stock_data.csv
```


## 🧪 Testing and Validation

The pipeline can be validated by checking:

- Airflow DAG runs successfully
- Stock data is extracted without errors
- CSV files are generated correctly
- Files contain expected columns
- Files are uploaded to the correct AWS S3 bucket
- Airflow logs show successful task completion

---

## 📈 Key Results

- Built an automated ETL pipeline for financial market data
- Orchestrated extraction, transformation and loading with Apache Airflow
- Stored processed datasets in AWS S3
- Created reusable pipeline logic for multiple stock symbols
- Demonstrated practical cloud-based data engineering workflow automation
