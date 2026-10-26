# [Spring] Flow 요청-응답 사이클

> 작성일: 2025-06-21 · 태그: 프레임워크/스프링, 심화

스프링부트의 기본적인 흐름은 아래와 같이 흘러간다.


##### 스프링 MVC 전체 요청 처리 흐름 (with spring boot)

```less
1. 웹 브라우저
        ↓ (HTTP 요청)
2. 내장 톰캣 (Tomcat)
        ↓
3. DispatcherServlet (Front Controller)
        ↓
4. HandlerMapping (어떤 Controller를 호출할지 결정)
        ↓
5. Controller (@RestController / @Controller)
        ↓
6. 비즈니스 로직 호출 (Service, Repository 등)
        ↓
7. Model & View 반환
        ↓
8. ViewResolver (View 이름 → View 객체로 변환)
        ↓
9. View (JSP, Thymeleaf 등 렌더링)
        ↓
10. DispatcherServlet
        ↓
11. 톰캣
        ↓
12. 웹 브라우저 응답 (HTML or JSON)
```

##### 각 단계별 특징
```less
3. DispatcherServlet 
	: 스프링 MVC의 중앙 관제탑, 모든 요청과 응답의 흐름을 제어
4. HandlerMapping 
	: 요청 URL에 맞는 컨트롤러를 찾아줌 (`@RequestMapping`, `@GetMapping` 등 기반)
5. @Controller or @RestController 
	: 요청 처리 메소드 실행
6. Service, Repository 
	: 비즈니스 로직, DB 처리 등 대부분의 로직이 여기에 위치
7. ModelAndView 또는 객체(JSON 등) 
	: View 렌더링용 데이터 or API 응답
8. ViewResolver 
	: 논리적 이름 `home` -> 실제 뷰 파일 `/templates/home.html` 등으로 변환
9. View 
	: HTML렌더링 or JSON 직렬화, Thymeleaf, JSP, Mustache, JSON 등
10. 응답 바인딩 
	: 최종 응답 데이터를 바이트로 만들어 HTTP 응답 바디에 사용.
```

##### 추가 개념
```less
1. RestController vs Controller
 : @RestController는 JSON반환, @Controller는 View렌더링
2. Filter, Interceptor
 : 요청 전/후 가로채기 (로그인 체크, 로깅 등)
3. ExceptionHandler
 : @ControllerAdvice로 예외 처리 전담
4. HttpMessageConverter
 : 객체 ↔ JSON/XML 자동 변환
5. Content Negotiation
 : 브라우저가 HTML, 모바일은 JSON 받을 때 자동 변환
6. ViewResolver 종류
 : Thymeleaf, JSP, Mustache 등. Spring Boot는 기본적으로 Thymeleaf 제공
 7. 어노테이션 흐름
  : @RequestMapping, @PathVariable, @RequestParam, @RequestBody 등 매핑 방식
```
