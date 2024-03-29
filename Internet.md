LAN
---

근거리 통신망이다.

Ethernet
---

현재 LAN을 구현하는 가장 일반적이고 보편적인 방법이다.
> TMI 를 뿜자면.. 네트워크에 연결된 각 단말들이 48bit MAC addr로<br>
> 데이터를 주고받는 기술이다..

Router
---

n개의 네트워크를 연결하는, 네트워크 패킷들이 오가는 지하철역 이라고 볼 수 있다.

해당 패킷의 목적지를 추출, 경로에 따라 다음 장치로 포워딩 해준다.

> 라우터는 정말 많은 기능을 하는데.. 이렇게만 정의하겠다.

GATEWAY
---

LAN 을 외부 네트워크에 연결하는 장치이다. 컴퓨터가 될수도 컴퓨터가 아닌 무언가가 될 수도 있다.

넓은 의미로는 이종의 네트워크 통로의 역할이다.

공항같은 개념인데, A 네트워크에서 B네트워크로 이동하려면 B네트워크의 GATEWAY를 꼭 거쳐야만 한다.

> 물론 A네트워크의 GATEWAY를 통해 나가겠지만 .. 

이 GATEWAY는 서로 다른 네트워크 상의 PROTOCOL을 적절하게 변환시켜 준다.

그래서 전송방식이 달라도 접속을 가능하게 도와준다.

WAP (Wireless Access Point)
---

무선 엑세스 포인트란

무선장치를 유선장치에 연결할 수 있게 하는 장치이다.

일반적으로 이 포인트는 유선망 라우터에 연결되며,

무선장치와 네트워크 상의 다른장치간 데이터를 중계한다.

이놈이 없다면 와이파이고 뭐고 없다고 볼 수 있다.

Internet
---

전세계 컴퓨터가 연결되어 TCP/IP 프로토콜을 이용하여 정보를 주고받는 공개 컴퓨터 통신망

Protocol
---

서로 다른 이기종의 컴퓨터 사이에 어떤 자료를, 어떤방식으로, 언제 주고받을지 정해놓은 규약!

> 간단하게 말하면 통신을 하기 위한 규약!

TCP/IP
---

IP (internet Protocol)

 - 호스트의 주소지정과 패킷 분할 및 조립 기능에 대한 규약
 - 인터넷 상의 각 컴퓨터는 자신의 IP주소를 갖는다.
 - IP주소는 네트워크 장치들이 서로를 인식하고 통신을 하기위해 사용한다.

TCP (Transport Control Protocol)
 
  - IP위에서 동작하는 프로토콜
  - 데이터의 전달을 보증하고, 보낸 순서대로 받게 해준다.
  
HostName & IP
---

인터넷에 연결된 컴퓨터에게 부여되는 고유한 이름이다.

호스트명은 도메인 네임으로, 사람이 읽고 이해 할 수 있는 이름

~~~
$ hostname 
~~~
> 사용중인 시스템의 호스트 네임을 출력한다.

~~~
$ ip addr
~~~
> 사용 중인 시스템의 IP주소를 출력한다.<br>
> inet에 명시된 번호가 ip주소이다.<br>
> 여담으로 1번은 루프백일 확률이 크다 1: 옆에 lo라고 적혀있는 inet은 무시하자...

DNS Service
---

인터넷 상의 각 컴퓨터는 hostname 과 ip addr을 갖고 있다.

hostname 은 사용자가 주로 사용하는 이름, ip addr은 실제 통신에서 사용되는 주소이다.

ip addr은 사람이 외우기 어렵고, 일관성도 없으므로, 

hostname을 ip주소로 변환해주는 service를 domain name system 이라고 부른다.

~~~
$ nslookup 호스트명
~~~

지정 hostname 의 ip주소를 읽어온다.

ex > nslookup www.naver.com

User Info
---

~~~
$ finger [user name]
~~~

> 사용자의 로그인 정보, 언제 어디서 했는지도 다나왕!

Send Message
===

write
---

~~~
$ write 사용자명 [단말기명]
~~~
> 단말기명이란 tty를 의미함...

wall
---

~~~
$ wall [말,파일]
~~~
> write all 의 준말

모두에게 공지를 때려버린다.

wall 명령은 일반사용자는 사용할 수 없다.

super user처럼 tty그룹에 속해있는 사용자만 가능하다.

mesg
---

~~~
$ mesg [y|n]
~~~
> 메세지 수신을 허용하거나 거절한다.

그냥 mesg 만 치면 현재 메세지 수신 여부를 출력한다.

파일 전송
===

ftp
---

ftp는 File Transfer Protocol 의 약자이다

파일을 전송하는 프로토콜이다.

Server - Client 사이의 파일 전송을 위한 서비스를 제공한다.

~~~
$ ftp -n [hostname]
$ sftp -n [hostname]
~~~
> hostname 으로 지정된 FTP 서버에 접속하여, 파일을 업로드 혹은 다운로드 한다.<br>
> 요즘은 github에 자료가 훨씬 많아서 wget을 쓰는게 더 ..

원격 접속
===

RDP
---

Remode Desktop Protocol 

원격 데스크톱 연결 프로토콜이다.

연결을 직접 해보도록 하자.

~~~
$ apt install xrdp
~~~

나는 ubuntu 를 사용하고 있으므로, yum을 사용하지 않는다.


~~~
$ systemctl enable xrdp.service
~~~

부팅시 xrdp 서비스가 자동으로 실행되도록 설정한다.

윈도우의 서비스 프로그램과 비슷한 맥락이다.

![](./img/firewall.JPG)

요렇게 방화벽도 열어주자

~~~
$ systemctl start xrdp.service
~~~

xrdp서비스를 실행한다.



ssh
---

Secure Shell의 준말이다.

~~~
ssh 사용자명@호스트명
ssh -l 사용자명 호스트명
~~~
> window 10 에서는 openSSh를 제공한다!!<br>
> C/Window/System32/OpenSsh 에서 ssh ~~ 하면 된당




