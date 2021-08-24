# Pixhawk
----------------------------------
자율 주행 선박 개발 중에 Pixhawk란 것을 알게 되었다. 잉? 자율 주행 관련 UI를 제공해 주다니 너무 어렸다.

그냥 지도에 좌표만 찍고 주행 버튼을 누르면 자동으로 이동한다. 쉽다 미쳤다. 또 ROS와 연동이 된다니 더욱 안 건드려 볼 수가 없었다.

* https://kwangpil.tistory.com/21 사이트를 통해서 기본적인 이론을 공부할 수 있었다.

## 7월 6일 <Pixhawk 배치>
<img src = "https://user-images.githubusercontent.com/48241432/129684199-6522dbb7-570b-4bff-a21c-0d0bf493080b.jpg" width="30%" height="height 30%">

* 첫 Pixhawk 연결, 프로그램은 QGC(QGroundControl)을 이용했다. 펌웨어는 PX4로 세팅

## 7월 7일 <Telemetry Redio 도입>
<img src = "https://user-images.githubusercontent.com/48241432/129687626-d9aeefb2-3d57-437a-9782-8042ecaf255d.jpg" width="30%" height="height 30%"> <img src = "https://user-images.githubusercontent.com/48241432/129687751-fe62d212-c01c-4d4a-a71d-44a665f2322b.jpg" width="30%" height="height 30%">

* Pixhawk의 하나의 장점이라 볼 수 있는 자율 주행. 즉, 미션모드가 있다. 이 미션모드를 사용하기 위해서는 위 사진과 같이 Telemetry Redio를 사용하여 원격 제어를 해야 하더라

## 7월 12~14일 <모터 제어(ESC)>
<img src = "https://user-images.githubusercontent.com/48241432/130559863-5d2fd0f7-bfce-45fe-9ff3-a9eba5149ca9.jpg" width="50%" height="height 50%">

* Pixhawk는 여러 모터를 제어할 수 있다. 대표적으로 BLDC라는 브러쉬리스 모터와 DC, 브러쉬 모터가 있다. 모터가 있다고 바로 돌아가는 것이 아니더라.
* ESC 모터 변속기는 모터를 제어할 수 있는 센서 같은 존재인데, 모터를 제어하는데 필수인 존재다.
<img src = "https://user-images.githubusercontent.com/48241432/130563601-25004bdc-d5bd-416b-8172-c172563405ab.jpg" width="50%" height="height 50%">

* ESC는 수신기와 배터리 연결부, 모터 연결부로 나누어져 있다.(위 사진 수신기 부분 빨간 선은 잘라버림) 수신기 부분은 보통 빨강, 흰색, 검정 3선으로 이루어져 있지만 빨강, 주황, 갈색으로도 이루어져 있는 경우가 있다.
* 빨강은 당연 VCC이고 검정 혹은 갈색은 GND, 흰색 및 주황은 PWM이다.
* 하지만 이날 모터 제어에는 실패했다. (이유는 모름)

## 7월 16일 <자율주행선박 견학, 부유테스트 진행>
* 좀 특별한 경험을 했다. Pixhawk를 이용한 자율 주행 선박의 운용을 옆에서 볼 수 있는 기회가 생겼다.
* 드론을 제작하는 전문가들을 만나면서 여러 정보를 얻을 수 있었다.
1. 미션모드를 수행하기 위해선 GPS의 성능에 따라 좌우될 수 있다.
> * GNSS 서비스, 듀얼 GPS, RTK GPS
2. 모터를 제어하기 위해선 모터 드라이버 혹은 ESC를 이용해야 함
3. 배터리의 용량
> * 예를 들어 4S 배터리는 최대 16.8V까지 충전이 가능하지만 이것도 과충전이다.
> * 배터리를 너무 사용해도 좋지 않다.(0V의 배터리는 죽은 것이다.)
4. 모터 제어의 실패 원인이 arming에 있을 수 있다. 매개변수 설정을 변경을 시도해봐라

* 이날 기구설계가 완료되어 바로 부유 테스트를 진행했다.

https://user-images.githubusercontent.com/48241432/130575667-6b75307e-406e-4c8a-bba5-bf6a060cd910.mp4


<img src = "https://user-images.githubusercontent.com/48241432/130569458-4a74217d-298d-4ffb-8d57-8ff8b396b187.jpg" width="50%" height="height 50%">

## 7월 22일 <모터제어 성공>


https://user-images.githubusercontent.com/48241432/130570993-bc8100a7-475b-4d61-b412-2d97eafaf109.mp4


* 드디어 모터 제어에 성공했다. 우여곡절이 많았지만 결국 성공해버렸다.
* 전문가의 조언에 따라 arming 관련 매개변수를 건드려봤다. 그러더니 되더라.
> * ARDUPILOT 공식 홈페이지를 참고했더니 모터가 움직이기 전에 arming을 해야 한다. 해야 하는 이유가 크게 두 가지가 있다더라.
> > 1. 드론이 준비가 되지 않았을 때 모터가 회전하는 것을 방지하기 위해
> > 2. RC가 구성되고 작동할 준비가 되기 전에 움직이는 것을 방지하기 위해
> * 그렇기에 하지 않으면 모터가 안 움직인다고... 근데 우리는 RC를 안 쓴다! 그래서 생각한 방법. Disarming 하면 된다. (이 방법이 과연 아무 문제없을 거라는 건 보장은 못 하지만 당장은 움직이니깐!)

## 7월 23일 <자율주행(미션모드)>

https://user-images.githubusercontent.com/48241432/130575622-90917348-ceda-4964-b50b-1c7d55262fdb.mp4


* 모터가 성공하자마자 바로 미션모드 테스트를 진행해보았다. 얼마나 감격스러운 순간인가
![KakaoTalk_20210812_154829431_03](https://user-images.githubusercontent.com/48241432/130576182-8c5ee4ca-9ac4-4937-8dd6-ebd9042ca402.jpg)

* 그런데 경로대로 가지 않는다? GPS의 오차 때문일 것으로 추정된다.
