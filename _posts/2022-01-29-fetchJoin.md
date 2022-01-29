---
title: "정보 처리 기사 상용 소프트웨어 개념 정리"
categories: "spring"
author_profile: false
toc: false
---

# n+1 문제
회원과 다수의 권한이 있는 oneToMany관계에서 회원을 조회할때 fetch.EAGER로 가져오면 회원이 조회되는 동시에 권한들을 가져오게 된다. 이때 권한을 한번에 조회하는게 아닌 회원1명 조회 -> 회원의 권한들 조회 ->다음회워조회 ->현재회원의 권한조회 를하게되어 한명의 사원당 1번의 쿼리가 추가로 발생되어 db검색시 db 서버에 부하가 가게된다.
```java
@Table(name="User")
public class User implements UserDetails {//implements UserDetails
    ...

    @OneToMany(mappedBy = "user",fetch = FetchType.EAGER)
    private List<UserRole> userRoles = new ArrayList<>();
    ...
```
### Result
```
Hibernate: select user0_.email as email1_2_, user0_.company_code as company_2_2_, user0_.creatat as creatat3_2_, user0_.department as departme4_2_, user0_.enabled as enabled5_2_, user0_.name as name6_2_, user0_.password as password7_2_, user0_.phone as phone8_2_, user0_.updatedate as updateda9_2_ from user user0_ where user0_.company_code=?
Hibernate: select userroles0_.user_email as user_ema3_3_0_, userroles0_.id as id1_3_0_, userroles0_.id as id1_3_1_, userroles0_.role_name as role_nam2_3_1_, userroles0_.user_email as user_ema3_3_1_, role1_.name as name1_1_2_ from user_role userroles0_ left outer join role role1_ on userroles0_.role_name=role1_.name where userroles0_.user_email=?
Hibernate: select userroles0_.role_name as role_nam2_3_0_, userroles0_.id as id1_3_0_, userroles0_.id as id1_3_1_, userroles0_.role_name as role_nam2_3_1_, userroles0_.user_email as user_ema3_3_1_, user1_.email as email1_2_2_, user1_.company_code as company_2_2_2_, user1_.creatat as creatat3_2_2_, user1_.department as departme4_2_2_, user1_.enabled as enabled5_2_2_, user1_.name as name6_2_2_, user1_.password as password7_2_2_, user1_.phone as phone8_2_2_, user1_.updatedate as updateda9_2_2_ from user_role userroles0_ left outer join user user1_ on userroles0_.user_email=user1_.email where userroles0_.role_name=?
Hibernate: select userroles0_.role_name as role_nam2_3_0_, userroles0_.id as id1_3_0_, userroles0_.id as id1_3_1_, userroles0_.role_name as role_nam2_3_1_, userroles0_.user_email as user_ema3_3_1_, user1_.email as email1_2_2_, user1_.company_code as company_2_2_2_, user1_.creatat as creatat3_2_2_, user1_.department as departme4_2_2_, user1_.enabled as enabled5_2_2_, user1_.name as name6_2_2_, user1_.password as password7_2_2_, user1_.phone as phone8_2_2_, user1_.updatedate as updateda9_2_2_ from user_role userroles0_ left outer join user user1_ on userroles0_.user_email=user1_.email where userroles0_.role_name=?
Hibernate: select userroles0_.user_email as user_ema3_3_0_, userroles0_.id as id1_3_0_, userroles0_.id as id1_3_1_, userroles0_.role_name as role_nam2_3_1_, userroles0_.user_email as user_ema3_3_1_, role1_.name as name1_1_2_ from user_role userroles0_ left outer join role role1_ on userroles0_.role_name=role1_.name where userroles0_.user_email=?
Hibernate: select userroles0_.role_name as role_nam2_3_0_, userroles0_.id as id1_3_0_, userroles0_.id as id1_3_1_, userroles0_.role_name as role_nam2_3_1_, userroles0_.user_email as user_ema3_3_1_, user1_.email as email1_2_2_, user1_.company_code as company_2_2_2_, user1_.creatat as creatat3_2_2_, user1_.department as departme4_2_2_, user1_.enabled as enabled5_2_2_, user1_.name as name6_2_2_, user1_.password as password7_2_2_, user1_.phone as phone8_2_2_, user1_.updatedate as updateda9_2_2_ from user_role userroles0_ left outer join user user1_ on userroles0_.user_email=user1_.email where userroles0_.role_name=?
Hibernate: select userroles0_.user_email as user_ema3_3_0_, userroles0_.id as id1_3_0_, userroles0_.id as id1_3_1_, userroles0_.role_name as role_nam2_3_1_, userroles0_.user_email as user_ema3_3_1_, role1_.name as name1_1_2_ from user_role userroles0_ left outer join role role1_ on userroles0_.role_name=role1_.name where userroles0_.user_email=?
Hibernate: select userroles0_.user_email as user_ema3_3_0_, userroles0_.id as id1_3_0_, userroles0_.id as id1_3_1_, userroles0_.role_name as role_nam2_3_1_, userroles0_.user_email as user_ema3_3_1_, role1_.name as name1_1_2_ from user_role userroles0_ left outer join role role1_ on userroles0_.role_name=role1_.name where userroles0_.user_email=?
Hibernate: select userroles0_.user_email as user_ema3_3_0_, userroles0_.id as id1_3_0_, userroles0_.id as id1_3_1_, userroles0_.role_name as role_nam2_3_1_, userroles0_.user_email as user_ema3_3_1_, role1_.name as name1_1_2_ from user_role userroles0_ left outer join role role1_ on userroles0_.role_name=role1_.name where userroles0_.user_email=?
Hibernate: select userroles0_.user_email as user_ema3_3_0_, userroles0_.id as id1_3_0_, userroles0_.id as id1_3_1_, userroles0_.role_name as role_nam2_3_1_, userroles0_.user_email as user_ema3_3_1_, role1_.name as name1_1_2_ from user_role userroles0_ left outer join role role1_ on userroles0_.role_name=role1_.name where userroles0_.user_email=?

```

## 해결법
EntityGraph를 사용해 FetchJoin을 해준다.
`Fetch join` 사용시 조희의 주체가 되는 Entity와 Fetch join이 걸린 Entity를 함께 select하게 되 쿼리를 한꺼번에 날릴수 있게된다.


```java
@NamedEntityGraph(name="User.userRoles",attributeNodes = @NamedAttributeNode("userRoles"))
@Table(name="User")
public class User implements UserDetails {//implements UserDetails
    ...

    @OneToMany(mappedBy = "user",fetch = FetchType.EAGER)
    private List<UserRole> userRoles = new ArrayList<>();
```
@NamedEntityGraph
name : 엔티티 그래프 이름 정의

attributeNodes : 함께 조회할 속성 선택



출처: https://data-make.tistory.com/628 [Data Makes Our Future]

정의한뒤 Repository에서 EntityGraph를 사용할 메소드위에 @EntityGraph 애노테이션을 사용하고 사용할 EntityGraph의 이름을 정의해준다.
```java


public interface UserRepository extends JpaRepository<User,String> {

    Optional<User> findByEmail(String email);
    void deleteByEmail(String email);
    @EntityGraph(value = "User.userRoles")//<-------
    List<User> findByCompanyCode(String companyCode);

}
```

## Result
```
Hibernate: select user0_.email as email1_2_0_, userroles1_.id as id1_3_1_, user0_.company_code as company_2_2_0_, user0_.creatat as creatat3_2_0_, user0_.department as departme4_2_0_, user0_.enabled as enabled5_2_0_, user0_.name as name6_2_0_, user0_.password as password7_2_0_, user0_.phone as phone8_2_0_, user0_.updatedate as updateda9_2_0_, userroles1_.role_name as role_nam2_3_1_, userroles1_.user_email as user_ema3_3_1_, userroles1_.user_email as user_ema3_3_0__, userroles1_.id as id1_3_0__ from user user0_ left outer join user_role userroles1_ on user0_.email=userroles1_.user_email where user0_.company_code=?
```

## 결론
EntityGraph를 사용해 n+1문제를 해결 하였다.