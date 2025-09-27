# ER Diagram Workshop – Submission Template

## Objective
To understand and apply ER modeling concepts by creating ER diagrams for real-world applications.

## Purpose
Gain hands-on experience in designing ER diagrams that represent database structure including entities, relationships, attributes, and constraints.

---

# Scenario A: City Fitness Club Management

**Business Context:**  
FlexiFit Gym wants a database to manage its members, trainers, and fitness programs.

**Requirements:**  
- Members register with name, membership type, and start date.  
- Each member can join multiple programs (Yoga, Zumba, Weight Training).  
- Trainers assigned to programs; a program may have multiple trainers.  
- Members may book personal training sessions with trainers.  
- Attendance recorded for each session.  
- Payments tracked for memberships and sessions.

### ER Diagram:
*Paste or attach your diagram here*  
<img width="797" height="800" alt="Screenshot 2025-09-27 082212" src="https://github.com/user-attachments/assets/7e02e807-2e73-47a4-8275-23dd69a6a80c" />


### Entities and Attributes

| Entity     |                   Attributes (PK, FK)                                   |              Notes                 |
|------------|-------------------------------------------------------------------------|------------------------------------|
| Client     |  client_ID (PK), fname, lname, gender, age, contact_add, email, password|Holds details of gym members.       |
|            |                                                                         |                                    |
| Membership |  mem_ID (PK), client_ID (FK), status, date                              |Membership details linked to client |
|            |                                                                         |                                    |
| Payment    | payment_ID (PK), client_ID (FK), date, amoun                            |Payments made by clients            |
|            |                                                                         |                                    |
| Schedule   | sched_ID (PK), client_ID (FK), trainor_ID (FK), session                 |Workout schedules assigned to client|
|            |                                                                         |                                    |
|Trainor     |trainor_ID (PK), name, sched_ID (FK), salary, email, password            |Trainers responsible for clients    |
|            |                                                                         |                                    |
|            |                                                                         |                                    |


### Relationships and Constraints

| **Relationship**              | **Cardinality** | **Participation**                             | **Notes**                                         |
| ----------------------------- | --------------- | --------------------------------------------- | ------------------------------------------------- |
| Client → Membership           | 1 : N           | Total (every membership belongs to a client)  | A client can have multiple memberships over time. |
| Client → Payment              | 1 : N           | Partial (not all clients may pay immediately) | A client can make many payments.                  |
| Client → Schedule             | 1 : N           | Partial                                       | A client can have many schedules assigned.        |
| Trainor → Schedule            | 1 : N           | Partial                                       | A trainer can manage multiple schedules.          |
| Client → Transaction Records  | 1 : N           | Partial                                       | A client can have multiple transactions.          |
| Transaction Records → Reports | 1 : N           | Total                                         | A report is always generated from transactions.   |
| Client → Reports              | 1 : N           | Partial                                       | Reports are client-specific.                      |
| Schedule → Trainor            | N : 1           | Partial                                       | Each schedule is linked to one trainer.           |



### Assumptions
Client is the central entity.

Membership, Payment, Schedule, Transaction Records, Reports all depend on Client.

Trainor connects with Schedule.

Reports depend on Transaction Records + Client.

---

# Scenario B: City Library Event & Book Lending System

**Business Context:**  
The Central Library wants to manage book lending and cultural events.

**Requirements:**  
- Members borrow books, with loan and return dates tracked.  
- Each book has title, author, and category.  
- Library organizes events; members can register.  
- Each event has one or more speakers/authors.  
- Rooms are booked for events and study.  
- Overdue fines apply for late returns.

### ER Diagram:
*Paste or attach your diagram here*  
![ER Diagram](er_diagram_library.png)

### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
|        |                    |       |
|        |                    |       |
|        |                    |       |
|        |                    |       |
|        |                    |       |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|              |            |               |       |
|              |            |               |       |
|              |            |               |       |

### Assumptions
- 
- 
- 

---

# Scenario C: Restaurant Table Reservation & Ordering

**Business Context:**  
A popular restaurant wants to manage reservations, orders, and billing.

**Requirements:**  
- Customers can reserve tables or walk in.  
- Each reservation includes date, time, and number of guests.  
- Customers place food orders linked to reservations.  
- Each order contains multiple dishes; dishes belong to categories (starter, main, dessert).  
- Bills generated per reservation, including food and service charges.  
- Waiters assigned to serve reservations.

### ER Diagram:
*Paste or attach your diagram here*  
![ER Diagram](er_diagram_restaurant.png)

### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
|        |                    |       |
|        |                    |       |
|        |                    |       |
|        |                    |       |
|        |                    |       |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
|              |            |               |       |
|              |            |               |       |
|              |            |               |       |

### Assumptions
- 
- 
- 

---

## Instructions for Students

1. Complete **all three scenarios** (A, B, C).  
2. Identify entities, relationships, and attributes for each.  
3. Draw ER diagrams using **draw.io / diagrams.net** or hand-drawn & scanned.  
4. Fill in all tables and assumptions for each scenario.  
5. Export the completed Markdown (with diagrams) as **a single PDF**
