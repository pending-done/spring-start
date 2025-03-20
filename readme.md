# 리드미 목차

- [프로젝트 초기 오류 해결](#프로젝트-초기-오류-해결)
- [컨트롤러](#컨트롤러)
- [스프링 폴더 간단 설명](#스프링-폴더-간단-설명)


# 프로젝트 초기 오류 해결

**3.X 이후 버전에서 자바 17버전 이상 설치해야함**

- 인텔리제이 전용 자바 17버전 설치
- Setting -> Build Tools -> Gradle 설정  
- 참고링크: https://jojoldu.tistory.com/698


**앱 실행후 바로 종료**

앱 실행해도 `localhost:8080` 서비스 안열리고 
`Process finished with exit code 0` 메세지 이후 종료되는 문제

의존성 추가
```gradle
dependencies {
    /* 다른 의존성들 */
    implementation 'org.springframework.boot:spring-boot-starter-web'
}
```

- 참고링크: https://hoehen-flug.tistory.com/40

--- 

# 컨트롤러

클라이언트와 연결되는 무언가. 
대충 클라이언트가 url에 주소를 입력하면 해당 주소에 맞는 html을 매핑시켜준다거나, 데이터를 연결시켜준다거나 하는 역할


### 컨트롤러 정의
```java
@Controller
public class HelloController {
    
}
```

- 프로젝트에 `controller` 패키지를 생성한다. (ex: hello.core.controller)
- class를 생성한다.
- class 정의부 바로 위에 `@Controller` 어노테이션을 붙여준다.

### 컨트롤러와 html 매핑
```java
@Controller
public class HelloController {
    
    @GetMapping("hello")
    public String hello(Model model){
        model.addAttribute("data","hello");
        return "hello";
    }
}
```
- `@GetMapping`을 이용해 url을 매핑시켜준다. 
  - `@GetMapping("hello")`: localhost:8080/hello 을 주소창에 입력하면 해당 메소드로 연결됨


- 매핑된 메서드는 `Model` 타입의 매개변수를 받음 (규칙같은거임)
- `model.addAttribute`를 이용해 인자를 넘겨줄 수 있음
  - 인자1: html에서 사용할 변수명
  - 인자2: 그 변수의 값
  - 위 예시를 보면 data라는 이름의 변수에 "hello" 값을 전달한거임


- `return`문에 html 파일명을 작성함 (`.html` 제외)
  - ex: `return "hello";`는 hello.html을 매핑

### hello.html
```html
<html xmlns:th="http://www.thymeleaf.org">
    <head>
    <!-- 생략 -->
    </head>
    <body>
        <p th:text="'안녕하세요' + ${data}">안녕하세요</p>
    </body>
</html>
```

- 컨트롤러한테 받은 `data` 변수를 저런식으로 사용함 (`${data}`)
- `<p th=text=어쩌구 ..` : 타임리프 문법임

---

# 스프링 폴더 간단 설명

## resources
뭔가 자원같은거 들어감, 이미지, html 등 ?

### resources/static
- 정적 자원 들어감 (`index.html`) 
- 프로그래밍 X

### resources/templates
- 타임리프 기반 `html`들 들어감
- 프로그래밍 O 




