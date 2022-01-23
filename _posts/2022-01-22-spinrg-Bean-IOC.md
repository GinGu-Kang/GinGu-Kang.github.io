---
title: "Spring IOC(Inversion of Control,제어의 역전) Container와 스프링 Bean - Spring 개념정리"
categories: "spring"
author_profile: false
---
#spring #blog








<br>
<br>
<br>

# Spring IOC(Inversion of Control,제어의 역전) Container와 스프링 Bean

## Goal

* Spring Bean 개념을 습득한다.
* Spring Bean의 개념을 이해하기 위한 IOC의 개념을 습득한다.




## 스프링 Bean? Spring IOC Container?
---
스프링 관련 강의를 처음 접하게 되면서 스프링 Bean이라는 단어가 굉장히 많이 나왔다. 강의에 나온 내용들을 따라하고 만들어보면서 Bean을 등록하고 의존관계를 설정하고 스프링 컨테이너가 관리하고 . 등등 계속해서 Bean 이라는 단어가 등장하고 머릿속에서는 개념이 잘 정리 되지 않았다. 내용을 정리하고 싶어 찾아보니 찾아본 블로그들에서**Spring IoC 컨테이너가 관리하는 자바 객체를 빈(Bean)**  이라고 나와 있었다…..그래서 Spring IoC는 뭐고 컨테이너는 또 뭘까


## Spring IOC Container
Spring IoC 컨테이너를 이해하기 위해 IOC(Inversion of Control,제어의 역전)의 개념을 알아야 한다.



#### **IOC(Inversion of Control,제어의 역전)의 개념**
---
* 코드의 흐름을 제어하는 주체가 바뀐것
* 오브젝트 생성, 오브젝트 생성주기 관리, 메소드 수행 등을 제 3자가 수행하는것.
* 제어권을 내가 아닌 다른 주체에게 넘기는 것


스프링을 사용하기 전까지 배운 자바 프로그래밍에서는 사용자가 객체들을 직접 생성하고 메소드를 호출하는 구조 였다. 
``` java
public class A{
    Student b = new Student();
    b.method();
}
```
와 같은 구조 이다. 하지만 Spring 프레임워크 에서는 프로그래머가 직접 객체를 생성하는 구조가 아닌 Spring Container가 java 객체의 생성과 관계설정, 사용, 제거 등의 작업을 제어 하는 IOC 방식을 사용한다.


## 스프링 Bean이란?
 이때, 프로그래머가 아닌 Spring IOC Container에게 관리당하는 java객체들을 **Spring Bean 객체** 라고 부른다. 

