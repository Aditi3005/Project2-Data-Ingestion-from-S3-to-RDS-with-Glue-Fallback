# Project2-Data-Ingestion-from-S3-to-RDS-with-Glue-Fallback
📌 Overview

This project implements a fault-tolerant data ingestion pipeline using AWS services.  
It reads data from Amazon S3 and loads it into Amazon RDS (MySQL).  
If the RDS operation fails, the system automatically falls back to AWS Glue Data Catalog.

The entire application is containerized using Docker for easy deployment and portability.


🎯 Key Features

- 📥 Read CSV data from Amazon S3
  
- 🗄️ Insert data into Amazon RDS (MySQL)
  
- 🔄 Automatic fallback to AWS Glue on failure
  
-  🐳 Fully Dockerized Python application
  
- ⚡ Error handling using try-except logic


🏗️ Architecture

   +------------------+
    |  Amazon S3  |
  +------------------+
             |
             v
    +------------------+
    | Dockerized App   |
    | (Python Script)  |
    +------------------+
      |             |
      v             v

+-----------+ +-------------+
| Amazon | | AWS Glue |
| RDS | | Catalog |
+-----------+ +-------------+
(Primary) (Fallback)


 🛠️ Tech Stack

- Python 3.9+
  
- AWS S3
  
- AWS RDS (MySQL)
  
- AWS Glue
  
- Docker

 📚 Libraries Used
- boto3
  
- pandas
  
- sqlalchemy

- pymysql


📂 Project Structure

├── app.py
├── Dockerfile
├── requirements.txt
└── README.md


⚙️ Configuration

Set the following environment variables:

AWS_ACCESS_KEY_ID=your_access_key
AWS_SECRET_ACCESS_KEY=your_secret_key
AWS_REGION=ap-south-1

S3_BUCKET=your_bucket_name
S3_KEY=your_file.csv

RDS_HOST=your_rds_endpoint
RDS_USER=your_username
RDS_PASSWORD=your_password
RDS_DB=your_database
RDS_TABLE=your_table

GLUE_DATABASE=your_glue_db
GLUE_TABLE=your_glue_table
S3_OUTPUT_PATH=s3://your-bucket/path/

🐳 Docker Usage:

Build Image:

sudo docker build -t data-pipeline-app .

![WhatsApp Image 2026-04-07 at 9 42 42 PM](https://github.com/user-attachments/assets/e5b83579-b2f1-4545-b592-ef39a5f9203f)


📸 Step-by-Step Execution with Screenshots:

Step 1: Upload CSV File to Amazon S3

- Created an S3 bucket
 
- Uploaded the input CSV file

  ![WhatsApp Image 2026-04-07 at 9 44 32 PM](https://github.com/user-attachments/assets/233e5b25-1216-46d4-879f-3a7dc2788598)


Step 2: Run Dockerized Python Application

-  Built Docker image using Dockerfile
 
- Ran container with required environment variables

![WhatsApp Image 2026-04-07 at 9 45 47 PM](https://github.com/user-attachments/assets/a740a7c9-118a-41b0-9f5c-470c98d1df40)


Step 3: Data Insertion into Amazon RDS

- Application connected to RDS MySQL
  
- Data successfully inserted into table

![WhatsApp Image 2026-04-07 at 9 48 11 PM](https://github.com/user-attachments/assets/4e2439d4-5774-448e-a338-72d8815c2be4)


 Step 4: Fallback to AWS Glue (If RDS Fails)
 
- If RDS connection or insertion fails, fallback is triggered
  
- Glue database and table are created
  ![WhatsApp Image 2026-04-07 at 9 50 07 PM](https://github.com/user-attachments/assets/dc631a1e-2418-43c9-8c7c-2d30cf7b4d41)

  


- S3 data is registered in Glue Data Catalog

  ![WhatsApp Image 2026-04-07 at 9 51 45 PM](https://github.com/user-attachments/assets/316c2f57-55f5-481c-aeea-95f0469e6ec5)

  

  

