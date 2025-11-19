# sql-3week-day02.md

SELECT name, age,
       LAG(age, 1) OVER (ORDER BY age) AS prev_age
FROM user;

SELECT name, age,
       LEAD(age, 1) OVER (ORDER BY age) AS next_age
FROM user;

SELECT name, age,
       age - LAG(age) OVER (ORDER BY age) AS diff_from_prev
FROM user;

SELECT name, department, age,
       FIRST_VALUE(name) OVER (
           PARTITION BY department
           ORDER BY age DESC
       ) AS oldest_in_dept
FROM user;

SELECT name, age,
       NTILE(4) OVER (ORDER BY age) AS quartile
FROM user;