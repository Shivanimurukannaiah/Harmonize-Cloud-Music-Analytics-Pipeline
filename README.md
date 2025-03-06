# Harmonize-Cloud-Music-Analytics-Pipeline
Harmonize: Cloud Music Analytics Pipeline
A Data Warehouse Solution for Music Streaming Analytics

AWS Redshift ETL Music Analytics

🎯 Project Overview
Sparkify, a fast-growing music streaming startup, needs a scalable cloud solution to analyze user activity and song data. This project builds a cloud-based data warehouse using Amazon Redshift to transform raw JSON logs (stored in S3) into structured tables optimized for analytics.

Key Features:
Extract: Pull song metadata and user activity logs from Amazon S3.

Transform: Structure raw JSON data into a star schema for efficient querying.

Load: Populate Redshift tables to power analytics (e.g., popular songs, user behavior).

📂 Files & Setup
Prerequisites
Python 3.x with libraries: boto3, psycopg2, configparser.

AWS Account with Redshift cluster and S3 access.

Redshift Cluster (use Redshift_Cluster_IaC.py to automate setup).

Configuration File: dwh.cfg (stores credentials and S3 paths).

File Structure
Copy
harmonize-data-warehouse/  
├── create_tables.py          # Creates database tables  
├── etl.py                    # Runs the ETL pipeline  
├── sql_queries.py            # SQL queries for table creation/data insertion  
├── dwh.cfg                   # Configuration file (not shared publicly)  
├── README.md                 # Project documentation  
└── Redshift_Cluster_IaC.py   # Infrastructure-as-Code for Redshift (optional)  
🗃️ Database Schema
Star Schema Design for efficient analytics:

Fact Table
songplays: Records of song plays (e.g., user ID, song ID, timestamp).

Dimension Tables
users: User details (name, gender, subscription level).

songs: Song metadata (title, artist, duration).

artists: Artist details (name, location).

time: Timestamp breakdown (hour, day, week, etc.).

🚀 How to Run
1. Setup Configuration
Update dwh.cfg with your AWS Redshift cluster details and S3 paths:

ini
Copy
[CLUSTER]
HOST=your-cluster-endpoint
DB_NAME=your-database-name
DB_USER=your-username
DB_PASSWORD=your-password
DB_PORT=5439

[IAM_ROLE]
ARN=your-iam-role-arn

[S3]
LOG_DATA='s3://udacity-dend/log_data'
LOG_JSONPATH='s3://udacity-dend/log_json_path.json'
SONG_DATA='s3://udacity-dend/song_data'
2. Create Tables
Run this to initialize tables in Redshift:

bash
Copy
python create_tables.py
3. Run ETL Pipeline
Extract data from S3, transform it, and load into Redshift:

bash
Copy
python etl.py
4. (Optional) Launch Redshift Cluster
Use the IaC script to automate cluster setup:

bash
Copy
python Redshift_Cluster_IaC.py
📊 Example Use Cases
Identify most-played songs.

Analyze user subscription trends (free vs. premium).

Track peak listening hours by region.

