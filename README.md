# EX-3-SubQueries-Views-and-Joins
# Create employee Table
```
CREATE TABLE EMP (EMPNO NUMBER(4) PRIMARY KEY,ENAME VARCHAR2(10),JOB VARCHAR2(9),MGR NUMBER(4),HIREDATE DATE,SAL NUMBER(7,2),COMM NUMBER(7,2),DEPTNO NUMBER(2));
```
# Insert the values
```
INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7369, 'SMITH', 'CLERK', 7902, '17-DEC-80', 800, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7499, 'ALLEN', 'SALESMAN', 7698, '20-FEB-81', 1600, 300, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7521, 'WARD', 'SALESMAN', 7698, '22-FEB-81', 1250, 500, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7566, 'JONES', 'MANAGER', 7839, '02-APR-81', 2975, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7654, 'MARTIN', 'SALESMAN', 7698, '28-SEP-81', 1250, 1400, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7698, 'BLAKE', 'MANAGER', 7839, '01-MAY-81', 2850, NULL, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7782, 'CLARK', 'MANAGER', 7839, '09-JUN-81', 2450, NULL, 10);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7788, 'SCOTT', 'ANALYST', 7566, '19-APR-87', 3000, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7839, 'KING', 'PRESIDENT', NULL, '17-NOV-81', 5000, NULL, 10);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7844, 'TURNER', 'SALESMAN', 7698, '08-SEP-81', 1500, 0, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7876, 'ADAMS', 'CLERK', 7788, '23-MAY-87', 1100, NULL, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7900, 'JAMES', 'CLERK', 7698, '03-DEC-81', 950, NULL, 30);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7902, 'FORD', 'ANALYST', 7566, TO_DATE('03-DEC-81', 'DD-MON-RR'), 3000, 20, 20);

INSERT INTO EMP (EMPNO, ENAME, JOB, MGR, HIREDATE, SAL, COMM, DEPTNO)
VALUES (7934, 'MILLER', 'CLERK', 7782, TO_DATE('23-JAN-82', 'DD-MON-RR'), 1300, 10, 10);
```
# Create department table
```
CREATE TABLE DEPT (DEPTNO NUMBER(2) PRIMARY KEY,DNAME VARCHAR2(14),LOC VARCHAR2(13));
```
# Insert the values in the department table
```
INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (10, 'ACCOUNTING', 'NEW YORK');

INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (20, 'RESEARCH', 'DALLAS');

INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (30, 'SALES', 'CHICAGO');

INSERT INTO DEPT (DEPTNO, DNAME, LOC) VALUES (40, 'OPERATIONS', 'BOSTON');
```
# Q1) List the name of the employees whose salary is greater than that of employee with empno 7566.
QUERY:
```
select ENAME from EMP where SAL>(select SAL from EMP where EMPNO=7566);
```
# OUTPUT:
![image](https://github.com/Thanikasreeb/EX-3-SubQueries-Views-and-Joins/assets/119557910/efb68c11-51ae-4e81-a325-7c1adc508c5d)

# Q2) List the ename,job,sal of the employee who get minimum salary in the company.
QUERY:
```
SELECT ename, job, sal FROM emp WHERE sal = (SELECT MIN(sal) FROM emp);
```
# OUTPUT:
![image](https://github.com/Thanikasreeb/EX-3-SubQueries-Views-and-Joins/assets/119557910/4b75a7d9-346f-41c5-8332-eaa49b625a4f)

# Q3) List ename, job of the employees who work in deptno 10 and his/her job is any one of the job in the department ‘SALES’.
QUERY:
```
SELECT e.ename, e.job FROM emp e, dept d WHERE e.deptno = 10 AND e.job IN (SELECT job FROM emp WHERE deptno = (SELECT deptno FROM dept WHERE dname = 'SALES'));
```
# OUTPUT:
![image](https://github.com/Thanikasreeb/EX-3-SubQueries-Views-and-Joins/assets/119557910/8debfd45-b06b-4d7b-8ad3-6eeb708c98e3)

# Q4) Create a view empv5 (for the table emp) that contains empno, ename, job of the employees who work in dept 10.
QUERY:
```
CREATE VIEW empv5 AS SELECT empno, ename, job FROM emp WHERE deptno = 10;
```
# OUTPUT:
![image](https://github.com/Thanikasreeb/EX-3-SubQueries-Views-and-Joins/assets/119557910/0cba37a0-e350-468a-98a6-9e5ffdc74c6a)

# Q5) Create a view with column aliases empv30 that contains empno, ename, sal of the employees who work in dept 30. Also display the contents of the view.
QUERY:
```
CREATE VIEW empv30 AS SELECT empno, ename, sal FROM emp WHERE deptno = 30; SELECT * FROM empv30; 
```
# OUTPUT:
![image](https://github.com/Thanikasreeb/EX-3-SubQueries-Views-and-Joins/assets/119557910/e8ef350b-5065-4866-865d-95fca34fb0f4)

# Q6) Update the view empv5 by increasing 10% salary of the employees who work as ‘CLERK’. Also confirm the modifications in emp table
QUERY:
```
UPDATE emp SET sal = sal * 1.10 WHERE empno IN (SELECT empno FROM empv5 WHERE job = 'CLERK'); SELECT * FROM emp;
```
# OUTPUT:
![image](https://github.com/Thanikasreeb/EX-3-SubQueries-Views-and-Joins/assets/119557910/91353539-f196-40d5-a564-49ee637370f0)
![image](https://github.com/Thanikasreeb/EX-3-SubQueries-Views-and-Joins/assets/119557910/30f7c779-dfee-499b-bdd6-fa494d40e39f)
![image](https://github.com/Thanikasreeb/EX-3-SubQueries-Views-and-Joins/assets/119557910/d88a53c0-e3a3-46aa-8c7b-378bdee14ae7)

# Create a Customer1 Table
```
CREATE TABLE Customer1 (customer_id INT,cust_name VARCHAR(20),city VARCHAR(20),grade INT,salesman_id INT);
```
# Inserting Values to the Table
```
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3002, 'Nick Rimando', 'New York', 100, 5001);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3007, 'Brad Davis', 'New York', 200, 5001);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3005, 'Graham Zusi', 'California', 200, 5002);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3008, 'Julian Green', 'London', 300, 5002);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3004, 'Fabian Johnson', 'Paris', 300, 5006);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3009, 'Geoff Cameron', 'Berlin', 100, 5003);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3003, 'Jozy Altidor', 'Moscow', 200, 5007);
INSERT INTO Customer1 (customer_id, cust_name, city, grade, salesman_id) VALUES(3001, 'Brad Guzan', 'London', NULL, 5005);
```

# Create a Salesperson1 table
```
CREATE TABLE Salesman1 (salesman_id INT,name VARCHAR(20),city VARCHAR(20),commission DECIMAL(4,2));
```

# Inserting Values to the Table
```
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5001, 'James Hoog', 'New York', 0.15);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5002, 'Nail Knite', 'Paris', 0.13);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5005, 'Pit Alex', 'London', 0.11);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5006, 'Mc Lyon', 'Paris', 0.14);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5007, 'Paul Adam', 'Rome', 0.13);
INSERT INTO Salesman1 (salesman_id, name, city, commission) VALUES(5003, 'Lauson Hen', 'San Jose', 0.12);
```

# Q7) Write a SQL query to find the salesperson and customer who reside in the same city. Return Salesman, cust_name and city.
QUERY:
```
SELECT S.name AS Salesman, C.cust_name, C.city FROM Salesman1 S ,Customer1 C where S.city = C.city;
```
# OUTPUT:
![image](https://github.com/Thanikasreeb/EX-3-SubQueries-Views-and-Joins/assets/119557910/7b3bc032-f206-4312-bf32-7aa1afc5f8ff)

# Q8) Write a SQL query to find salespeople who received commissions of more than 13 percent from the company. Return Customer Name, customer city, Salesman, commission.
QUERY:
```
SELECT c.cust_name AS CustomerName, c.city AS CustomerCity, s.name AS Salesman, s.commission FROM Salesman1 s JOIN Customer1 c ON s.salesman_id = c.salesman_id WHERE s.commission > 0.13;
```
# OUTPUT:
![image](https://github.com/Thanikasreeb/EX-3-SubQueries-Views-and-Joins/assets/119557910/59b58b9a-ad9c-49d2-8736-65c1ef8b74f8)

# Q9) Perform Natural join on both tables
QUERY:
```
SELECT * FROM Salesman1 NATURAL JOIN Customer1;
```
# OUTPUT:
![image](https://github.com/Thanikasreeb/EX-3-SubQueries-Views-and-Joins/assets/119557910/631daad5-9dfc-489f-9acb-f7c3b10c75bb)

# Q10) Perform Left and right join on both tables
QUERY:
```
-- Left Join SELECT * FROM Customer1 LEFT JOIN Salesman1 ON Customer1.salesman_id = Salesman1.salesman_id;
```
# OUTPUT:
![image](https://github.com/Thanikasreeb/EX-3-SubQueries-Views-and-Joins/assets/119557910/ede7bb27-6c83-43c1-acd2-31c4fa096c07)
![image](https://github.com/Thanikasreeb/EX-3-SubQueries-Views-and-Joins/assets/119557910/4925a850-17b5-4a12-8aef-a9dc7bf698c9)
![image](https://github.com/Thanikasreeb/EX-3-SubQueries-Views-and-Joins/assets/119557910/d7241ef6-3911-4b87-a3b0-bb860d9568f4)

# RESULT:
The required subqueries,views and join are created successfully.


