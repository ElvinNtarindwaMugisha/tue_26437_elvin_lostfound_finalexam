## NTARINDWA MUGISHA ELVIN

## ID: 26437

## PL/SQL EXAM.

# 📦  Project Title: Lost & Found Item Management System project
(University)
##  **Phase I**

## 🧭 Introduction

In many universities, managing lost and found items is still handled manually or with basic spreadsheets. These outdated systems are prone to errors, data loss, and delays, which complicate the recovery process for students and staff. As universities handle an increasing volume of users and transactions, the demand for a secure, automated, and centralized system has become crucial.

The Lost & Found Item Management System, built on Oracle PL/SQL, addresses these challenges by providing a robust, digital platform for reporting, tracking, and claiming lost items. It not only improves accuracy and efficiency but also ensures a secure claims process through database integrity constraints, user roles, and automated workflows.

By integrating PL/SQL-based procedures, triggers, and packages, the system enforces data reliability and supports a scalable, user-friendly solution for managing personal item recovery in educational institutions.

---

## 🎯 Problem Statement

Universities currently struggle with inefficient, manual lost-and-found management. Traditional paper logs or spreadsheets:

- Lack real-time tracking  
- Are prone to human error and record loss  
- Delay the recovery of lost items  
- Do not support proper ownership verification or user notifications  

This creates frustration for users and an administrative burden on staff.

---

## 🌐 Context of Use

The system is designed to serve university environments where item loss and recovery are frequent and must be handled reliably. It ensures:

- Secure item reporting and retrieval for students, staff, and faculty  
- Role-based access for administrators to manage item status and approve claims  
- Automated tracking and notification of found and claimed items  

---

## 🧑‍💼 Target Users and System Roles

- **🎓 Student/Staff**:  
  Initiate the process by reporting a lost item or searching for it. They also submit claims when an item is found.

- **🧑‍💼 Administrator**:  
  Manages item records, validates reported items and claims, and approves the return of found items.

- **💽 Database**:  
  Serves as the central data store where all item and claim details are securely stored and retrieved.

- **🔁 Claim Workflow System**:  
  Automates the process of matching found items to lost item reports and monitors the progress of claims.

- **🔔 Notification System**:  
  Sends real-time updates to users when their lost item is found or when a claim has been approved or rejected.

---

## 🏆 Project Goals

- Automate the lost and found item tracking process  
- Ensure security and ownership validation through database constraints and triggers  
- Provide real-time notifications for faster item recovery  
- Improve transparency through audit trails and user activity logs  
- Reduce staff workload and eliminate inefficiencies caused by manual systems  



##  Phase II: Requirements and Business Process Modeling

---

## 🧭 1. Define the Scope

### 🔁 Business Process: Lost Item Recovery Management

---

### 📄 Description

This process outlines how a university’s Lost & Found Item Management System facilitates the reporting, tracking, and claiming of lost items. The system aims to ensure secure, efficient, and transparent handling of item recovery while reducing manual intervention through automation and structured database operations.

The workflow starts when a user reports a lost item. That data is stored, reviewed by an administrator, and compared to newly reported found items. Once a match is identified, a claim is initiated, verified, and—if approved—followed by a user notification for collection.

---

### 🎯 Objectives

- Digitally streamline how lost items are reported, stored, matched, and claimed.  
- Integrate MIS principles to ensure visibility, traceability, and user accountability.  
- Reduce data entry errors and manual delays through automation.  
- Provide real-time notifications and efficient claims management.

---

### 📈 Expected Outcomes

- Faster return of lost items through systematic tracking.  
- Decreased workload for university staff through automated processes.  
- Secure and transparent validation of item ownership.  
- Improved user satisfaction through real-time communication and audit trails.

---

## 🧩 2. Identify Key Entities

| Entity         | Description                                                                 |
|----------------|------------------------------------------------------------------------------|
| Student/Staff  | Reports lost items or submits claims for found items.                       |
| Administrator  | Reviews, validates, and approves item records and user claims.              |
| Item           | Represents reported lost or found items with full metadata.                 |
| Claim          | Tracks user-submitted requests to retrieve matched found items.             |
| Notification   | System-generated alerts for item status and claim updates.                  |

---

## 🏊 3. Swimlanes to Use in BPMN Diagram

Design your BPMN with these lanes to clarify responsibilities:

- **Student/Staff** – Report items and submit claims.  
- **Administrator** – Manage validation and approvals.  
- **Database** – Stores all item, user, and claim data.  
- **Claim Workflow System** – Matches lost and found reports.  
- **Notification System** – Sends claim status and update alerts.

---

## 🗺️ 4. BPMN Diagram (UML Notation)

![PHASEII](https://github.com/user-attachments/assets/0bfb1aa1-37ef-4f4b-9d2d-bc67d453cfc1)


---

## 🧾 5. Explanation of the BPMN Diagram

### 🧱 Main Components and Workflow

The BPMN process consists of multiple swimlanes showing interactions between users and the system:

- A user reports a lost item.
- The system stores it and flags it for review.
- When a found item is logged, the system attempts to match it to reported items.
- An administrator validates the match and either approves or rejects the claim.
- Notifications are triggered based on the outcome.
- The process ends when the user receives or is denied the item.

---

## 🧠 6. How the Process Supports MIS Functions

- **Decision-Making**: Real-time reports help admins validate claims faster.  
- **Operational Efficiency**: Workflow automation replaces manual logging.  
- **Centralized Data**: All actions and transactions are stored in the database.  
- **Transparency**: Each user action is logged and traceable via auditing features.

---

## 🏛️ 7. Importance to Organizational Efficiency

Implementing this system reduces delays in item recovery, increases data accuracy, and supports secure, automated handling of claims. This reduces the workload on staff while enhancing trust and transparency for users—perfectly aligning with core MIS objectives in modern institutions.


##  Phase III: Logical Model Design

---

### 🔢 1. Logical Model (Entity-Attribute Table)

| **Entity**     | **Attributes**                                                                 | **PK / FK**                                        | **Data Types**                          |
|----------------|--------------------------------------------------------------------------------|----------------------------------------------------|-----------------------------------------|
| **Users**      | user_id, first_name, last_name, email, user_type, phone_number                 | PK: user_id                                        | INT, VARCHAR2, VARCHAR2, VARCHAR2, VARCHAR2, VARCHAR2 |
| **Item**       | item_id, item_name, description, date_lost, location_lost, status, reported_by | PK: item_id<br>FK: reported_by → Users(user_id)    | INT, VARCHAR2, VARCHAR2, DATE, VARCHAR2, VARCHAR2, INT |
| **FoundItem**  | found_item_id, item_id, date_found, location_found, found_by                   | PK: found_item_id<br>FKs: item_id, found_by        | INT, INT, DATE, VARCHAR2, INT           |
| **Claim**      | claim_id, item_id, claimed_by, claim_date, status, admin_id                    | PK: claim_id<br>FKs: item_id, claimed_by, admin_id | INT, INT, INT, DATE, VARCHAR2, INT      |
| **Notification** | notification_id, user_id, message, date_sent, is_read                         | PK: notification_id<br>FK: user_id → Users(user_id) | INT, INT, VARCHAR2, DATE, CHAR(1)       |

---

### 🔃 2. Relationships & Constraints

#### 🧩 Relationships

| **From Entity** | **To Entity**     | **Relationship Type** | **Description**                                        |
|-----------------|------------------|------------------------|--------------------------------------------------------|
| Users           | Item             | One-to-Many            | One user can report multiple lost items               |
| Users           | FoundItem        | One-to-Many            | One user can report found items                       |
| Users           | Claim            | One-to-Many            | A user can submit multiple claims                     |
| Users           | Notification     | One-to-Many            | One user can receive many notifications               |
| Item            | FoundItem        | One-to-One (optional)  | A lost item may be linked to one found item           |
| Item            | Claim            | One-to-One (per claim) | One item can be claimed at a time                     |
| Claim           | Admin (Users)    | Many-to-One            | Each claim is validated by an admin user              |

---

#### ✅ Constraints

- `email` → **UNIQUE NOT NULL**
- `user_type` → **CHECK** (`IN ('Student', 'Staff', 'Faculty')`)
- `status` (in `Item` and `Claim`) → **CHECK** (`IN ('Lost', 'Found', 'Claimed', 'Pending', 'Approved', 'Rejected')`)
- `is_read` in `Notification` → **CHECK** (`IN ('Y', 'N')`)
- `item_id`, `user_id`, etc. → **FOREIGN KEY** constraints
- `claim_id`, `found_item_id` → **PRIMARY KEY** constraints

---

### 🧮 3. Normalization (Up to 3NF)

| **Form** | **Explanation**                                                                 |
|----------|---------------------------------------------------------------------------------|
| **1NF**  | Each field contains atomic values; no repeating groups.                        |
| **2NF**  | All non-key attributes fully dependent on the primary key.                     |
| **3NF**  | No transitive dependencies; all attributes directly depend on the key only.    |

---

### 🌍 4. Handling Real-World Data Scenarios

- Multiple users can report and search for lost items.
- Each lost item can be matched to a found item (and vice versa).
- Only administrators can approve or reject claims.
- Notifications are sent automatically to inform users of claim status or item recovery.
- Data integrity is maintained through relational constraints and validation checks.

---

### 📊 5. Presentation & ERD Diagram

> This ER diagram visually represents the logical relationships between entities:

![PHASEIII](https://github.com/user-attachments/assets/865549c7-45a7-40d0-92b0-057850d2bb3b)


---

