# Data Science Job Trends Analysis with AWS

This project leverages AWS services to build an end-to-end data pipeline that monitors and analyzes data science job trends across various locations, companies, roles, and required skills. The project uses AWS features directly, without custom coding, for data storage, transformation, and visualization.

## Project Overview

With the increasing demand for data scientists, this project aims to provide insights into the job market trends, such as popular job locations, top hiring companies, common roles, and essential skills. The pipeline automates data collection, transformation, and visualization, enabling data-driven insights without the need for custom coding.

## Data Source

The data used in this project is sourced from Kaggle and can be accessed [here](https://www.kaggle.com/code/nickyeapen/data-science-job-trend-analysis/).

## Architecture and Workflow

1. **Data Collection (Amazon S3)**: Data on job postings is stored in Amazon S3, the centralized data lake for raw data files.
2. **Data Cataloging (AWS Glue Crawler)**: AWS Glue Crawler is used to automatically scan the data in S3, infer schema, and populate the AWS Glue Data Catalog.
3. **Data Transformation (AWS Glue ETL)**: Using Glue's ETL capabilities, data is cleaned, organized, and processed for analysis.
4. **Data Visualization (Amazon QuickSight)**: The processed data is visualized in QuickSight with interactive dashboards that provide insights into job trends, including locations, companies, roles, and skills.

## AWS Services Used

- **Amazon S3**: Serves as the data lake, storing raw and processed data.
- **AWS IAM**: Manages access to resources securely across AWS services.
- **AWS Glue**:
  - **Glue Crawler**: Scans and catalogs data from S3.
  - **Glue ETL**: Transforms raw data into a structured format.
- **Amazon QuickSight**: Creates a dashboard for visualizing insights.

## Key Insights from the Dashboard

1. **Top Locations for Data Science Jobs**: Identifies the most popular geographic areas for data science positions.
2. **Top 15 Companies Hiring for Data Science Roles**: Highlights the top companies in the data science job market.
3. **Top Roles in Data Science Jobs**: Showcases the most in-demand job titles in data science.
4. **Top Skills Required in Data Science Jobs**: Lists essential skills frequently sought after in data science job postings.

## Quick Start Guide

1. **Set Up S3 Buckets**:
   - Create S3 buckets for raw and processed data storage.
   - Upload job postings data to the raw data bucket.

2. **Configure IAM Roles and Policies**:
   - Create IAM roles to allow S3, Glue, and QuickSight access.
   - Attach necessary policies for S3 read/write and Glue operations.

3. **AWS Glue Crawler and ETL Setup**:
   - Configure a Glue Crawler to scan the S3 bucket and catalog the data.
   - Set up an ETL job in Glue to clean and structure the data.

4. **Visualize with Amazon QuickSight**:
   - Connect QuickSight to the Glue Data Catalog.
   - Build and customize visualizations for insights.


## Resources and Documentation

See [Documentation](docs/documentation.md) for in-depth setup instructions and configurations.
