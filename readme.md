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
