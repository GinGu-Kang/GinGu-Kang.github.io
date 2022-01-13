---
title: "Spring 시작하기"
categories: "Spring"
---

# 스프링 입문
나는 학부생활과 연구실 생활을 하며 주로 python에서의 opencv, Django, mediapipe 등을 주로 다뤄왔다. 하지만 Django에 대한 글을 봤을때 대규모 서비스를 공부하기에는 Django에 대한 글보다 java진영의 spring에 대한 정보가 더많기 때문에 spring을 공부를 시작하게 되었다. spring을 입문하기 위한 공부자료는 유튜브에서 배달에 민족 김영한개발자님의 영상을 보며 공부한 것들을 기록해보려 한다.

# 영상에서의 공부 방법
영한님의 강의에서는 이론 수업에 힘들어하는 개발자들을 위하여 간단한 웹 어플리케이션 개발 실습을 하며 강의를 진행 한다. 
<br>
<br>

### 웹어플리케이션 개발 순서
---
<ol>
    <li>스프링 프로젝트 생성</li>
    <li>스프링 부트로 웹 서버 실행</li>
    <li>회원 도메인 개발</li>
    <li>웹 MVC 개발</li>
    <li>DB 연동 </li>
    <li>테스트 케이스 작성</li>
</ol>
의 순서대로 진행된다.
<br>
  
### 사용 기술
---
<ol>
    <li>Spring boot</li>
    <li>JPA</li>
    <li>Tomcat</li>
    <li>Gradle</li>
    <li>Thymeleaf</li>
    <li>HIBERNATE</li>
</ol>


# 스프링 부트란(Spring Boot)란?
스프링 부트란 사용자가 직접 셋팅해야하는 자주 사용하지만 복잡하고 무수한 설정들을 대부분 미리설정해놓은 라이브러리이다.


# 프로젝트 생성
*사전 준비물*
* java 11
* IDE:IntelliJ or Eclipse 설치 

강의자와 다른 환경에서 공부할때 생기는 불편함을 방지하기 위하여 기존에 사용하던 이클립스가 아닌 인텔리제이를 설치했다. 인텔리제이를 처음 사용해 보았는데 인텔리제이는 사용자 친화적인 UI와 Visual Studio Code 와 같이 다양한 플러그인들을 손쉽게 다운받고 적용할 수 있어 굉장히 편리했다.

### 스프링 부트 스타터 사이트
[링크](https://start.spring.io/)

링크를 클릭하여 스프링 부트 스타터 사이트로 이동한다.

![image](/assets/images/spring/spring_starter.png)

### Project
라이브러리를 가져와 주는 빌드 도구를 선택하는 부분 이 프로젝트에서는 **Gradle**을 사용한다. 현업에서는 Gradle을 주로 많이 쓴다고 함(Ant 와 Maven의 장점만 모아서 만듬)
### Spring Boot 
스프링 부트의 버전을 선택해주는 곳이다. Snapshot 은 아직 만들고 있는 버전이고 m1은 정식 릴리즈 된 버전이 아니다. 때문에 정식 릴리즈 된 **2.6.2** 버전을 사용한다

### Project Metadata
* Group
기업의 도메인 명을 적는 부분, 인터넷 주소를 뒤집어 써놓은 형태이다.

* Artifact
빌드되어 나올때의 결과물(jar) 프로젝트 명과 같은 것
* Description
설명이 들어가는 부분

### Dependencies
 스프링 부트 기반으로 프로젝트 생성시에 어떤 라이브러리를 가져올꺼냐 설정해주는 부분.이 프로젝트에서는 아래의 라이브러리를 초기에 가져온다
* Spring Web
* Thymeleaf
	* Thymeleaf는  템플릿 양식과 특정 모델에 따른 데이터를 결합하여 page를 출력해준다. 
* Spring Boot DevTools 
	* 스프링 실행시 코드가 변경될때마다 재시작해야하는 번거로움을 줄여주는 도구.



### Generate
최하단의 Generate 부분을 눌러 프로젝트를 생성후 압축 해제
![image](/assets/images/spring/generate.png)


# 인텔리제이에서 프로젝트 파일 열기
![image](/assets/images/spring/open_project.png)
인텔리제이의 첫화면에서 Open 버튼을 누르고 생성해준 파일을 찾아 open


# 프로젝트 내부 파일 살펴 보기
![image](/assets/images/spring/project_in.png)
* .idea 
	* 인텔리제이가 사용하는 설정파일
* src
	* main
		* 실제 코드들이 들어가는 공간
		* resources
			*  실제 자바 코드를 제외한 xml등의 설정 파일이 이곳에 들어간다. static에는 값이 동적으로 변경되지 않아도 되는 정적 html 파일이 들어간다.
	* test
		* 테스트 코드들과 관련된 소스들이 이곳에 들어간다 요즘에는 테스크 코드가 프로젝트를 진행할때 굉장히 중요하다고 한다. 영상을 찾아봐도 실제 개발코드를 작성하는 시간은 30% 이고 나머지를 테스트 코드를 작성에 사용한다고 한다


# build.gradle
![image](/assets/images/spring/build_gradle.png)




