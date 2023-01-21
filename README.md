# SQL-Queries
Here is the place where you can find my beginner SQL Queres I am comfortable with
CREATE TABLE company (
    id                  NUMBER(3) CONSTRAINT pk_company PRIMARY KEY,
    name                VARCHAR2(100) NOT NULL,
    commercial_contact  VARCHAR2(50),
    technical_contact   VARCHAR2(50),
    president           VARCHAR2(50),
    last_contacted      DATE,
    budget              NUMBER(8,2),
    budget_range_start  NUMBER(8,2) NOT NULL,
    budget_range_end    NUMBER(8,2) NOT NULL
);
INSERT INTO company (id,name,commercial_contact,president,budget_range_start,budget_range_end ) VALUES (1,'OUR BRILLIANT FUTURE LTD','LUISA JACKSON','JOHN SMITH',25000,50000);
INSERT INTO company (id,name,president,budget,budget_range_start,budget_range_end ) VALUES (2,'TESTING MAGIC','JUSTIN BLACK',35000,25000,50000);
INSERT INTO company (id,name,technical_contact,president,last_contacted,budget,budget_range_start,budget_range_end ) VALUES (3,'MAKING PROGRESS','ANGIE CROOD','CHARLES DEAN',DATE '2020-01-01',350000,125000,500000);
INSERT INTO company (id,name,commercial_contact,technical_contact,last_contacted,budget,budget_range_start,budget_range_end ) VALUES (4,'SKILL MASTERY','NIGEL OAKS','NIGEL OAKS',DATE '2020-02-15',12000,10000,24000);
INSERT INTO company (id,name,last_contacted,budget,budget_range_start,budget_range_end ) VALUES (5,'UNDECIDED AND CO.',DATE '2015-12-31',51000,51000,100000);

COMMIT;

SELECT ID, NAME FROM COMPANY;

SELECT NAME, COALESCE (COMMERCIAL_CONTACT, TECHNICAL_CONTACT, PRESIDENT, 'NO CONTACT DATA*')AS CONTACT_NAME, NVL (BUDGET,BUDGET_RANGE_START) FROM COMPANY;
SELECT ID, NVL2(PHONE, NAME, JOB_ID) FROM EMPLOYEE;

SELECT ID, NAME, DEPARTMENT_ID, nullif(id,department_id) from employee;

select * from company where last_contacted > '01-JAN-19'order by last_contacted asc;

select name as company_name, nullif (commercial_contact, technical_contact)as exclusively_commercial_contact, NVL2(last_contacted, budget, budget_range_start) AS budget
, last_contacted AS last_contacted_date FROM company
WHERE LNNVL(last_contacted < DATE '2019-01-01') ORDER BY last_contacted NULLS FIRST;

select * from employee where salary > all(50000,100000,1);

select * from employees;

SELECT employee_id, first_name, last_name,salary from EMPLOYEES;

SELECT employees.salary, employees.job_title
FROM employees;

select * from employees;

SELECT 1+1 from employees;
select 1+1 from dual;
select * from dual; --pentru mena

SELECT first_name, last_name, job_title, salary, salary+1000 as "new salary" 
from employees;


select first_name, last_name, job_title, salary, NVL(salary *1.1)
FROM employees;


select 2* null
FROM dual;

select first_name, last_name, job_title, salary, salary*1.1, NVL (salary, 0)
FROM employees;

select first_name, last_name, job_title, salary, nvl( salary, 1000) from employees;


select last_name as nume, first_name as prenume, department_name, NVL  (department_name,
'DEVOPS dept') as departament from employees;

select first_name, Last_name, salary, salary*1.275, NVL (salary*1.12785,0) 
as "new salary", department_name as "super departament" from employees;

--operatorul de concatenare ||

SELECT
    first_name
    || ' '
    || last_name
    || ' are salariul de '
    || salary
    || 'si are jobul '
    || job_title AS "prenume si nume"
FROM
    employees;


--operatorul distinct

SELECT DISTINCT job_title
FROM employees;


SELECT DISTINCT first_name, last_name
from employees;

select * from employees where salary > 1000;

select first_name, last_name, job_title from employees where job_title = 'Intern';

SELECT * FROM employees where salary < 9875;


SELECT first_name, last_name 
FROM employees;

select * FROM employees;

SELECT first_name, last_name, salary
FROM employees
WHERE salary > 5500;

SELECT first_name, last_name, salary from employees where salary <> 5500;

SELECT first_name, last_name, salary
FROM employees
WHERE salary BETWEEN 5000 and 11000;



SELECT first_name, last_name, salary
FROM employees
WHERE salary BETWEEN 5000 AND 11000
ORDER BY salary DESC, first_name;


--tema
SELECT
    employee_id                              AS id,
    first_name                               AS nume,
    last_name                                AS prenume,
    email                                    AS "e-mail",
    phone                                    AS telefon,
    hire_date                                AS "data de angajare",
    manager_id                               AS "idul managerului",
    job_title                                AS "titlul jobului",
    salary                                   AS salariu,
    nvl(salary * 0.1, 0)                     AS "10 la suta din salariu",
    nvl(department_name, 'fara departament') AS departament
FROM
    employees
ORDER BY
    salary;

SELECT manager_id, NVL(manager_id, 1) as "manager_id=1"
FROM employees;

SELECT first_name, last_name, salary as "old salary", salary+salary*0.2345 as "new new salary" ,NVL(salary*0.2345, 0) as percentage from employees;

SELECT first_name, last_name, salary FROM employees where salary < 11000
ORDER BY salary DESC;

SELECT first_name, last_name FROM employees 
WHERE last_name = 'Pop';

SELECT first_name, last_name, salary
FROM employees
WHERE salary BETWEEN 10000 and 30000
ORDER BY salary;


SELECT first_name, last_name, salary
FROM employees
WHERE salary >=10000 AND salary <=30000
ORDER BY salary;

SELECT first_name, last_name, job_title FROM employees
where job_title != 'Stock Clerk';

SELECT first_name, last_name, salary
FROM employees 
WHERE salary IN (5000, 5500, 7000, 7500, 11000);

SELECT first_name, last_name, job_title
FROM employees
WHERE job_title IN ('Stock Clerk', 'Sales Manager')
ORDER BY first_name;

SELECT first_name, last_name, job_title
FROM employees
WHERE job_title LIKE '%Manager';


SELECT first_name, last_name, job_title
FROM employees
WHERE job_title LIKE '%SQL%';

SELECT first_name, last_name
FROM employees
WHERE first_name LIKE '_a%'
ORDER BY first_name;

SELECT first_name, last_name
FROM employees WHERE first_name LIKE 'M%'
ORDER by last_name;


SELECT first_name, last_name
FROM employees WHERE first_name LIKE '%a';




SELECT first_name, last_name, salary

from employees
where salary is NULL;


SELECT first_name, last_name, salary, job_title
from employees
where salary = 5000 OR job_title = 'Stock Clerk';



SELECT
    first_name,
    last_name,
    salary,
    job_title
FROM
    employees
WHERE
    job_title = 'Stock Clerk'
    OR salary > 11300;


SELECT first_name, last_name, salary
from employees
WHERE salary = 5000 or salary = 5500 or salary =7000 or salary =7500;

SELECT first_name, last_name, salary, job_title
from employees
WHERE job_title LIKE '%Developer' or job_title LIKE '%Programmer' or job_title LIKE '%DEVELOPER%' or job_title LIKE '%PROGRAMMER%' or job_title LIKE '%developer%';

SELECT first_name, last_name, manager_id, salary
FROM employees
WHERE manager_id is NULL or salary IN (6000,6500,5000,7000,11200,13245);
--TEMA
SELECT first_name, last_name, job_title
FROM employees
WHERE job_title LIKE '%Developer%' or job_title LIKE '%Intern%' or job_title LIKE '%Programmer%' or job_title LIKE '%DEVELOPER%'
ORDER BY job_title ASC;

SELECT first_name, last_name, salary, salary*1.12 as "salariu nou", job_title
FROM employees
WHERE salary > 7000 or job_title LIKE '%Shipping Clerk%'
or salary > 7000 or job_title LIKE '%Engineer%' 
or salary > 7000 or job_title LIKE '%Manager%';

Select first_name, last_name, salary, salary*1.12 as "salariu nou", job_title
FROM employees
WHERE salary > 7000 AND job_title ='Shipping Clerk'
or salary > 7000 AND job_title LIKE '%Engineer%'
or salary > 7000 AND job_title LIKE '%Manager%'
ORDER BY salary ASC;


SELECT first_name, last_name, hire_date
from employees
WHERE hire_date LIKE '%___-16%';


SELECT first_name, last_name, hire_date
from employees
WHERE hire_date LIKE '%__JAN-16%';

SELECT first_name, last_name, job_title, salary, salary*12 as "salariu anual"
from employees
where job_title like '%Sales Representative%' or job_title like '%SQL Developer%';

SELECT first_name, last_name 
FROM employees
where employee_id = 100 or employee_id = 53;

--ssf ctrl-space

SELECT first_name, last_name, salary
FROM employees
WHERE salary > 5000 and salary < 7600
order by salary asc;




SELECT first_name, last_name, salary
FROM employees
WHERE salary between 5000 and 7600
order by salary asc;

SELECT first_name, last_name, hire_date
from employees
where hire_date >= '01-JAN-16' and hire_date <='31-OCT-16'
order by hire_date ASC;

SELECT first_name, last_name, job_title
from employees
where job_title = 'Stock Clerk' and salary > 7000;

SELECT first_name, last_name, job_title
from employees
where job_title LIKE 'Stock Clerk' and salary > 7000;

SELECT first_name, last_name, job_title, salary
from employees
WHERE (job_title LIKE '%Developer%' or job_title LIKE '%Manager%')
AND
(salary between 7000 and 18000)
order by salary asc;

SELECT first_name, last_name, hire_date, salary, job_title
from employees 
WHERE (hire_date BETWEEN '01-JAN-16' and '29-FEB-16')
and (job_title = 'Sales Representative' or job_title = 'Stock Clerk')
AND (salary between '7000' and '12000')
order by hire_date,salary;

SELECT first_name, last_name, job_title,salary
FROM employees
WHERE job_title = 'Stock Clerk'
AND salary !=  n '12100'
order by salary desc;
--2
SELECT first_name, last_name, salary, job_title, Hire_date
from employees
where hire_date > '01-MAR-16' 
AND salary between 6000 and 9000
order by salary desc;

--3
SELECT first_name, last_name, salary, manager_id
from employees
where last_name IN ('Kennedt', 'Dixon', 'Payne', 'Suciu')
AND (salary < 11500)
and (manager_id = 3);

--4
SELECT first_name, last_name, salary, job_title
from employees
Where job_title LIKE '%Stock Clerk%' or job_title LIKE '%Accountant%'
and
salary != 5500 or salary != 4400 or salary != 4950
order by salary desc;

--5
SELECT
    first_name,
    last_name,
    salary,
    job_title
FROM
    employees
WHERE
    job_title LIKE '%Developer%'
    OR job_title LIKE '%Sales Representative%'
    AND salary > 8000
    order by salary desc;

SELECT first_name, last_name, salary,
FROM employees;



Select first_name,last_name, salary
FROM employees
Where salary NOT BETWEEN 7000 and 10000
order by salary desc;

Select first_name,last_name, salary, hire_date

FROM employees
Where NOT (hire_date LIKE '%MAR%' or hire_date LIKE '%APR%' or hire_date LIKE '%MAY%')
order by hire_date;


SELECT first_name, last_name, job_title
from employees
WHERE NOT (job_title LIKE '%Developer%'or job_title LIKE '%Manager%'or job_title LIKE' %Programmer%' 
or job_title LIKE '%DEVELOPER%'or job_title LIKE '%eveloper%');


SELECT
    first_name,
    last_name,
    salary
FROM
    employees
WHERE
    salary NOT IN ( 6000, 7250, 11000, 11250 );


SELECT
    first_name,
    last_name,
    salary
FROM
    employees
WHERE
   NOT  (salary = 6000 or salary = 7250 or salary=11000 or salary= 11250);


Select first_name, last_name, salary
from employees
WHERE salary = '5500';





