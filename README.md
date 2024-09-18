# network-study-diary

> 네트워크 개념을 다지기 위한 스터디 활동

## 🖋️ 스터디 기록 및 회고

 - [1회차 네트워크 거시적으로 살펴보기](https://github.com/silberbullet/network-study-diary/blob/main/network_study/1_2_%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC_%EA%B1%B0%EC%8B%9C%EC%A0%81%EC%9C%BC%EB%A1%9C_%EC%82%B4%ED%8E%B4%EB%B3%B4%EA%B8%B0.md)
 - [2회차 네트워크 미시적으로 살펴보기](https://github.com/silberbullet/network-study-diary/blob/main/network_study/1_3_%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC_%EB%AF%B8%EC%8B%9C%EC%A0%81%EC%9C%BC%EB%A1%9C_%EC%82%B4%ED%8E%B4%EB%B3%B4%EA%B8%B0.md)
 - [3회차 이더넷, NIC와 케이블](https://github.com/silberbullet/network-study-diary/blob/main/network_study/2_1%EA%B3%BC_2_%EC%9D%B4%EB%8D%94%EB%84%B7_NIC%EC%99%80%EC%BC%80%EC%9D%B4%EB%B8%94.md)
 - [4회차 허브, 스위치](https://github.com/silberbullet/network-study-diary/blob/main/network_study/2_3%EA%B3%BC_4_%ED%97%88%EB%B8%8C_%EC%8A%A4%EC%9C%84%EC%B9%98.md)
 - [5회차 LAN을 넘어서는 네트워크 계층](https://github.com/silberbullet/network-study-diary/blob/main/network_study/3_1_LAN%EC%9D%84_%EB%84%98%EC%96%B4%EC%84%9C%EB%8A%94_%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC_%EA%B3%84%EC%B8%B5.md)
 - [6회차 IP 주소](https://github.com/silberbullet/network-study-diary/blob/main/network_study/3_2_IP_%EC%A3%BC%EC%86%8C.md)
 - [7회차 라우팅]()
 - [8회차 전송 계층 개요: IP의 한계와 포트]()
---

<img width="368" alt="bookInfo" src="https://github.com/user-attachments/assets/30f20200-ca17-4f12-9558-ba877d9ffc17">


## ❓스터티 목적

### 1. 네트워크 생태계에 살아가는 우리

우리는 스마트폰이나 데스크톱을 활용해 인터넷을 이용해 봤거나, **주변의 다른 장치와 정보를 주고 받아 본 적이 있을 것**입니다. 이 모든 것이 컴퓨터 네트워크가 있기에 가능한 일입니다. `컴퓨터 네트워크` 는 우리 일상의 지탱하는 주요 기반 기술 입니다.

> **컴퓨터 네트워크 란?**

데스크톱, 노트북, 스마트폰은 대부분 주변 장치와 유무선으로 연결되어 정보를 주고받을 수 있습니다. 그렇게 연결된 장치는 또 다른 주변 장치와 연결 됩니다. 더 나아가 마치 **그물처럼 서로 연결되어 정보를 주고받을 수 있는 통신망**을 `컴퓨터 네트워크` 혹은 `네트워크` 라고 합니다.

현대 정보는 네트워크와 연결된 지구 반대편에 있는 장치와도 정보를 주고받을 수 있습니다. 이를 가능하게 하는 기술이 바로 `인터넷` 입니다. 인터넷은 **네트워크를 연결하는 네트워크**를 의미합니다.

### 2. 개발자는 왜 네트워크를 이해해야 할까요?

> **개발자가 컴퓨터 네트워크를 알아야 하는 이유**

개발자는 다른 장치와 상호 작용하여 실행되는 프로그램을 개발하는 경우가 많습니다.

개발자의 업무는 크게 `프로그램을 만드는 업무` 와 `프로그램을 유지보수 하는 업무` 로 나뉘어 집니다.

네트워크 지식은 두 가지 업무에 모두 도움을 줄 수 있습니다.

`프로그램을 만드는 업무` 에서는 프로그래밍 언어나 웹 프레임워크 혹은 라이브러리를 사용할 때 **네트워크에 대한 배경지식 있어야만 활용할 수 있는 기능**들이 있습니다.

**TCP/UDP나 HTTP와 쿠키** 같은 지식이 없다면 다음과 같은 스프링 프레임워크의 기능을 제대로 이해하기 어렵습니다.

배포 때도 마찬가지 입니다. **DNS, HTTP/HTTPS, 포트 번호** 등 다양한 네트워크 배경지식들이 필요합니다. 또한 **프로그램의 안정성과 안정성을 높이고 싶을 때**도 네트워크 지식은 유용하게 활용 됩니다.

`프로그램을 유지보수 하는 업무` 에서는 **인터넷 연결이 안되는 문제부터, 크게는 웹 서버가 동작하지 않는 문제**까지, 네트워크 지식은 문제 발생 시 해결의 큰 실마리가 됩니다.

> **책을 통해 해당 질문을 자신 있게 대답 할 수 있습니다!**

- **DNS의 정의와 동작 과정에 관해 설명하세요.**
- **TCP와 UDP의 차이는 무엇인가요?**
- **HTTP와 HTTPS의 차이는 무엇인가요?**

## ❗스터디 방향성

### 🖋️ 필기 정리 (권장 사항)

스터디 전에 자신이 공부해 온 내용을, 가능한 만큼 필기하여 정리합니다. (블로그, 노트앱 등)

바쁜 일정을 갖고 있는 구성원들도 있기 때문에 필기 정리는 개인 상황에 따라 생략할 수 있도록 배려합니다.

### 회차별 스터디 회고 (짧게)

- 알게 된 것을 작성해도 됨.
- 스터디 요약 느낌에 가깝게 작성해도 됨.
- 토의하고 싶은 주제를 작성해도 됨.
