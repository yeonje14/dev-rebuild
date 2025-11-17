# sql-2week-day04.md

UPDATE user
SET age = 25
WHERE name = 'Noah';

UPDATE user
SET location = 'Seoul'
WHERE department = 'Dev';

DELETE FROM user
WHERE id = 15;



ALTER TABLE user
ADD COLUMN salary INT;

ALTER TABLE user
DROP COLUMN salary;

ALTER TABLE user
RENAME COLUMN salary TO base_salary;



ALTER TABLE user
MODIFY age TINYINT;

UPDATE user u
JOIN department d ON u.department = d.dept_name
SET u.department_id = d.dept_id;

DELETE u
FROM user u
LEFT JOIN department d ON u.department_id = d.dept_id
WHERE d.dept_id IS NULL;

UPDATE user SET age = age + 1 WHERE department = 'HR';

UPDATE user SET location = 'Senior Zone' WHERE age >= 30;

UPDATE user SET location='Seoul'
WHERE department='Dev' AND location <> 'Seoul';

UPDATE user SET department='Unknown' WHERE department IS NULL;

SELECT id, name FROM user WHERE department_id IS NULL;

DELETE FROM user WHERE department_id IS NULL;

UPDATE user SET name='Ellie' WHERE name='Ella';

UPDATE user
SET location='Young Zone'
WHERE age < (SELECT AVG(age) FROM user);

SELECT COUNT(*) FROM user WHERE department='Marketing';

DELETE FROM department WHERE location <> 'Seoul';

ALTER TABLE user ADD COLUMN salary INT;

UPDATE user SET salary=3000 WHERE salary IS NULL;

SELECT name, salary FROM user ORDER BY salary DESC LIMIT 3;

SELECT u.* 
FROM user u 
LEFT JOIN department d ON u.department_id = d.dept_id
WHERE d.dept_id IS NULL;

DELETE u
FROM user u
LEFT JOIN department d ON u.department_id = d.dept_id
WHERE d.dept_id IS NULL;