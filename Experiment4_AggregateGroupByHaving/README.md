# Experiment 4: Aggregate Functions, Group By and Having Clause

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- **MIN()** – Smallest value  
- **MAX()** – Largest value  
- **COUNT()** – Number of rows  
- **SUM()** – Total of values  
- **AVG()** – Average of values

**Syntax:**
```sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;
```
### GROUP BY
Groups records with the same values in specified columns.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;
```
### HAVING
Filters the grouped records based on aggregate conditions.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

**Question 1**
--
How many medical records does each doctor have?

Sample table:MedicalRecords Table



For example:

Result
DoctorID    TotalRecords
----------  ------------
3           4
5           1
6           1
7           1
8           3


```sql
select DoctorID,count(*) as TotalRecords from MedicalRecords group by DoctorID
```

**Output:**

<img width="1217" height="557" alt="Screenshot 2025-10-25 083410" src="https://github.com/user-attachments/assets/3102c48a-ff7e-4cbf-8d72-a2ded21186f9" />

**Question 2**
---
What is the most common diagnosis among patients?

Sample table:MedicalRecords Table



For example:

Result
Diagnosis              DiagnosisCount
---------------------  --------------
Childhood vaccination  3


```sql
select Diagnosis,count(*) as DiagnosisCount from MedicalRecords group by  Diagnosis order by  DiagnosisCount Desc
limit 1;
```

**Output:**

<img width="1091" height="341" alt="Screenshot 2025-10-25 084010" src="https://github.com/user-attachments/assets/dd8d751d-0fcd-4432-988f-f2093cecdd35" />


**Question 3**
---
How many patients have expired insurance coverage for each insurance company?

Sample table:Insurance Table



For example:

Result
InsuranceCompany  TotalExpiredPatients
----------------  --------------------
ABC Insurance     1
DEF Insurance     1
GHI Insurance     1
JKL Insurance     1
MNO Insurance     1
PQR Insurance     1
STU Insurance     1
VWX Insurance     1
XYZ Insurance     1
YZA Insurance     1

```sql
select InsuranceCompany,count(*) as TotalExpiredPatients from Insurance where ValidityPeriod < CURRENT_DATE group by InsuranceCompany
```

**Output:**

<img width="915" height="742" alt="Screenshot 2025-10-25 084021" src="https://github.com/user-attachments/assets/0cc69129-eb27-4012-ac31-e166050ec103" />


**Question 4**
---
Write a SQL query to calculate the average purchase amount of all orders. Return average purchase amount.

Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id

----------  ----------  ----------  -----------  -----------

70001       150.5       2012-10-05  3005         5002

70009       270.65      2012-09-10  3001         5005

70002       65.26       2012-10-05  3002         5001

 

For example:

Result
AVERAGE
----------
1461.765


```sql
select avg(purch_amt) as AVERAGE from orders
```

**Output:**

<img width="560" height="346" alt="Screenshot 2025-10-25 084030" src="https://github.com/user-attachments/assets/e641d2cf-1146-4b7d-abaa-0c90e017f5e0" />


**Question 5**
---
Write a SQL query to find the total income of employees aged 40 or above.

Table: employee

name        type
----------  ----------
id          INTEGER
name        TEXT
age         INTEGER
city        TEXT
income      INTEGER
For example:

Result
total_income
------------
1800000


```sql
select sum(income) as total_income from employee where age>=40
```

**Output:**

<img width="619" height="345" alt="Screenshot 2025-10-25 084039" src="https://github.com/user-attachments/assets/809a41c6-848f-4437-a62f-5cd22c99d085" />


**Question 6**
---
Write a SQL query to calculate total purchase amount of all orders. Return total purchase amount.

Sample table: orders

ord_no      purch_amt   ord_date    customer_id  salesman_id

----------  ----------  ----------  -----------  -----------

70001       150.5       2012-10-05  3005         5002

70009       270.65      2012-09-10  3001         5005

70002       65.26       2012-10-05  3002         5001

For example:

Result
TOTAL
----------
17541.18


```sql
select sum(purch_amt) as TOTAL from orders
```

**Output:**

<img width="556" height="347" alt="Screenshot 2025-10-25 084048" src="https://github.com/user-attachments/assets/ca6bfbe9-21ed-4c8d-9a34-3a064fc8fe76" />


**Question 7**
---
Write a SQL query to find the total number of unique cities in the customer table?

Table: customer

name        type
----------  ----------
id          INTEGER
name        TEXT
city        TEXT
email       TEXT
phone       INTEGER
For example:

Result
unique_cities
-------------
10

```sql
select count(DISTINCT city) as unique_cities from customer;
```

**Output:**

<img width="613" height="346" alt="Screenshot 2025-10-25 084055" src="https://github.com/user-attachments/assets/ba0be8f7-0180-4a3e-a884-4a6b54a5f1f2" />

**Question 8**
---
Write a SQL query to identify the cities (addresses) where the average salary is greater than Rs. 5000, as per the "customer1" table.

Sample table: customer1



For example:

Result
address     AVG(salary)
----------  -----------
Bhopal      8500.0
Indore      10000.0
Mumbai      6500.0


```sql
select address,avg(salary) as 'AVG(salary)' from customer1 group by address having avg(salary)>5000;
```

**Output:**

<img width="699" height="465" alt="Screenshot 2025-10-25 084104" src="https://github.com/user-attachments/assets/8872fd34-9e17-48fd-a84d-0d34faafb721" />


**Question 9**
---
Write the SQL query that performs grouping by age groups and displays the maximum salary for each group, excluding groups where the maximum salary is not greater than 8000. 

Note: Calculate the age group as multiples of 5.

Eg., 20,22,23 comes in age group 20. 

25,27,29 comes in age group 25.

Sample table: customer1



For example:

Result
age_group   MAX(salary)
----------  -----------
20          10000
25          8500


```sql
select (age/5) * 5 as age_group,MAX(salary) as 'MAX(salary)' from customer1 group by age_group having MAX(salary)>8000
```

**Output:**

<img width="747" height="396" alt="Screenshot 2025-10-25 084112" src="https://github.com/user-attachments/assets/67c145e8-eb0f-4811-8b76-b2182d1681d4" />


**Question 10**
---
Write the SQL query that achieves the grouping of data by age intervals using the expression (age/5)5, calculates the total salary sum for each group, and excludes groups where the total salary sum is not greater than 5000.

Sample table: customer1



For example:

Result
age_group   SUM(salary)
----------  -----------
20          16500
25          16500

```sql
select (age/5) * 5 as age_group,sum(salary) as 'SUM(salary)' from customer1 group by age_group having sum(salary)>5000;
```

**Output:**

<img width="750" height="400" alt="Screenshot 2025-10-25 084119" src="https://github.com/user-attachments/assets/2d3c8f9d-9c09-43a3-8486-79d4bd563440" />


## COMPLETION STATUS

<img width="1417" height="149" alt="Screenshot 2025-10-25 084513" src="https://github.com/user-attachments/assets/bdb9f2c8-be78-4429-8be9-30e1913efed4" />




## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
