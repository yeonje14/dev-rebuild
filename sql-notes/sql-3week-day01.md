# sql-3week-day01.md

SELECT name, age,
       ROW_NUMBER() OVER (ORDER BY age DESC) AS rn
FROM user;



SELECT name, age,
       RANK() OVER (ORDER BY age DESC) AS rnk
FROM user;

SELECT name, age,
       DENSE_RANK() OVER (ORDER BY age DESC) AS drnk
FROM user;

SELECT name, department, age,
       ROW_NUMBER() OVER (PARTITION BY department ORDER BY age DESC) rn
FROM user;

SELECT name, department, age,
       RANK() OVER (PARTITION BY department ORDER BY age DESC) rnk
FROM user;

SELECT *
FROM (
    SELECT name, department, age,
           ROW_NUMBER() OVER (PARTITION BY department ORDER BY age DESC) rn
    FROM user
) t
WHERE rn = 1;