

나는 늘 마인크래프트 서버를 PC로 직접 구동해왔다. 
그렇기에 몇 가지 불편함을 항상 느껴왔는데, 이는 다음과 같다:

	1. 현실적으로 서버를 24시간 구동하지 못 해, 시간이 맞지 않으면 접속할 수 없다.
	2. 서버가 PC의 리소스를 잡아먹는다.(크지는 않지만)
	3. 24시간 서버를 만들고 싶다는 생각에 잠을 이루지 못한다.


## *<font color="#acbf69">시작하기</*font*>*

내 PC로 서버를 24시간 구동하지 못하는 이유는 전기세가 부담되기 때문이다.
때문에 리눅스를 설치할 수 있고, 전력 소비량이 낮은 디바이스가 필요했다.

### 후보들
- LG G Pad (~~제 기능을 하지 못함~~)
- HP 넷북
- 클라우드 (AWS, Azure 등)

처음에는 더 이상 사용하지 않는 LG G pad로 서버를 가동하려고 했다. HP 넷북의 충전기를 찾을 수 없었고, 클라우드는 비싸보였기 때문이다.


### LG G Pad

Termux를 통해 손쉽게 서버를 열 수 있었지만, 당연하게도 문제가 있었다.

G Pad에는 총 4GB의 램이 있는데, 시스템이 대부분을 사용하고 있었다. 내가 서버에 할당할 수 있는 램은 1GB 남짓이었고, 자연스럽게 서버의 성능으로 이어졌다.

![](https://i.imgur.com/IDWqWEZ.png)
![](https://i.imgur.com/MPZ2bgI.png)
![xy50MgS.png}100*100](https://i.imgur.com/xy50MgS.png)

>  ***<font color="#7f7f7f">그냥 서버가 아님</font>***


### Azure

다른 방법을 찾던 중 Microsoft Azure에서 무료로 크레딧을 제공해준다는 사실을 알게 되었다. 

$130 크레딧을 받았고, 최소 2개월 동안은 서버를 운영하고 싶었기에 적절한 VM 사양을 선택해야 했다.

그렇게 선택한 것이 2Core, 4GB. 처음에는 큰 문제가 없다고 느꼈으나, 여러 명이 접속해 멀리 이동하거나, 네더포탈을 이용할 때 서버가 멈추는 상황이 발생했다. 

내가 가진 크레딧으로는 충분한 사양을 얻지 못 했고, 다른 방법을 찾기로 했다.

>  ***<font color="#7f7f7f">사양과 기간 사이의 타협점을 찾지 못 함</font>


### Google Cloud Platform(GCP)

무려 $300의 크레딧을 받았다. 게다가 가격도 매우 저렴했기에 매우 만족하며 사용하는 중이다. 


![](https://i.imgur.com/8nQlQUO.png)

구글 계정 로그인 후 다음과 같이 들어간다. 
좌상단 바 > Compute Engine > VM 인스턴스


![](https://i.imgur.com/xQzkGXy.png)

적당한 사양으로 우분투 VM 인스턴스를 만든다. 
나의 경우에는 8Core, 12GB을 선택했는데, 한 달에 $35밖에 하지 않는다.



![](https://i.imgur.com/JvKtjlA.png)

이제 ssh를 통해 접속해야 하는데, GCP에서 제공하는 기능을 써도 상관없다.


```
$sudo apt update

$sudo apt upgrade

$sudo apt install openjdk-17-jdk
```

위의 명령어로 자바를 설치하고, 원하는 버전의 서버 버킷을 찾아 sftp로 가상머신에 업로드한다.
