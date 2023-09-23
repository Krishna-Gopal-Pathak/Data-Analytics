## Database
A database is a system that allows users to store and organize data.

## SQL
- Relational Database

**Structure**  
- Table-based

## NoSQL
- Non-relational Databases
**Structure**
- key-value pairs
- Document-based
- Graph databases
- Wide-column stores

## Database Platforms
- MySQL
- PostgreSQL
- Microsoft SQL Server
- Oracle PL/SQL
- snowflake
- Amazon REDSHIFT

## Excel Use
- Small Amount of Data
- One-Time Analysis
- Quick Chart/Graph
- Untrained Person

## Database Use
- Large Amount of Data
- Store real-time data from websites/apps
- Easily combine with different datasets
- Automate steps and can re-use
- Easy and safe access
- Data Integrity
- Deep search capabilities

## Data Type
- What value, column can be stored?
  - **String:** char, varchar, etc.
  - **Numeric:** int, float, bool, etc
  - **date and time**
 
## Commonly Used Data Type
- **int:** specify integer value. 
- **float:** specify decimal value.
- **bool:** specify boolean value true or false.
- **char:** fixed-length string that contains a number, letter, and special character.
- **varchar:** variable-length string that contains a number, letter, and special character.
- **date:** date format YYYY-MM-DD.
- **datetime:** YYYY-MM-DD hh:mm:ss.

## Primary Key
- Unique column in a table.
- Table can have only one primary key, which should be unique and NOT NULL.

## Foreign Key
- Used to link two or more tables together
- Table can have any number of foreign keys, and can contain duplicate and NULL values.

## Constraints
- Constraints are used to specify rules for data in a table.
- Ensures accuracy and reliability of data in the table.

## Commonly used constraints 
- **NOT NULL:** Column cannot have NULL value.
- **UNIQUE:** Columns have unique values.
- **Primary key:**  Unique and NOT NULL.
- **Foreign key:**
- **Check:** satisfies a specific condition.
- **Default:** If no value is specified for a column then set a default value.
- **Create Index:** Create and retrieve data from the database very quickly.

## Create Table
```bash
CREATE TABLE cust1
(
	"ID" int8 primary key,
	"Name" varchar(50) not null,
	"Age" int not null,
	"City" char(50),
	"Salary" numeric
);
```

## Insert Values
```bash
INSERT INTO cust1 ("ID", "Name", "Age", "City", "Salary") 
VALUES 
(1, 'Ram', 26, 'Delhi', 9000),
(2, 'Kris', 27, 'Goa', 9000);
```
## Update Values
```bash
UPDATE cust1
SET "Name" = 'Krishna', "Age" = 30
WHERE "ID" = 2;
```
## Delete Values
- Delete existing records in a table.
```bash
Delete FROM cust1 WHERE "ID"=2
```

## Drop
- Delete a table
```bash
DROP TABLE cust1
```

## Truncate
- Deletes the data inside a table, but not the table itself.
```bash
TRUNCATE TABLE cust1
```

## Select Statement
```bash
select "Name", "Age" from cust1
```

## Where Clause
- Extract only those records that fulfilled specified conditions.
- Used with SELECT statement.
```bash
select "Name" from cust1 where "Age"=26
```

## Operators
- Reserved words and characters used with WHERE clause.
  - **Arithematic operators:** Addition(+), Substraction(-), Multiplication(*), Division(/), Modulus(%).
  - **Comparison operators:** Equal(=), Not Equal(!=), Greater Than(>), Greater Than Equals to(>=).
  - **Logical operators:** All, IN, BETWEEN, LIKE, AND, OR, NOT, ANY
  - **Bitwise operator:** Bitwise AND(&), Bitwise OR(|)
 
## AND
```bash
select * from cust1 where "City"='Delhi' AND "Age"<26
```

## LIMIT clause
- It specifies the maximum number of rows to return in the result set.
```bash
select * from cust1 LIMIT 2;
```

## ORDER BY
- Sort Result-set in ASC and DESC
```bash
select * from cust1 ORDER BY "Name" ASC;
```
```bash
select * from cust1 ORDER BY "Name" DESC;
```

## How to import CSV file to SQL
**Demo.csv**

![image](https://github.com/Krishna-Gopal-Pathak/Data-Analytics/assets/142927819/453a0af3-c809-4ec1-946e-9516b1c7cf6e)

**Create a Database with Excel data-header name**
```bash
CREATE TABLE cust1
(
	customer_id int8 primary key,
	first_name varchar(50),
	last_name varchar(50),
	email varchar(100),
	address_id int8
);
```

**Import Excel**
```bash
COPY customer(customer_id,first_name,last_name,email,address_id)
FROM 'D:\Repo\Data-Analytics\SQL for Data Analytics\DemoData.csv'
DELIMITER ','
CSV HEADER;
```

## Functions in SQL
- Set of SQL statements to perform a specific task.
- A function accepts input parameters, performs actions, and then return the result.

## Types of function
- **System Defined Function:** built in functions eg- rand(), round(), upper(), lower(), count(), sum(), max(), etc.
- **User-Defined Function:** Once you define a function can call it in the same way as the built-in functions.

## Most Used String Function
- String functions are used to perform an operation on an input string and return an output string.
  
  - **NOW():** returns the current system date and time.
  - **FORMAT():** used to set the format of a field.
  - **REPLACE():** Replaces all occurrences of a substring within a string, with a new
    ```bash
    select REPLACE(first_name, 'Mary', 'Mohan'), first_name, last_name from customer
    ```
  - **TRIM():** removes leading and trailing spaces (or other specified characters) from
  - **UPPER()**
    ```bash
    select UPPER(first_name) from customer
    ```
  - **LOWER()**
    ```bash
    select LOWER(first_name) from customer
    ```
  - **LENGTH()**
    ```bash
    select LENGTH(first_name), first_name from customer
    ```
  - **SUBSTRING()**
    ```bash
    select SUBSTRING(first_name, 1, 3), first_name from customer
    ```

## Most Used Aggregate Function
- Used with **GROUP BY** and **SELECT** statement.
- Performs calculation on multiple values and returns single value.

  - **COUNT()**
  - **SUM()**
  - **AVG()**
  - **MAX()**
  - **MIN()**
  - **ROUND()**

**Create Database**
```bash
CREATE TABLE payment
(
	customer_id int8 primary key,
	amount numeric,
	mode varchar(50),
	payment_date DATE
);
```
**Import CSV file**

![image](https://github.com/Krishna-Gopal-Pathak/Data-Analytics/assets/142927819/7d61dc41-df5d-4c13-9321-602cb27d1c24)


  - **COUNT()**
    ```bash
    SELECT count(*) from payment
    ```
     ```bash
    SELECT count(amount) from payment
    ```
  - **SUM()**
    ```bash
    SELECT SUM(amount) from payment
    ```
  - **AVG()**
    ```bash
    SELECT AVG(amount) from payment
    ```
   
  - **MAX()**
    ```bash
    SELECT MAX(amount) from payment
    ```
  - **MIN()**
    ```bash
    select LENGTH(first_name), first_name from customer
    ```
  - **ROUND()**
    ```bash
    SELECT ROUND(AVG(amount), 2) from payment
    ```

## GROUP BY Statement
- Used with aggregate function **COUNT()**, **SUM()**, **AVG()**, **MAX()**, **MIN()** 
- GROUP BY statement group rows that have the same values.
  ```bash
  SELECT mode, SUM(amount) 
  FROM payment
  GROUP BY mode
  ```

  ```bash
  SELECT mode, SUM(amount) AS Total 
  FROM payment
  GROUP BY mode
  ORDER BY Total ASC
  ```
    
## HAVING Clause
- Used to apply a filter on the result of GROUP BY based on a specified condition.
  ```bash
  SELECT mode, SUM(amount) AS Total 
  FROM payment
  GROUP BY mode
  HAVING SUM(amount) >= 100 
  ORDER BY Total ASC
  ```
  ```bash
  SELECT mode, SUM(amount) AS Total 
  FROM payment
  GROUP BY mode
  HAVING SUM(amount) >= 100 AND SUM(amount) <= 200
  ORDER BY Total ASC
  ```
  
## TIMESTAMP
- **TIME:** HH:Mi:SS
- **DATE:** YYYY-MM-DD
- **YEAR:** YYYY or YY
- **TIMESTAMP:** YYYY-MM-DD HH:Mi:SS
- **TIMESTAMPTZ:** Contain date, time and time zone

## TIMESTAMP functions/operators
- SHOW TIMEZONE
- SELECT NOW()
- SELECT TIMEOFDAY()
- SELECT CURRENT_TIME
- SELECT CURRENT_DATE

## EXTRACT function
- Extracts a part from a given date value.
- **Syntax:** SELECT EXTRACT(MONTH FROM date_field) FROM Table
  - **YEAR**
    ```bash
    SELECT EXTRACT(YEAR FROM payment_date) AS Year from payment
    ```
  - **QUARTER**
  - **MONTH**
    ```bash
    SELECT EXTRACT(MONTH FROM payment_date) AS Year from payment
    ```
  - **WEEK**
  - **DAY**
    ```bash
    SELECT EXTRACT(DAY FROM payment_date) AS Year from payment
    ```
  - **HOUR**
  - **MINUTE**
  - **DOW**             //day of week
    ```bash
    SELECT EXTRACT(DOW FROM payment_date) AS Year from payment
    ```        
  - **DOY**             //day of year
    ```bash
    SELECT EXTRACT(DOY FROM payment_date) AS Year from payment
    ```  

## JOIN
- JOIN clause is used to combine data from two or more tables, based on a related column between them.

## Types of Joins
- INNER JOIN
- LEFT JOIN
- RIGHT JOIN
- FULL JOIN

**INNER JOIN**
- Return records that have matching values in both tables.
 ```bash
SELECT * from payment AS p INNER JOIN customer AS c ON p.customer_id=c.customer_id
```

**LEFT JOIN**
- Return all records from the left table and the matched table from the right table.
 ```bash
SELECT * from customer AS c LEFT JOIN payment AS p ON c.customer_id=p.customer_id
```
