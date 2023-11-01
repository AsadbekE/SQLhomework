# SQLhomework

SELECT NAME FROM department D 
WHERE NAME LIKE 'S%'  
AND id IN 
(SELECT dept_id 
FROM employee e 
WHERE gender = 'Male'  
AND AGE > 30 
AND (e.dept_id = D.id) 
AND dept_id in 
(SELECT dept_id 
FROM employee 
WHERE gender = 'Female'  
AND AGE > 30))


--explanation

1st part:

SELECT dept_id 
FROM employee 
WHERE gender = 'Female'
AND AGE > 30

In this part of the query we write a select statement to find the departments that 
have got 'Female' employees whose age is over 30


2nd part:

SELECT dept_id 
FROM employee e 
WHERE gender = 'Male'  
AND AGE > 30 
AND (e.dept_id = D.id) 
AND dept_id IN ()

In this subquery we find departments which have got 'Male' employee aging over 30
and filter the departments with the another in department table by (e.dept_id = D.id) constraint
Finally, we match the dept_id with the dept_id in the 1st part of the query and get the departments
which have got both male and female employees


3rd part:

SELECT Name FROM department D 
WHERE Name LIKE 'S%'  
AND id IN ()

This is the main query. First, it returns name of the department whose name begins with the letter 'S'
And filters id by the result of 2nd part
