---
layout: single
title:  "비즈니스 데이터 요구사항 정ㅣ"
categories: spring
toc: true
author_profile: false
published: false
---


# 비즈니스 요구사항 정리
### 데이터

* 기기(mat)
	* 시리얼
	* 계산방식
	* 임계값
	* 재고무게
	* 최근 갱신 날짜
	* 이메일 보내기 여부
	* 위치
	* 상품주문갯수
	* 박스 무게
	* 배터리
	* 회사코드(fk)
* 회사(company)
	* 회사코드
	* 업종
	* 회사이름
	* 회사주소
	* 생성일자
	* 대표 아이디
* 직종 카테고리(business_category)
	* 직종 이름
* 사용자(user)
	* 이메일(pk)
	* 회사코드(fk)
	* 비밀번호
	* 이름
	* 전화번호
	* 부서
	* 생성일자
* 권한(role)
	* 아이디(pk)
	* 사용자이메일(fk)
	* 유저 관리권한
	* 기기 관리권한
	* 회사 정보 수정권한
* 제품(product)
	* 제품코드(pk)
	* 회사코드(fK)
	* 제품 카테고리(fk)
	* 제품 이미지
	* 제품 무게
	* 제품 이름
* 제품카테고리(product_category)
	* 아이디(pk)
	* 카테고리 명
	* 회사 코드(fk)
* 기기 목록(mat_category)
	* 시리얼
	* 매트 종류
* 통지 이메일(notice_email)
	* 이메일(pk)
	* 매트 시리얼(fk)

* 문의사항(question)
	* 아이디(pk)
	* 유저 이메일(fk)
	* 비밀글 여부
	* 제목
	* 문의글
	* 만들어진시간
	* 회사코드
* 답변(answer)
	* id(pk)
	* 답변글
	* 답변시간
	* 질문아이디
* 기기 종류(mat_category)
	* id(pk)
	* 기기 가격
	* 기기 정보
	* 기기 최대 무게
* 생산된 기기 목록(mat_deviece)
	* 시리얼
	*  기기종류
* 종류별 주문갯수(mat_category_order)
	* 아이디(pk)
	* 주문 id(fk)
	* 매트종류 (fk)
	* 주문갯수
* 주문(order)_
	* 아이디(pk)
	* 주문 주소
	* 배송상태
	* 희망주문날짜
	* 주문자 이메일
	* 생성날짜
	* 송장번호
	* 입금자명(추가)
* 기기 입출고 로그(inOut_log) (No sql)
	* 입/출고 시간
	* 제품명
	* 제품코드
	* 입출고 상태
	* 변동 갯수
	* 현재 갯수
	* 시리얼
	* 장소
