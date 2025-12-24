
https://rawcdn.githack.com/parrot2155/12_janggi/157947b497bfdc8ebbf315e66c7305e7a693b186/%EC%8B%AD%EC%9D%B4%EC%9E%A5%EA%B8%B0.html

<br>

# 🦁 십이장기 (Twelve Janggi)
별도의 설치 없이, 브라우저에서 즉시 실행 가능한 1:1 전략 보드게임입니다.
<br>

<p align="center">
  <img src="https://github.com/user-attachments/assets/989ae864-9ce4-4a1b-8187-94cfbb79d1eb" width="420px" height="235px"/>

</p>

<br>

## 📖 프로젝트 소개 (About)
십이장기는 가로 3칸, 세로 4칸의 미니 장기판에서 펼쳐지는 턴제 전략 게임입니다. 일본의 '동물 장기(Animal Shogi)' 규칙을 기반으로 하되, 한국의 전통 장기 테마를 입혀 고풍스러운 UI로 재해석했습니다.

이 프로젝트의 가장 큰 특징은 "Zero Assets" 입니다. 무거운 이미지 파일이나 오디오 파일 없이, 오직 Code(CSS & JS) 만으로 그래픽과 사운드를 실시간으로 구현하여 경량화를 달성했습니다.

<br>

## ✨ 주요 기능 (Key Features)
⚡ 초경량 & 고속 로딩: 외부 이미지나 mp3 파일이 전혀 없습니다. 단일 HTML 파일 하나로 모든 것이 동작합니다.

📱 반응형 디자인 (Mobile First): 데스크탑은 물론 모바일 터치 환경에서도 완벽하게 동작하며, 화면 크기에 따라 레이아웃이 자동 조정됩니다.

🔊 절차적 오디오 (Procedural Audio): Web Audio API를 사용하여 착수음, 포획음, 승리음을 실시간으로 합성(Synthesis)하여 재생합니다.

💡 직관적인 UX: 각 장기말 위에 이동 가능한 방향을 나타내는 '인디케이터(Indicator)'를 표시하여 초보자도 쉽게 플레이할 수 있습니다.

🧠 완벽한 룰 구현: 이동, 포획, 승급(Promotion), 잡은 말 놓기(Drop), 1턴 버티기 승리(Try Rule) 등 모든 게임 규칙이 구현되어 있습니다.

<br>

# 🛠 기술 스택 (Tech Stack)

이 프로젝트는 무거운 프레임워크 없이 Vanilla JS와 Utility-first CSS를 사용하여 가볍고 효율적으로 구축되었습니다.

### Core

<img src="https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white"/>	시맨틱 마크업 및 게임 구조 설계

<img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black"/>	ES6+ 문법, DOM 조작, 게임 로직(상태 관리, 룰 검증) 구현

<img src="https://img.shields.io/badge/CSS3-1572B6?style=flat-square&logo=css3&logoColor=white"/>	커스텀 애니메이션 및 레이아웃 스타일링

### Styling & UI

<img src="https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=flat-square&logo=tailwind-css&logoColor=white"/>	CDN 방식 적용. 반응형 디자인(Mobile-First), Flex/Grid 레이아웃 구성

<img src="https://img.shields.io/badge/Font_Awesome-528DD7?style=flat-square&logo=font-awesome&logoColor=white"/>	UI 아이콘 (설정, 리셋, 뒤로가기 등)
Google Fonts	Noto Serif KR (본문 및 UI), Jua (타이포그래피) - 웹 폰트 적용

### Audio & Assets

#### Web Audio API	
Asset-less Sound. 별도의 mp3 파일 없이 OscillatorNode와 GainNode를 사용하여 효과음(착수음, 승리음 등)을 실시간 합성(Synthesis)
#### CSS Painting	
이미지 파일 대신 CSS border, shadow, gradient를 조합하여 장기말과 보드의 질감 구현


<br>

## 💻 개발 상세 (Development Details)

### 1. 게임 로직 및 상태 관리 (Game Logic)

#### State Management : gameState 객체를 통해 보드 배열(1D Array), 현재 턴, 잡은 기물 목록, 게임 종료 여부를 중앙 관리.

#### Grid System : 1차원 배열(0~11)을 3x4 2차원 그리드로 매핑하여 좌표 계산 및 이동 경로 검증.

#### Move Validation : 각 기물(King, Jang, Sang, Ja)별 이동 가능 벡터를 정의하고, 경계값 및 아군 충돌 여부를 실시간 연산.

#### Special Rules :

Drop Rule : 잡은 말을 빈 칸에 배치하는 로직 및 Ja(자)의 배치 제한 구역(Last Rank) 검증.

Promotion : Ja(자)가 상대 진영 끝에 도달 시 Hou(후)로 승급하는 로직 구현.

Win Conditions : Checkmate(왕을 잡음) 또는 Try Rule(왕이 적진 끝에 도달) 조건 자동 감지.

### 2. 반응형 및 인터랙션 (UX/UI)

#### Responsive Layout :

#### Mobile : 세로 모드 최적화 (상대방 위 / 나 아래).

#### Desktop : 가로 모드 자동 전환 (좌우 배치).

#### Visual Cues :

선택된 기물의 이동 가능 경로를 보드에 점(valid-move)으로 표시.

기물 자체에 이동 가능한 방향을 나타내는 미니 인디케이터(Indicator) 렌더링.

#### Animations: CSS Keyframes를 활용한 승리 모달 팝업, 턴 알림, 기물 선택 시 튀어오르는 효과 등 마이크로 인터랙션 구현.

### 3. 절차적 오디오 (Procedural Audio)

외부 사운드 파일을 로드하는 대기 시간을 없애기 위해 브라우저 내장 AudioContext를 활용했습니다.

    // 예시: 착수음 생성 로직
    function playMoveSound() {
        const osc = audioContext.createOscillator(); // 진동자 생성
        osc.type = 'square'; // 나무 탁 치는 듯한 파형
        osc.frequency.setValueAtTime(180, t); // 주파수 설정
        // ... Gain(볼륨) 제어를 통한 ADSR 엔벨로프 적용
    }


## 🕹️ 게임 규칙 (Rules)

게임은 **초나라(Player 1)**가 먼저 시작하며, 번갈아 가며 한 번씩 둡니다. 

자신의 차례에는 (1) 말을 이동하거나 (2) 잡은 말을 배치할 수 있습니다.

### 1. 말 이동하기 & 잡기

  내 말을 이동 가능한 곳으로 1칸 움직입니다.

  이동하려는 칸에 상대방의 말이 있다면, 그 말을 잡고 내 포로로 만듭니다.

  잡은 말은 게임판 옆 '대기실'에 보관되며, 언제든 다시 사용할 수 있습니다.

  주의: 승급한 말을 잡으면, 다시 원래의 신분인 **자(子)**로 돌아옵니다.

### 2. 잡은 말 사용하기 (떨구기)

  이동하는 대신, 잡어둔 말을 게임판의 빈 칸 어디든 내려놓을 수 있습니다. 이것을 한 수로 칩니다.

  전략적으로 상대의 길을 막거나, 왕을 위협하는 용도로 사용하세요.

  제한 규칙: '자(子)'는 더 이상 앞으로 갈 곳이 없는 상대 진영의 마지막 줄에는 내려놓을 수 없습니다. (움직일 수 없기 때문입니다)

### 3. 승급 (Promotion)

  자(子)가 전진하여 상대방 진영의 가장 끝 줄에 도착하면, 즉시 후(侯)로 변신합니다.

  후(侯)는 이동 방향이 늘어나 더 강력해집니다. (기물 디자인이 뒤집힙니다)

### 4. 승리 조건

  다음 두 가지 중 하나를 먼저 달성하면 승리합니다.

  왕 잡기 (Checkmate): 상대방의 **왕(王)**을 잡으면 즉시 승리합니다.

  왕의 도달 (Try Rule): 나의 **왕(王)**이 안전하게 상대방 진영의 마지막 줄에 도착하면 승리합니다.

  단, 도착하자마자 바로 상대 말에게 잡히는 상황이라면 승리로 인정되지 않습니다.

<br>


## 💻 코드 하이라이트 (Code Highlights)

1. 에셋 없는 사운드 구현 (Web Audio API)
오디오 파일 로딩 없이 즉각적인 반응성을 위해 주파수(Frequency)를 직접 제어합니다.

2. 상태 기반 렌더링 (State-Driven Rendering)
게임의 상태(gameState)가 변경될 때마다 UI를 다시 그리는 단방향 데이터 흐름을 따릅니다.
