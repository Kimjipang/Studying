

### TCP(Transmission Control Protocol) - 전송 제어 프로토콜

<img width="400" alt="스크린샷 2022-10-12 오후 2 50 24" src="https://user-images.githubusercontent.com/91196025/195848470-88aea3fa-ad15-4aec-8d17-2f1192c57fe2.png">


- 특징 : 

  - 연결지향 - TCP 3 Way handshake

    - 출발지와 목적지를 연결하고 메세지(데이터)를 전송 

      -> 목적지 서버가 꺼져있는 곳에 보낼 일이 없음.

  - 데이터 전달 보증

    - 패킷이 중간에 소실되면 알 수 있음.

  - 순서 보장

  - 신뢰할 수 있는 프로토콜

    -> 대부분 애플리케이션에서 TCP 사용하는 이유!

> 연결지향

<img width="400" alt="스크린샷 2022-10-07 오후 4 52 57" src="https://user-images.githubusercontent.com/91196025/195848611-e3ccc099-1ee2-4834-8cdd-66629bc4ae31.png">

1. 클라이언트에서 서버로 SYN(연결 요청)을 보냄.
2. ACK(요청 수락) 메세지와 함께 클라이언트에서 서버로 SYN(연결 요청)을 보냄.
3. 서버로부터 받은 SYN에 대한 ACK을 보내는데, (4). 데이터를 함께 전송하기도 함.

> 데이터 전달 보증

<img width="400" alt="스크린샷 2022-10-12 오후 3 28 52" src="https://user-images.githubusercontent.com/91196025/195848693-e808d3a0-7ceb-4efb-9b7f-140611787cc5.png">

- 받은 쪽(서버)에서 보낸 쪽(클라이언트)으로 데이터를 받았다는 메세지를 전송해줌. 

  -> 서버에서 아무 응답이 없다면 전달 과정에서 문제가 생긴 것!

> 순서 보장

<img width="1144" alt="스크린샷 2022-10-12 오후 3 37 01" src="https://user-images.githubusercontent.com/91196025/195848772-55ddb17c-27d9-478c-b8e1-b8f0d2e5a538.png">


- 패킷 1, 2, 3 순으로 보낸다고 가정. 

- 1, 3, 2 순으로 왔을 때, 2부터 다시 보내게끔 함.

  ```markdown
  > TCP는 신뢰할 수 있는 프로토콜이다.
  ```

  

### UDP(User Datagram Protocol) - 사용자 데이터그램 프로토콜

- 기능이 거의 없음.

- 데이터 전달 및 순서가 보장되지 않음.

  -> 대신, 단순하고 속도가 빠르다.

  ```markdown
  > IP와 거의 유사
  > IP에서 PORT 와 체크섬 정도 추가되었음.
  	> PORT란 하나의 IP에서 (A,B)2개의 애플리케이션을 사용한다고 했을 때, A에 대한 정보(패킷)인지를 구별해주는 역할
  	> 체크섬이란 받은 정보에 대한 것이 정확한지 검증해주는 역할
  	
  	// 요즘 UDP가 각광받고 있다고 함.
  ```



### PORT

<img width="400" alt="스크린샷 2022-10-12 오후 4 21 48" src="https://user-images.githubusercontent.com/91196025/195848881-8484909b-5342-47b6-aa50-bc777294c808.png">


- 같은 IP에 여러 프로세스를 실행하고자 할 때 그들을 서로 구분하기 위한 역할로 쓰임.

