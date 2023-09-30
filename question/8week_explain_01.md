### KMS
1. MySQL은 다른 RDBMS보다 통계 정보가 정확하지 않다고 하는데   
통계 정보의 정확도를 높이기 위해서 필요한 설정 방법과 
부족한 정확성을 보완하기 위해 실제 테이블에 정보를 얻는 방법을 설명하시오.

2.   
```SQL
-- 현재 세션의 시스템 변수값
innodb_stats_transient_sample_pages = 20
innodb_stats_persistent_sample_pages = 100
-- 테이블의 설정 값
STATS_AUTO_RECALC = 1;
```   
새 테이블을 생성했을 때 샘플링 되는 페이지의 수를 알려주세요.