### KMS
1.
```sql
SELECT /*+ BNL (e,de) */ *
FROM employees e
INNER JOIN dept_emp de ON de.emp_no=e.emp_no;
```
해당 코드를 실행하면 힌트를 무시하고 네스티드 루프 조인이 되는데
힌트를 적용하게 하려면 어떤 작업을 해야할까요?

2. 
네스티드 루프 조인 
```SQL
-- 1
SELECT * FROM T1 INNER JOIN T2 ON P1(T1,T2)
                 INNER JOIN T3 ON P2(T2,T3)
  WHERE P(T1,T2,T3)

-- 2
SELECT * T1 LEFT JOIN T2 ON P1(T1,T2) 
            LEFT JOIN T3 ON AND P2(T1,T3)
  WHERE P(T1,T2,T3)
  
-- P1(X,Y)는 조인 컬럼 동등 조건입니다.
-- P(T1,T2,T3)의 조건
P(T1,T2,T2) = C1(T1) AND C2(T2) AND C3(T3)
```
1번 SQL과 2번 SQL에서 WHERE 조건이 언제 적용 되는지 설명해주세요.