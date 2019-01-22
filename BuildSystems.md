# Spring Boot - Build Systems

스프링 부트에서 빌드 시스템을 선택하는 것은 중요한 작업이다. 우리는 Maven 혹은 Gradle 을 추천하며, 의존성 관리를 위해서 제공한다. 스프링은 다른 빌드 시스템을 지원하지 않는다. 

# Dependency Management

스프링 부트 팀은 스프링 부트 버젼 지원을 위한 의존성 리스트를 매번 릴리스마다 제공한다. 당신은 빌드 설정 파일에 의존성을 위한 버젼을 쓸 필요가 없다. 스프링 부트는 자동적으로 의존성 버젼을 자동으로 설정한다. 기억해야할 것은 당신은 스프링 부트 버젼을 업그레이드 할때 의존성은 자동적으로 업그레이드 된다. 

노트 - 만약 당신이 특정 의존성 버젼을 원한다면 당신은 당신의 설정 파일을 지정할 수 있다. 그러나 스프링 부트 팀은 매우 추천한다. 이것은 특정 버젼의 의존성을 지정하지 않는다. 

# Maven Dependency

Maven 설정을 위해서 우리는 스프링 부트 스타터 부모 프로젝트를 상속해야한다. 이는 스프링 부트 스터타 의존성을 관리하기 위해 이용한다. 이것으로 우리는 스타터 부모를 상속 받고 pom.xml 파일에 아래와 같이 볼 수 있다. 

```
<parent>
   <groupId>org.springframework.boot</groupId>
   <artifactId>spring-boot-starter-parent</artifactId>
   <version>1.5.8.RELEASE</version>
</parent>
```

우리는 스프링 부트 페어런트 스타터 의존성을 특정 버젼을 지정한다. 그리고 다른 스타터 의존성을위해서 우리는 스프링 부트 버젼을 지정할 필요가 없다. 

```
<dependencies>
   <dependency>
      <groupId>org.springframework.boot</groupId>
      <artifactId>spring-boot-starter-web</artifactId>
   </dependency>
</dependencies>
```

# Gradle Dependency

우리는 스프링 부트 스타터 의존성을 build.gradle 파일에 임포트 할 수 있다. 우리는 스프링 부트 스타터 부모 의존성을 Maven, Gradle 가 필요하다. 

```
buildscript {
   ext {
      springBootVersion = '1.5.8.RELEASE'
   }
   repositories {
      mavenCentral()
   }
   dependencies {
      classpath("org.springframework.boot:spring-boot-gradle-plugin:${springBootVersion}")
   }
}
```

단순히 Gradle 에서 우리는 특정 스프링 부트 버젼넘버를 의존성에 추가할 필요가 없다. 스프링 부트는 자동적으로 버젼에 기반한 의존성을 설정한다.

```
dependencies {
   compile('org.springframework.boot:spring-boot-starter-web')
}
```

