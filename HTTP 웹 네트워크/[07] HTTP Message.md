### HTTP 메시지

> HTTP 메시지 구조

<img width="400" alt="스크린샷 2022-10-18 오전 12 13 30" src="https://user-images.githubusercontent.com/91196025/196375249-0b775ad8-afdf-4f0f-a38b-e02139ea0f5e.png">



> Start-line (시작 라인)

```markdown
request-line(요청 메시지) 혹은 status-line(응답 메시지)으로 구성
```

- request-line(요청 메시지)

<img width="400" alt="스크린샷 2022-10-18 오전 11 55 47" src="https://user-images.githubusercontent.com/91196025/196375380-13ad928f-cce7-450f-a688-fb4abadc4f1a.png">

```markdown
request-line = method SP(공백) request-target SP HTTP-version CRLF(엔터/공백라인)
```

- method : GET
  - HTTP 메서드 : 서버가 수행해야 할 동작을 지정하는 것
    - 종류 : GET, POST, PUT, DELETE
- request-target : /search?q=hello&hl=ko
  - 절대경로 : "/"로 시작하는 경로
- HTTP-version : HTTP/1.1



- status-line(응답 메시지)

```markdown
status-line = HTTP-version SP status-code SP reason-phrase CRLF
```

<img width="400" alt="스크린샷 2022-10-18 오후 2 29 17" src="https://user-images.githubusercontent.com/91196025/196375516-1f79f8f0-7854-49e5-92fd-c25db275970c.png">

- HTTP-version : HTTP/1.1
- status-code : 요청 성공, 실패를 나타냄
  - 200 : 성공
  - 400 : 클라이언트 요청 오류
  - 500 : 서버 내부 오류
- reason-phrase(이유 문구) : 사람이 이해할 수 있는 짧은 상태 코드 설명 글



> HTTP Header

- HTTP 전송에 필요한 모든 부가정보



> HTTP Message Body

- 실제 전송할 데이터
- HTML 문서, 이미지, 영상, JSON 등 byte로 표현 가능한 모든 데이터 전송 가능
