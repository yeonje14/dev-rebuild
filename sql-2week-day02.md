# 2week 2day
DELETE FROM user
WHERE id = 12;

SELECT * FROM user;

SELECT u.name, d.dept_name, d.location
FROM user u
JOIN department d ON u.department_id = d.dept_id;

SELECT d.dept_name, COUNT(u.id) AS cnt
FROM department d
LEFT JOIN user u ON u.department_id = d.dept_id
GROUP BY d.dept_name;

SELECT d.dept_name, ROUND(AVG(u.age),2) AS avg_age
FROM department d
LEFT JOIN user u ON u.department_id = d.dept_id
GROUP BY d.dept_name;

SELECT d.dept_name, COUNT(u.id) AS cnt
FROM department d
LEFT JOIN user u ON u.department_id = d.dept_id
GROUP BY d.dept_name
HAVING cnt >= 3;

SELECT department, MAX(age), MIN(age)
FROM user
GROUP BY department;

SELECT location, COUNT(*) AS cnt
FROM user
GROUP BY location;

SELECT u.id, u.name, u.department AS user_dept, d.dept_name AS dept_dept,
       u.location AS user_loc, d.location AS dept_loc
FROM user u
LEFT JOIN department d ON u.department_id = d.dept_id
WHERE u.department IS NULL
   OR u.location IS NULL
   OR u.department <> d.dept_name
   OR u.location <> d.location;

SELECT department, COUNT(*) AS cnt
FROM user
GROUP BY department
ORDER BY cnt DESC
LIMIT 1;

SELECT AVG(age)
FROM user
WHERE department = 'Dev';

SELECT location, department, COUNT(*)
FROM user
GROUP BY location, department
ORDER BY location, department;

SELECT u.name, u.age, d.dept_name
FROM user u
JOIN department d ON u.department_id = d.dept_id
WHERE u.age = (
    SELECT MAX(age) FROM user WHERE department_id = d.dept_id
);

SELECT department, AVG(age) AS avg_age
FROM user
GROUP BY department
HAVING avg_age >= 28;

SELECT COUNT(*)
FROM user u
JOIN department d ON u.department_id = d.dept_id;