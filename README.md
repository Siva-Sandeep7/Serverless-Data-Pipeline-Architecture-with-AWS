# Student Data Management System

This project is a data engineering solution that combines a web application for student data entry with an ETL pipeline for data processing and storage in AWS.

## Project Structure

```
.
├── run.py              # Flask web application
├── etl.py             # AWS Glue ETL job script
├── lambda.py          # AWS Lambda function
├── templates/         # HTML templates
└── static/           # Static assets (CSS, JS, images)
```

## Components

### 1. Web Application (run.py)
A Flask-based web application that provides:
- Student data entry form
- Fields for registration number, name, standard, and subject marks (Math, Science, Computer)
- Data submission endpoint

### 2. ETL Pipeline (etl.py)
An AWS Glue ETL job that:
- Reads student and marks data from S3 staging area
- Performs data transformations and joins
- Writes processed data to a data warehouse in S3
- Uses PySpark for data processing
- Implements data union operations
- Handles data compression using Snappy format

### 3. AWS Lambda Function (lambda.py)
Serverless function for handling specific AWS events and triggers.

## AWS Infrastructure

The project utilizes several AWS services:
- S3 buckets for data storage:
  - Staging area: `s3://project-de-datewithdata/staging/`
  - Data warehouse: `s3://project-de-datewithdata/warehouse/`
- AWS Glue for ETL processing
- AWS Lambda for serverless computing

## Setup and Installation

1. Clone the repository
2. Install required Python packages:
   ```bash
   pip install flask boto3 pyspark
   ```
3. Configure AWS credentials
4. Set up required AWS resources (S3 buckets, Glue jobs, Lambda functions)

## Running the Application

1. Start the Flask web application:
   ```bash
   python run.py
   ```
2. Access the web interface at `http://localhost:5000`
3. The ETL job can be triggered manually or scheduled in AWS Glue

## Data Flow

1. Data is entered through the web interface
2. Data is stored in S3 staging area
3. ETL job processes the data:
   - Joins student and marks data
   - Performs data transformations
   - Writes to data warehouse
4. Processed data is available in the warehouse for analysis

## Security

- AWS credentials should be properly configured
- S3 bucket permissions should be set appropriately
- IAM roles should be configured for AWS services

## Contributing

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request

## License

This project is licensed under the MIT License - see the LICENSE file for details. 