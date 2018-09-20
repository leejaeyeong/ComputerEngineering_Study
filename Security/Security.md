# Security

## 1. Cookie
Cookie란 인터넷을 통해 웹  사이트에 방문했을 때 Client에 저장되는 기록 정보 파일이다. Cookie는 사용자가 웹 사이트를 방문할 때마다 읽히고 수시로 새로운 정보로 변경된다.  
- **Sever와 Client 간 Cookie의 흐름**  
Client가 HTTP Request를 하면 Sever는 Cookie 정보를 바탕으로 Client에게 Response를 해준다. Client가 새로운 Request를 보낼 경우 새로운 Cookie 정보와 함꼐 Server에 전송한다.

- **Cookie의 종류**  
 - Session Cookie : 메모리에 저장되며 Browser 종료 시 삭제되는 Cookie
 - Persistent Cookie : Browser의 종료와 관계없이 장기간 유지되는 Cookie
 - Secure Cookie : 암호화 된 Cookie를 말하며 HTTPS에서만 사용한다.   
 - Third-Party Cookie : 방문한 도메인과 광고 배너 등을 관리할때 경로를 추적하귀 위해 사용하는 Cookie

- **Cookie의 특징**
  1. HTTP Request 시 Cookie에 대한 정보를 매 Header에 추가하여 보내기 때문에 추가 트래픽을 발생시킨다.
  2. Cookie가 유출되면 보안에 치명적인 문제가 발생할 수 있다.  

## 2. Session
Session이란 Client로 부터 Request를 받아 이것을 일정하 유지하는 기술이다. Cookie와는 다르게 서버에 저장되기 때문에 사용자 정보가 노출되지 않는다.

- **Session의 원리**
 - 각 Client마다 Server에서 ID 생성하고 관리한다.
 - Server에서는 Client의 Cookie를 이용해 Session ID에 저장한다.
 - Client는 다시 Request를 할 경우 Cookie를 이용하여 Session ID에 값을 전달한다.  


- **Session의 장점**
 - 각 Client에게 고유 ID를 부여하고 Sever에 저장하기 때문에 Cookie 보다 보안성이 우수하다.  
 - Session ID로 Client를 구분하여 요구에 맞는 Service를 제공할 수 있다.   


- **Session의 단점**
 - Server에 저장되기 때문에 그만큼의 부하와 저장 공간을 필요로한다.  


- **Sever와 Client 동작**    
 - Client가 Server에 접속을 시도하면 Sever는 Client의 Request Header를 확인해 Session ID를 보냈는지 확인한다. 만약 Session ID가 없다면 Sever는 Client의 Session ID를 생성하고 Cookie를 저장한다. 그리고 Client에게 보내는 Response Header에 Session ID에 관한 항목을 추가한다.
