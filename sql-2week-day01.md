## Today i learn the transaction and commit rollback so many thing for sql

-- department에 새 부서 추가
INSERT INTO department (dept_name, location)
VALUES ('Design', 'Seoul');

-- user에 새 직원 추가
INSERT INTO user (name, age, department_id)
VALUES ('Ryan', 27, 5);  -- Design 부서가 dept_id=5일 때

INSERT INTO user (name, age, department_id)
VALUES
('Tom', 22, 1),
('Ella', 26, 3),
('Sophie', 28, 4);

-- 특정 직원의 위치 수정
UPDATE user
SET location = 'Busan'
WHERE name = 'Ella';

-- 특정 부서의 위치 변경
UPDATE department
SET location = 'Jeju'
WHERE dept_name = 'Design';

UPDATE user
SET age = 29, location = 'Seoul'
WHERE id = 3;

-- 특정 직원 삭제
DELETE FROM user WHERE name = 'Tom';

-- 특정 부서 삭제
DELETE FROM department WHERE dept_name = 'Design';

START TRANSACTION;   -- 트랜잭션 시작
UPDATE user SET age = age + 1;
DELETE FROM user WHERE name = 'Ella';
ROLLBACK;            -- 취소(변경 전으로 되돌림)
COMMIT;              -- 확정(변경 반영)

-- INSERT
INSERT INTO user (name, age, department_id) VALUES ('Leo', 24, 2);

-- UPDATE
UPDATE user SET location = 'Busan' WHERE name = 'Leo';

-- DELETE
DELETE FROM user WHERE name = 'Leo';

-- TRANSACTION
START TRANSACTION;
INSERT INTO user (name, age, department_id) VALUES ('Mira', 25, 4);
UPDATE department SET location = 'Gwangju' WHERE dept_name = 'Sales';
ROLLBACK;  -- 취소
COMMIT;    -- 확정