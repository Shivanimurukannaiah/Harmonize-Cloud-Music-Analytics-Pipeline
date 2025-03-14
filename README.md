# Harmonize: Cloud Music Analytics Pipeline  
*A Data Warehouse Solution for Music Streaming Analytics*

---

## 🎯 Project Overview  
Sparkify, a fast-growing music streaming startup, requires a scalable cloud solution to analyze user activity and song data. This project implements a cloud-based data warehouse using **Amazon Redshift**, transforming raw JSON logs (stored in S3) into structured tables optimized for analytics.

---

## ✨ Key Features  
- **Extract**: Retrieve song metadata and user activity logs from Amazon S3.  
- **Transform**: Convert raw JSON data into a star schema for efficient querying.  
- **Load**: Populate Redshift tables to power analytics, such as identifying popular songs and understanding user behavior.

---

## 📂 Files & Setup  

### **Prerequisites**  
- Python 3.x with libraries: `boto3`, `psycopg2`, `configparser`.  
- AWS Account with Redshift cluster and S3 access.  
- Redshift Cluster (use `Redshift_Cluster_IaC.py` to automate setup).  
- Configuration File: `dwh.cfg` (stores credentials and S3 paths).  

### **File Structure**  
harmonize-data-warehouse/
├── create_tables.py # Creates database tables
├── etl.py # Runs the ETL pipeline
├── sql_queries.py # SQL queries for table creation/data insertion
├── dwh.cfg # Configuration file (not shared publicly)
├── README.md # Project documentation
└── Redshift_Cluster_IaC.py # Infrastructure-as-Code for Redshift (optional)


---

## 🗃️ Database Schema  

### **Star Schema Design**  
Designed for efficient analytics with the following structure:

#### **Fact Table**  
- `songplays`: Records of song plays (e.g., user ID, song ID, timestamp).  

#### **Dimension Tables**  
- `users`: User details (name, gender, subscription level).  
- `songs`: Song metadata (title, artist, duration).  
- `artists`: Artist details (name, location).  
- `time`: Timestamp breakdown (hour, day, week, etc.).  

---

## 🚀 How to Run  

1. Clone the repository:
git clone <repository-url>
cd harmonize-data-warehouse

2. Set up your AWS Redshift cluster using `Redshift_Cluster_IaC.py` or manually configure it.

3. Update the `dwh.cfg` file with your AWS credentials and S3 bucket paths.

4. Create the necessary tables:
python create_tables.py

---

## 🛠️ Technologies Used  

- **AWS Services**: Redshift, S3.  
- **Programming Language**: Python.  
- **Libraries**: boto3, psycopg2.  

---

## 📈 Use Cases  

This project enables Sparkify’s analytics team to answer business questions such as:  
1. What are the most played songs?  
2. How do user behaviors vary by subscription level?  

---

## 📜 License  

This project is licensed under the MIT License - see the LICENSE file for details.

---
