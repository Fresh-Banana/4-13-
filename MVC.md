# MVC란?
`MVC의 정의:`애플리케이션(앱)개발을 영역을 나누어 효과적으로 하는 방식
    * 각 영역이 하는 역할을 나눈다
* `M`-> Model(모델)
* `V`-> View(뷰)
* `C`-> controller(컨트롤러)
## M
```java
model.addAttribute("data", "안녕하세요");
```
* 클라이언트(프론트의 웹,URL)의 응답으로 돌려주는 **데이터**를 **model**이라고 한다
## view
```java
<p th:text="'안녕하세요 ' + ${data}">안녕하세요 손님</p>
```
* mode(데이터,처리결과)을 받아서 화며에 출력함
## controller
```java
@Controller
public class HelloController {

    @GetMapping("/hello")
    public String hello(Model model){
        model.addAttribute("data", "안녕하세요");
        return "hello";
    }
}
```
```java
@GetMapping("/hello")
public String hello(Model model){
    return "hello";
}
```
* Model과view를 연결하는 영역
## 핸들러란?
`핸들러의 정의:` URL(클라이언트)에 있는 요청을 **처리하는** 메서드를 핸들러라고함
```java
public String hello() // 여기부터가 진짜 핸들러
 {
    return "hello";
}
```
## 어탭터란?
`어탭터의 정의:` 선택된 핸들러(메소드)를 스프링이 실행시켜주는 내부 객체
## 동작순서
1. 핸들러(메서드) 조회
2. 핸들러의 어댑터 조회
3. 어댑터 실행
4. 핸들러 실행
    * 어탭터->핸들러를 실행
5. Modelandview 반환
    * Model(데이터)-> view로 보냄(객체를 만들어 저장하여 보냄)
6. viewResolver 호출
    * 화면으로 보여주기 위해 view 이름을 view 파일로 변환
    * return hello -> view Resolver-> hello.html
7. view 반환
    * 변환한 파일을 실행할 코드와 연결함
8. 뷰렌더링
    * 화면을 출력함
  