### HTTP 헤더 - 캐시와 조건부 요청

> 캐시가 없을 때

```markdown
- 동일한 요청을 2번 진행해도 서버로부터 응답을 받아야 함
```

- 데이터가 변경되지 않아도 계속 네트워크를 통해서 데이터를 다운로드 받아야 함.
- 인터넷 네트워크는 매우 느리고 비쌈.
- 브라우저 로딩 속도가 느림
- 느린 사용자 경험

> 캐시 적용

```markdown
- 동일한 요청을 2번 이상 진행할 때 캐시 저장소를 먼저 확인하여, 캐시에 저장되어 있는 응답이면 바로 내려줌.
	// 캐시가 유효한 시간이 있음 
		-> cache-control: max-age=60 // 60초
```

- 응답 결과 캐시에 저장

<img width="600" alt="스크린샷 2022-10-20 오후 2 46 44" src="https://user-images.githubusercontent.com/91196025/196892185-36812952-713f-457a-ad53-8dc4b67c29b8.png">

- 요청에 대한 응답을 캐시에서 조회

<img width="600" alt="스크린샷 2022-10-20 오후 2 47 56" src="https://user-images.githubusercontent.com/91196025/196892209-fb2bac64-4d37-45e9-86e1-12a501798ee0.png">

- 캐시 유효 시간이 초과되었을 때

<img width="600" alt="스크린샷 2022-10-20 오후 2 56 22" src="https://user-images.githubusercontent.com/91196025/196892230-cd72c531-c8a1-4b78-9617-d0ab600b1a10.png">

- 캐시 시간이 초과되었기 때문에 서버로부터 다시 응답을 요청하고, 받은 응답을 또 다시 캐시에 저장함.
  - 또 다시 네트워크 다운로드가 발생



### 검증 헤더와 조건부 요청

#### 캐시 시간 초과

- 캐시 유효 시간이 초과해서 서버에 다시 요청하면 두 가지 상황이 발생함.

  1. 서버에서 기존 데이터를 변경

  2. 서버에서 기존 데이터를 변경하지 않음

     ```markdown
     - 기존 데이터가 변경되었다면 새로운 응답을 받아야 하지만, 변경되지 않았다면 저장해두었던 캐시를 다시 사용할 수 있음!!
     		-> but, 클라이언트와 서버의 데이터가 동일하다는 사실을 확인할 			방법이 필요함!
     		
     	:: 이 방법이 검증 헤더와 조건부 요청임.
     ```

#### 검증 헤더

- 캐시 데이터와 서버 데이터가 같은지 검증하는 데이터
- Last-modified, ETag

> 검증 헤더 (Last-Modified) // 데이터가 마지막으로 수정된 시간

<img width="600" alt="스크린샷 2022-10-20 오후 3 14 11" src="https://user-images.githubusercontent.com/91196025/196892332-67717b3c-40ab-4f4c-9aa8-117f20c5a2f1.png">



#### 조건부 요청

- 검증 헤더로 조건에 따른 분기
- If-Modified-Since: Last-Modified 사용
- If-None-Match: ETag 사용
- 조건 만족시 200 OK | 조건 만족하지 않으면 304 Not Modified

<img width="600" alt="스크린샷 2022-10-20 오후 3 43 24" src="https://user-images.githubusercontent.com/91196025/196892525-0ffe438a-7e87-46fa-95d7-d9bc290092fe.png">

> if-modified-since // 조건부 요청(Last-Modified 와 같이 사용)

<img width="500" alt="스크린샷 2022-10-20 오후 3 15 26" src="https://user-images.githubusercontent.com/91196025/196892616-99d67fde-616d-4491-bf86-5c7065fe71c4.png">

```markdown
클라이언트와 서버의 last-modified 가 동일하면 저장해두었던 캐시를 다시 사용
```

- 캐시 유효 시간이 초과해도 서버의 데이터가 갱신되지 않으면 서버가 304 Not Modified 응답을 내림(바디는 없고 헤더만 있음)

  -> 클라이언트는 서버로부터 받은 응답 헤더 정보를 확인하고 저장해둔 캐시 정보	를 갱신해 데이터 재활용

#### Last-Modified & If-Modified-Since 단점

- 1초 미만 단위로 캐시 조정이 불가함.

- 날짜 기반의 로직 사용

- 데이터를 수정해서 날짜가 다르지만, 같은 데이터를 수정해서 데이터 결과가 동일한 경우

- 서버에서 별도의 캐시 로직을 관리하고 싶은 경우

  - ex). 스페이스나 주석처럼 크게 영향이 없는 변경에서 캐시를 유지하고 싶은 경우

    -> 이러한 단점을 보완하여 나온 것이 ETag, If-None-Match

    

> ETag, If-None-Match

- ETag(Entity Tag)
- 캐시용 데이터에 임의의 고유한 버전 이름을 달아둠
  - ex). ETag : "v1.0", ETag: "a2jiodsfdasf"
- 데이터가 변경되면 이 이름을 바꾸어서 변경(Hash를 다시 생성)
  - ex). ETag: "aaaa" -> ETag: "bbbb"
- ETag를 서버에 보내서 같으면 유지, 다르면 다시 받기!



:: **결과적으로는 네트워크 다운로드가 발생하는 것은 동일하지만 용량이 적은 헤더 정보만 응답으로 받기 때문에 매우 실용적임.**





#### 캐시 제어 헤더

> Cache-Control

**캐시 지시어(directives)**

- Cache-Control: max-age
  - 캐시 유효 시간, 초 단위
- Cache-Control: no-cache
  - 데이터는 캣해도 되지만, 항상 본(Origin) 서버에 검증하고 사용
- Cache-Control: no-store
  - 데이터에 민감한 정보가 있으므로 저장하면 안됨

> Pragma

**캐시 제어(하위 호환)**

- Pragma: no-cache
- HTTP 1.0 하위 호환

> Expires

**캐시 만료일 지정**

- expires: Mon, 01 Jan 1990 00:00:00 GMT

- 캐시 만료일을 정확한 날짜로 지정
- HTTP 1.0부터 사용
- 지금은 더 유연한 Cache-Control: max-age 권장
- Cache-Control: max-age와 함께 사용하면 Expires는 무시



#### 프록시 캐시

> 원 서버 직접 접근(Origin Server)

<img width="600" alt="스크린샷 2022-10-20 오후 4 41 15" src="https://user-images.githubusercontent.com/91196025/196892747-dc2036b0-5382-48d8-9b5b-d72ba34dde9a.png">

- 원 서버에 접근하려고 하는 모든 클라이언트는 통신하기까지 소요 시간이 500ms 걸리게 됨.

  -> 프록시 캐시라는 것을 도입

<img width="600" alt="스크린샷 2022-10-20 오후 4 49 54" src="https://user-images.githubusercontent.com/91196025/196892764-cfb0d480-b86b-4209-b597-62297e60b4a7.png">

- 원 서버에 접근하지 않고 프록시 캐시 서버에 접근하여 응답을 빠르게 받을 수 있음!

```markdown
> 단! 첫 번째 유저는 프록시 캐시 서버로부터 요청을 받을 수 없고, 두 번째 유저부터 프록시 캐시 서버로부터 응답 받을 수 있음
```



#### 캐시 무효화

> Cache-Control

**확실한 캐시 무효화 응답**

- Cache-Control : no-cache, no-store, must-revalidate
- Pragma : no-cache
  - HTTP 1.0 하위 호환
