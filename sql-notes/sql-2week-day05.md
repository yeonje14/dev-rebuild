# sql-2week-day05.md

SELECT name, age
FROM user
WHERE age >= 30
ORDER BY age DESC
LIMIT 5;

SELECT name FROM user WHERE age BETWEEN 25 AND 30;  

SELECT name FROM user WHERE name LIKE 'A%';

SELECT department, AVG(age)
FROM user
GROUP BY department;

SELECT department, AVG(age) avg_age
FROM user
GROUP BY department
HAVING avg_age >= 28;

SELECT u.name, d.dept_name
FROM user u
JOIN department d ON u.department_id = d.dept_id;

SELECT d.dept_name, COUNT(u.id)
FROM department d
LEFT JOIN user u ON u.department_id = d.dept_id
GROUP BY d.dept_name;

SELECT name, age
FROM user
WHERE age > (SELECT AVG(age) FROM user);

age > ANY (SELECT age FROM user WHERE department='Dev');

age > ALL (SELECT age FROM user WHERE department='Dev');

UPDATE user
SET location='Seoul'
WHERE id=3;   -- 반드시 특정 조건을 건다

SELECT name FROM user
WHERE age > (SELECT AVG(age) FROM user);

SELECT u.name
FROM user u
JOIN department d ON u.department_id=d.dept_id
WHERE d.location='Seoul';

SELECT AVG(age) FROM user
WHERE department='Marketing';

SELECT * FROM user
WHERE age = (SELECT MAX(age) FROM user);

SELECT department, COUNT(*) cnt
FROM user
GROUP BY department
ORDER BY cnt DESC;

SELECT name FROM user
WHERE department IN ('HR');

SELECT name, age FROM user
WHERE department='Dev'
ORDER BY age ASC;

SELECT name FROM user WHERE name LIKE 'L%';

DELETE FROM user WHERE department IS NULL;

SELECT u.name, u.age, u.department
FROM user u
WHERE u.age = (
    SELECT MIN(age)
    FROM user
    WHERE department = u.department
);

UPDATE user u
JOIN department d ON u.department = d.dept_name
SET u.department_id = d.dept_id;

SELECT location, COUNT(*) FROM user GROUP BY location;

SELECT name FROM user
WHERE age < (SELECT AVG(age) FROM user);

SELECT name FROM user WHERE department IN ('HR','Marketing');

SELECT MAX(age) - MIN(age) 
FROM user WHERE department='Dev';