# IC-2K25-96-DBMS-VARUN-KALKHOR


LAB 1
Program 1
Problem Statment
Write a SQL statement to create a simple table countries including coloumns country_id,country_name and region_id.

Approach / Algorithm
Use the CREATE TABLE command.
Define the three required columns.
Specify appropriate data types for each column.
Execute the statement.
SQL Query
CREATE TABLE countries (
    country_id VARCHAR(2),
    country_name VARCHAR(40),
    region_id DECIMAL(10,0)
);
Time Complexity
O(1) — Creating the table is a constant-time DDL operation from the user's perspective.
Space Complexity
O(1) initially, excluding storage required for future table data.
Sample Input
CREATE TABLE countries (
    country_id VARCHAR(2),
    country_name VARCHAR(40),
    region_id DECIMAL(10,0)
);
Sample Output
Query OK, 0 rows affected
Screenshot
Learning Outcome
Learned how to create a basic table using CREATE TABLE.
Learned how to define columns and their data types.


Program 2
Problem Statement
Write a SQL statement to create a simple table countries including country_id, country_name and region_id, which already exists. �
assignment-1.docx
Approach / Algorithm
Use CREATE TABLE IF NOT EXISTS so that MySQL creates the table only when it does not already exist.
SQL Query
CREATE TABLE IF NOT EXISTS countries (
    country_id VARCHAR(2),
    country_name VARCHAR(40),
    region_id DECIMAL(10,0)
);
Time Complexity
O(1) for the DDL operation.
Space Complexity
O(1) initially.
Sample Input
CREATE TABLE IF NOT EXISTS countries (
    country_id VARCHAR(2),
    country_name VARCHAR(40),
    region_id DECIMAL(10,0)
);
Sample Output
Query OK, 0 rows affected.
Learning Outcome
Learned the purpose of IF NOT EXISTS.
Learned how to avoid an error when a table already exists.



Program 3
Problem Statement
Write a SQL statement to create the structure of a table dup_countries similar to countries. �
assignment-1.docx
Approach / Algorithm
Use the MySQL LIKE clause to copy the structure of the existing countries table.
SQL Query
CREATE TABLE dup_countries
LIKE countries;
Time Complexity
O(1) for the table-definition operation.
Space Complexity
O(1) with respect to row data because only the structure is copied.
Sample Input
CREATE TABLE dup_countries
LIKE countries;
Sample Output
Query OK, 0 rows affected
Learning Outcome
Learned how to copy an existing table's structure.
Learned the use of CREATE TABLE ... LIKE.



Program 4
Problem Statement
Create a duplicate copy of the countries table including both structure and data, with the name dup_countries. �
assignment-1.docx
Approach / Algorithm
Use CREATE TABLE ... AS SELECT to create a new table using the result of a query on the existing table.
SQL Query
CREATE TABLE dup_countries
AS SELECT * FROM countries;
Time Complexity
O(n) where n is the number of records copied.
Space Complexity
O(n) because the duplicate table stores the copied records.
Sample Input
CREATE TABLE dup_countries
AS SELECT * FROM countries;
Sample Output
Query OK, 0 rows affected
Learning Outcome
Learned how to create a table from a SELECT query.
Learned how to copy table data along with its columns.



Program 5
Problem Statement
Write a SQL statement to create a countries table with a NULL constraint as specified in the assignment. �
assignment-1.docx
Approach / Algorithm
The intended constraint is treated as NOT NULL, ensuring that values cannot be omitted from the specified columns.
SQL Query
CREATE TABLE countries (
    country_id VARCHAR(2) NOT NULL,
    country_name VARCHAR(40) NOT NULL,
    region_id DECIMAL(10,0) NOT NULL
);
Time Complexity
O(1).
Space Complexity
O(1) initially.
Sample Input
INSERT INTO countries
VALUES (NULL, 'India', 1);
Sample Output
ERROR: Column 'country_id' cannot be null
Learning Outcome
Learned the purpose of the NOT NULL constraint.
Learned how constraints control valid table data.



Program 6
Problem Statement
Create a table jobs with job_id, job_title, min_salary and max_salary, and ensure that max_salary does not exceed 25000. �
assignment-1.docx
Approach / Algorithm
Use a CHECK constraint on max_salary.
SQL Query
CREATE TABLE jobs (
    job_id VARCHAR(10) NOT NULL,
    job_title VARCHAR(35) NOT NULL,
    min_salary DECIMAL(6,0),
    max_salary DECIMAL(6,0),
    CHECK (max_salary <= 25000)
);
Time Complexity
O(1) for table creation.
Space Complexity
O(1) initially.
Sample Input
INSERT INTO jobs
VALUES ('J01', 'Manager', 10000, 30000);
Sample Output
ERROR: Check constraint violated
Learning Outcome
Learned how to use the CHECK constraint.
Learned how to restrict column values according to a condition.



Program 7
Problem Statement
Create a countries table and ensure that only Italy, India and China can be entered. �
assignment-1.docx
Approach / Algorithm
Use a CHECK constraint with the IN operator.
SQL Query
CREATE TABLE countries (
    country_id VARCHAR(2),
    country_name VARCHAR(40)
        CHECK (country_name IN ('Italy', 'India', 'China')),
    region_id DECIMAL(10,0)
);
Time Complexity
O(1) for the table creation operation.
Space Complexity
O(1) initially.
Sample Input
INSERT INTO countries
VALUES ('US', 'USA', 1);
Sample Output
ERROR: Check constraint violated
Learning Outcome
Learned how to restrict values using CHECK.
Learned how to use the IN operator inside a constraint.



Program 8
Problem Statement
Create job_history with employee_id, start_date, end_date, job_id and department_id, ensuring the specified format for end_date. �
assignment-1.docx
Approach / Algorithm
Define end_date as a date field and apply the required condition from the assignment.
SQL Query
CREATE TABLE job_history (
    employee_id DECIMAL(6,0) NOT NULL,
    start_date DATE NOT NULL,
    end_date DATE NOT NULL,
    job_id VARCHAR(10) NOT NULL,
    department_id DECIMAL(4,0) NOT NULL
);
Time Complexity
O(1).
Space Complexity
O(1) initially.
Sample Input
INSERT INTO job_history
VALUES (101, '2025-01-01', '2025-12-31', 'J01', 10);
Sample Output
Query OK, 1 row affected
Learning Outcome
Learned how to define date columns.
Learned how date values are stored in SQL.
Note: MySQL's native DATE format is YYYY-MM-DD; the --/--/---- wording in the assignment is a display-format description rather than MySQL's actual storage format.



Program 9
Problem Statement
Create countries and ensure that duplicate values of country_id are not allowed. �
assignment-1.docx
Approach / Algorithm
Apply a UNIQUE constraint to country_id.
SQL Query
CREATE TABLE countries (
    country_id VARCHAR(2) UNIQUE,
    country_name VARCHAR(40),
    region_id DECIMAL(10,0)
);
Time Complexity
O(1) for table creation.
Space Complexity
O(n) for the unique index maintained for n records.
Sample Input
INSERT INTO countries
VALUES ('IN', 'India', 1);

INSERT INTO countries
VALUES ('IN', 'India', 2);
Sample Output
First query: Query OK
Second query: ERROR - Duplicate entry 'IN'
Learning Outcome
Learned the UNIQUE constraint.
Learned how duplicate values can be prevented.



Program 10
Problem Statement
Create jobs with default values such that job_title is blank, min_salary is 8000, and max_salary is NULL when no value is supplied. �
assignment-1.docx
Approach / Algorithm
Use the DEFAULT keyword for the required columns.
SQL Query
CREATE TABLE jobs (
    job_id VARCHAR(10) NOT NULL,
    job_title VARCHAR(35) NOT NULL DEFAULT ' ',
    min_salary DECIMAL(6,0) DEFAULT 8000,
    max_salary DECIMAL(6,0) DEFAULT NULL
);
Time Complexity
O(1).
Space Complexity
O(1) initially.
Sample Input
INSERT INTO jobs (job_id)
VALUES ('J01');

SELECT * FROM jobs;
Sample Output
JOB_ID | JOB_TITLE | MIN_SALARY | MAX_SALARY
J01    |           | 8000       | NULL
Learning Outcome
Learned how to use DEFAULT.
Learned how default values are automatically inserted.



Program 11
Problem Statement
Create countries and make country_id a key field that does not contain duplicate values. �
assignment-1.docx
Approach / Algorithm
Define country_id as the PRIMARY KEY.
SQL Query
CREATE TABLE countries (
    country_id VARCHAR(2) NOT NULL PRIMARY KEY,
    country_name VARCHAR(40),
    region_id DECIMAL(10,0)
);
Time Complexity
O(1) for table creation.
Space Complexity
O(n) for the primary-key index.
Sample Input
INSERT INTO countries
VALUES ('IN', 'India', 1);

INSERT INTO countries
VALUES ('IN', 'India', 2);
Sample Output
First query: Query OK
Second query: ERROR - Duplicate entry 'IN'
Learning Outcome
Learned about primary keys.
Learned that a primary key uniquely identifies records.



Program 12
Problem Statement
Create countries with a unique country_id that stores an automatically incremented value. �
assignment-1.docx
Approach / Algorithm
Use an integer AUTO_INCREMENT column and make it a key.
SQL Query
CREATE TABLE countries (
    country_id INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
    country_name VARCHAR(40),
    region_id DECIMAL(10,0)
);
Time Complexity
O(1) for each generated ID.
Space Complexity
O(n) for storing the records.
Sample Input
INSERT INTO countries (country_name, region_id)
VALUES ('India', 1);

INSERT INTO countries (country_name, region_id)
VALUES ('China', 2);

SELECT * FROM countries;
Sample Output
COUNTRY_ID | COUNTRY_NAME | REGION_ID
1          | India        | 1
2          | China        | 2
Learning Outcome
Learned AUTO_INCREMENT.
Learned how databases automatically generate unique numeric IDs.



Program 13
Problem Statement
Create countries such that the combination of country_id and region_id is unique. �
assignment-1.docx
Approach / Algorithm
Create a composite primary key consisting of country_id and region_id.
SQL Query
CREATE TABLE countries (
    country_id VARCHAR(2),
    country_name VARCHAR(40),
    region_id DECIMAL(10,0),
    PRIMARY KEY (country_id, region_id)
);
Time Complexity
O(1) for table creation.
Space Complexity
O(n) for the composite key index.
Sample Input
INSERT INTO countries
VALUES ('IN', 'India', 1);

INSERT INTO countries
VALUES ('IN', 'India', 1);
Sample Output
First query: Query OK
Second query: ERROR - Duplicate entry 'IN-1'
Learning Outcome
Learned composite keys.
Learned how multiple columns can collectively identify a record.



Program 14
Problem Statement
Create job_history with employee_id having no duplicate values and job_id referencing existing values in the jobs table. The supplied jobs table has JOB_ID as its primary key. 

Approach / Algorithm
Make employee_id the primary key.
Define job_id.
Create a foreign key from job_history.job_id to jobs.job_id.
Use the InnoDB storage engine.

SQL Query
CREATE TABLE job_history (
    employee_id DECIMAL(6,0) NOT NULL PRIMARY KEY,
    start_date DATE NOT NULL,
    end_date DATE NOT NULL,
    job_id VARCHAR(10) NOT NULL,
    department_id DECIMAL(4,0),
    FOREIGN KEY (job_id)
        REFERENCES jobs(job_id)
    ) ENGINE=InnoDB;

Time Complexity
O(1) for table creation; foreign-key validation during insertion is dependent on the referenced index.
Space Complexity
O(n) for storing records and indexes.

Sample Input
INSERT INTO job_history
VALUES (101, '2025-01-01', '2025-12-31', 'INVALID', 10);

Sample Output
ERROR - Cannot add or update a child row:
a foreign key constraint fails

Learning Outcome
Learned foreign-key constraints.
Learned how one table can reference another table.
Learned the importance of InnoDB for foreign-key relationships.



Program 15
Problem Statement
Create employees with a unique employee_id and ensure that the combination of department_id and manager_id exists in the departments table. The supplied departments table contains DEPARTMENT_ID and MANAGER_ID as the relevant composite key.

Approach / Algorithm
Make employee_id the primary key.
Define employee information columns.
Create a composite foreign key using department_id and manager_id.
Reference the corresponding pair in departments.

SQL Query
CREATE TABLE employees (
    employee_id DECIMAL(6,0) NOT NULL PRIMARY KEY,
    first_name VARCHAR(20),
    last_name VARCHAR(25) NOT NULL,
    email VARCHAR(25) NOT NULL,
    phone_number VARCHAR(20),
    hire_date DATE NOT NULL,
    job_id VARCHAR(10),
    salary DECIMAL(8,2),
    commission DECIMAL(2,2),
    manager_id DECIMAL(6,0),
    department_id DECIMAL(4,0),
    FOREIGN KEY (department_id, manager_id)
        REFERENCES departments(department_id, manager_id)
    ) ENGINE=InnoDB;

Time Complexity
O(1) for table creation.
Space Complexity
O(n) for records and indexes.

Sample Input
INSERT INTO employees
VALUES
(101, 'John', 'Smith', 'JOHN',
'9999999999', '2025-01-01',
NULL, 10000, NULL, 999, 999);

Sample Output
ERROR - Cannot add or update a child row:
a foreign key constraint fails

Learning Outcome
Learned composite foreign keys.
Learned how multiple columns can reference multiple columns in another table.




Program 16
Problem Statement
Create employees with a unique employee_id, a foreign key department_id referencing departments, and another foreign key job_id referencing jobs. The tables use the InnoDB engine. 

Approach / Algorithm
Define employee_id as the primary key.
Define employee-related columns.
Create a foreign key for department_id.
Create another foreign key for job_id.
Use ENGINE=InnoDB.

SQL Query
CREATE TABLE employees (
    employee_id DECIMAL(6,0) NOT NULL PRIMARY KEY,
    first_name VARCHAR(20),
    last_name VARCHAR(25) NOT NULL,
    email VARCHAR(25) NOT NULL,
    phone_number VARCHAR(20),
    hire_date DATE NOT NULL,
    job_id VARCHAR(10),
    salary DECIMAL(8,2),
    commission DECIMAL(2,2),
    manager_id DECIMAL(6,0),
    department_id DECIMAL(4,0),
    FOREIGN KEY (department_id)
        REFERENCES departments(department_id),
    FOREIGN KEY (job_id)
        REFERENCES jobs(job_id)
    ) ENGINE=InnoDB;

Time Complexity
O(1) for table creation.
Space Complexity
O(n) for records and indexes.

Sample Input
INSERT INTO employees
VALUES
(101, 'John', 'Smith', 'JOHN',
'9999999999', '2025-01-01',
'INVALID', 10000, NULL, NULL, 10);

Sample Output
ERROR - Cannot add or update a child row:
a foreign key constraint fails

Learning Outcome
Learned how to create multiple foreign keys.
Learned relationships between parent and child tables.
Learned the importance of the InnoDB engine for foreign keys.



Program 17
Problem Statement
Create employees with job_id referencing jobs.job_id. Use ON UPDATE CASCADE and ON DELETE RESTRICT. �

Approach / Algorithm
Define employee_id as the primary key.
Define job_id.
Reference jobs(job_id).
Apply ON UPDATE CASCADE.
Apply ON DELETE RESTRICT.

SQL Query
CREATE TABLE employees (
    employee_id DECIMAL(6,0) NOT NULL PRIMARY KEY,
    first_name VARCHAR(20),
    last_name VARCHAR(25) NOT NULL,
    job_id VARCHAR(10) NOT NULL,
    salary DECIMAL(8,2),
    FOREIGN KEY (job_id)
        REFERENCES jobs(job_id)
        ON UPDATE CASCADE
        ON DELETE RESTRICT
    ) ENGINE=InnoDB;

Time Complexity
O(1) for table creation.
Space Complexity
O(n) for records and indexes.

Sample Input
UPDATE jobs
SET job_id = 'J02'
WHERE job_id = 'J01';
Sample Output
The corresponding employee JOB_ID is automatically updated.

Learning Outcome
Learned ON UPDATE CASCADE.
Learned ON DELETE RESTRICT.
Learned how changes in parent tables can affect child tables.
Program 18
Problem Statement
Create employees with job_id referencing jobs.job_id, using ON DELETE CASCADE and ON UPDATE RESTRICT.

Approach / Algorithm
Define employee_id as the primary key.
Define job_id as a foreign key.
Apply ON DELETE CASCADE.
Apply ON UPDATE RESTRICT.

SQL Query
CREATE TABLE employees (
    employee_id DECIMAL(6,0) NOT NULL PRIMARY KEY,
    first_name VARCHAR(20),
    last_name VARCHAR(25) NOT NULL,
    job_id VARCHAR(10) NOT NULL,
    salary DECIMAL(8,2),
    FOREIGN KEY (job_id)
        REFERENCES jobs(job_id)
        ON DELETE CASCADE
        ON UPDATE RESTRICT
    ) ENGINE=InnoDB;
Time Complexity
O(1) for table creation.
Space Complexity
O(n) for records and indexes.

Sample Input
DELETE FROM jobs
WHERE job_id = 'J01';
Sample Output
The employees having JOB_ID = 'J01' are automatically deleted.

Learning Outcome
Learned ON DELETE CASCADE.
Learned how deletion of parent records can automatically delete related child records.



Program 19
Problem Statement
Create employees with job_id referencing jobs.job_id, using ON DELETE SET NULL and ON UPDATE SET NULL. The child foreign-key column must accept NULL.

Approach / Algorithm
Define job_id as nullable.
Create a foreign key referencing jobs.
Use ON DELETE SET NULL.
Use ON UPDATE SET NULL.

SQL Query
CREATE TABLE employees (
    employee_id DECIMAL(6,0) NOT NULL PRIMARY KEY,
    first_name VARCHAR(20),
    last_name VARCHAR(25) NOT NULL,
    job_id VARCHAR(10) DEFAULT NULL,
    salary DECIMAL(8,2),
    FOREIGN KEY (job_id)
        REFERENCES jobs(job_id)
        ON DELETE SET NULL
        ON UPDATE SET NULL
    ) ENGINE=InnoDB;

Time Complexity
O(1) for table creation.
Space Complexity
O(n) for records and indexes.

Sample Input
DELETE FROM jobs
WHERE job_id = 'J01';

Sample Output
Employee JOB_ID is automatically changed to NULL.

Learning Outcome
Learned ON DELETE SET NULL.
Learned ON UPDATE SET NULL.
Learned why the child foreign-key column must allow NULL.



Program 20
Problem Statement
Create employees with job_id referencing jobs.job_id, using ON DELETE NO ACTION and ON UPDATE NO ACTION. 

Approach / Algorithm
Define employee_id as the primary key.
Define job_id.
Reference jobs(job_id).
Apply ON DELETE NO ACTION.
Apply ON UPDATE NO ACTION.
Use InnoDB.

SQL Query
CREATE TABLE employees (
    employee_id DECIMAL(6,0) NOT NULL PRIMARY KEY,
    first_name VARCHAR(20),
    last_name VARCHAR(25) NOT NULL,
    job_id VARCHAR(10),
    salary DECIMAL(8,2),
    FOREIGN KEY (job_id)
        REFERENCES jobs(job_id)
        ON DELETE NO ACTION
        ON UPDATE NO ACTION
    ) ENGINE=InnoDB;
    
Time Complexity
O(1) for table creation.
Space Complexity
O(n) for records and indexes.

Sample Input
DELETE FROM jobs
WHERE job_id = 'J01';

Sample Output
ERROR - Cannot delete or update a parent row:
a foreign key constraint fails

Learning Outcome
Learned ON DELETE NO ACTION.
Learned ON UPDATE NO ACTION.
Learned how referential integrity prevents invalid parent-table changes.
Overall Learning Outcomes
After completing this lab, the following concepts are covered:
Creating tables using CREATE TABLE.
Using IF NOT EXISTS.
Copying table structures using LIKE.
Copying table data using CREATE TABLE ... AS SELECT.
Applying NOT NULL constraints.
Using CHECK constraints.
Using UNIQUE constraints.
Creating primary keys.
Creating composite keys.
Using AUTO_INCREMENT.
Setting default values using DEFAULT.
Creating foreign-key relationships.
Creating composite foreign keys.
Using the InnoDB storage engine.
Understanding referential actions:
CASCADE
RESTRICT
SET NULL
NO ACTION
