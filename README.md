### DB 정보(3번 과제와 동일)

DB 경로 : database-1.cgsqdm8ubkh3.ap-northeast-2.rds.amazonaws.com

Database : mysql

PORT : 3306

user : admin

password : password

![image](https://user-images.githubusercontent.com/103189961/230875491-2864a115-f0b7-41b3-901a-6a8844eaf6fd.png)


### 사전 과정

(1) first_half 테이블 및 데이터 생성

![image](https://user-images.githubusercontent.com/103189961/230882436-ec491512-9fdb-4ea6-a37a-3a1c54343d8f.png)

![image](https://user-images.githubusercontent.com/103189961/230882514-0112bc24-a184-4cd9-bf98-f9d40aad0f8a.png)

(2) july 테이블 및 데이터 생성

![image](https://user-images.githubusercontent.com/103189961/230882703-b4526c51-5095-4d5e-91c8-5027ca5fc176.png)

![image](https://user-images.githubusercontent.com/103189961/230882784-bfaef59d-4f8d-4d14-a8ec-b1f4df7d510e.png)

### 문제

7월 아이스크림 총 주문량과 상반기의 아이스크림 총 주문량을 더한 값이 큰
순서대로 상위 3 개의 맛을 조회하는 SQL 문을 작성해주세요.

select fh.flavor
from first_half fh join 
(select flavor, sum(total_order) as total_order_july from july group by flavor) jul on fh.flavor = jul.flavor
group by flavor
order by sum(fh.total_order + jul.total_order_july) desc limit 3;

(결과 화면)

![image](https://user-images.githubusercontent.com/103189961/230886628-dff5372e-704f-4163-8ed3-5c4f27b19edb.png)

