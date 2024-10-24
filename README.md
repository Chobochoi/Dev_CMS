# Samwoo
## 프로젝트 진행 내역
### 2405~2408 CPR 체험
#### 개발환경 : Unreal Engine 5.3
#### 사용장비 : Vive XR Elite / Vive Ultimate Tracker
#### 프로젝트 요약 : 실제 환경에서 응급상황 시 CPR 및 제세동기 사용을 직접 할 수 있도록 체험.
![ScreenShot00000](https://github.com/user-attachments/assets/dd99c676-6fd6-4bfb-bd7c-c99c029bd63a)
#### 프로젝트 진행 :
- 24년 5월 4주차 : 기획서 작성 완료 및 환경 제작 완료
- 24년 6월 1,2 주차 : Vive XR Elite 플러그인 연동 및 Vive Ultimate Tracker 작동 테스트
- 24년 6월 3주차 : Vive Ultimate Tracker 위치 조정 로직 개발 및 테스트
- 24년 6월 4주차 ~ 7월 1주차 : 애니 및 인스트럭터와 통신 코드 개발 및 테스트 (애니 IP : 192.168.0.201 인스트럭터 IP : 192.168.0.68 콘텐츠 IP : 192.168.0.101)
- 24년 7월 2주차 : 리듬게임 형식의 Widget 개발 및 난이도 조절, 실제 애니 데이터로 Widget 난이도 테스트  
- 24년 7월 3주차 : 시나리오 순서별 핸드 터치 인터랙션 개발
- 24년 7월 4주차 : 1차 테스트 용 패키징 완료 (애니 및 인스트럭터 전체 통신 테스트, CPR 압박 난이도 테스트, 전체 시나리오 진행 및 사용자 테스트)
- 24년 8월 1주차 : 2차 테스트 패키징 (CPR 난이도 하향 조정 및 시나리오 전체 길이 조절)
- 24년 8월 2주차 : 3차 테스트 패키징 (고등학생 40명 및 전직원 테스트)
- 24년 8월 3주차 : 4차 테스트 패키징 (현직 119 구급대원 테스트) 
- 24년 8월 4주차 : 완료
#### 프로젝트 이슈사항 및 해결방안 : 
- Vive XR Elite와 Vive Ultimate Tracker의 호환은 5.2 버전이상에서의 베타버전으로만 제공하였기 때문에 최초 프로젝트 생성 시 5.1 버전으로 진행하여 5.3으로의 버전 업 문제가 있었다.
- Vive Ultimate Tracker를 쓰는 가장 큰 이유는 Tracker 추적을 통한 CPR 애니 위치 연동이였는데, 위치값 보정 및 화면 재조정이 쉽지 않았다. (가장 오래 걸린 작업)
  아래와 같이 로직을 짜서 해결하였다. 
![image](https://github.com/user-attachments/assets/6690f086-6784-40d8-9df3-e7aa5da6a208)
![image](https://github.com/user-attachments/assets/03ffe16f-8131-46c3-929f-42742ce9611f)
![image](https://github.com/user-attachments/assets/ca36e453-a32f-4e6a-96fd-df90379b660b)
![image](https://github.com/user-attachments/assets/622869e0-d7eb-4b22-9ae8-da9d7cbb7720)
![image](https://github.com/user-attachments/assets/36bde1c3-414e-4dc9-8b71-c6812795bf2f)
![image](https://github.com/user-attachments/assets/21d4f5b0-250b-4dff-85ea-cb5b98dfd86b)
- CPR 압박 과정을 리듬게임 형식으로 제작하게 되어 해당 판정에 대한 범위 및 레이턴시 설정하는데에 어려움이 있었다.
  1. 언리얼 내의 메타사운드를 활용해 120bpm (CPR 압박 속도 100~120bpm) 으로 비트사운드를 개발하여 압박에 관한 타이밍을 알려주었다. 
  2. 판정에 관한 판정 범위 증가를 해주었다. 시중에 있는 리듬 게임을 참고하여 6fps의 레이턴시를 주고 해당 입력 값 들 중 최고값으로 판정하였다. 
     판정 범위 증가 사유 : 
     1. 애니를 직접 압박 한다는 점
     2. 실제 리듬게임 방식과 다르게 압박데이터가 틱 단위로 넘어와 그래프 형식이라 판정 체크 시 최고 점수가 아닐 수 있다는 점
     3. VR 환경에서의 60fps가 고정적이지 않다는 점을 감안 
- 일반인, CPR 자격증 보유자, 현직 119 구조대원 등의 직접적 체험 후 피드백 적용이 쉽지 않았다. 
  CPR에 관한 지식이 있고 CPR을 시행할 수 있는 전문가라고 하더라도 VR에 익숙치 않은 사람들이 다수였다. 해당 부분에 관하여 사전에 VR 숙련도에 관한 질문을 하고 Case를 분류하여 난이도 조절 및 피드백을 받는 방식으로 하였다.

### 2403~2405 광주반도체 직업체험

### 2402~2403 부산항만연수원 지게차 안전사고 예방  

### 2312~2402 거창 승강기 CBT 승강기

### 2309~2312 폴리텍 꿈드림공작소 

### 2307~2309 재난 안전 체험 (지진발생 즉시대피)

### 2305~2307 재난 안전 체험 (태풍발생 즉시대피)

### 2303~2305 재난 안전 체험 (지진발생 실내대비)
