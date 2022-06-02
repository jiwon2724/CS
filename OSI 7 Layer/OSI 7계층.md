## OSI 7계층
<img src = "https://tails5555.github.io/assets/img/post/network/osi_structure.png"/><br>


### 1. 물리 계층(Physical Layer)<br>
0과 1의 나열을 아날로그 신호로 바꾸어 흘려 보내고(encoding), 아날로그 신호가 들어오면 0과 1의 나열로 해석하여(decoding)<br>
물리적으로 연결된 두 대의 컴퓨터가 0과 1의 나열을 주고받을 수 있게 해주는 모듈(modue)<br>

<img src = "https://velog.velcdn.com/images%2Fjewon119%2Fpost%2F1271343a-c45d-4241-a13d-c2b636c0c8df%2Fmuly.png"/><br>

`물리 계층의 기술은 어디에 구현되어 있을까?`<br>
1계층 모듈은 하드웨어적으로 구현되어 있다. (PHY 칩이라는데.. 잘 모르겠다 -_-) 하드웨어도 input을 받아서 output을 만들어내는 건 같다!<br>

### 2. 데이터 링크 계층(Data Link Layer)
여러 대의 컴퓨터가 통신하려면, 라우터로 계층구조를 이루며 연결되어 있다.<br>
송신자는 데이터의 앞 뒤에 특정한 비트열을 붙인다. 이렇게 해서 여러 발송지로 부터 전달받은 데이터를 잘 끊어 읽을 수 있게된다.

<img src = "https://velog.velcdn.com/images%2Fnoahshin__11%2Fpost%2F678c7b38-d95c-44a5-b710-1bfa6d11d335%2Fimage.png"/><br>

`그래서 결국 Data-link Layer란?`<br>
같은 네트워크(스위치로 연결된)에 있는 여러 대의 컴퓨터들이 데이터를 주고받기 위해서 필요한 모듈이다.<br>
Framing(데이터 앞 뒤에 특정 비트열을 붙여 원본데이터를 감싼 것)은 Data-link Layer에 속하는 작업들 중 하나이다.<br>

<img src = "https://velog.velcdn.com/images%2Fnoahshin__11%2Fpost%2F54d08101-a2d6-4a1d-b44d-ae5b5e7bd912%2Fimage.png"/><br>

`Data-link Layer 기술은 어디에 구현되어 있을까?`
2계층 모듈도 1계층 모듈처럼 하드웨어적을 구현되어 있다.(랜카드)<br>


### 3. 네트워크 계층(Network Layer)<br>
더 많은 컴퓨터들 사이의 통신<br>

<img src = "https://velog.velcdn.com/images%2Fnoahshin__11%2Fpost%2F0521b218-d887-49b5-9bef-02eb97bf947f%2Fimage.png"/><br>
A는 B에게 데이터를 보내고 싶으면 데이터 앞에 목적지 주소(B의 주소)를 붙인다. 보내는 컴퓨터는 상대방의 IP주소를 알고있어야 전송이 가능하다.<br>
다시 돌아와서, A는 (가)라우터에게 데이터(패킷)을 보낸다. `패킷이란?` 컴퓨터간에 데이터를 주고받을 때, 네트워크를 통해 전송되는 데이터 조각이다.<br>
(가)라우터가 패킷을 받으면 패킷을 열어서 목적지 IP주소를 확인 후, 연결된 IP주소가 없을경우 연결된 다음 라우터(마)로 보낸다. 이 작업을 반복한다.<br>

`그래서 결국 NetWork Layer란?`<br>
수많은 네트워크들의 연결로 이루어지는 inter-network 속에서 어딘가에 있는 목적지 컴퓨터로 데이터를 전송하기 위해, IP주소를 이용해서 길을 찾고(routing)<br>
자신 다음의 라우터에게 데이터를 넘겨주는 것(forwarding)

<img src = "https://velog.velcdn.com/images%2Fnoahshin__11%2Fpost%2F220307b7-9076-47dc-8d57-70d1b102977a%2Fimage.png"/><br>

`Network Layer 기술은 어디에 구현되어 있을까?`<br>
운영체제 커널에 소프트웨어 적으로 구현되어 있다.<br>

## 4. 전송 계층(Transport Layer)
이제 인터넷 상의 모든 컴퓨터가 서로와 통신할 수 있게 되었다!<br>
데이터를 받는 수신자는 전 세계 컴퓨터로부터 데이터를 받을 것이다. 예를들어 3개의 메세지를 받았다고 가정하고, 해당 컴퓨터는 여러개의 프로그램들이 실행되고 있다.<br>
컴퓨터는 3개의 메세지를 프로세스(실행중인 프로그램)들에게 나누어 주려고 한다. 어떤 데이터를 무슨 프로세스에게 줘야할 지 컴퓨터는 어떻게 알 수 있을까?<br>
우선, 데이터를 받고자 하는 프로세스들은 포트번호 라는 것을 가져야 한다. `포트번호란?` 하나의 컴퓨터에서 동시에 실행되고 있는 프로세스들이 서로 겹치지 않게 가져야하는 정수 값.<br>

송신자는 데이터를 보낼 때 데이터를 받을 수신자 컴퓨터에 있는 프로세스의 포트 번호를 붙여서 보낸다.<br>
<img src = "https://velog.velcdn.com/images%2Fnoahshin__11%2Fpost%2F97c8c3c7-a424-4899-b05d-0d6548c0fca5%2Fimage.png"/><br>
우리가 검색창에 www.naver.com 을 입력하는 것은 사실은 뒤에 wwww.naver.com:80 << 80이 생략된 것이다. 우리는 네이버의 포트번호도 알고있는 셈이다.<br>

`그래서 결국 Transport Layer란?`<br>
port 번호를 사용하여 도착지 컴퓨터의 최종 도착지인 프로세스에 까지 데이터가 도달하게 하는 모듈이다.<br>
<img src = "https://velog.velcdn.com/images%2Fnoahshin__11%2Fpost%2F13aa2ad4-070a-4b45-87e9-224d7c2be92f%2Fimage.png"/><br>

`Transport Layer 기술은 어디에 구현되어 있을까?`<br>
운영체제 커널에 소프트웨어 적으로 구현되어 있다.<br>

## 5. 어플리케이션 계층(Application Layer)
사실 현대의 인터넷은 OSI 모델이 아니라 TCP/IP 모델을 따르고 있다. TCP/IP 모델도 OSI 모델과 마찬가지로 네트워크 시스템에 대한 모델이다.<br>
<img src = "https://velog.velcdn.com/images%2Fnoahshin__11%2Fpost%2Fa63fae14-3a89-4344-97d8-1cfb0c4fa71c%2Fimage.png"/><br>
어플리케이션이라 함은 현재 우리가 사용하고 있는 서비스를 가르킨다. 이메일, 웹, 텍스트 메시지, 유튜브, 넷플릭스등 우리로부터 떼어낼 수 없는 것들을 말한다.<br>
이러한 서비스들을 제공하는 계층을 어플리케이션 레이어라고 한다.<br>

<img src = "https://velog.velcdn.com/images%2Fnoahshin__11%2Fpost%2F67b275c1-3aca-4a4b-8bf0-693518ee2725%2Fimage.png"/><br>

위 그림은 1~7계층(TCP/IP 모델로는 1~5)의 과정을 HTTP 인코딩과 디코딩의 과정이다.<br>

네트워크 시스템은 하나의 커다란  소프트웨어라고 할 수 있다.<br>

OSI 7 Layer 모델은 거대한 네트워크 스프트웨어의 구조를 설명하는 것이다.<br><br>

출저 : https://www.youtube.com/watch?v=1pfTxp25MA8


