---
title: "Spring IOC(Inversion of Control,제어의 역전)와 스프링 Bean - Spring 개념정리"
categories: "spring"
author_profile: false
---
#spring #blog






# Spring IOC(Inversion of Control,제어의 역전)와 스프링 Bean - Spring 개념정리

## Goal

* Spring Bean 개념을 습득한다.
* Spring Bean의 개념을 이해하기 위한 IOC의 개념을 습득한다.




## 스프링 Bean? Spring IOC Container?
---
스프링 관련 강의를 처음 접하게 되면서 스프링 Bean이라는 단어가 굉장히 많이 나왔다. 강의에 나온 내용들을 따라하고 만들어보면서 Bean을 등록하고 의존관계를 설정하고 스프링 컨테이너가 관리하고 . 등등 계속해서 Bean 이라는 단어가 등장하고 머릿속에서는 개념이 잘 정리 되지 않았다. 내용을 정리하고 싶어 찾아보니 찾아본 블로그들에서**Spring IoC 컨테이너가 관리하는 자바 객체를 빈(Bean)**  이라고 나와 있었다…..그래서 Spring IoC는 뭐고 컨테이너는 또 뭘까 개념을 정리해 보자.


## Spring IOC Container
Spring IoC 컨테이너를 이해하기 위해서는 IOC(Inversion of Control,제어의 역전)의 개념을 알고 있어야한다. 



#### **IOC(Inversion of Control,제어의 역전)의 개념**
* 코드의 흐름을 제어하는 주체가 바뀐것
* 오브젝트 생성, 오브젝트 생성주기 관리, 메소드 수행 등을 제 3자가 수행하는것.
* 제어권을 내가 아닌 다른 주체에게 넘기는 것



이라고 볼수 있다. 지금 까지 배운 자바 프로그래밍에서는 사용자가 객체들을 직접 생성하고 메소드를 호출하는 구조 였다. `Student a = new Student();`  하지만 Spring IoC Container 에서는 프로그래머가 직접 객체를 생성해서 사용하는 것이아닌 Spring Container가 객체들을 생성, 생성주기 관리 하는 제어권을 갖고 있다.  


## 스프링 Bean이란?
 이렇게 프로그래머가 아닌 Spring Container에게 관리당하는 java객체들을 **Spring Bean 객체** 라고 부른다. 