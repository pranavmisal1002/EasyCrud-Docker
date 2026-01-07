#  EasyCRUD – Full Stack Application Deployment
EasyCRUD is a full-stack CRUD (Create, Read, Update, Delete) application deployed using **Amazon RDS**, **EC2**, and **Docker**.  
The backend is developed using **Spring Boot**, the frontend uses **React + Nginx/httpd**, and the database runs on **MariaDB (RDS)**.

## Project Architecture
- **Frontend**: React application served using Nginx (Docker container)
- **Backend**: Spring Boot REST API (Docker container)
- **Database**: Amazon RDS (MariaDB)
- **Infrastructure**: EC2 (Ubuntu)
- **Containerization**: Docker

## Phase 1: Database Setup (Amazon RDS)
Step 1: Create RDS Database
    1.	Login to AWS Console → RDS
    2.	Click Create database
    3.	Choose:
         o	Database Engine: MariaDB
         o	Template: Free Tier / Production (as required)
         o	DB Identifier: student-db
         o	Master Username & Password
    4.	Connectivity:
         o	VPC: Same VPC as EC2
         o	Public Access: Yes (for testing)
         o	Security Group: Allow 3306 from EC2 Security Group
    5.	Click Create Database
    6.	Copy the RDS Endpoint
    
