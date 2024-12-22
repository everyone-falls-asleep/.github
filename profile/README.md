<div id="top"></div>

<div align='center'>

<h1><b>티켓 예매 대행 서비스 : 소켓팅</b></h1>

🔗 [배포 링크](https://socketing.hjyoon.me/)

<img src="" alt="intro title image"/>

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

총 기간이 5주인 프로젝트였지만 3~4일 안에 1차 MVP를 개발하고 빠르게 피드백 & 유저테스트를 진행하여  
그를 바탕으로 3~4일에 한번씩 MVP를 업데이트 하는 계획을 세웠고 5주간 6번의 유저테스트와 8번 업데이트 하여 8차 MVP로 마무리 했습니다.
<br>

<!-- Top Button -->
<p style='background: black; width: 32px; height: 32px; border-radius: 50%; display: flex; justify-content: center; align-items: center; margin-left: auto;'><a href="#top" style='color: white; '>▲</a></p>

<br>

## <span id="2">🏃 2. 팀원 소개</span>

<div align="center">

|          [팀장 채동현](https://github.com/donghyun-chae)          |  [팀원2 이름](https://github.com/username2)   |
| :---------------------------------------------------------------: | :-------------------------------------------: |
| <img src="/images/donghyun.jpg" width="120px;" alt="팀원1 사진"/> | <img src="" width="120px;" alt="팀원2 사진"/> |

</div>

<br>

<!-- Top Button -->
<p style='background: black; width: 32px; height: 32px; border-radius: 50%; display: flex; justify-content: center; align-items: center; margin-left: auto;'><a href="#top" style='color: white; '>▲</a></p>

<br>

## <span id="3">📅 3. 개발 일정</span>

> 프로젝트 개발 기간: 2024.11.10 ~ 2024.12.14

<br>

<!-- Top Button -->
<p style='background: black; width: 32px; height: 32px; border-radius: 50%; display: flex; justify-content: center; align-items: center; margin-left: auto;'><a href="#top" style='color: white; '>▲</a></p>

<br>

## <span id="4">📚 4. 아키텍처</span>

<img src="/images/arc.png" width="120px;" alt="아키텍처"/>

## <span id="5">❓ 5. 유저테스트</span>

<br>

<!-- Top Button -->
<p style='background: black; width: 32px; height: 32px; border-radius: 50%; display: flex; justify-content: center; align-items: center; margin-left: auto;'><a href="#top" style='color: white; '>▲</a></p>

<br>

## <span id="6">6. 💻 주요 기능 소개</span>

프로젝트의 주요 기능을 GIF를 첨부하여 설명해주세요.

### 1) 홈

| - 화면                                            | - 화면                                            | - 화면                                            |
| ------------------------------------------------- | ------------------------------------------------- | ------------------------------------------------- |
| <img src="" alt="-화면" width="288" height="608"> | <img src="" alt="-화면" width="288" height="608"> | <img src="" alt="-화면" width="288" height="608"> |

### 2) 게시글

| 상세페이지 화면                                   | 게시물 작성 - ??                                  | 게시물 작성 - ??                                  |
| ------------------------------------------------- | ------------------------------------------------- | ------------------------------------------------- |
| <img src="" alt="-화면" width="288" height="608"> | <img src="" alt="-화면" width="288" height="608"> | <img src="" alt="-화면" width="288" height="608"> |

### 3) 404 & 로딩 화면

| - 화면                                            | - 화면                                            | - 화면                                            |
| ------------------------------------------------- | ------------------------------------------------- | ------------------------------------------------- |
| <img src="" alt="-화면" width="288" height="608"> | <img src="" alt="-화면" width="288" height="608"> | <img src="" alt="-화면" width="288" height="608"> |

<br>

<!-- Top Button -->
<p style='background: black; width: 32px; height: 32px; border-radius: 50%; display: flex; justify-content: center; align-items: center; margin-left: auto;'><a href="#top" style='color: white; '>▲</a></p>

<br>

## <span id="7">7. 📄 상세 담당 업무</span>

### 1) 팀원1 이름

- **🎨 디자인**

  - 로고 디자인 및 이미지 제작

- **💻 화면 개발**

  - 로그인 화면
  - 검색 화면
  - 채팅 화면

- **🧑‍💻 구현 기능**

  - 로딩 페이지
    - 회원가입 후 로그인 모달이 올라오는 로딩페이지
  - 팔로워 목록 및 팔로워 취소&팔로우
    - 팔로워 목록을 getFollowerList로 서버에 요청하여 리스트 출력

- **♻️ 리팩토링**
  - 관련 설명

<br>

<!-- Top Button -->
<p style='background: black; width: 32px; height: 32px; border-radius: 50%; display: flex; justify-content: center; align-items: center; margin-left: auto;'><a href="#top" style='color: white; '>▲</a></p>

<br>

## <span id="8">🚦 11. 기술적 도전 및 이야기</span>

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
