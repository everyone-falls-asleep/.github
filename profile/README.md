<div id="top"></div>

<div align='center'>

<h1><b>티켓 예매 대행 서비스 : 소켓팅</b></h1>

🔗 [배포 링크](https://socketing.hjyoon.me/)

<img src="/images/메인.png" alt="메인" width="720" height="480">

</div>

<br>

## 0. 목차

1. [프로젝트 소개](#1)
2. [팀원 소개](#2)
3. [개발 일정](#3)
4. [아키텍처](#4)
5. [유저 테스트](#5)
6. [주요 기능 소개](#6)
7. [상세 담당 업무](#7)
8. [기술적 도전 및 이야기](#8)
9. [앞으로 개선할 점](#9)

<br />

## <span id="1">🚩 1. 프로젝트 소개</span>

Youtube: [프로젝트 발표 영상](https://youtu.be/Kee5ar3oDZ4)

SW사관학교 정글9기 나만의 무기 만들기 섹션에서 만든 티켓 예매 대행 서비스 소켓팅(Socketing)입니다.

### 주제 선정 이유

저희 팀은 평소 티켓팅을 하며 많은 불편함을 느꼈고 그 중에서도 빈 자리로 표시 됐음에도  
"이미 다른 고객님께서 선택한 자리입니다" 라고 나오는 문제를 해결해보자는 생각으로 주제 선정을 진행하였습니다.
<img src="/images/이선좌.gif" width="500px;" alt="이선좌"/>

### 개발 계획

총 기간이 5주인 프로젝트였지만 3일 안에 1차 MVP를 개발하고 빠르게 유저테스트를 진행하여  
그를 바탕으로 3-4일에 한번씩 MVP를 업데이트 하는 계획을 세웠고 5주간 6번의 유저테스트와 8번 업데이트 하여 8차 MVP로 마무리 했습니다.

> [1~8차 MVP 과정](https://github.com/everyone-falls-asleep/socketing-client/releases)

<br>

<!-- Top Button -->
<p style='background: black; width: 32px; height: 32px; border-radius: 50%; display: flex; justify-content: center; align-items: center; margin-left: auto;'><a href="#top" style='color: white; '>▲</a></p>

<br>

## <span id="2">🏃 2. 팀원 소개</span>

<div align="center">

|          [팀장 채동현](https://github.com/donghyun-chae)           |  [팀원 김혜다](https://github.com/username2)   |           [팀원 박연우](https://github.com/yeonupark)            |             [팀원 윤효전](https://github.com/hjyoon)              |  [팀원 최지인](https://github.com/username2)   |
| :----------------------------------------------------------------: | :--------------------------------------------: | :--------------------------------------------------------------: | :---------------------------------------------------------------: | :--------------------------------------------: |
| <img src="/images/donghyun.jpg" width="120px;" alt="채동현 사진"/> | <img src="" width="120px;" alt="김혜다 사진"/> | <img src="/images/yeonu.jpeg" width="120px;" alt="박연우 사진"/> | <img src="/images/hyojeon.jpg" width="120px;" alt="윤효전 사진"/> | <img src="" width="120px;" alt="최지인 사진"/> |

</div>

<br>

<!-- Top Button -->
<p style='background: black; width: 32px; height: 32px; border-radius: 50%; display: flex; justify-content: center; align-items: center; margin-left: auto;'><a href="#top" style='color: white; '>▲</a></p>

<br>

## <span id="3">📅 3. 개발 일정</span>

### 프로젝트 개발 기간: 2024.11.10 ~ 2024.12.14

<br>

<!-- Top Button -->
<p style='background: black; width: 32px; height: 32px; border-radius: 50%; display: flex; justify-content: center; align-items: center; margin-left: auto;'><a href="#top" style='color: white; '>▲</a></p>

<br>

## <span id="4">📚 4. 아키텍처</span>

<img src="/images/arc.png" width="500px;" alt="아키텍처"/>

<details>
<summary> StoryBook 사용 이유 </summary>

<div>
사용이유 <br />
~~

</div>
</details>

<details>
<summary> Redis 사용 이유 </summary>

<div>
Redis 사용 이유:
- 대기열 관리: Queue에 데이터를 삽입 및 삭제할 때 원자성을 보장하여 데이터 무결성을 유지.   
- 실시간 좌석 선택 현황 브로드캐스팅: 예매 과정에서 실시간으로 변경되는 좌석 현황을 임시 저장소로 활용, 이를 WebSocket으로 브로드캐스팅.   
- 좌석 선택 만료 처리: 선택된 좌석의 만료 시간을 관리하여, 제한 시간 초과 시 자동으로 해제 처리.   
- 메시지 브로커 기능: Redis Stream을 사용해 메시지 브로커로 활용, 이벤트 기반 처리를 간소화.

요약: Redis는 실시간 통신(WebSocket)에서 임시 저장소 및 메시지 브로커로 사용되어 안정적이고 빠른 데이터 처리를 지원.

</div>
</details>

<details>
<summary> PostgreSQL 사용 이유 </summary>

<div>
PostgreSQL 사용 이유:
- MongoDB 활용의 한계: 프로젝트 특성상 MongoDB의 비정형 데이터 처리 장점을 극대화하기 어려움.
- 단순한 DB 스키마: 관계형 데이터베이스로 충분히 처리 가능하며, 데이터 무결성과 안정성을 제공.

</div>
</details>

<details>
<summary> 서버를 분리한 이유 </summary>

<div>
서버를 분리한 이유:
- 스케일 아웃 설계: 대규모 트래픽을 처리하기 위해 이벤트 기반 아키텍처를 적용하여, 수평 확장이 용이한 구조 설계를 목표로 함.
- Kubernetes 도입의 어려움: 제한된 프로젝트 기간 내 Kubernetes를 도입하는 대신, Redis Stream을 활용해 서버를 용도별로 분리하여 처리.
- 효율성 극대화: 서버 역할을 분리함으로써 각 서버가 특정 작업에 최적화된 성능을 발휘하도록 설계.

요약: 서버 분리는 대용량 트래픽 처리와 확장성을 고려한 실용적 접근 방식. Redis Stream을 활용하여 효율적인 이벤트 처리를 지원.

</div>
</details>

## <span id="5">❓ 5. 유저테스트</span>

<details>
<summary> 유저 테스트 피드백 정리 및 반영 </summary>

<div>

| 20대 | 티켓팅 경험 X | 없습니다.                                                                                                                                                                                                                                                                                                       | 빠르게 진행되는게 너무 좋습니다.                                                                     |                                                             |
| ---- | ------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- | ----------------------------------------------------------- |
| 20대 | 티켓팅 경험 O | 모바일 이용시 밑에 반정도가 고정되어있어서 화면이 작게 느껴짐 ㅜㅜ 불편해요**→ 예매 버튼이 스크롤을 내리지 않아도 보이게 하려고 맵을 줄였는데 버튼도 보이면서 맵도 크게 보이게 수정해 보겠습니다!**                                                                                                             |                                                                                                      |                                                             |
| 20대 | 티켓팅 경험 O | 회원가입이 필요한 줄 모르고, 로그인을 했을 때 로그인이 안 된다고만 해서 당황했어요! ‘회원가입되지 않은 회원이다’와 같은 안내 문구가 뜬다면 좋을 것 같아요..!**→ 바로 추가하겠습니다!**                                                                                                                          |                                                                                                      |                                                             |
| 30대 | 티켓팅 경험 O | 친구 추가하는 란이 어디인지 못찾았어요 ㅠ**→ 찾기 쉽게 변경(알림으로 알려주거나 좀더 찾기쉬운 위치로 옮기기)해보겠습니다!**                                                                                                                                                                                     | **금액 별 좌석 구분**/ **소켓에 연결된 사람들을 친구로 추천**해주기?                                 |                                                             |
| 30대 | 티켓팅 경험 O | 평소 긴박하게 티케팅 하던 버릇이 나와 그냥 정신없이 클릭했습니다ㅠ 그래도 간편했던것같아요. 소켓페이를 미리 충전해두면 더 빨리 결제가 진행되는 시스템인가요?**→ 아뇨 소켓페이는 저희가 기본적으로 10만원씩 충전해드리는데 그 금액 내에서 결제가 바로 가능합니다! 좀 더 금액을 늘릴예정이고 충전은 불가합니다!** |                                                                                                      |                                                             |
| 50대 | 티켓팅 경험 X | 함께 예매할 친구도 회원가입이 필요한게 어렵습니다→ **친구 추가하는 버튼을 찾기 쉽게 변경(알림으로 알려주거나 좀더 찾기쉬운 위치로 옮기기)해보겠습니다! 그리고 회원가입은 유저테스트 전에 미리 안내 해드리겠습니다!**                                                                                            | 좌석선택시 블럭별로 색이 구분되어 **가격이 옆에 따로 표시** 되었으면합니다                           | 블럭만 표시되지말고 **좌석도 구분**될수 있었으면 좋겠습니다 |
| 20대 | 티켓팅 경험 O | 보유 소켓 조회를 눌러야 얼마남았는지 뜨는게 불편해요 (급하게 할 경우)→ **아! 이건 결제하는 느낌을 내려고 추가 한건데 다른 방안도 생각 해보겠습니다!**                                                                                                                                                           |                                                                                                      |                                                             |
| 50대 | 티켓팅 경험 X | 티켓 재판매 금지를 위해 휴대폰으로 본인인증 했으면 합니다.**→ 암표 방지에 대해 저희도 좀 더 생각해 보겠습니다!**                                                                                                                                                                                                | **좌석 선택 할때 가격이 보였으면 합니다**                                                            | **좌석별 가격이** 잘 구분되어 보였으면 합니다               |
| 30대 | 티켓팅 경험 O | 소켓페이 말고 신용카드 할인이 있어서 신용카드로 예매하고 싶습니다 선택권이 없네요ㅠ**→ 저희가 실제 결제 시스템은 도입하지 않을 예정이라.. ㅜㅜ 의견 감사합니다!!**                                                                                                                                              | 구역별 누르는게 아니라 그냥 **한번에 보이는것**도 좋을것같긴합니다                                   | 늘 고생이 많으십니다                                        |
| 20대 | 티켓팅 경험 O | 모바일로 좌석이 엄청 작게나와요**→ 예매 버튼이 스크롤을 내리지 않아도 보이게 하려고 맵을 줄였는데 버튼도 보이면서 맵도 크게 보이게 수정해 보겠습니다!**                                                                                                                                                         |                                                                                                      |                                                             |
| 50대 | 티켓팅 경험 O | 취소하고 다시 주문하고 싶었는데 그러지 못했다**→ 좌석별 취소버튼과 다시 예매 상세페이지로 가는 버튼을 추가하면 좋을거 같습니다. 의견 감사합니다!**                                                                                                                                                              | **취소하고 더 좋은 자리를 새로 선택**하거나 **친구와 함께 예약하는 변경**을 쉽게 할 수 있게 해주세요 | 멋진 프로그램 응원합니다                                    |
|      |               | 많이 좋아졌다! 그리고 진행과정이 색깔 채워지는 걸로 보여서 이게 시스템이 먹통인가 아닌가를 인식할 수 있어서 좋았다! **→ 결제 진행과정 말하는듯 ,**                                                                                                                                                              |                                                                                                      |                                                             |

</div>
</details>

<br>

<!-- Top Button -->
<p style='background: black; width: 32px; height: 32px; border-radius: 50%; display: flex; justify-content: center; align-items: center; margin-left: auto;'><a href="#top" style='color: white; '>▲</a></p>

<br>

## <span id="6">6. 💻 주요 기능 소개</span>

<details>
<summary><span style="font-size: 1.2em; font-weight: bold">공연 등록</span></summary>

<div>

<img src="/images/01공연등록.gif" alt="공연등록" width="720" height="480">

</div>
</details>

<details>
<summary><span style="font-size: 1.2em; font-weight: bold">구역 설정</span></summary>

<div>

<img src="/images/02구역설정.gif" alt="구역설정" width="720" height="480">

</div>
</details>

<details>
<summary><span style="font-size: 1.2em; font-weight: bold">대기열</span></summary>

<div>

<img src="/images/03대기열.gif" alt="대기열" width="720" height="480">

</div>
</details>

<details>
<summary><span style="font-size: 1.2em; font-weight: bold">구역 그라데이션</span></summary>

<div>

<img src="/images/04그라데이션.gif" alt="그라데이션" width="720" height="480">

</div>
</details>

<details>
<summary><span style="font-size: 1.2em; font-weight: bold">실시간 렌더링</span></summary>

<div>

<img src="/images/05실시간렌더링.gif" alt="실시간렌더링" width="720" height="480">

</div>
</details>

<details>
<summary><span style="font-size: 1.2em; font-weight: bold">함께 예매하기</span></summary>

<div>

<img src="/images/06연석.gif" alt="연석" width="720" height="480">

</div>
</details>

<details>
<summary><span style="font-size: 1.2em; font-weight: bold">결제</span></summary>

<div>

<img src="/images/07결제.gif" alt="결제" width="720" height="480">

</div>
</details>

<details>
<summary><span style="font-size: 1.2em; font-weight: bold">마이 페이지</span></summary>

<div>

<img src="/images/08마이페이지.gif" alt="마이페이지" width="720" height="480">

</div>
</details>

<details>
<summary><span style="font-size: 1.2em; font-weight: bold">관리자 페이지</span></summary>

<div>

<img src="/images/09관리자페이지.gif" alt="관리자페이지" width="720" height="480">

</div>
</details>

<br>

<!-- Top Button -->
<p style='background: black; width: 32px; height: 32px; border-radius: 50%; display: flex; justify-content: center; align-items: center; margin-left: auto;'><a href="#top" style='color: white; '>▲</a></p>

<br>

## <span id="7">7. 📄 상세 담당 업무</span>

### 1) 채동현

### 2) 김혜다

### 3) 박연우

---

### 4) 윤효전

- **프로젝트 초기 설정 및 DevOps 업무**

  - 프로젝트 전반적인 환경 구성 및 기술 스택 선정.
  - CI/CD 파이프라인 구축 (GitHub Actions 활용) 및 환경 변수 암호화 설정 (Ansible 활용).
  - AWS 인프라 설계 및 관리, 도메인 설정 및 배포 환경 구성.

- **백엔드 설계 및 구현**

  - API 서버, Socket 서버, Queue 서버, Scheduling 서버 등 주요 백엔드 서비스 개발 및 서버 역할 분리.
  - PostgreSQL과 Redis 통합, Redis Stream을 활용한 이벤트 기반 대기열 처리 로직 구현.
  - Socket.IO 기반 실시간 소켓 이벤트 로직 설계 및 구현.

- **스케줄링 및 시간 기반 로직 개발**

  - 좌석 선택 만료 처리와 결제 타임아웃 처리 등 스케줄링 로직 설계 및 구현.

- **성능 최적화 및 시스템 안정성**
  - 전반적인 백엔드 로직 리팩토링 및 시간 복잡도 개선.
  - Locust를 활용한 Socket 부하 테스트로 실제 사용자 환경 시뮬레이션 및 성능 검증.

---

### 5) 최지인

- **공연 상세 페이지의 공연 일정 필터링 기능 구현**

  - Context API로 공연 날짜와 사용자가 선택한 날짜의 상태를 관리
  - 달력 UI로 공연 날짜와 사용자가 선택한 날짜를 시각화

- **결제 제한 시간 내 결제하기 기능 구현**

  - 유저, 주문 정보 등의 유효성을 검증하여 예외 처리
  - 트랜잭션 적용으로 DB에 저장되는 결제 데이터의 원자성 보장
  - Redis의 임시 주문 데이터에 TTL을 적용하여 결제 시간 제한

- **마이 페이지, 판매자 페이지 데이터 조회 API 구현**

  - 예매 취소된 주문은 조회 데이터에서 제외되도록 처리
  - 판매자 페이지에 표시할 매출액을 쿼리로 집계
  - 프런트 개발자가 작업하기 편한 방식으로 응답 객체를 생성

---

<br>

<!-- Top Button -->
<p style='background: black; width: 32px; height: 32px; border-radius: 50%; display: flex; justify-content: center; align-items: center; margin-left: auto;'><a href="#top" style='color: white; '>▲</a></p>

<br>

## <span id="8">🚦 8. 기술적 도전 및 이야기</span>

<details>
<summary> 기술적 도전 및 이야기 </summary>

<div>

1. 문제 상황 <br />

2. 시도 <br />

3. 해결방안 <br />

</div>
</details>

<br>

<!-- Top Button -->
<p style='background: black; width: 32px; height: 32px; border-radius: 50%; display: flex; justify-content: center; align-items: center; margin-left: auto;'><a href="#top" style='color: white; '>▲</a></p>

<br>

## <span id="9">9. 📝 앞으로 개선할 점</span>

앞으로 개선할 점

<br>

<!-- Top Button -->
<p style='background: black; width: 32px; height: 32px; border-radius: 50%; display: flex; justify-content: center; align-items: center; margin-left: auto;'><a href="#top" style='color: white; '>▲</a></p>

<br>

## 번외

### 포스터

<img src="/images/poster.jpg" width="500px;" alt="포스터"/>
