### HTTP 헤더 - 일반 헤더

- header-field = field-name: OWS field-value OWS // (OWS : 띄어쓰기 허용)

- field-name은 대소문자 구분 안함.

  <img width="400" alt="스크린샷 2022-10-19 오후 2 56 42" src="https://user-images.githubusercontent.com/91196025/196701271-a2982ed0-795e-4238-ac82-2739d739797b.png">

> 용도

- HTTP 전송에 필요한 모든 부가정보

  ex). 메시지 바디의 내용, 메시지 바디의 크기, 압축, 인증, 등등

> 분류 - RFC2616(과거)

<img width="400" alt="스크린샷 2022-10-19 오후 2 59 55" src="https://user-images.githubusercontent.com/91196025/196701308-34889764-e886-414f-8b3f-e85cd72ea24a.png">

- General Header : 메시지 전체에 적용되는 정보 // ex). Connection : close

- Request Header : 요청 정보 // ex). User-Agent : Mozilla/5.0

- Response Hearder : 응답 정보 // ex). Server : Apache

- Entity Header : 엔티티 바디 정보 // ex). Content-Type : text/html, Content-Length : 3423

  - 엔티티 본문의 데이터를 해석할 수 있는 정보를 제공하는 것.

    ex). 데이터 유형(html, json), 데이터 길이, 압축 정보 등등

```markdown
현재는 RFC2616 폐기되고 RFC7230~7235 등장함.
```

> RFC723x

- 엔티티(Entity) -> 표현(Representation)
- Representation = representation Metadata + Representation Data
- 표현 = 표현 메타데이터 + 표현 데이터

![스크린샷 2022-10-19 오후 3 13 45](https://user-images.githubusercontent.com/91196025/196701458-76dbfbf8-f695-4d0f-82e7-b26f417b6b3c.png)

- 표현은 요청이나 응답에서 전달할 실제 데이터
- 표현 헤더는 표현 데이터를 해석할 수 있는 정보 제공
  - 데이터 유형(html, json), 데이터 길이, 압축 정보 등등



#### 표현(Representation)

- Content-Type : 표현 데이터의 형식
- Content-Encoding : 표현 데이터의 압축 방식
- Content-Language : 표현 데이터의 자연 언어
- Content-Length : 표현 데이터의 길이

```markdown
표현 헤더는 전송, 응답 둘다 사용 가능
```

> Content-Type

**표현 데이터의 형식 설명**

- 미디어 타입, 문자 인코딩

- ex).

  - text/html; charset=utf-8

  - application/json

  - image/png

    <img src="/Users/jihwankim/Desktop/Typora/스크린샷 2022-10-19 오후 6.31.32.png" alt="스크린샷 2022-10-19 오후 6.31.32" style="zoom:33%;" />

> Content-Encoding

**표현 데이터 인코딩**

- 표현 데이터를 압축하기 위해 사용

- 데이터를 전달하는 곳에서 압축 후 인코딩 헤더 추가

- 데이터를 읽는 쪽에서 인코딩 헤더의 정보로 압축 해제

- ex).

  - gzip

  - deflate

  - identity

    <img src="/Users/jihwankim/Desktop/Typora/스크린샷 2022-10-19 오후 6.34.25.png" alt="스크린샷 2022-10-19 오후 6.34.25" style="zoom:33%;" />

    

> Content-Language

**표현 데이터의 자연 언어**

- 표현 데이터의 자연 언어를 표현
- ex).
  - ko
  - en
  - en-US

> Content-Length

**표현 데이터의 길이**

- 바이트 단위
- Transfer-Encoding(전송 코딩)을 사용하면 Content-Length를 사용하면 안됨



#### 협상(Content Negotiation)

**클라이언트가 선호하는 표현 요청**

- Accept : 클라이언트가 선호하는 미디어 타입 전달
- Accept-Charset : 클라이언트가 선호하는 문자 인코딩
- Accept-Encoding : 클라이언트가 선호하는 압축 인코딩
- Accept-Language : 클라이언트가 선호하는 자연 언어



#### 전송 방식

- 단순 전송
- 압축 전송
- 분할 전송
- 범위 전송



#### 일반 정보

- From
- Referer
  - 현재 요청된 페이지의 이전 페이지 주소
  - Referer를 사용해서 유입 경로 분석 가능
- User-Agent
  - 클라이언트의 애플리케이션 정보(웹 브라우저의 정보)
- Server
- Date



#### 특별한 정보

- Host : 요청한 호스트 정보(도메인)
  - 요청에서 사용
  - 필수 헤더임
  - 하나의 서버가 여러 도메인을 처리해야 할 때
  - 하나의 IP 주소에 여러 도메인이 적용되어 있을 때 
- Location : 페이지 리다이렉션
  - 웹 브라우저는 3xx 응답의 결과에 Location 헤더가 있으면, Location 위치로 자동 이동(리다이렉트)
- Allow : 허용 가능한 HTTP 메서드
- Retry-After : 유저 에이전트가 다음 요청을 하기까지 기다려야 하는 시간



#### 인증

- Authorization : 클라이언트의 인증 정보를 서버에 전달
- WWW-Authenticate : 리소스 접근시 필요한 인증 방법 정의



#### 쿠키 

- Set-Cookie : 서버에서 클라이언트로 쿠키 전달(응답)
- Cookie : 클라이언트가 서버에서 받은 쿠키를 저장하고, HTTP 요청시 서버로 전달

![스크린샷 2022-10-19 오후 9.57.52](/Users/jihwankim/Desktop/Typora/스크린샷 2022-10-19 오후 9.57.52.png)

- 클라이언트에서 서버로 요청을 하면 서버가 클라이언트로부터 받은 정보를 Set-Cookie에 담아 클라이언트에게 다시 전달함.
- 클라이언트에는 쿠키 저장소가 있다.

![스크린샷 2022-10-19 오후 9.59.19](/Users/jihwankim/Desktop/Typora/스크린샷 2022-10-19 오후 9.59.19.png)

- 요청시 무조건 쿠키 저장소에 있는 쿠키를 꺼내 HTTP 헤더에 포함시켜 서버에 보냄.

![스크린샷 2022-10-19 오후 10.00.48](/Users/jihwankim/Desktop/Typora/스크린샷 2022-10-19 오후 10.00.48.png)

- 어떤 요청이라도 쿠키 정보를 자동으로 포함시킴.
  - 네트워크 트래픽 추가 유발
- 보안에 민감한 정보는 절대 저장하면 안됨



> 쿠키 - 생명주기(Expires, max-age)

- Set-Cookie : expires=Thu, 19-Oct-2022 22:06:16 GMT
  - 만료일이 되면 쿠키 삭제
- Set-Cookie : max-age=3600(3600초)
  - 0이나 음수를 지정하면 쿠키 삭제
- 세션 쿠키 : 만료 날짜를 생략하면 브라우저 종료시까지 유지
- 영속 쿠키 : 만료 날짜를 입력하면 해당 날짜까지 유지
