### SQL의 종류 ( DDL, DML, DCL, TCL )

- Data Define Language (데이터 정의어) : 테이블 생성에 관련

  -> CREATE, ALTER, DROP

- Data Manipulation Language (데이터 조작어) : 테이블에 저장된 데이터를 관리하는데 사용 

  -> SELECT, INSERT, UPDATE, DELETE

- Data Control Language (데이터 제어어) : 데이터베이스의 권한을 부여할 때 사용

  -> GRANT, REVOKE 

- Transactional Control Language (트랜잭션 제어어) : 데이터의 보안, 무결성, 회복, 병행 수행제어 등을 정의하는데 사용  // DCL에서 COMMIT, ROLLBACK을 따로 TCL로 분리하기도 함!!

  -> COMMIT(트랜잭션의 작업 결과를 반영), ROLLBACK(트랜잭션의 작업을 취소 및 원래대로 복구)
  

### Index가 무엇이고 언제 많이 사용하는지

- 데이터베이스 테이블의 검색 속도를 향상시키기 위한 자료구조


### CI/CD가 무엇인지

- Continuous Integration(지속적 통합)와 Continuous Delivery or Continuous Deployment(지속적 배포)라 불리는데, 서비스 개발 단계부터 배포 까지의 모든 단계들을 자동화하여 더 효율적이고 빠르게 사용자에게 배포할 수 있다는 장점이 있습니다. 



### JPA가 무엇이며 장점은?

- 자바 진영에서 ORM 기술 표준으로 사용하는 인터페이스 모음

  -> 대표적인 오픈소스로 Hibernate 있음

- 가장 큰 이유는 SQL 지향적 개발에서 벗어나 객체 중심 개발로 전환할 때 사용합니다.

  - 객체 지향으로 개발을 하게 되면 생산성이 좋아지고 유지보수도 용이함.

- 기본적인 CRUD와 페이징 처리 등 많은 부분이 구현되어 있어 비즈니스 로직에 집중 가능

  -> SQL문을 자동으로 생성해주기 때문에 개발이 빨라짐


### ORM이 무엇인가요? 

- Object Relational Mapping으로서, 객체와 관계형 데이터베이스를 Mapping 해주는 도구입니다. 
- 관계형 데이터베이스에서 조회한 데이터를 Java 객체로 변환하여 리턴해주고, Java 객체를 관계형 데이터베이스에 저장해주는 라이브러리 혹은 기술


### MyBatis란? 

- Object Mapping 기술
- 자바의 관계형 데이터베이스 프로그래밍을 좀 더 쉽게 할 수 있게 도와주는 프레임워크
- SQL문을 직접 작성하여 쿼리 수행 결과를 객체와 매핑
- 복잡한 쿼리문도 작성할 수 있다는 장점


### JVM이란?

![스크린샷 2022-10-10 오후 9 01 40](https://user-images.githubusercontent.com/91196025/196181721-502d6962-b42e-4181-b340-fdf53816fdf5.png)
- 자바 버츄얼 머신으로 CPU가 Java를 인식하고 실행할 수 있게 하는 가상 컴퓨터
- *.java -> .class -> 기계어
- CPU는 자바 소스코드(원시 코드, 즉 *.java)를 인식하지 못해 기계어로 컴파일 해줘야 함. 
  - OS에 도달하기 위해서는 JVM을 거쳐야 하기 때문에 JVM이 인식할 수 있는 Java bytecode(*.class)로 변환해야 함.

- 자바 버츄얼 머신으로 CPU가 Java를 인식하고 실행할 수 있게 하는 가상 컴퓨터
- *.java -> .class -> 기계어
- CPU는 자바 소스코드(원시 코드, 즉 *.java)를 인식하지 못해 기계어로 컴파일 해줘야 함. 
  - OS에 도달하기 위해서는 JVM을 거쳐야 하기 때문에 JVM이 인식할 수 있는 Java bytecode(*.class)로 변환해야 함.
