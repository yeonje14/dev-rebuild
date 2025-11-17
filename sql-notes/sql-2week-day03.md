# sql-2week-day3

SELECT name, age
FROM user
WHERE age > (SELECT AVG(age) FROM user);

SELECT name, age
FROM user
WHERE age = (SELECT MAX(age) FROM user WHERE department='Dev');

SELECT u.name, u.age, u.department
FROM user u
WHERE u.age > (
    SELECT AVG(age)
    FROM user
    WHERE department = u.department
);

SELECT name, age
FROM user
WHERE age > ANY (SELECT age FROM user WHERE department='HR');

SELECT name, age
FROM user
WHERE age > ALL (SELECT age FROM user WHERE department='Dev');

SELECT d.dept_name
FROM department d
WHERE NOT EXISTS (
    SELECT 1
    FROM user u
    WHERE u.department_id = d.dept_id
);

SELECT name
FROM user
WHERE department IN (
    SELECT dept_name FROM department WHERE location='Seoul'
);

SELECT name FROM user WHERE location='Incheon';

SELECT u.name, u.age, d.dept_name
FROM user u
JOIN department d ON u.department_id=d.dept_id
WHERE u.age >= (SELECT AVG(age) FROM user);

SELECT department
FROM user
GROUP BY department
HAVING COUNT(*) > (
    SELECT COUNT(*) FROM user WHERE department='Dev'
);

SELECT name, age
FROM user
WHERE age = (SELECT MAX(age) FROM user);

SELECT department, COUNT(*)
FROM user
GROUP BY department
HAVING COUNT(*) > (
    SELECT MIN(cnt)
    FROM (SELECT COUNT(*) AS cnt FROM user GROUP BY department) AS t
);

SELECT d.dept_name
FROM department d
WHERE EXISTS (
    SELECT 1 FROM user u WHERE u.department_id = d.dept_id AND u.name LIKE 'A%'
);

SELECT d.dept_name, ROUND(AVG(u.age),2) AS avg_age,
       (SELECT AVG(age) FROM user) AS all_avg
FROM department d
JOIN user u ON u.department_id = d.dept_id
GROUP BY d.dept_name;

SELECT u.name, u.age, d.dept_name
FROM user u
JOIN department d ON u.department_id=d.dept_id
WHERE u.age = (
    SELECT MIN(age) FROM user WHERE department_id = d.dept_id
);