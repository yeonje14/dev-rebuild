# Day 3 SQL 

# 1. each average age for department
SELECT department, AVG(age) FROM user GROUP BY department;

# 2. each people for department
SELECT department, COUNT(*) FROM user GROUP BY department;

# 3. each department for over the average 26
SELECT department, AVG(age) FROM user GROUP BY department, HAVING AVG(age) >= 26;

# 4. each department for most high age
SELECT department, MAX(age) FROM user GROUP BY department;

# 5. each department is over the age sum is 75
SELECT department, SUM(age) FROM user GROUP BY department HAVING SUM(age) >= 75;



