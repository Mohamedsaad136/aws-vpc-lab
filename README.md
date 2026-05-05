#  Building My Amazon VPC 


##  Overview

In this hands-on project, I built a Virtual Private Cloud (VPC) on AWS from scratch,
configured subnets across two Availability Zones, set up an Internet Gateway,
configured route tables, and deployed an RDS MySQL database instance.

---

##  Architecture

The architecture includes:
- **1 VPC** — `My VPC` (CIDR: `10.0.0.0/16`) in `us-west-2` (Oregon)
- **Availability Zone 1:**
  - Public Subnet 1 → Web Server (EC2)
  - Private Subnet 1 → RDS MySQL
- **Availability Zone 2:**
  - Private Subnet 2 → RDS MySQL (Multi-AZ standby)
- **Internet Gateway** — attached to the VPC for public internet access
- **Public Route Table** — routes `0.0.0.0/0` → Internet Gateway

---

##  Steps Performed

### 1. Create the VPC
- CIDR Block: `10.0.0.0/16`
- DNS Resolution: Enabled
- VPC ID: `vpc-00ffe1646dddf02a9`

### 2. Create Subnets
| Subnet | AZ | Type | Purpose |
|---|---|---|---|
| Public Subnet 1 | us-west-2a | Public | Web Server |
| Private Subnet 1 | us-west-2a | Private | RDS Primary |
| Private Subnet 2 | us-west-2b | Private | RDS Standby |

### 3. Internet Gateway
- Created and attached to `My VPC`
- ID: `igw-0c167cebb13f6ffe0`

### 4. Route Table
- Created **Public Route Table**
- Added route: `0.0.0.0/0` → Internet Gateway
- Associated with Public Subnet 1

### 5. RDS MySQL Instance
- DB Identifier: `mydb`
- Engine: MySQL Community
- Class: `db.t3.micro`
- AZ: `us-west-2a`
- VPC: `My VPC`
- Not publicly accessible 

---

---

##  AWS Services Used

- Amazon VPC
- Amazon EC2 (Web Server)
- Amazon RDS (MySQL)
- Internet Gateway
- Route Tables
- Security Groups
- DB Subnet Groups
