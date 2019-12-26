---
title: "Microbit Car"
categories:
  - Project
tags:
  - 임베디드
---

## 개요
Microbit를 이용한 원격 조종 자동차 제작

## 설계
<li>송신 마이크로비트의 A를 누르면 우회전</li>
<li>B를 누르면 좌회전</li>
<li>동시에 A, B를 누르면 전진</li>
<li>마이크로비트를 흔들면 멈춤</li>
<br>
## 블럭 코딩
##### 1. Receiver microbit
![receiver]({{ site.url }}{{ site.baseurl }}/assets/images/microbit_car/Receiver.jpg)
```javascript
radio.onReceivedNumber(function (receivedNumber) {
    if (receivedNumber == 1) {
        motorbit.turnleft(70)
    } else if (receivedNumber == 2) {
        motorbit.turnright(70)
    } else if (receivedNumber == 3) {
        motorbit.forward(70)
    } else {
        motorbit.brake()
    }
})
radio.setGroup(1)
```
<br><br>
##### 2. Sender microbit
![sender]({{ site.url }}{{ site.baseurl }}/assets/images/microbit_car/Sender.jpg)
###### javascript
```javascript
input.onButtonPressed(Button.A, function () {
    radio.sendNumber(1)
})
input.onButtonPressed(Button.B, function () {
    radio.sendNumber(2)
})
input.onButtonPressed(Button.AB, function () {
    radio.sendNumber(3)
})
input.onGesture(Gesture.Shake, function () {
    radio.sendNumber(4)
})
radio.setGroup(1)
```
<br>
## 사진
###### Car
![car]({{ site.url }}{{ site.baseurl }}/assets/images/microbit_car/car.jpg)
<br><br>
###### Receiver microbit
![receiver_microbit]({{ site.url }}{{ site.baseurl }}/assets/images/microbit_car/Receive_microbit.jpg)
<br><br>
###### Sender microbit
![sender_microbit]({{ site.url }}{{ site.baseurl }}/assets/images/microbit_car/Sender_microbit.jpg)

