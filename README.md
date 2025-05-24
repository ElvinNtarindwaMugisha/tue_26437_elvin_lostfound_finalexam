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

![bpmn](https://github.com/user-attachments/assets/7374a41e-9723-4595-987c-650d3510c892)



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

![erd](https://github.com/user-attachments/assets/5c4faaf4-fdc4-4361-8df9-e44b73388cda)



---
### 🌀 *Phase IV*

### *Pluggable database creation*
![finalexam phase4](https://github.com/user-attachments/assets/72c73eac-a5ba-4e35-8cae-8c94b18426ec)
![finalexam phase4(1)](https://github.com/user-attachments/assets/3f15f39e-b9e7-4802-9cc4-ae8962c83400)


📠 *What This Phase Covers*
This phase focuses on creating a Pluggable Database (PDB) and converting the logical model into a physical database structure. It ensures that all tables, relationships, and constraints are implemented to meet project requirements.

🔨*Database Creation*
The Pluggable Database (PDB) was created using the following naming format:
sql
Database Name:tue_26437_elvin_lostfound_db
Username: elvin
Password: elvin

Steps Executed in SQL Command Prompt
1.Create a pluggable database:
sql
create pluggable database tue_26437_elvin_lostfound_db
  2  admin user tue_26437_elvin_lostfound_db identified by elvin
  3  file_name_convert=('D:\ORACLE\ORADATA\ORCADATA\XE\PDBseed\','D:\ORACLE\ORADATA\XE\tue_26437_elvin_lostfound_db\');

 Pluggable database created.

2.Open the newly created PDB:

sql
 alter pluggable database tue_26437_elvin_lostfound_db open ;

Pluggable database altered.

Purpose: Makes the PDB active and ready for operations.

3.save the newly created PDB.
sql
SQL> alter pluggable database tue_26437_elvin_lostfound_db save state;

Pluggable database altered.

Purpose: Ensures the PDB remains open after the database restarts.

4. Set the Session Container
   
sql
SQL> alter session set container =tue_26437_elvin_lostfound_db;

Session altered.

Purpose: Switches the session to the newly created PDB for subsequent operations.

5.User Creation and Privilege Assignment

Create a Database User
sql
SQL> create user elvin identified by elvin;

User created.

Purpose: Creates a new user, elvin, with the password elvin.

Grant Basic Privileges
sql
 SQL> grant all privileges to elvin;

Grant succeeded.

Purpose: To assigns full privileges for database operations.

### *Oracle Enterprise Manager (OEM)*

Oracle Enterprise Manager (OEM) is not a PL/SQL keyword or feature—it’s Oracle’s web-based administrative console for the entire Oracle technology stack (databases, middleware, engineered systems, cloud services, etc.). When people mention OEM while discussing PL/SQL code, they’re usually talking about using the OEM interface to manage, monitor, or debug that code inside the database.

### ⚖️ *Oracle Enterprise Manager (OEM)*

The OEM interface confirmed:

Successful creation of the database.

Proper implementation of relationships between tables.

### 📸 *OEM confirm successful database creation and table relationships.*

![OEM(elv)](https://github.com/user-attachments/assets/4dffd428-7d50-40e8-aa9f-f1ed47a91dbd)
![OEM(elv1)](https://github.com/user-attachments/assets/9a33ac9a-3f34-41ae-9fa7-32f9cde5e02d)



### 🔭 *Conclusion About this phase*

This phase successfully established the pluggable database and implemented the physical structure, enabling efficient data management for the Biometric based transaction system.

## Phase V

### Physical Database Structure

Physical Database Structure converts the logical Entity-Relationship model into a physical Oracle database structure, implementing all required tables, relationships, and data integrity constraints to support biometric-based authentication for secure financial transactions.

## 🧱 *Table Creation*

Here are the created tables & codes used to create them

📋 *User table* 

```sql
CREATE TABLE Users (
    UserID INT PRIMARY KEY,
    FirstName VARCHAR2(50),
    LastName VARCHAR2(50),
    Email VARCHAR2(100) UNIQUE NOT NULL,
    UserType VARCHAR2(20) CHECK (UserType IN ('Student', 'Staff', 'Faculty')),
    PhoneNumber VARCHAR2(15) DEFAULT NULL
);
```


📋 *Item table*


```sql
CREATE TABLE Item (
    ItemID INT PRIMARY KEY,
    ItemName VARCHAR2(100),
    Description VARCHAR2(255),
    DateLost DATE,
    LocationLost VARCHAR2(100),
    Status VARCHAR2(20) CHECK (Status IN ('Lost', 'Found', 'Claimed')),
    ReportedBy INT,
    FOREIGN KEY (ReportedBy) REFERENCES Users(UserID)
);
```



📋 *FoundItem table*

```sql
CREATE TABLE FoundItem (
    FoundItemID INT PRIMARY KEY,
    ItemID INT,
    DateFound DATE,
    LocationFound VARCHAR2(100),
    FoundBy INT,
    FOREIGN KEY (ItemID) REFERENCES Item(ItemID),
    FOREIGN KEY (FoundBy) REFERENCES Users(UserID)
);
```

📋 *Claim Table*

```sql
CREATE TABLE Claim (
    ClaimID INT PRIMARY KEY,
    ItemID INT,
    ClaimedBy INT,
    ClaimDate DATE,
    Status VARCHAR2(20) CHECK (Status IN ('Pending', 'Approved', 'Rejected')),
    AdminID INT,
    FOREIGN KEY (ItemID) REFERENCES Item(ItemID),
    FOREIGN KEY (ClaimedBy) REFERENCES Users(UserID),
    FOREIGN KEY (AdminID) REFERENCES Users(UserID)
);
```
📋 *Notification Table*
```sql
CREATE TABLE Notification (
    NotificationID INT PRIMARY KEY,
    UserID INT,
    Message VARCHAR2(255),
    DateSent DATE,
    IsRead BOOLEAN DEFAULT FALSE,
    FOREIGN KEY (UserID) REFERENCES Users(UserID)
);
```

## *Inserting data*
```
-- Insert Users
INSERT INTO Users VALUES (1, 'John', 'Doe', 'john.doe@example.com', 'Student', '0789123456');
INSERT INTO Users VALUES (2, 'Jane', 'Smith', 'jane.smith@example.com', 'Staff', '0789988776');
INSERT INTO Users VALUES (3, 'Elvin', 'Mugisha', 'elvin@example.com', 'Faculty', '0788344556');

-- Insert Items
INSERT INTO Item VALUES (100, 'Backpack', 'Black Adidas backpack', TO_DATE('2025-05-01','YYYY-MM-DD'), 'Library', 'Lost', 1);

-- Insert Found Items
INSERT INTO FoundItem VALUES (200, 100, TO_DATE('2025-05-02','YYYY-MM-DD'), 'Library Entrance', 2);

-- Insert Claims
INSERT INTO Claim VALUES (300, 100, 1, TO_DATE('2025-05-03','YYYY-MM-DD'), 'Pending', 3);

-- Insert Notifications
INSERT INTO Notification VALUES (400, 1, 'Your lost item has been found.', TO_DATE('2025-05-03','YYYY-MM-DD'), FALSE);
 
```


## *Integrity Validation Queries*

### *Each Item Has At Most One Claim.*

```sql
        
SELECT item_id, COUNT(*) AS num_claims
FROM Claim
GROUP BY item_id;
```
📌 Confirms no duplicate claims are made per item.

🧾 Summary
This phase successfully implements the physical database structure for the Lost & Found Item Management System using Oracle SQL. With all relationships, constraints, and data insertions tested, the system is now ready for real-time operations, procedure execution, and advanced PL/SQL programming.



## Phase VI


   
1.###  *DDL (Data Definition Language) and DML (Data Manipulation Language)*

```sql
-- Insert example
INSERT INTO Item VALUES (101, 'Phone', 'iPhone 12', TO_DATE('2025-05-05', 'YYYY-MM-DD'), 'Cafeteria', 'Lost', 1);

-- Update example
UPDATE Item
SET Status = 'Claimed'
WHERE ItemID = 100;

-- Delete example
DELETE FROM Notification WHERE NotificationID = 400;

-- Alter table to add a column for tracking last update
ALTER TABLE Item ADD LastUpdated DATE;

-- Drop an unused column (if needed)
-- ALTER TABLE Users DROP COLUMN PhoneNumber;
```
![DML DDL phase](https://github.com/user-attachments/assets/f4405d1f-ea23-4ead-8b5d-f774982dbe56)

2.*Simple Problem Statement*

*Problem Statement:*

In the Lost & Found Item Management System, staff users need to efficiently retrieve information about lost items by location and report date, update item statuses when claimed, and handle errors in data manipulation. Modularizing these operations will improve maintainability and error handling.


 Procedure: Fetch Lost Items by Location
```sql
CREATE OR REPLACE PROCEDURE GetLostItemsByLocation (
    p_location IN VARCHAR2
) IS
BEGIN
    FOR rec IN (
        SELECT ItemName, Description, DateLost
        FROM Item
        WHERE LocationLost = p_location AND Status = 'Lost'
    ) LOOP
        DBMS_OUTPUT.PUT_LINE('Item: ' || rec.ItemName || ', Lost On: ' || rec.DateLost);
    END LOOP;
EXCEPTION
    WHEN OTHERS THEN
        DBMS_OUTPUT.PUT_LINE('Error fetching lost items: ' || SQLERRM);
END;
/
```

Function: Count Claimed Items
```sql
CREATE OR REPLACE FUNCTION CountClaimedItems RETURN NUMBER IS
    v_count NUMBER;
BEGIN
    SELECT COUNT(*) INTO v_count FROM Item WHERE Status = 'Claimed';
    RETURN v_count;
EXCEPTION
    WHEN OTHERS THEN
        RETURN -1;
END;
/
```
Cursor + Exception Handling Example
```sql
DECLARE
    CURSOR c_items IS
        SELECT ItemID, ItemName FROM Item WHERE Status = 'Lost';
    v_itemID Item.ItemID%TYPE;
    v_name Item.ItemName%TYPE;
BEGIN
    OPEN c_items;
    LOOP
        FETCH c_items INTO v_itemID, v_name;
        EXIT WHEN c_items%NOTFOUND;
        DBMS_OUTPUT.PUT_LINE('Lost Item: ' || v_name || ' (ID: ' || v_itemID || ')');
    END LOOP;
    CLOSE c_items;
EXCEPTION
    WHEN OTHERS THEN
        DBMS_OUTPUT.PUT_LINE('Error processing cursor: ' || SQLERRM);
END;
/
```
Testing
```sql
-- Test the procedure
EXEC GetLostItemsByLocation('Library');

-- Test the function
SELECT CountClaimedItems FROM dual;

-- Use the package
EXEC LostAndFoundPkg.ShowFoundItems;
SELECT LostAndFoundPkg.GetTotalFound FROM dual;
```

Package Example
a. Package Specification
```sql
CREATE OR REPLACE PACKAGE LostAndFoundPkg IS
    PROCEDURE ShowFoundItems;
    FUNCTION GetTotalFound RETURN NUMBER;
END LostAndFoundPkg;
/
```
b. Package Body
```sql
CREATE OR REPLACE PACKAGE BODY LostAndFoundPkg IS

    PROCEDURE ShowFoundItems IS
    BEGIN
        FOR rec IN (SELECT ItemID, DateFound FROM FoundItem) LOOP
            DBMS_OUTPUT.PUT_LINE('Item ID: ' || rec.ItemID || ', Found: ' || rec.DateFound);
        END LOOP;
    EXCEPTION
        WHEN OTHERS THEN
            DBMS_OUTPUT.PUT_LINE('Error: ' || SQLERRM);
    END;

    FUNCTION GetTotalFound RETURN NUMBER IS
        total NUMBER;
    BEGIN
        SELECT COUNT(*) INTO total FROM FoundItem;
        RETURN total;
    EXCEPTION
        WHEN OTHERS THEN
            RETURN -1;
    END;

END LostAndFoundPkg;
/
```

### *Phase VII*

## 🗂 1. Problem Statement Development
    
### ✅ 1. Problem Statement Development
📌 Problem Statement
In our Lost & Found Item Management System, unauthorized or unintended modifications to the database—especially during restricted periods like weekdays and public holidays—could compromise the integrity and auditability of sensitive information such as user claims and item reports.

To enhance system reliability, we propose implementing:

Triggers to block unauthorized actions on specific days.

Packages to automate auditing tasks.

Auditing to track all critical operations (INSERT, UPDATE, DELETE) for accountability.

🎯 Justification
Triggers help enforce business rules automatically.

Packages group auditing procedures and functions to make the system modular and reusable.

Auditing ensures we maintain a secure and transparent trail of all sensitive database activity.

## ✅*2. Trigger Implementation*

### 📌 *Step 1: Create the Holiday Reference Table*

```sql
CREATE TABLE Holidays (
    HolidayDate DATE PRIMARY KEY,
    Description VARCHAR2(100)
);
```
### 📌 *Step 2: Insert Upcoming Holidays (for testing, choose relevant dates)*
```sql
INSERT INTO Holidays VALUES (TO_DATE('2025-06-01', 'YYYY-MM-DD'), 'Heroes Day');
INSERT INTO Holidays VALUES (TO_DATE('2025-06-05', 'YYYY-MM-DD'), 'Unity Day');
COMMIT;
```

*📌 Step 3: Trigger to Restrict Weekday and Holiday Manipulations*


*This trigger blocks INSERT/UPDATE/DELETE on the Item table:*
```sql
CREATE OR REPLACE TRIGGER trg_restrict_weekday_holiday
BEFORE INSERT OR UPDATE OR DELETE ON Item
FOR EACH ROW
DECLARE
    v_today DATE := SYSDATE;
    v_day   VARCHAR2(10);
    v_count NUMBER;
BEGIN
    SELECT TO_CHAR(v_today, 'DY') INTO v_day FROM dual;

    -- Check if today is Mon-Fri
    IF v_day IN ('MON', 'TUE', 'WED', 'THU', 'FRI') THEN
        RAISE_APPLICATION_ERROR(-20001, 'Modification not allowed on weekdays.');
    END IF;

    -- Check if today is a holiday
    SELECT COUNT(*) INTO v_count FROM Holidays WHERE HolidayDate = TRUNC(v_today);
    IF v_count > 0 THEN
        RAISE_APPLICATION_ERROR(-20002, 'Modification not allowed on holidays.');
    END IF;
END;

```
## * 🔨1. Simple Trigger Implementation*

### ✅ Simple Trigger Implementation on Claim Table

#### 🔹 BEFORE INSERT Trigger

```sql
CREATE OR REPLACE TRIGGER trg_claim_before_insert
BEFORE INSERT ON Claim
FOR EACH ROW
BEGIN
  IF :NEW.Status NOT IN ('Pending', 'Approved', 'Rejected') THEN
    RAISE_APPLICATION_ERROR(-20010, 'Invalid status for a claim.');
  END IF;
END;
```
🔍 Purpose: Prevents inserting invalid status values even before the row hits the table.

#### 🔹 Trigger 2: AFTER DELETE
```sql
CREATE OR REPLACE TRIGGER trg_claim_after_delete
AFTER DELETE ON Claim
FOR EACH ROW
BEGIN
  DBMS_OUTPUT.PUT_LINE('Claim with ID ' || :OLD.claim_id || ' has been deleted.');
END;
```
🔍 Purpose: Tracks deleted claim entries. In production, you'd usually log this to an AuditLog table instead of DBMS_OUTPUT.

#### 📦 Optional Audit Logging in AFTER DELETE (Using Your Package)
```sql
CREATE OR REPLACE TRIGGER trg_claim_audit_after_delete
AFTER DELETE ON Claim
FOR EACH ROW
BEGIN
  pkg_audit_log.log_action(USERENV('SESSIONID'), 'DELETE', 'Claim', 'ALLOWED');
END;
```

## 🔨 *2. Compound Trigger Implementation*

✅ What Is a Compound Trigger?
A compound trigger in Oracle is useful when:

You’re updating multiple rows in a single operation (bulk update).

You need to track state between row-level and statement-level parts of the trigger.

You want to audit or validate actions that span more than one row in a transaction.

📘 Example Use Case for Your Project
Let’s say you want to:

Track how many claims are attempted in one statement.

Prevent more than 3 claims being inserted at once, to avoid abuse or mistakes.


✅ Compound Trigger (on Claim table)

```sql
CREATE OR REPLACE TRIGGER trg_claim_bulk_limit
FOR INSERT ON Claim
COMPOUND TRIGGER

  -- Declare a variable to count inserted claims in the same transaction
  g_claim_count NUMBER := 0;

BEFORE STATEMENT IS
BEGIN
  -- Reset count at start of the statement
  g_claim_count := 0;
END BEFORE STATEMENT;

BEFORE EACH ROW IS
BEGIN
  -- Count each row BEFORE it is inserted
  g_claim_count := g_claim_count + 1;
END BEFORE EACH ROW;

AFTER STATEMENT IS
BEGIN
  -- At the end of the bulk insert, reject if too many claims were inserted
  IF g_claim_count > 3 THEN
    RAISE_APPLICATION_ERROR(-20003, 'You cannot insert more than 3 claims at once.');
  END IF;

  -- Optionally log this operation into AuditLog
  INSERT INTO AuditLog (UserID, Operation, TableName, Status)
  VALUES (USERENV('SESSIONID'), 'INSERT', 'Claim', 'ALLOWED');
END AFTER STATEMENT;

END trg_claim_bulk_limit;
/
```

---

### 🧠 Explanation & Integration

| **Component**       | **Purpose**                                              | **Compatibility**                                 |
|---------------------|----------------------------------------------------------|---------------------------------------------------|
| `BEFORE STATEMENT`  | Initializes a counter                                    | ✅ Works independently of other triggers           |
| `BEFORE EACH ROW`   | Increments count for each insert                         | ✅ Does not conflict with existing auditing        |
| `AFTER STATEMENT`   | Blocks operation if bulk insert > 3 rows; logs audit     | ✅ Fully compatible with your `AuditLog` table     |
| `Audit Insert`      | Tracks that the action happened                          | ✅ Enhances system security and accountability     |

🧪 Example Test Case (Should Fail)

```sql
-- This should raise an error because it inserts more than 3 claims
INSERT INTO Claim (claim_id, item_id, claimed_by, claim_date, status, admin_id)
SELECT 500 + ROWNUM, 100, 1, SYSDATE, 'Pending', 3
FROM dual CONNECT BY LEVEL <= 4;
```

## *🛰️ 3. Auditing with Restrictions and Tracking*

*📌 Step 1: Create an Audit Table*

```sql
CREATE TABLE AuditLog (
    AuditID NUMBER GENERATED BY DEFAULT AS IDENTITY PRIMARY KEY,
    UserID INT,
    Operation VARCHAR2(10),
    TableName VARCHAR2(30),
    ActionDate TIMESTAMP DEFAULT SYSTIMESTAMP,
    Status VARCHAR2(10)
);
```



*📌 Step 2: Create a Trigger for Auditing*
Example: Audit trigger on Claim table

```sql
CREATE OR REPLACE TRIGGER trg_audit_claim
AFTER INSERT OR DELETE OR UPDATE ON Claim
FOR EACH ROW
DECLARE
    v_status VARCHAR2(10) := 'ALLOWED';
BEGIN
    INSERT INTO AuditLog (UserID, Operation, TableName, Status)
    VALUES (USERENV('SESSIONID'), ORA_SYSEVENT, 'Claim', v_status);
END;
```




## 🔐 Auditing with Restrictions and Tracking

This section of the system enhances **data security, accountability, and transparency** by implementing audit tracking, access restrictions, and reusable PL/SQL logic. It ensures that all critical changes to the database are monitored and unauthorized manipulations are prevented.

---

### ✅ 1. Audit Table: `AuditLog`

A centralized log table was created to record sensitive operations such as `INSERT`, `UPDATE`, and `DELETE` on critical tables like `Claim`, `Users`, and `FoundItem`.

```sql
CREATE TABLE AuditLog (
  AuditID NUMBER GENERATED BY DEFAULT AS IDENTITY PRIMARY KEY,
  UserID INT,
  Operation VARCHAR2(10),       -- e.g., INSERT, DELETE, UPDATE
  TableName VARCHAR2(30),       -- e.g., 'Claim'
  ActionDate TIMESTAMP DEFAULT SYSTIMESTAMP,
  Status VARCHAR2(10)           -- e.g., 'ALLOWED', 'DENIED'
);
```

✅ 2. Audit Triggers for Key Tables
Audit triggers were implemented on the most sensitive tables.

🔹 Claim Table Trigger
```sql
CREATE OR REPLACE TRIGGER trg_audit_claim
AFTER INSERT OR DELETE OR UPDATE ON Claim
FOR EACH ROW
BEGIN
  INSERT INTO AuditLog (UserID, Operation, TableName, Status)
  VALUES (USERENV('SESSIONID'), ORA_SYSEVENT, 'Claim', 'ALLOWED');
END;
```
🔹 Users Table Trigger
```sql
CREATE OR REPLACE TRIGGER trg_audit_users
AFTER INSERT OR DELETE OR UPDATE ON Users
FOR EACH ROW
BEGIN
  INSERT INTO AuditLog (UserID, Operation, TableName, Status)
  VALUES (USERENV('SESSIONID'), ORA_SYSEVENT, 'Users', 'ALLOWED');
END;
```
🔹 FoundItem Table Trigger
```sql
CREATE OR REPLACE TRIGGER trg_audit_founditem
AFTER INSERT OR DELETE OR UPDATE ON FoundItem
FOR EACH ROW
BEGIN
  INSERT INTO AuditLog (UserID, Operation, TableName, Status)
  VALUES (USERENV('SESSIONID'), ORA_SYSEVENT, 'FoundItem', 'ALLOWED');
END;
```
✅ 3. PL/SQL Audit Logging Package
A reusable PL/SQL package was created to modularize audit logging for consistency and ease of maintenance.

📦 Package Specification

```sql
CREATE OR REPLACE PACKAGE pkg_audit_log IS
  PROCEDURE log_action(p_user_id INT, p_operation VARCHAR2, p_table_name VARCHAR2, p_status VARCHAR2);
END pkg_audit_log;
```
📦 Package Body
```sql
CREATE OR REPLACE PACKAGE BODY pkg_audit_log IS
  PROCEDURE log_action(p_user_id INT, p_operation VARCHAR2, p_table_name VARCHAR2, p_status VARCHAR2) IS
  BEGIN
    INSERT INTO AuditLog (UserID, Operation, TableName, Status)
    VALUES (p_user_id, p_operation, p_table_name, p_status);
  END;
END pkg_audit_log;
```
📌 Trigger Using the Package
```sql
CREATE OR REPLACE TRIGGER trg_users_pkg_audit
AFTER INSERT OR DELETE OR UPDATE ON Users
FOR EACH ROW
BEGIN
  pkg_audit_log.log_action(USERENV('SESSIONID'), ORA_SYSEVENT, 'Users', 'ALLOWED');
END;
```

✅ 4. Trigger to Block Unauthorized Changes on Weekdays & Holidays
To prevent risky modifications, this trigger blocks INSERT, UPDATE, or DELETE on the Item table if:

Today is Monday to Friday (weekday), or

Today is a registered holiday in the Holidays table

```sql
CREATE OR REPLACE TRIGGER trg_restrict_weekday_holiday
BEFORE INSERT OR UPDATE OR DELETE ON Item
FOR EACH ROW
DECLARE
    v_today DATE := SYSDATE;
    v_day   VARCHAR2(10);
    v_count NUMBER;
BEGIN
    SELECT TO_CHAR(v_today, 'DY') INTO v_day FROM dual;

    IF v_day IN ('MON', 'TUE', 'WED', 'THU', 'FRI') THEN
        RAISE_APPLICATION_ERROR(-20001, 'Modification not allowed on weekdays.');
    END IF;

    SELECT COUNT(*) INTO v_count FROM Holidays WHERE HolidayDate = TRUNC(v_today);
    IF v_count > 0 THEN
        RAISE_APPLICATION_ERROR(-20002, 'Modification not allowed on holidays.');
    END IF;
END;
```
### 🧠 Summary: How This Enhances Security and Accountability

| **Feature**              | **Description**                                                                 |
|--------------------------|---------------------------------------------------------------------------------|
| 🔐 **Access Restriction** | Prevents changes to data during weekdays and holidays                          |
| 🧾 **Auditing**           | Logs all DML (INSERT, UPDATE, DELETE) operations on critical tables             |
| 👤 **User Tracking**      | Captures user ID and session for accountability                                 |
| ⏰ **Time Tracking**      | Records exact date and time of every action                                     |
| ✅ **Audit Status Logging** | Shows whether the action was allowed or denied                              |
| 🧩 **MIS Integration**    | Feeds audit data to reports and dashboards for decision-making                  |


## 🏁 Conclusion

The **Lost & Found Item Management System** is a robust, secure, and well-structured Oracle PL/SQL-based application designed to digitize and streamline the process of reporting, tracking, and claiming lost items in institutional environments such as universities.

Through the implementation of:

- **Well-designed relational tables** with data integrity constraints
- **Advanced PL/SQL features** like procedures, functions, packages, triggers, and compound triggers
- **Security mechanisms** such as weekday/holiday restrictions and auditing
- **Real-time tracking and logging** of user activity and sensitive operations

…this system ensures **data accuracy**, **accountability**, and **user-friendly automation** of previously manual workflows.

It also supports integration with **Management Information Systems (MIS)** by providing structured logs, audit trails, and access controls — which help in reporting, analytics, and decision-making.

### 🎯 Final Outcome

The system not only solves real-world inefficiencies in traditional lost-and-found tracking but also demonstrates how Oracle PL/SQL can be used to build **scalable**, **secure**, and **intelligent** database applications with both operational and administrative value.



