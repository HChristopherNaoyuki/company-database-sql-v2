# Company Database SQL V2

A comprehensive SQL-based relational database designed to model a fictional corporate 
structure inspired by *The Office*. This schema includes employees, branches, clients, 
suppliers, and sales tracking with a focus on referential integrity and realistic relationships.

---

## Table of Contents

1. [Project Overview](#project-overview)
2. [Schema Architecture](#schema-architecture)
   * [Entity Relationship Model](#entity-relationship-model)
   * [Tables and Constraints](#tables-and-constraints)
3. [Installation & Setup](#installation--setup)
4. [Data Population](#data-population)
5. [Sample Queries](#sample-queries)
6. [Features](#features)
7. [Use Cases](#use-cases)
8. [Acknowledgments](#acknowledgments)
9. [Disclaimer](#disclaimer)

---

## Project Overview

**Company Database SQL V2** is a SQL-based data model of a mid-size corporation with multiple branches and employees. 
The project emphasizes realistic business logic with normalized design patterns, foreign key relationships, and integrity constraints. 
It is suitable for educational purposes, database design exercises, and as a foundation for enterprise applications.

GitHub Repository: [https://github.com/HChristopherNaoyuki/company-database-sql-v2.git](https://github.com/HChristopherNaoyuki/company-database-sql-v2.git)

---

## Schema Architecture

### Entity Relationship Model

The database models the following key entities:

* **Employee**
* **Branch**
* **Client**
* **Works\_With (Sales)**
* **Branch\_Supplier**

Relationships:

* Each **employee** may report to a supervisor (self-referencing).
* Each **branch** has one manager (employee).
* Employees are assigned to **branches**.
* Each **client** is associated with a **branch**.
* **Employees** work with **clients** through the **works\_with** table that logs sales.
* **Branches** are supported by **suppliers** via the **branch\_supplier** table.

### Tables and Constraints

| Table             | Description                                                      |
| ----------------- | ---------------------------------------------------------------- |
| `employee`        | Stores employee data and references their supervisor and branch  |
| `branch`          | Contains branch information and links to a manager (employee)    |
| `client`          | Represents corporate clients associated with a specific branch   |
| `works_with`      | Associative table linking employees with clients and total sales |
| `branch_supplier` | Lists suppliers for each branch and their supply types           |

All foreign keys enforce referential integrity with proper `ON DELETE` behaviors like `CASCADE` and `SET NULL`.

---

## Installation & Setup

### Prerequisites

* SQL Server, MySQL, or compatible RDBMS
* SQL execution environment (e.g., MySQL Workbench, DBeaver, pgAdmin)

### Steps

1. Clone the repository:

   ```bash
   git clone https://github.com/HChristopherNaoyuki/company-database-sql-v2.git
   cd company-database-sql-v2
   ```

2. Open your SQL tool and execute the script:

   * Run the entire SQL script provided in `solution.sql` or use the contents from the repository directly.

---

## Data Population

The script includes sample data to demonstrate relationships and enable test queries. Highlights:

* Corporate-level executives (e.g., David Wallace)
* Branch managers for Scranton, Stamford, and Corporate
* Multiple clients per branch
* Realistic supplier assignments
* Sales activities between employees and clients

---

## Sample Queries

```sql
-- List all employees
SELECT * FROM employee;

-- Get total sales per employee
SELECT emp_id, SUM(total_sales) AS total_sales
FROM works_with
GROUP BY emp_id;

-- Find all clients worked with by Jim Halpert
SELECT c.client_name
FROM works_with ww
JOIN client c ON ww.client_id = c.client_id
WHERE ww.emp_id = 108;

-- Get suppliers for Stamford branch
SELECT supplier_name, supply_type
FROM branch_supplier
WHERE branch_id = 3;
```

---

## Features

* Full relational integrity with cascading rules
* Self-referencing foreign key (employee-supervisor)
* Branch and manager dependency with `ON DELETE SET NULL`
* Many-to-many relationships via associative tables
* Realistic, detailed data for testing business scenarios

---

## Use Cases

* Academic database design projects
* SQL teaching and training
* Sample backend schema for fictional applications
* Mock data for analytics and reporting tools

---

## Acknowledgments

* Inspired by characters and structure from *The Office*
* Created for educational and demonstrational purposes

---

## DISCLAIMER

UNDER NO CIRCUMSTANCES SHOULD IMAGES OR EMOJIS BE INCLUDED DIRECTLY 
IN THE README FILE. ALL VISUAL MEDIA, INCLUDING SCREENSHOTS AND IMAGES 
OF THE APPLICATION, MUST BE STORED IN A DEDICATED FOLDER WITHIN THE 
PROJECT DIRECTORY. THIS FOLDER SHOULD BE CLEARLY STRUCTURED AND NAMED 
ACCORDINGLY TO INDICATE THAT IT CONTAINS ALL VISUAL CONTENT RELATED TO 
THE APPLICATION (FOR EXAMPLE, A FOLDER NAMED IMAGES, SCREENSHOTS, OR MEDIA).

I AM NOT LIABLE OR RESPONSIBLE FOR ANY MALFUNCTIONS, DEFECTS, OR ISSUES 
THAT MAY OCCUR AS A RESULT OF COPYING, MODIFYING, OR USING THIS SOFTWARE. 
IF YOU ENCOUNTER ANY PROBLEMS OR ERRORS, PLEASE DO NOT ATTEMPT TO FIX THEM 
SILENTLY OR OUTSIDE THE PROJECT. INSTEAD, KINDLY SUBMIT A PULL REQUEST 
OR OPEN AN ISSUE ON THE CORRESPONDING GITHUB REPOSITORY, SO THAT IT CAN 
BE ADDRESSED APPROPRIATELY BY THE MAINTAINERS OR CONTRIBUTORS.

---
