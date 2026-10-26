# [Spring] Project JDK와 Gradle JDK의 차이점

> 작성일: 2025-06-18 · 태그: 프레임워크/스프링, 심화

Java프로젝트에서 프로젝트 JDK와 Gradle JDK는 서로 다른 목적을 가진 설정이다. 둘 다 JDK(Java Development Kit)를 사용하지만, 적용되는 범위와 역할이 다르다.

##### 1. 프로젝트 JDK
- 역할 : 프로젝트의 Java코드를 컴파일하고 실행하는 데 사용되는 JDK이다.
- 적용대상:
	- 개발자가 작성한 코드
	- IDE에서 코드 자동 완성, 경고 등
- 설정위치:
	- IntelliJ 기준 : `Project Structure > Project > Project SDK`
- 예시:
	- Java 17로 작성된 프로젝트라면, Project JDK는 Java 17이어야 한다.

##### Gradle JDK
- **역할:** Gradle 빌드 도구가 **자체적으로 동작**할 때 사용하는 JDK입니다.
- **적용 대상:**
    - `gradle` 명령 실행 시 사용하는 JDK
    - 예: `./gradlew build`, Gradle Wrapper 실행
- **설정 위치:**
    - IntelliJ 기준: `Settings > Build, Execution, Deployment > Build Tools > Gradle > Gradle JVM`
- **주의할 점:**
    - Gradle JDK와 Project JDK가 다를 수 있음
    - 예를 들어, Gradle은 Java 11로 실행되지만, 프로젝트는 Java 17을 사용할 수 있음

##### 왜 분리돼 있을까?
- **Gradle 자체는 Java 프로그램이기 때문에**, 어떤 JDK로 실행할지 정해줘야 함
- 하지만 **Gradle이 빌드하는 프로젝트는 그와 다른 JDK를 필요로** 할 수 있음
- 예: Gradle은 Java 11로 실행되지만, `sourceCompatibility = JavaVersion.VERSION_17`으로 프로젝트를 Java 17로 빌드

##### 왜 이런 구성이 필요할까?
- **Gradle 플러그인이나 빌드 도구가 Java 11까지밖에 지원하지 않을 때**
- **회사에서 Gradle 실행 환경은 Java 11, 프로젝트는 Java 17 이상을 요구**하는 경우
- Gradle 자체는 JDK 11로 문제없이 작동하면서, 프로젝트는 최신 Java 기능을 활용 가능
