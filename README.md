#  EasyCRUD – Full Stack Application Deployment
EasyCRUD is a full-stack CRUD (Create, Read, Update, Delete) application deployed using **Amazon RDS**, **EC2**, and **Docker**.  
The backend is developed using **Spring Boot**, the frontend uses **React + Nginx/httpd**, and the database runs on **MariaDB (RDS)**.


---

## 🛠️ Tech Stack

- **Cloud:** AWS (EC2, RDS)
- **Backend:** Spring Boot (Java)
- **Frontend:** Vite + Node.js
- **Database:** MariaDB (Amazon RDS)
- **Containerization:** Docker
- **Web Server:** Apache (inside frontend container)

---

## ⚙️ Prerequisites

- AWS Account
- Ubuntu EC2 Instance
- Amazon RDS (MariaDB)
- Git installed
- Docker installed
- Required ports open in Security Groups:
  - `22` (SSH)
  - `80` (Frontend)
  - `8080` (Backend)
  - `3306` (RDS – only from EC2 SG)

---

# 🔹 PHASE 1: Database Setup (Amazon RDS – MariaDB)

## Step 1: Create RDS Database

1. Login to **AWS Console → RDS**
2. Click **Create database**
3. Choose the following options:
   - **Database Engine:** MariaDB
   - **Template:** Free Tier / Production (as required)
   - **DB Identifier:** `student-db`
   - **Master Username & Password:** (set your own)
4. Connectivity:
   - **VPC:** Same VPC as EC2
   - **Public Access:** Yes (for testing)
   - **Security Group:** Allow inbound `3306` from EC2 Security Group
5. Click **Create Database**
6. Copy the **RDS Endpoint**

---

## Step 2: Launch and Prepare EC2 Instance

1. Launch an **Ubuntu EC2 instance**
2. SSH into the instance
3. Update the system:

```bash
sudo apt update -y
```
## Step 3: Install MySQL Client

Install MySQL client on the EC2 instance to connect with the Amazon RDS database.

```bash
sudo apt install mysql-client -y
```
## Step 4: Connect to RDS from EC2

Use the RDS endpoint to connect to the MariaDB database from the EC2 instance.

```bash
mysql -h <RDS-ENDPOINT> -u admin -p
```
## Step 5: Database Operations

Execute the following SQL commands inside the MySQL shell:

```sql
SHOW DATABASES;
CREATE DATABASE student_db;
USE student_db;
```
## Step 6: Create Students Table

Create the `students` table to store student records.

```sql
CREATE TABLE students (
  id BIGINT NOT NULL AUTO_INCREMENT,
  name VARCHAR(255),
  email VARCHAR(255),
  course VARCHAR(255),
  student_class VARCHAR(255),
  percentage DOUBLE,
  branch VARCHAR(255),
  mobile_number VARCHAR(255),
  PRIMARY KEY (id)
);
```
