# Network

## 1. what is a network?
- 네트워크는 다양한 정보통신 자원이 연결되어 일을 수행 데에 있어서 상호 정보교환을 수행 할 수 있게 해주는 연결 형태를 말한다.

## 2. LAN / WAN
- **LAN (Local Area Network)**  
논리적으로 가까운 거리에 위치한 네트워크 집합을 의미한다.
- **WAN (Wide Area Network)**  
최소 2개 이상의 LAN이 모여 이루는 넓은 범위의 네트워크 집합을 의미한다.

## 3. Protocol
 - 프로토콜이란 네트워크상에 있는 장비 사이에서 정확한 데이터의 송신과 수신을 위해 마련된 규칙들을 말한다.

## 4. TCP/IP
- TCP/IP는 Network Protocol의 한 종류로 Network 접속을 위한 통신 규약이라고 할 수 있다. TCP/IP는 TCP라는 Protocol과 IP라는 Protocol을 합쳐서 사용하는 것을 의미한다. IP는 192.168.114.0과 같은 주소 체계를 가지고 있고 TCP는 신뢰성 높은 데이터 송수신을 제공한다는 특징을 갖고 있다. Network에서 Network divice들이 상호 연결되기 위해서는 TCP/IP Protocol 토콜을 필수적으로 준수해야 한다.

## 5. OSI Layer 7
- OSI 7계층은 시스템의 동작을 계층을 활용하여 나타낸 것이다. OSI 7 계층을 활용하여 문제가 발생했을 때 각 단계별로 파악하여 물리적인 문제인지 응용프로그램과 관련이 있는 문제인지 등을 쉽게 파악할 수 있다.

- 7계층 – 응용 계층(Application):
응용 계층은 사용자와 가장 가까운 계층이다. 사용자가 이용하는 응용프로그램이 응용 계층에 해당된다고 할 수 있다. 대표적으로 구글 크롬(Google Chrome), 사파리(Safari), 스카이프(Skype) 등이 있다.

- 6계층 – 표현 계층(Presentation):
표현 계층은 네트워크 형식을 응용프로그램 형식으로 변환하거나 응용프로그램을 네트워크 형식으로 변환하는 계층이다. 대표적으로 데이터를 암호화, 복호화하는 과정이 표현 계층에서 이루어 진다.

- 5계층 – 세션 계층(Session):
세션 계층에서는 인증 및 서비스 계층이라고 할 수 있다. 응용 프로그램과의 연결을 담당한다.

- 4계층 – 전송 계층(Transport):
전송 계층에서는 Host간의 데이터 전송 조율을 담당한다. 데이터를 전송할 때 용량, 속도, 목적지 등을 처리한다. 대표적으로 TCP/IP Protocol이 있다.  
- 3계층 – 네트워크 계층(Network):
라우터 기능 대부분이 네트워크 계층에 자리잡는다. 가장 기본적으로 볼 때 이 계층은 다른 여러 라우터를 통한 라우팅을 비롯한 패킷 전달을 담당한다.

- 2계층 – 데이터 링크 계층(Data Link):
데이터 링크 계층은 연결된 노드 간의 데이터 전송을 제공하며 물리 계층의 오류 수정도 처리한다.
- 1계층 – 물리 계층(Physical)
물리 계층은 시스템의 물리적 표현을 나타낸다. 유선으로 연결된 케이블의 종류, 무선 주파수, 핀 배치 등 물리 요건에 대해 다룬다.

## 6. Server & Client

- Server와 Client는 Network에서 제공되는 서비스를 기준으로 서비스를 요청하는 Host가 Client, 서비를 제공하는 Host가 Server이다. 여기서 Host란 컴퓨팅 기능이 있는 시스템을 말한다.

- Server는 서비스를 주고받는 호스트들의 관계에서 특정 서비스를 제공하는 시스템이다. 일반적으로 서버는 클라이언트보다 먼저 실행 상태가 되어 클라이언트의 요청에 대기해야 한다. 클라이언트의 요청이 있을 때마다 서비스를 반복해서 제공해야 한다.

- Client는 서비스를 요청하는 시스템이다. 호스트는 다양한 서비스를 서로 주고받기 때문에 임의의 호스트가 클라이언트나 서버로 고정되지는 않는다. 이용하는 서비스의 종류에 따라서 클라이언트가 될 수도 있고, 서버가 될 수도 있다. 그러므로 특정 서비스를 기준으로 클라이언트와 서버라는 상대적 용어로 구분한다.

## 7. Synchronous/Asynchronous
- System에서 Data를 처리할 때 동기적으로 처리하는 방식과 비동기적으로 처리하는 방식이 있다. 1만 명의 Client에게 이메일을 보내는 시스템을 동기적, 비동기적으로 처리한다고 예를들을 경우 동기적인 처리방식은 1명 부터 10,000명에게 순차적으로 모두 이메일을 전송하는 방식이다. 동기적인 처리 방식의 경우 10,000에게 모두 이메일을 보낼 때 까지 다른 작업은 수행하지 못한다. 반대로 비동기적으로 Data를 처리하는 방식은 10,000명에게 이메일을 보내라는 명령을 받았을 때 이메일을 보내는 별도의 시스템에게 10,000명에게 이메일을 보내라는 명령을 하는 것이다.

## 8. HTTP/HTTPS
- **HTTP란?** Hypertext transfer protocol의 약자로 인터넷에서 사용하는 웹 서버와 인터넷 웹 브라우저(Client) 사이에 문서 전송을 위한 통신 규약이다.

- **HTTPS란?** 기존에 HTTP에서 보안성이 강화된 프로토콜이다. HTTPS의 S는 secure socket을 의미한다.

- **HTTPS 암호화**


## 9. Request / Response
- HTTP Request는 Client에서 보낸 요청 내용이 저장되어 있고 HTTP Response는 Sever에서 보낸 응답 내용이 저장되어 있다. 또한 Request와 Response는 Head와 Body로 구분되고 Head와 Body는 빈 공백 한 줄로 구분된다. Header에는 요청주소 버전정보 요청 도메인 요청 페이지와 관련된 정보와 시간들, body에는 사용자가 입력했던 내용이 들어간다.
- **Response** 또한 Request오 마찬가지로 Head와 Body로 구분되는데 Head에는 프로토콜 버전 및 응답코드, 웹 서버 배너 정보, HTTP Body 사이즈 등이 포함되고 Body에는 Client가 요청한 웹 브라우저의 HTML태그 등의 기타 정보들이 포함된다.

- **Request의 형식**  
```
Request-Line
*(( general-header | request-header | entity-header ) CRLF)
CRLF
[ message-body ]
```
첫 줄에는 Request-Line이 오고 이어서 여러 종류의 헤더가 나온다. 줄바꿈을 두번 한 후에는 Body가 오게된다. Request method는 8가지는 다음과 같다.
 - OPTIONS : 요청 URI에서 사용할 수 있는 Method를 물어본다.  

 - GET : 요청 URI의 정보를 가져온다.  

 - HEAD : GET 요청에서 body는 제외하고 헤더만 가져온다.  

 - POST : 요청 URI의 리소스의 새로운 정보를 보낸다.  

 - PUT : 요청 URI에 저장될 정보를 보낸다.   

 - DELETE : 요청 URI의 리소스를 삭제한다.  

 - TRACE : 보낸 메시지를 다시 돌려보낸다.  

 - CONNECT : 프록시에 사용하기 위해 예약된 Method이다  

- **Response의 형식**
```
Status-Line
*(( general-header | response-header | entity-header ) CRLF)
CRLF
[ message-body ]
```
Response의 형식은 첫줄이 Statuse-Line인 것과 request header 대신 response header가 들어간 것 빼고는 Request의 형식과 동일하다. Response의 상태를 나타내는 코드는 다음과 같다.
 - 1xx : 정보성   

 - 2xx : 성공   

 - 3xx : 리다이렉트   

 - 4xx : 클라이언트 오류  

 - 5xx : 서버 오류

## 10. Header
- Header란 Network에서 data를 송수신할 때 부가적인 data들을 의미한다. 예를들어 data를 전송할 때는 보내려는 data 뿐만 아니라 받는 주소, 오류 검사, data의 종류, protocol의 종류 등을 다 확인해야한다. Header는 이러한 정보들을 가지고 있다. HTTP의 경우 General, Request, Response, Entity의 header가 있다.
 -  General - 클라이언트, 서버 또는 HTTP와 관계된 정보

 -  Request - 문서 양식과 서버의 매개 변수들

 -  Response - 응답을 보내는 서버에 대한 정보

 -  Entitiy - 클라이언트와 서버 사이에 전송되는 데이터에 대한 정보
