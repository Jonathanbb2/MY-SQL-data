# MY-SQL-data

this is from mySQL learning experience
-- Create the database
CREATE DATABASE RagonWorkers;

-- Switch to the new database
USE RagonWorkers;

-- Create Persons table
CREATE TABLE Persons (
  Id INT PRIMARY KEY,
  FirstName VARCHAR(25),
  LastName VARCHAR(25),
  Age INT,
  Institute VARCHAR(25) DEFAULT 'ragon',
  Gender VARCHAR(10)
);

-- Create Orders table
CREATE TABLE Orders (
  Id INT PRIMARY KEY,
  Dateday DATE,
  PersonId INT,
  Location VARCHAR(50),
  FOREIGN KEY (PersonId) REFERENCES Persons(Id)
);

-- Insert 5 records into Persons table
INSERT INTO Persons (Id, FirstName, LastName, Age, Gender)
VALUES
  (1, 'Jonathan', 'Bonilla', 19, 'Male'),
  (2, 'Musie', 'Ghrebemichael', 25, 'Male'),
  (3, 'Michael', 'Johnson', 40, 'Male'),
  (4, 'Emily', 'Davis', 35, 'Female'),
  (5, 'Marcus', 'Jones', 22, 'Male');

-- Update each person's gender individually
UPDATE Persons
SET Gender = 'Male'
WHERE Id = 1;


UPDATE Persons
SET Gender = 'Male'
WHERE Id = 2;

UPDATE Persons
SET Gender = 'Male'
WHERE Id = 3;

UPDATE Persons
SET Gender = 'Female'
WHERE Id = 4;

UPDATE Persons
SET Gender = 'Male'
WHERE Id = 5;

-- Insert 5 more records into Persons table
INSERT INTO Persons (Id, FirstName, LastName, Age, Gender)
VALUES
  (6, 'John', 'Doe', 30, 'Male'),
  (7, 'Jane', 'Smith', 27, 'Female');
 

-- Check the updated tables
SELECT * FROM `Table Employee`;
SELECT * FROM Orders;

-- Insert 5 records into Orders table
INSERT INTO Orders (Id, Dateday, PersonId, Location)
VALUES
  (1, '2023-06-25', 1, 'Boston'),
  (2, '2023-06-26', 2, 'New York'),
  (3, '2023-06-27', 3, 'Brockton'),
  (4, '2023-06-28', 4, 'Chicago'),
  (5, '2023-06-29', 5, 'Miami');

INSERT INTO Orders (Id, Dateday, PersonId, Location, Address)
VALUES
  (6, '2023-07-01', 6, 'Los Angeles'),
  (7, '2023-07-02', 7, 'San Francisco'),
  (8, '2023-07-03', 8, 'Seattle'),
  (9, '2023-07-04', 9, 'Las Vegas'),
  (10, '2023-07-05', 10, 'Denver');

-- Rename the Persons table to Table Employee
ALTER TABLE  TableEmployee RENAME TO  `Table Employee`;

-- Delete corresponding records from Orders table
DELETE FROM Orders WHERE PersonId > 7;

-- Delete rows from Table Employee
DELETE FROM `Table Employee` WHERE Id > 7;

-- Delete columns Age, Gender, and Institute
ALTER TABLE `Table Employee` DROP COLUMN Age;
ALTER TABLE `Table Employee` DROP COLUMN Gender;
ALTER TABLE `Table Employee` DROP COLUMN Institute;

-- Add new columns Salary, Joining Date, and Department
ALTER TABLE `Table Employee` ADD COLUMN Salary INT;
ALTER TABLE `Table Employee` ADD COLUMN `Joining Date` DATE;
ALTER TABLE `Table Employee` ADD COLUMN Department VARCHAR(25);

-- Update Salary, Joining Date, and Department values for each employee
UPDATE `Table Employee` SET Salary = 10000000, `Joining Date` = '2019-01-20', Department = 'Finance' WHERE Id = 1;
UPDATE `Table Employee` SET Salary = 60000000, `Joining Date` = '2019-01-15', Department = 'IT' WHERE Id = 2;
UPDATE `Table Employee` SET Salary = 89000000, `Joining Date` = '2019-02-05', Department = 'Banking' WHERE Id = 3;
UPDATE `Table Employee` SET Salary = 20000000, `Joining Date` = '2019-02-25', Department = 'Insurance' WHERE Id = 4;
UPDATE `Table Employee` SET Salary = 22000000, `Joining Date` = '2019-02-28', Department = 'Finance' WHERE Id = 5;
UPDATE `Table Employee` SET Salary = 40000000, `Joining Date` = '2019-05-10', Department = 'IT' WHERE Id = 6;
UPDATE `Table Employee` SET Salary = 12300000, `Joining Date` = '2019-06-20', Department = 'Banking' WHERE Id = 7;

-- Check the updated table
SELECT * FROM `Table Employee`;

-- Gets all employees
SELECT * FROM `Table Employee`;

-- Displays first and last name of all employees
SELECT FirstName, LastName FROM `Table Employee`;

-- Displayes first name using the "eMPLOYEES FIRST NAME"
SELECT FirstName AS "Employee Name" FROM `Table Employee`;

-- Get all "Last_Name" and "First_Name" of employees whose salary is greater than 5000000.
SELECT LastName, FirstName FROM `Table Employee` WHERE Salary > 5000000;

-- Get all "Last_Name", "First_Name", and "Department" of employees whose Department is Finance.
SELECT LastName, FirstName, Department FROM `Table Employee` WHERE Department = 'Finance';

-- Get all employees' first_names in alphabetical order.
SELECT FirstName FROM `Table Employee` ORDER BY FirstName ASC;

-- Get the first_name of employees whose name ends with 'n'.
SELECT FirstName FROM `Table Employee` WHERE FirstName LIKE '%s';

-- Get all details of employees whose joining date is between April 2019 and June 2019.
SELECT * FROM `Table Employee` WHERE `Joining Date` BETWEEN '2019-04-01' AND '2019-06-30';

-- Who are all the employees from the IT department.
SELECT * FROM `Table Employee` WHERE Department = 'IT';

-- Which employee had the minimum salary.
SELECT * FROM `Table Employee` WHERE Salary = (SELECT MIN(Salary) FROM `Table Employee`);

-- which employee has the maximum salary
SELECT * FROM `Table Employee` WHERE Salary = (SELECT MAX(Salary) FROM `Table Employee`);

-- Drop tables
DROP TABLE `Table Employee`;
DROP TABLE Orders;


-- Create Employee table
CREATE TABLE Employee (
  Empid INT PRIMARY KEY,
  EmpName VARCHAR(25),
  Department VARCHAR(25),
  ContactNo INT,
  EmailId VARCHAR(40),
  EmpHeadID VARCHAR(10)
);

INSERT INTO Employee (Empid, EmpName, Department, ContactNo, EmailId,EmpHeadID)
VALUES
  (101, 'Isha', 'E-101', 1234567890, 'isha@gmail.com', 105),
  (102, 'Priya', 'E-104', 1234567890, 'Priyo@yahoo.com', 103),
  (103, 'Neha', 'E-101', 1234567890, 'Neha@gmail.com', 101),
  (104, 'Rahul', 'E-102', 1234567890, 'Rahul@yahoo.com', 105),
  (105, 'Abhishek', 'E-101', 1234567890, 'Abhishek@gmail.com', 102);


-- Check the updated tables
SELECT * FROM `Table Employee`;
SELECT * FROM Orders;
Select * FROM Employee;


-- Create EMPDEPT table
CREATE TABLE EMPDEPT (
  DeptID VARCHAR(25) PRIMARY KEY,
  DeptName VARCHAR(25),
  Dept_Off VARCHAR(25),
  DeptHead INT,
  FOREIGN KEY (DeptHead) REFERENCES Employee (Empid)
);

-- Insert data into EMPDEPT table
INSERT INTO EMPDEPT (DeptID, DeptName, Dept_Off, DeptHead)
VALUES
  ('E-101', 'HR', 'Monday', 105),
  ('E-102', 'Development', 'Tuesday', 101),
  ('E-103', 'House keeping', 'Saturday', 103),
  ('E-104', 'Sales', 'Sunday', 104),
  ('E-105', 'Purchage', 'Tuesday', 104);
  
  
  -- Create EmpSalary table
CREATE TABLE EmpSalary (
  EmpID INT,
  Salary DECIMAL(10, 2),
  IsPermanent VARCHAR(3),
  FOREIGN KEY (EmpID) REFERENCES Employee (Empid)
);

-- Insert data into EmpSalary table
INSERT INTO EmpSalary (EmpID, Salary, IsPermanent)
VALUES
  (101, 2000, 'Yes'),
  (102, 10000, 'Yes'),
  (103, 5000, 'No'),
  (104, 1900, 'Yes'),
  (105, 2300, 'Yes');
  
  Create Table Project (
  
  ProjectID VARCHAR(10) PRIMARY KEY,
  Duration INT
  );
  
  INSERT INTO Project (ProjectID, Duration)
  VALUES
  
  ('P-1' , 23),
  ('P-2' , 15),
  ('P-3' , 45),
  ('P-4' , 2),
  ('P-5' , 30);
  
   Create Table Country (
  
  Cid VARCHAR(10) PRIMARY KEY,
  Cname VarChar(20)
  );
  
  INSERT INTO Country (Cid, Cname)
  VALUES
  
  ('C-1' , 'India'),
  ('C-2' , 'USA'),
  ('C-3' , 'CHINA'),
  ('C-4' , 'Pakistan'),
  ('C-5' , 'Russia');
  
 CREATE TABLE ClientTable (
  ClientID VARCHAR(10) PRIMARY KEY,
  ClientName VARCHAR(20),
  Cid VARCHAR(20),
  FOREIGN KEY (Cid) REFERENCES Country(Cid)
  );
  
  INSERT INTO ClientTable (ClientID, ClientName, Cid)
  VALUES
  
  ('Cl-1' , 'ABC Group', 'C-1'),
  ('Cl-2' , 'PQR', 'C-2'),
  ('Cl-3' , 'XYZ', 'C-3'),
  ('Cl-4' , 'Tech altum', 'C-4'),
  ('Cl-5' , 'MNP', 'C-5');
  

  
  -- Create the EMP Project table
CREATE TABLE `EMP Project` (
  EmpID INT,
  ProjectID VARCHAR(10),
  ClientID VARCHAR(10),
  StartYear INT,
  EndYear INT,
  FOREIGN KEY (EmpID) REFERENCES Employee(EmpID),
  FOREIGN KEY (ProjectID) REFERENCES Project(ProjectID),
  FOREIGN KEY (ClientID) REFERENCES ClientTable(ClientID)
);

-- Insert values into EMP Project table
INSERT INTO `EMP Project` (EmpID, ProjectID, ClientID, StartYear, EndYear)
VALUES
  (101, 'p-1', 'CL-1', 2010, 2010),
  (102, 'p-2', 'CL-2', 2010, 2012),
  (103, 'p-3', 'CL-3', 2013, NULL),
  (104, 'p-4', 'CL-4', 2014, 2015),
  (105, 'p-5', 'CL-5', 2015, NULL);
  
  
  SELECT * FROM Employee;
  SELECT * FROM EmpDept;
  SELECT * FROM EmpSalary;
  SELECT * FROM project;
  SELECT * FROM Country;
  SELECT * FROM ClientTable;
  SELECT * FROM EMP Project;
  
  
  SELECT * FROM Employee;
  
  SELECT EmpName FROM Employee WHERE EmpName LIKE '%p';

SELECT COUNT(*) FROM Employee WHERE Empid IN (
  SELECT EmpID FROM EmpSalary WHERE IsPermanent = 'Yes' AND Salary > 5000
);

SELECT * FROM Employee WHERE EmailId LIKE '%@gmail.com';

SELECT * FROM Employee WHERE Department IN ('E-104', 'E-102');

SELECT DeptName FROM EMPDEPT WHERE DeptID = 'E-102';

SELECT SUM(Salary) FROM EmpSalary WHERE IsPermanent = 'Yes';

SELECT EmpName FROM Employee WHERE EmpName LIKE '%a';

SELECT Projectid, COUNT(DISTINCT empID) AS NumDepartments
FROM EMP Project
GROUP BY Projectid;


SELECT COUNT(*) FROM `EMP Project` WHERE StartYear = 2010;

SELECT COUNT(*) FROM `EMP Project` WHERE StartYear = EndYear;

SELECT EmpName FROM Employee WHERE SUBSTRING(EmpName, 3, 1) = 'h';

SELECT DeptName FROM EMPDEPT WHERE DeptID IN (
SELECT Department FROM Employee WHERE Empid > 103
);
SELECT EmpName FROM Employee WHERE EmpHeadID = (
  SELECT Empid FROM Employee WHERE EmpName = 'Abhishek'
);
SELECT EmpName FROM Employee WHERE Empid = (
  SELECT DeptHead FROM EMPDEPT WHERE DeptName = 'HR'
);

SELECT EmpName FROM Employee WHERE EmpHeadID IN (
  SELECT Empid FROM Employee WHERE Empid IN (
    SELECT EmpID FROM EmpSalary WHERE IsPermanent = 'Yes'
  )
);

SELECT * FROM Employee WHERE Empid IN (
  SELECT DeptHead FROM EMPDEPT WHERE Dept_Off = 'Monday'
);

SELECT * FROM ClientTable WHERE Cid IN (
SELECT Cid FROM Country WHERE Cname = 'India'
);

SELECT * FROM Employee WHERE Department = 'E-102';


-- Create Workers table
CREATE TABLE Workers (
    WORKER_ID INT PRIMARY KEY,
    FIRST_NAME VARCHAR(50),
    LAST_NAME VARCHAR(50),
    SALARY INT,
    JOINING_DATE DATETIME,
    DEPARTMENT VARCHAR(50)
);

-- Insert data into Workers table
INSERT INTO Workers (WORKER_ID, FIRST_NAME, LAST_NAME, SALARY, JOINING_DATE, DEPARTMENT)
VALUES
    (1, 'Monika', 'Arora', 1000000, '2014-02-20 09:00:00', 'HR'),
    (2, 'Niharika', 'Verma', 80000, '2014-06-11 09:00:00', 'Admin'),
    (3, 'Vishal', 'Signhal', 300000, '2014-02-20 09:00:00', 'HR'),
    (4, 'Amitabh', 'Singh', 500000, '2014-02-20 09:00:00', 'Admin'),
    (5, 'Vivek', 'Bhati', 500000, '2014-06-11 09:00:00', 'Admin'),
    (6, 'Vipul', 'Diwan', 200000, '2014-06-11 09:00:00', 'Account'),
    (7, 'Satish', 'Kumar', 75000, '2014-01-20 09:00:00', 'Account'),
    (8, 'Geetika', 'Chauhan', 90000, '2014-04-11 09:00:00', 'Admin');

-- Create BONUS table with foreign key constraint
CREATE TABLE BONUS (
    WORKER_REF_ID INT,
    BONUS_DATE VARCHAR(50),
    BONUS_AMOUNT VARCHAR(50),
    FOREIGN KEY (WORKER_REF_ID) REFERENCES Workers(WORKER_ID)
);

-- Insert data into BONUS table
INSERT INTO BONUS (WORKER_REF_ID, BONUS_DATE, BONUS_AMOUNT)
VALUES
    (1, '2016-02-20 00:00:00', '5000'),
    (2, '2016-06-11 00:00:00', '3000'),
    (3, '2016-02-20 00:00:00', '4000'),
    (1, '2016-02-20 00:00:00', '4500'),
    (2, '2016-06-11 00:00:00', '3500');

-- Create TITLE table with foreign key constraint
CREATE TABLE TITLE (
    TITLE_ID INT PRIMARY KEY,
    WORKER_REF_ID INT,
    WORKER_TITLE VARCHAR(50),
    AFFECTED_FROM VARCHAR(50),
    FOREIGN KEY (WORKER_REF_ID) REFERENCES Workers(WORKER_ID)
);

-- Insert data into TITLE table
INSERT INTO TITLE (WORKER_REF_ID, WORKER_TITLE, AFFECTED_FROM)
VALUES
    (1, 'Manager', '2016-06-11 00:00:00'),
    (2, 'Executive', '2016-06-11 00:00:00'),
    (8, 'Executive', '2016-06-11 00:00:00'),
    (5, 'Manager', '2016-06-11 00:00:00'),
    (4, 'Asst. Manager', '2016-06-11 00:00:00'),
    (7, 'Executive', '2016-06-11 00:00:00'),
    (6, 'Lead', '2016-06-11 00:00:00'),
    (3, 'Lead', '2016-06-11 00:00:00');


-- Select From Tables

SELECT * FROM title;

SELECT * FROM BONUS;


SELECT * FROM EMPSALARY;

    
-- Drop the Bonus table
DROP TABLE Bonus;

-- Drop the Title table
DROP TABLE Title;

-- Drop the Workers table
DROP TABLE Workers;

-- 1 Write an SQL query to fetch "FIRST_NAME" from the Worker table using the alias name <WORKER_NAME>:

SELECT FIRST_NAME AS WORKER_NAME FROM Workers;

-- 2 Write an SQL query to fetch "FIRST_NAME" from the Worker table in upper case:

SELECT UPPER(FIRST_NAME) FROM Workers;

-- 3 Write an SQL query to fetch unique values of DEPARTMENT from the Worker table:

SELECT DISTINCT DEPARTMENT FROM Workers;

-- 4 +Write an SQL query to print the first three characters of FIRST_NAME from the Worker table:

SELECT LEFT(FIRST_NAME, 3) FROM Workers;

-- 5 Write an SQL query to find the position of the alphabet ('a') in the first name column 'Amitabh' from the Worker table:

SELECT LOCATE('a', FIRST_NAME) FROM Workers WHERE FIRST_NAME = 'Amitabh';

-- 6 Write an SQL query to print the FIRST_NAME from the Worker table after removing white spaces from the right side:

SELECT LTRIM(FIRST_NAME) FROM Workers;

-- 8 Write an SQL query to print the DEPARTMENT from the Worker table after removing white spaces from the left side:

SELECT LTRIM(DEPARTMENT) FROM Workers;

-- 9 Write an SQL query that fetches the unique values of DEPARTMENT from the Worker table and prints its length:

SELECT DISTINCT DEPARTMENT, LENGTH(DEPARTMENT) FROM Workers;

-- 10 Write an SQL query to print the FIRST_NAME from the Worker table after replacing 'a' with 'A':

SELECT REPLACE(FIRST_NAME, 'a', 'A') FROM Workers;

-- 11 Write an SQL query to print the FIRST_NAME and LAST_NAME from the Worker table into a single column COMPLETE_NAME. A space char should separate them:

SELECT CONCAT(FIRST_NAME, ' ', LAST_NAME) AS COMPLETE_NAME
FROM Workers;

-- 12 Write an SQL query to print all Worker details from the Worker table order by FIRST_NAME Ascending and DEPARTMENT Descending.

SELECT *
FROM Workers
ORDER BY FIRST_NAME ASC, DEPARTMENT DESC;

-- 13 Write an SQL query to print details for Workers with the first names "Vipul" and "Satish" from the Worker table.

SELECT *
FROM Workers
WHERE FIRST_NAME IN ('Vipul', 'Satish');

-- 14 Write an SQL query to print details of workers excluding first names "Vipul" and "Satish" from the Worker table.

SELECT *
FROM Workers
WHERE FIRST_NAME NOT IN ('Vipul', 'Satish');

-- 15 Write an SQL query to print details of Workers with DEPARTMENT name as "Admin".

SELECT * FROM Workers WHERE DEPARTMENT = 'Admin';

-- 16 Write an SQL query to print details of the Workers whose FIRST_NAME contains 'a'.

SELECT *
FROM Workers
WHERE FIRST_NAME LIKE '%a%';

-- 17 Write an SQL query to print details of the Workers whose FIRST_NAME ends with 'h' and contains six alphabets.

SELECT *
FROM Workers
WHERE FIRST_NAME LIKE '______h';

-- 18  Write an SQL query to print details of the Workers whose SALARY lies between 100000 and 500000.

SELECT *
FROM Workers
WHERE SALARY BETWEEN 100000 AND 500000;

-- 18 Write an SQL query to print details of the Workers who joined in Feb'2014.

SELECT *
FROM Workers
WHERE JOINING_DATE >= '2014-02-01' AND JOINING_DATE < '2014-03-01';

-- 19 Write an SQL query to fetch the count of employees working in the department 'Admin'.

SELECT COUNT(*) AS Employee_count
FROM Workers
WHERE DEPARTMENT = 'Admin';

-- 20 Write an SQL query to fetch worker names with salaries >= 50000 and <= 100000.

SELECT FIRST_NAME, LAST_NAME
FROM Workers
WHERE SALARY BETWEEN 50000 AND 100000;

-- 21 Write an SQL query to fetch the no. of workers for each department in descending order.

SELECT DEPARTMENT, COUNT(*) AS WorkerCount
FROM Workers
GROUP BY DEPARTMENT
ORDER BY WorkerCount DESC;

-- 22 Write an SQL query to print details of the Workers who are also Managers.

SELECT W.*
FROM Worker W
INNER JOIN TITLE T ON W.WORKER_ID = T.WORKER_REF_ID AND T.WORKER_TITLE = 'Manager';

-- 23 Write an SQL query to fetch duplicate records having matching data in some fields of a table.

SELECT FIRST_NAME, LAST_NAME, COUNT(*) AS DuplicateCount
 FROM Workers 
 GROUP BY FIRST_NAME, LAST_NAME 
 HAVING COUNT(*) > 1;

select * from Workers;
-- 24 Write an SQL query to show the current date and time.

SELECT CURRENT_TIMESTAMP AS CurrentDateTime;

-- 25 Write an SQL query to show the top n (say 10) records of a table.

SELECT *
FROM title
LIMIT 10;

-- 26 Write an SQL query to fetch the list of employees with the same salary.

SELECT FIRST_NAME, LAST_NAME, SALARY
FROM Workers
WHERE SALARY IN (
    SELECT SALARY
    FROM Workers
    GROUP BY SALARY
    HAVING COUNT(*) > 1
);

-- 27 Write an SQL query to show the second-highest salary from a table.

SELECT DISTINCT SALARY
FROM Workers
ORDER BY SALARY DESC
LIMIT 1, 1;


-- 29 Write an SQL query to fetch the departments that have less than five people in them.

SELECT DEPARTMENT
FROM Workers
GROUP BY DEPARTMENT
HAVING COUNT(*) < 5;

-- 30 Write an SQL query to show all departments along with the number of people in there.

SELECT DEPARTMENT, COUNT(*) AS EmployeeCount
FROM Workers
GROUP BY DEPARTMENT;

-- 31 Write an SQL query to show the last record from a table.

SELECT *
FROM BONUS
ORDER BY WORKER_REF_ID DESC
LIMIT 1;

-- 32 Write an SQL query to fetch the first row of a table.

SELECT *
FROM workers
LIMIT 1;

select * from workers;

-- 33 Write an SQL query to fetch the last five records from a table.

SELECT *
FROM department
ORDER BY PrimaryKeyColumn DESC
LIMIT 5;

-- 34 Write an SQL query to print the name of employees having the highest salary in each department.

SELECT t.DEPARTMENT, w.FIRST_NAME, w.LAST_NAME, w.SALARY
FROM Workers w
INNER JOIN (
    SELECT DEPARTMENT, MAX(SALARY) AS MaxSalary
    FROM Workers
    GROUP BY DEPARTMENT
) t ON w.DEPARTMENT = t.DEPARTMENT AND w.SALARY = t.MaxSalary;

-- 35 Write an SQL query to fetch departments along with the total salaries paid for each of them.

SELECT DEPARTMENT, SUM(SALARY) AS TotalSalary
FROM Workers
GROUP BY DEPARTMENT;

-- 36 Write an SQL query to fetch the names of workers who earn the highest salary.

SELECT FIRST_NAME, LAST_NAME
FROM Workers
WHERE SALARY = (
    SELECT MAX(SALARY)
    FROM Workers
);

-- 37 write
