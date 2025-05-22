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



## ✳️ Phase II: Requirements and Business Process Modeling

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


## 🌀 Phase III: Logical Model Design

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

### 🌀 **Phase IV**

### **Pluggable database creation**
![pdbs creation](https://github.com/user-attachments/assets/9070771a-45cd-404a-b8bc-6871701f5783)

📠 **What This Phase Covers**
This phase focuses on creating a Pluggable Database (PDB) and converting the logical model into a physical database structure. It ensures that all tables, relationships, and constraints are implemented to meet project requirements.

🔨**Database Creation**
The Pluggable Database (PDB) was created using the following naming format:
```sql
Database Name:wed_26642_biometric_Based_Transaction_System
Username: evelyne
Password: evelyne
```
Steps Executed in SQL Command Prompt
1.Create a pluggable database:
```sql
create pluggable database wed_26642_biometric_Based_Transaction_System
  2  admin user wed_26642_biometric_Based_Transaction_System identified by evelyne
  3  file_name_convert=('D:\ORACLE\ORADATA\ORCADATA\XE\PDBseed\','D:\ORACLE\ORADATA\XE\wed_26642_biometric_Based_Transaction_System\');

 Pluggable database created.
```
2.Open the newly created PDB:

```sql
 alter pluggable database wed_26642_biometric_Based_Transaction_System open ;

Pluggable database altered.
```
Purpose: Makes the PDB active and ready for operations.

3.save the newly created PDB.
```sql
SQL> alter pluggable database wed_26642_biometric_Based_Transaction_System save state;

Pluggable database altered.
```
Purpose: Ensures the PDB remains open after the database restarts.

4. Set the Session Container
   
```sql
SQL> alter session set container =wed_26642_biometric_Based_Transaction_System;

Session altered.
```
Purpose: Switches the session to the newly created PDB for subsequent operations.

5.User Creation and Privilege Assignment

Create a Database User
```sql
SQL> create user tue_falcon identified by falcon;

User created.
```
Purpose: Creates a new user, evelyne, with the password evelyne.

Grant Basic Privileges
```sql
 SQL> grant all privileges to tue_falcon;

Grant succeeded.
```
Purpose: To assigns full privileges for database operations.

### **Oracle Enterprise Manager (OEM)**

Oracle Enterprise Manager (OEM) is not a PL/SQL keyword or feature—it’s Oracle’s web-based administrative console for the entire Oracle technology stack (databases, middleware, engineered systems, cloud services, etc.). When people mention OEM while discussing PL/SQL code, they’re usually talking about using the OEM interface to manage, monitor, or debug that code inside the database.

### ⚖️ **Oracle Enterprise Manager (OEM)**

The OEM interface confirmed:

Successful creation of the database.

Proper implementation of relationships between tables.

### 📸 **OEM confirm successful database creation and table relationships.**

![OEM dashboard](https://github.com/user-attachments/assets/da1887a0-ada6-49dc-9438-1263e42a3706)

![Resourece](https://github.com/user-attachments/assets/e26621ba-00d4-4a08-a6cc-88d8841be41f)

### 🔭 **Conclusion About this phase**

This phase successfully established the pluggable database and implemented the physical structure, enabling efficient data management for the Biometric based transaction system.

## 🌀 **Phase V**

### Physical Database Structure

Physical Database Structure converts the logical Entity-Relationship model into a physical Oracle database structure, implementing all required tables, relationships, and data integrity constraints to support biometric-based authentication for secure financial transactions.

## 🧱 **Table Creation**

Here are the created tables & codes used to create them

📋 **User table** 

```sql
CREATE TABLE users (
    user_id NUMBER PRIMARY KEY,
    username VARCHAR2(50) NOT NULL UNIQUE,
    email VARCHAR2(100),
    created_at DATE DEFAULT SYSDATE
);
```


📋 **Transaction table**


```sql
CREATE TABLE transactions (
    transaction_id NUMBER PRIMARY KEY,
    user_id NUMBER NOT NULL,
    transaction_type VARCHAR2(50),
    amount NUMBER(10, 2),
    transaction_time DATE DEFAULT SYSDATE,
    FOREIGN KEY (user_id) REFERENCES users(user_id) ON DELETE CASCADE
);
```


📋 **Biometric Data table**

```sql
CREATE TABLE biometric_data (
    user_id NUMBER PRIMARY KEY, 
    fingerprint_data BLOB,
    face_scan BLOB,
    iris_scan BLOB,
    created_at DATE DEFAULT SYSDATE,
    FOREIGN KEY (user_id) REFERENCES users(user_id) ON DELETE CASCADE
);
```



📋 **AuthenticationLogs Table**

```sql
CREATE TABLE authentication_logs (
    log_id NUMBER PRIMARY KEY,
    transaction_id NUMBER NOT NULL,
    user_id NUMBER NOT NULL,
    auth_status VARCHAR2(20), 
    attempt_time DATE DEFAULT SYSDATE,
    FOREIGN KEY (transaction_id) REFERENCES transactions(transaction_id) ON DELETE CASCADE,
    FOREIGN KEY (user_id) REFERENCES users(user_id) ON DELETE CASCADE
);
```



Inserting data

📋 **User table**

```sql

INSERT INTO users (user_id, username, email,created_at)
VALUES (1, 'Niece', 'niece@gmail.com', TO_DATE('2024-05-19','YYYY-MM-DD'));
INSERT INTO users (user_id, username, email, created_at)
VALUES (2, 'lina Umuganwa', 'lina@mail.com', TO_DATE('2024-05-19','YYYY-MM-DD'));
INSERT INTO users (user_id, username,email,created_at)
VALUES (3, 'Racia Akliza' , 'rc@gmail.com',TO_DATE('2024-04-25','YYYY-MM-DD'));

```

📋 **Transaction table**

```sql
         
 INSERT INTO transactions 
         (transaction_id, 
          user_id, 
          transaction_type, 
          amount,
          transaction_time)
    VALUES (101, 
            1, 
           'Payment', 
           2500000,
           SYSDATE);       

INSERT INTO transactions
        (transaction_id,
         user_id,
         transaction_type,
         amount,
         transaction_time)
VALUES  (102,  
         2,             
         'Payment',     
         1000000,        
         SYSDATE);
         
 INSERT INTO transactions
        (transaction_id,
         user_id,
         transaction_type,
         amount,
         transaction_time)
VALUES  (103,
         3,             
         'Deposit',      
         3000000,        
         SYSDATE);
```

📋 **Biometric data table**

```sql
INSERT INTO biometric_data 
        (user_id,
         fingerprint_data, 
         face_scan,
         iris_scan,
         created_at)
 VALUES (1, 
         EMPTY_BLOB(),
         EMPTY_BLOB(),
         EMPTY_BLOB(),
         SYSDATE);
         
INSERT INTO biometric_data
        (user_id,
         fingerprint_data,
         face_scan,
         iris_scan,
         created_at)
VALUES  (2,          
         EMPTY_BLOB(),  
         EMPTY_BLOB(), 
         EMPTY_BLOB(),  
         SYSDATE);   
         
INSERT INTO biometric_data
        (user_id,
         fingerprint_data,
         face_scan,
         iris_scan,
         created_at)
VALUES  (3,          
         EMPTY_BLOB(),  
         EMPTY_BLOB(), 
         EMPTY_BLOB(),  
         SYSDATE);
```


### 📋 **Authentication table**

```sql
   
 INSERT INTO authentication_logs 
         (log_id,
         transaction_id,
         user_id,
         auth_status,
         attempt_time)
      VALUES (1001,
             101,
             1, 
             'SUCCESS',
              SYSDATE);

INSERT INTO authentication_logs
        (log_id,
         transaction_id,
         user_id,
         auth_status,
         attempt_time)
VALUES  (1002,  
         102,   
         2,
         'SUCCESS',     
         SYSDATE);
 
INSERT INTO authentication_logs
        (log_id,
         transaction_id,
         user_id,
         auth_status,
         attempt_time)
VALUES  (1003,  
         103,   
         3,
         'FAIL',     
         SYSDATE);  
```


## **3 ▪ Integrity Validation Queries**

### **Check each transaction has exactly one latest auth result.**

```sql
        
SELECT t.transaction_id, COUNT(l.log_id) AS attempts
FROM   transactions t
LEFT JOIN authentication_logs l
       ON l.transaction_id = t.transaction_id
GROUP  BY t.transaction_id; 
```

![data integrity validation qeuries ](https://github.com/user-attachments/assets/a40be81b-0787-4524-ad40-4cab50e5d77d)

### **Confirm no orphan biometric rows**

An orphan row is a record that has lost (or never had)

If a row in biometrics points to an employee_id that no longer exists (or never existed) in employees, that biometric row is an orphan.

So “orphan biometric rows” simply means biometric-data rows whose foreign-key reference to the parent entity (e.g., employee, user, patient) is broken or missing.

```sql
SELECT user_id
FROM   biometric_data b
LEFT JOIN users u USING (user_id)
WHERE  user_id IS NULL; 
```

![Every user_id present in biometric_data is also present in users (Data Integrity)](https://github.com/user-attachments/assets/b89beab8-31e9-4354-9b2d-c98a63f6c185)

## Phase VI

### 🔄 **Database Interaction and Transactions**

This phase focuses on performing Database Operations (both DML and DDL), utilizing various join types to interact with the database and ensure reliable data management. Additionally, it covers Transaction Management to maintain data consistency and integrity during multi-step operations. This ensures the system remains consistent and accurate when processing multiple transactions.

1. Database Operations
   
### ⚓ **DDL (Data Definition Language)**

Create essential tables for the system

As we have done above DDL is for creating table 

Here is an example of of creating AuthenticationLogs Table

```sql
CREATE TABLE authentication_logs (
    log_id NUMBER PRIMARY KEY,
    transaction_id NUMBER NOT NULL,
    user_id NUMBER NOT NULL,
    auth_status VARCHAR2(20), 
    attempt_time DATE DEFAULT SYSDATE,
    FOREIGN KEY (transaction_id) REFERENCES transactions(transaction_id) ON DELETE CASCADE,
    FOREIGN KEY (user_id) REFERENCES users(user_id) ON DELETE CASCADE
);
```

![AuthenticationLogs table](https://github.com/user-attachments/assets/8c4e9d43-60cb-4d2a-a5d0-3e71d2aa91a2)

### ❄️ **DML (Data Manipulation Language)**

Insert, update, and delete sample data:

Here is an example of inserting data as we did it in the above queries

```sql
   
 INSERT INTO authentication_logs 
         (log_id,
         transaction_id,
         user_id,
         auth_status,
         attempt_time)
      VALUES (1001,
             101,
             1, 
             'SUCCESS',
              SYSDATE);
```

Updating data in my Database

```sql

-- Update
UPDATE users SET username = 'Evelyne' WHERE user_id = 1;

```

![updating data](https://github.com/user-attachments/assets/9ec0b95a-112b-477e-830e-023419601895)

Here is the table which shows the updated user after using the query

![Table of updated user](https://github.com/user-attachments/assets/122de8cd-cf8b-48d1-b197-446614c5abbb)

Deleting data in database 

```sql
DELETE FROM authentication_logs
WHERE log_id = 1003;  
```

![query to delete data](https://github.com/user-attachments/assets/59c2ae37-6fd2-4fdf-b8a6-f6a952ea8215)

Here is an example of deleted data in Authentication table as we know before we had 3 data inserted in table authentication.So deleted data where log_id=1003

![A table which shows deleted data](https://github.com/user-attachments/assets/78ea97df-8f0d-43f8-b6a7-25135e52c181)

2. Task Requirements

### 🛡️ **Simple Problem Statement**

Problem: Identify users who frequently perform high-value transactions (above a certain threshold) to improve security monitoring.

Use of Windows Functions Example:

```sql
SELECT 
    user_id, 
    amount,
    RANK() OVER (PARTITION BY user_id ORDER BY amount DESC) AS transaction_rank
FROM transactions
WHERE amount > 1000000;
```
![Selecting query](https://github.com/user-attachments/assets/6ecc29f9-961b-4ed4-965c-0624258d1aa3)

3. Procedures and Functions
   
### 🔐 **Procedure to Fetch Transactions by User**

```sql
CREATE OR REPLACE PROCEDURE fetch_transactions_by_user (
    p_user_id IN NUMBER
) AS
BEGIN
    FOR rec IN (
        SELECT * FROM transactions WHERE user_id = p_user_id
    ) LOOP
        DBMS_OUTPUT.PUT_LINE('Transaction: ' || rec.transaction_id || ', Amount: ' || rec.amount);
    END LOOP;
EXCEPTION
    WHEN OTHERS THEN
        DBMS_OUTPUT.PUT_LINE('Error: ' || SQLERRM);
END;

```
## **Cursors are used implicitly in this section:**

### **🔍 Explanation:**

- The line FOR rec IN (SELECT * FROM transactions WHERE user_id = p_user_id) uses a cursor FOR loop.

- This is an example of a implicit cursor.

- Oracle automatically creates and manages the cursor for the SQL query inside the loop.

- The variable rec represents each row returned by the query.
  
**💡 If you want to use an explicit cursor, here's how you would rewrite it:**

```sql
CREATE OR REPLACE PROCEDURE fetch_transactions_by_user_explicit (
    p_user_id IN NUMBER
) AS
    CURSOR txn_cursor IS
        SELECT * FROM transactions WHERE user_id = p_user_id;
    txn_row txn_cursor%ROWTYPE;
BEGIN
    OPEN txn_cursor;
    LOOP
        FETCH txn_cursor INTO txn_row;
        EXIT WHEN txn_cursor%NOTFOUND;
        DBMS_OUTPUT.PUT_LINE('Transaction: ' || txn_row.transaction_id || ', Amount: ' || txn_row.amount);
    END LOOP;
    CLOSE txn_cursor;
EXCEPTION
    WHEN OTHERS THEN
        DBMS_OUTPUT.PUT_LINE('Error: ' || SQLERRM);
END;

```


### ♻️ **Function to Get Total Transaction Amount** 

```sql
CREATE OR REPLACE FUNCTION get_total_amount (
    p_user_id IN NUMBER
) RETURN NUMBER IS
    total_amt NUMBER := 0;
BEGIN
    SELECT SUM(amount) INTO total_amt FROM transactions WHERE user_id = p_user_id;
    RETURN NVL(total_amt, 0);
EXCEPTION
    WHEN NO_DATA_FOUND THEN RETURN 0;
    WHEN OTHERS THEN RETURN -1;
END;

```

![total amount queries](https://github.com/user-attachments/assets/7819e951-e00e-425b-9fd5-8ca474021cfa)

4. **Testing**
   
Run tests with sample data:

```sql
-- Test procedure
EXEC fetch_transactions_by_user(1);

-- Test function
SELECT get_total_amount(1) AS total_spent FROM dual;

```

5. Packages

### 🚧 **Create Package Specification**

🎡 Create Package Body

```sql
CREATE OR REPLACE PACKAGE biometric_pkg IS
  PROCEDURE fetch_transactions_by_user(p_user_id NUMBER);
END biometric_pkg;

```
You must now write and compile the package body like this:
```sql
CREATE OR REPLACE PACKAGE BODY biometric_pkg IS

  PROCEDURE fetch_transactions_by_user(p_user_id NUMBER) IS
    v_amount transactions.amount%TYPE;
  BEGIN
    FOR rec IN (SELECT transaction_id, amount, transaction_time
                FROM transactions
                WHERE user_id = p_user_id) LOOP
      DBMS_OUTPUT.PUT_LINE('Transaction ID: ' || rec.transaction_id ||
                           ', Amount: ' || rec.amount ||
                           ', Time: ' || rec.transaction_time);
    END LOOP;
  END;

END biometric_pkg;

```

Query for calling procedure

```sql
BEGIN
  biometric_pkg.fetch_transactions_by_user(1);
END;

```
### 🌀**Phase VII**

## 🗂 1. Problem Statement Development
    
### 🔹 Problem Statement:
In the Biometric-Based Transaction Authorization System, it is critical to ensure that all data manipulations—especially those involving sensitive user and transaction records—are tightly controlled, secure, and auditable. This is to prevent unauthorized changes that could compromise data integrity or breach security regulations.

To address this, the system must:

Restrict users (e.g., employees) from performing insert, update, or delete operations during weekdays (Monday–Friday) and on official public holidays.

Log and audit all critical changes to maintain accountability and support forensic reviews.

Use PL/SQL triggers, packages, and functions to automate these controls.

###🔹 Justification:

Triggers are required to enforce time-based and holiday-based restrictions on table manipulations.

Packages and functions provide modular and reusable logic for checking holidays and logging activity.

Auditing enables real-time tracking of sensitive operations to strengthen security and support compliance.

## 📠**2. Trigger Implementation**

### 🔹 **Step 1: Holiday Table**

```sql
CREATE TABLE holidays (
    holiday_date DATE PRIMARY KEY,
    description VARCHAR2(100)
);

-- Sample holidays for next month (e.g., June)
INSERT INTO holidays VALUES (TO_DATE('2025-06-01', 'YYYY-MM-DD'), 'Independence Day');
INSERT INTO holidays VALUES (TO_DATE('2025-06-25', 'YYYY-MM-DD'), 'Liberation Day');
COMMIT;

```
**🔹 Step 2: Restriction Trigger**
```sql
CREATE OR REPLACE TRIGGER trg_block_weekday_and_holiday_dml
BEFORE INSERT OR UPDATE OR DELETE ON transactions
FOR EACH ROW
DECLARE
    v_day VARCHAR2(10);
    v_today DATE := TRUNC(SYSDATE);
    v_next_month_start DATE := TRUNC(ADD_MONTHS(SYSDATE, 1), 'MM');
    v_next_month_end DATE := LAST_DAY(v_next_month_start);
    v_count INTEGER;
BEGIN
    -- Check for weekday (Mon–Fri)
    SELECT TO_CHAR(v_today, 'DY', 'NLS_DATE_LANGUAGE=ENGLISH') INTO v_day FROM dual;
    IF v_day IN ('MON', 'TUE', 'WED', 'THU', 'FRI') THEN
        RAISE_APPLICATION_ERROR(-20001, 'DML operations are not allowed on weekdays.');
    END IF;

    -- Check for holidays in next month
    SELECT COUNT(*) INTO v_count
    FROM holidays
    WHERE holiday_date = v_today
      AND holiday_date BETWEEN v_next_month_start AND v_next_month_end;

    IF v_count > 0 THEN
        RAISE_APPLICATION_ERROR(-20002, 'DML operations are not allowed on public holidays.');
    END IF;
END;

```

## **🧿 1. Simple Trigger Implementation**

This trigger blocks INSERT, UPDATE, DELETE on weekdays and public holidays.

```sql
CREATE OR REPLACE TRIGGER trg
BEFORE INSERT OR UPDATE OR DELETE ON transactions
FOR EACH ROW
DECLARE
    v_day VARCHAR2(10);
    v_today DATE := TRUNC(SYSDATE);
    v_next_month_start DATE := TRUNC(ADD_MONTHS(SYSDATE, 1), 'MM');
    v_next_month_end DATE := LAST_DAY(v_next_month_start);
    v_is_holiday NUMBER := 0;
BEGIN
    -- Check if today is a weekday (Mon–Fri)
    SELECT TO_CHAR(v_today, 'DY', 'NLS_DATE_LANGUAGE=ENGLISH') INTO v_day FROM dual;
    IF v_day IN ('MON', 'TUE', 'WED', 'THU', 'FRI') THEN
        RAISE_APPLICATION_ERROR(-20001, 'DML operations are not allowed on weekdays.');
    END IF;

    SELECT COUNT(*) INTO v_is_holiday
    FROM holidays
    WHERE holiday_date = v_today
      AND holiday_date BETWEEN v_next_month_start AND v_next_month_end;

    IF v_is_holiday > 0 THEN
        RAISE_APPLICATION_ERROR(-20002, 'DML operations are not allowed on public holidays.');
    END IF;
END;
```

## 🔨 **2. Compound Trigger Implementation**

This trigger tracks multiple row changes (bulk operations) and audits them as a group, improving performance and consistency.

```sql
CREATE OR REPLACE TRIGGER trg_audit_transactions_bulk
FOR INSERT OR UPDATE OR DELETE ON transactions
COMPOUND TRIGGER

    TYPE t_log_record IS RECORD (
        action_type VARCHAR2(10),
        table_name  VARCHAR2(50),
        user_name   VARCHAR2(50),
        old_data    CLOB,
        new_data    CLOB
    );

    TYPE t_log_table IS TABLE OF t_log_record INDEX BY PLS_INTEGER;
    v_logs t_log_table;
    v_index PLS_INTEGER := 0;

AFTER EACH ROW IS
BEGIN
    v_index := v_index + 1;
    
    IF INSERTING THEN
        v_logs(v_index).action_type := 'INSERT';
        v_logs(v_index).new_data := 'Amount: ' || :NEW.amount || ', Type: ' || :NEW.transaction_type;
        
    ELSIF UPDATING THEN
        v_logs(v_index).action_type := 'UPDATE';
        v_logs(v_index).old_data := 'Amount: ' || :OLD.amount || ', Type: ' || :OLD.transaction_type;
        v_logs(v_index).new_data := 'Amount: ' || :NEW.amount || ', Type: ' || :NEW.transaction_type;
        
    ELSIF DELETING THEN
        v_logs(v_index).action_type := 'DELETE';
        v_logs(v_index).old_data := 'Amount: ' || :OLD.amount || ', Type: ' || :OLD.transaction_type;
    END IF;

    v_logs(v_index).user_name := USER;
    v_logs(v_index).table_name := 'transactions';
END AFTER EACH ROW;

AFTER STATEMENT IS
BEGIN
    FOR i IN 1 .. v_logs.COUNT LOOP
        INSERT INTO audit_log (action_type, table_name, user_name, old_data, new_data)
        VALUES (
            v_logs(i).action_type,
            v_logs(i).table_name,
            v_logs(i).user_name,
            v_logs(i).old_data,
            v_logs(i).new_data
        );
    END LOOP;
END AFTER STATEMENT;

END trg_audit_transactions_bulk;

```
## **🛰️ 3. Auditing with Restrictions and Tracking**

**🔹 Step 1: Audit Table**

```sql
CREATE TABLE audit_log (
    log_id NUMBER GENERATED BY DEFAULT AS IDENTITY PRIMARY KEY,
    action_type VARCHAR2(10),
    table_name VARCHAR2(50),
    user_name VARCHAR2(50),
    action_time TIMESTAMP DEFAULT SYSTIMESTAMP,
    old_data CLOB,
    new_data CLOB
);

```

**Step 2: Audit Trigger**

```sql
CREATE OR REPLACE TRIGGER trg_audit_transactions
AFTER INSERT OR UPDATE OR DELETE ON transactions
FOR EACH ROW
DECLARE
    v_old_data CLOB := NULL;
    v_new_data CLOB := NULL;
BEGIN
    IF INSERTING THEN
        v_new_data := 'Amount: ' || :NEW.amount || ', Type: ' || :NEW.transaction_type;
        INSERT INTO audit_log (action_type, table_name, user_name, new_data)
        VALUES ('INSERT', 'transactions', USER, v_new_data);
        
    ELSIF UPDATING THEN
        v_old_data := 'Amount: ' || :OLD.amount || ', Type: ' || :OLD.transaction_type;
        v_new_data := 'Amount: ' || :NEW.amount || ', Type: ' || :NEW.transaction_type;
        INSERT INTO audit_log (action_type, table_name, user_name, old_data, new_data)
        VALUES ('UPDATE', 'transactions', USER, v_old_data, v_new_data);
        
    ELSIF DELETING THEN
        v_old_data := 'Amount: ' || :OLD.amount || ', Type: ' || :OLD.transaction_type;
        INSERT INTO audit_log (action_type, table_name, user_name, old_data)
        VALUES ('DELETE', 'transactions', USER, v_old_data);
    END IF;
END;


```

**🔹 Step 3: Optional — Use a Package for Auditing**
```sql
CREATE OR REPLACE PACKAGE audit_pkg AS
    PROCEDURE log_action(
        p_action_type IN VARCHAR2,
        p_table_name IN VARCHAR2,
        p_user_name IN VARCHAR2,
        p_old_data IN CLOB,
        p_new_data IN CLOB
    );
END audit_pkg;
/

CREATE OR REPLACE PACKAGE BODY audit_pkg AS
    PROCEDURE log_action(
        p_action_type IN VARCHAR2,
        p_table_name IN VARCHAR2,
        p_user_name IN VARCHAR2,
        p_old_data IN CLOB,
        p_new_data IN CLOB
    ) IS
    BEGIN
        INSERT INTO audit_log (
            action_type, table_name, user_name, old_data, new_data
        ) VALUES (
            p_action_type, p_table_name, p_user_name, p_old_data, p_new_data
        );
    END log_action;
END audit_pkg;

```


## **📩 MAIN CONCLUSION OF ALL PHASES**

The Biometric-Based Transaction Authorization System database schema provides a robust security framework that replaces vulnerable traditional authentication methods with advanced biometric verification, effectively addressing fraud risks across multiple sectors while delivering a seamless user experience without credential management burdens; the carefully structured relational model—with encrypted biometric storage, comprehensive transaction tracking, and thorough audit trails—ensures regulatory compliance, optimal performance, and enterprise-level scalability.
