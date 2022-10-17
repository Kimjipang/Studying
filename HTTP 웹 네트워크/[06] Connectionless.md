### Connectionless(비 연결성)

<img width="400" alt="스크린샷 2022-10-14 오후 11 06 10" src="https://user-images.githubusercontent.com/91196025/196191096-1e7ea91c-64bb-4ae3-a4da-118a773af4db.png">

- 클라이언트와 서버가 연결을 유지하면 둘 사이에 통신이 오가지 않아도 연결을 하고 있음.

  -> 연결을 유지하고 있는 모델의 수가 많다고 하면 서버 자원 소모가 큼.

  

<img width="400" alt="스크린샷 2022-10-14 오후 11 09 57" src="https://user-images.githubusercontent.com/91196025/196191150-64d0247d-7d1a-4c9f-a321-954bdcdcbad7.png">


- 연결을 유지하지 않는 경우에는 서버 자원 소모가 비교적 크지 않음.

  -> 최소한의 자원으로 서버를 유지할 수 있음.



```markdown
					=========== 비 연결성의 장점 ===========
- 웹 브라우저에서 사용되는 HTTP는 기본적으로 연결을 유지하지 않는 Connectionless한 모델임.
- 많은 사람들이 서비스를 동시에 이용하더라도 실제 서버에서 동시에 처리하는 요청은 수십개 이하로 매우 작다고 함.

	-> 이러한 이유들로 인해 서버 자원을 매우 효율적으로 사용할 수 있음.
	
					=========== 비 연결성의 한계점 ===========
- 연결을 유지하지 않기 때문에 TCP/IP 연결을 새로 맺어야 함
	-> 3 Way handshake 시간 추가
- 웹 브라우저로 사이트를 요청하면 HTML뿐만 아니라, JS, CSS, 이미지 등 많은 자원이 함께 다운로드

	-> 이러한 한계점은 HTTP 지속 연결(Persistent Connections)로 해결함. 현재는 HTTP/2, HTTP/3에서 더 많은 최적화가 이루어진 상태라고 함.
```





> HTTP 초기 - 과거

<img width="400" alt="스크린샷 2022-10-17 오후 10 18 34" src="https://user-images.githubusercontent.com/91196025/196191201-37bb93b1-3f08-46c5-ace6-c0b35d719ff8.png">

- 하나의 요청을 할 때마다 3-way handshake를 통해 연결하고 응답 받으면 연결을 끊었음. 





> HTTP 지속 연결(Persistent Connections) - 현재

<img width="400" alt="스크린샷 2022-10-17 오후 10 20 23" src="https://user-images.githubusercontent.com/91196025/196191221-c22a191e-c935-4c0e-a965-99517aafab9b.png">

- 필요한 모든 자원을 다 응답 받고 난 후 연결을 종료하게끔 하여 속도를 최적화 함.

