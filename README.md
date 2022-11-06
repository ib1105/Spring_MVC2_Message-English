# Spring_MVC2_Message-Internationalization

기본셋팅

Annotation Processors > Enable annotation processing 체크

Gradle > Build and run using, Run tests using = IntelliJ IDEA

File Encodings > Global Encoding, Project Encoding, Default encodeing for properties files : UTF-8

**스프링 메시지 소스 설정**

스프링은 기본적인 메시지 관리 기능을 제공한다.

**스프링 부트**

스프링 부트를 사용하면 스프링 부트가 MessageSource 를 자동으로 스프링 빈으로 등록한다.

스프링 부트를 사용하면 다음과 같이 메시지 소스를 설정할 수 있다.

[application.properties](http://application.properties)

spring.messages.basename=messages,config.i18n.messages

**스프링 부트 메시지 소스 기본 값**

MessageSource 를 스프링 빈으로 등록하지 않고, 스프링 부트와 관련된 별도의 설정을 하지 않으면

messages 라는 이름으로 기본 등록된다. 따라서 messages_en.properties ,

messages_ko.properties , messages.properties 파일만 등록하면 자동으로 인식된다.

messages.properties :기본 값으로 사용(한글)

messages_en.properties : 영어 국제화 사용

**주의! 파일명은 massage가 아니라 messages다! 마지막 s에 주의하자**

**타임리프 메시지 적용**

타임리프의 메시지 표현식 #{...} 를 사용하면 스프링의 메시지를 편리하게 조회할 수 있다.

예를 들어서 방금 등록한 상품이라는 이름을 조회하려면 #{label.item} 이라고 하면 된다.

<div th:text="#{label.item}"></h2>

**참고로 파라미터는 다음과 같이 사용할 수 있다.**

hello.name=안녕 {0}

<p th:text="#{[hello.name](http://hello.name)(${item.itemName})}"></p>

**웹 애플리케이션에 국제화 적용하기**

앞서 MessageSource 테스트에서 보았듯이 메시지 기능은 Locale 정보를 알아야 언어를 선택할 수 있다.

결국 스프링도 Locale 정보를 알아야 언어를 선택할 수 있는데, 스프링은 언어 선택시 기본으로 Accept-

Language 헤더의 값을 사용한다.
