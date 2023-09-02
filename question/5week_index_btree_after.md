+ KMS
1. 
CREATE TABLE articles (   
       id INT UNSIGNED AUTO_INCREMENT NOT NULL PRIMARY KEY,   
       title VARCHAR (200),   
       body TEXT,   
       FULLTEXT (title, body) with parser ngram   
      ) ENGINE = InnoDB;

 INSERT INTO articles (title, body) VALUES   
     ( 'MySQL Tutorial', 'DBMS stands for DataBase ...'),   
     ( 'How To Use MySQL Well', 'After you went through a ...'),   
     ( 'Optimizing MySQL', 'In this tutorial we will show ...'),   
     ( '1001 MySQL Tricks', '1. Never run mysqld as root 2. ..1001'),   
     ( 'MySQL vs. YourSQL', 'In the following database  comparison ...'),   
     ( 'MySQL Security', 'When configured properly, MySQL ...');   
     이렇게 데이터를  삽입했을때 1001은 몇개가 인덱스에 추가되었을까요?
  
2. 
create table tb_parent (   
	id int not null,   
	fd varchar(100) not null,primary key (id)   
) engine=innodb;   

create table tb_child (   
	id int not null,   
	pid int default null,   
	fd varchar(100) default null,   
	primary key (id),   
	key ix_parentid (id),   
	constraint child_ibfk_1 foreign key (pid) references     tb_parent (id) on delete cascade   
) engine = innodb;  

insert into tb_parent values (1,'parant-1'),(2,'parant-2');  
insert into tb_child values (100,1,'child-100');

-- 커넥션-1   
SET AUTOCOMMIT = 0;
SELECT * FROM tb_parent where fd like '%pa%' FOR UPDATE;

이후   
-- 커넥션-2   
SET AUTOCOMMIT = 0;   
update tb_child set pid=1 where id = 100; (1)   
-- 커넥션-3   
SET AUTOCOMMIT = 0;  
insert into tb_parent values (3,'parant-3'),(4,'parant-4'); (2)     
-- 커넥션-4   
SET AUTOCOMMIT = 0;   
update tb_child set pid=2 where id = 100; (3)   
    
  
1,2,3번을 실행했을때 데드락이 걸리는건 몇번일까요?   
데드락이 걸린 번호와 안걸린 번호를 골라주세요   
그리고 그 이유도 같이 설명해주세요.

+ 튜브
1. MySQL B-Tre를 전문(Full Text) 검색에서는 사용할 수 없는 이유에 대해 설명해주세요.
2. 유니크 인덱스와 일반 세컨더리 인덱스의 읽기와 쓰기의 성능에 대해 설명해주세요.
