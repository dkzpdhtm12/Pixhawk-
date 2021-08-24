# Pixhawk
----------------------------------
자율 주행 선박 개발 중에 Pixhawk란 것을 알게 되었다. 젠장 자율 주행 관련 UI를 제공해 주다니 너무 어렸다.

그냥 지도에 좌표만 찍고 주행 버튼을 누르면 자동으로 이동한다. 쉽다 미쳤다. 또 ROS와 연동이 된다니 더욱 안 건드려 볼 수가 없었다.

* https://kwangpil.tistory.com/21 사이트를 통해서 기본적인 이론을 공부할 수 있었다.

## 7월 6일 <Pixhawk 배치>
<img src = "https://user-images.githubusercontent.com/48241432/129684199-6522dbb7-570b-4bff-a21c-0d0bf493080b.jpg" width="30%" height="height 30%">
* 첫 Pixhawk 연결, 프로그램은 QGC(QGroundControl)을 이용했다. 펌웨어는 PX4로 세팅

## 7월 7일 <Telemetry Redio 도입>
<img src = "https://user-images.githubusercontent.com/48241432/129687626-d9aeefb2-3d57-437a-9782-8042ecaf255d.jpg" width="30%" height="height 30%"> <img src = "https://user-images.githubusercontent.com/48241432/129687751-fe62d212-c01c-4d4a-a71d-44a665f2322b.jpg" width="30%" height="height 30%">
* Pixhawk의 하나의 장점이라 볼 수 있는 자율주행. 즉, 미션모드가 있다. 이 미션모드를 사용하기 위해서는 위 사진과 같이 Telemetry Redio를 사용하여 원격 제어를 해야하더라

## 7월 12~14일 <모터 제어(ESC)>
<img src = "https://user-images.githubusercontent.com/48241432/130559863-5d2fd0f7-bfce-45fe-9ff3-a9eba5149ca9.jpg" width="50%" height="height 50%">
* Pixhawk는 여러 모터를 제어할 수 있다. 대표적으로 BLDC라는 브러쉬리스 모터와 DC, 브러쉬 모터가 있다. 모터가 있다고 바로 돌아가는 것이 아니더라.
* ESC 모터 변속기는 모터를 제어할 수 있는 센서같은 존재인데, 모터를 제어하는데 필수인 존재다.
<img src = "https://user-images.githubusercontent.com/48241432/130563157-1a411227-4263-4b25-8d9a-93a13507cbd9.jpg" width="50%" height="height 50%">

