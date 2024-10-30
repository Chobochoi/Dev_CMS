# Samwoo
## 프로젝트 진행 내역
---
[CPR 체험](#2405~2408 CPR 체험)
---
## 2405~2408 CPR 체험
#### 개발환경 : Unreal Engine 5.3 / Desktop i9-10900 RTX3070 RAM 32G
#### 사용장비 : Vive XR Elite / Vive Ultimate Tracker
#### 프로젝트 요약 : 실제 환경에서 응급상황 시 CPR 및 제세동기 사용을 직접 할 수 있도록 VR로 학습 및 체험.
![ScreenShot00000](https://github.com/user-attachments/assets/dd99c676-6fd6-4bfb-bd7c-c99c029bd63a)
#### 프로젝트 주요 기능 :
- 리듬게임 형식의 3D Widget

![CPR_WidgetTest](https://github.com/user-attachments/assets/2eb102ef-4085-4e1a-93aa-0f026e164969)

- 실제 애니의 위치가 변경되었을 시, VR 콘텐츠 상의 위치 재조정
![image](https://github.com/user-attachments/assets/6690f086-6784-40d8-9df3-e7aa5da6a208)
![image](https://github.com/user-attachments/assets/03ffe16f-8131-46c3-929f-42742ce9611f)
![image](https://github.com/user-attachments/assets/ca36e453-a32f-4e6a-96fd-df90379b660b)
![image](https://github.com/user-attachments/assets/622869e0-d7eb-4b22-9ae8-da9d7cbb7720)
![image](https://github.com/user-attachments/assets/36bde1c3-414e-4dc9-8b71-c6812795bf2f)
![image](https://github.com/user-attachments/assets/21d4f5b0-250b-4dff-85ea-cb5b98dfd86b)

#### 프로젝트 진행 :
- 24년 5월 4주차 : 기획서 작성 완료 및 환경 제작 완료
- 24년 6월 1,2주차 : Vive XR Elite 플러그인 연동 및 Vive Ultimate Tracker 작동 테스트
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
- CPR 압박 과정을 리듬게임 형식으로 제작하게 되어 해당 판정에 대한 범위 및 레이턴시 설정하는데에 어려움이 있었다.
  1. 언리얼 내의 메타사운드를 활용해 120bpm (CPR 압박 속도 100~120bpm) 으로 비트사운드를 개발하여 압박에 관한 타이밍을 알려주었다. 
  2. 판정에 관한 판정 범위 증가를 해주었다. 시중에 있는 리듬 게임을 참고하여 6fps의 레이턴시를 주고 해당 입력 값 들 중 최고값으로 판정하였다. 
     판정 범위 증가 사유 : 
     1. 애니를 직접 압박 한다는 점
     2. 실제 리듬게임 방식과 다르게 압박데이터가 틱 단위로 넘어와 그래프 형식이라 판정 체크 시 최고 점수가 아닐 수 있다는 점
     3. VR 환경에서의 60fps가 고정적이지 않다는 점을 감안 
- 일반인, CPR 자격증 보유자, 현직 119 구조대원 등의 직접적 체험 후 피드백 적용이 쉽지 않았다. 
  CPR에 관한 지식이 있고 CPR을 시행할 수 있는 전문가라고 하더라도 VR에 익숙치 않은 사람들이 다수였다. 해당 부분에 관하여 사전에 VR 숙련도에 관한 질문을 하고 Case를 분류하여 난이도 조절 및 피드백을 받는 방식으로 하였다.

#### 기타 :
- CPR 기본 사항
[01_CPR 메인.pdf](https://github.com/user-attachments/files/17533674/01_CPR.pdf)

- Vive XR Elite 및 Vive Ultimate Tracker 사용방법
[99_Vive XR Elite 사용 방법 정리.pdf](https://github.com/user-attachments/files/17533669/99_Vive.XR.Elite.pdf)


### 2403~2405 광주반도체 직업체험
#### 개발환경 : Unreal Engine 5.1 / Desktop i9-10900 RTX3070 RAM 32G 
#### 사용장비 : Oculus Queset2
#### 프로젝트 요약 : 반도채 8대 공정의 학습을 위한 VR 체험 콘텐츠. 
#### 프로젝트 주요기능: 
- 반도체 공정 학습을 위한 도구 사용을 현실과 동일 시 하여 학습효과 증대

![광주반도체_ScopeCut](https://github.com/user-attachments/assets/93ef98f3-d1e6-47ac-add6-ab87736b4668)

- 학습모드 / 퀴즈모드로 나누어서 체험에서 끝이 아닌 평가 및 교육효과 증대

#### 프로젝트 진행 : 
- 24년 3월 2주차 : 프로젝트 생성, 체험 방식(학습모드 / 퀴즘모드) 에 따른 GameInstance 및 GameMode 설계, 사용자의 선택에 따른 시나리오 Level Open 테스트
  1. 학습모드 : 체험자가 반도체 장비에 익숙해지기 전 학습 및 체험하는 콘텐츠
  2. 퀴즈모드 : 반도체 장비가 익숙해지고 시험 및 테스트를 위해 진행하는 콘텐츠
- 24년 3월 3주차 : 학습모드 / 퀴즈모드를 분리하여 각 모드 별 시나리오 진행 방식 설계
- 24년 3월 4주차 : 각 모드 별 통신 테스트, 반도체 작동방식 숙지 및 Guide Widget 및 Trigger Guide 개발
- 24년 4월 1~3주차 : 반도체 검사기 인터랙션 개발
- 24년 4월 4주차 : 반도체 검사기 유지보수 인터렉션 개발
- 24년 4월 5주차 : 1차 테스트 패키징 (학습모드 QA 진행)
- 24년 5월 1주차 : 피드백 적용 후 2차 테스트 패키징
- 24년 5월 2주차 : 2차 피드백 적용 및 퀴즈모드 통신테스트
- 24년 5월 3주차 : 3차 테스트 패키징 (학습모드 / 퀴즈모드)
- 24년 5월 4주차 : 퀴즈모드 점수 송수신 관련 오류 수정
- 24년 5월 5주차 : 최종 패키징 및 납품

#### 프로젝트 이슈사항 및 해결방안 :


### 2402~2403 부산항만연수원 지게차 안전사고 예방  
#### 개발환경 : Unreal Engine 5.1 / Desktop i9-10900 RTX3070 RAM 32G 
#### 사용장비 : Vive Pro / BaseStation (2EA) 
#### 프로젝트 요약 : 지게차 후방 충돌 사고 예방을 위한 VR 안전체험 학습 및 시청형 VR360
#### 프로젝트 주요기능: 
- LineTrace를 활용환 인터랙션 제작

![ForkLift_Teleport](https://github.com/user-attachments/assets/c885c6a3-9949-469e-9fb8-4173db66207e)
![ForkLift_LineTrace](https://github.com/user-attachments/assets/ecf0e523-8b88-4bd4-b2f8-d20af8ef86d8)

- SceneCapture2D를 활용한 백미러 및 후방충돌방지 카메라 뷰

![ForkLift_BackMirror2](https://github.com/user-attachments/assets/7dddd779-6658-463e-b2b8-a9579202b2fb)
![ForkLift_BackMirror](https://github.com/user-attachments/assets/461c5790-8c28-46ae-aaa3-a7837f502bff)

- 시청형 VR360 진행 시 통신을 위한 Widget

![시청형](https://github.com/user-attachments/assets/37d5ca6f-5b8d-4692-843f-cd2d9f93d6d9)

#### 프로젝트 진행 : 
- 24년 2월 1,2주차 : 프로젝트 생성, 체험모드에 따른 GameInstance 및 GameMode 설계 개발
  1. 체험형은 HMD를 활용한 인터랙션을 활용한 사용자의 직접 체험
  2. 시청형 VR360은 HMD를 착용하여 자동 재생 되다가 인터랙션이 필요한 부분에 일시정지, EyeTracking으로 일정시간 만족하여야 다시 재생되는 방식
- 24년 2월 3주차 : 시청형 통신 테스트
  1. 제어 PC에 패킷 Send 및 Receive
  2. 수신받은 String에 따른 Play, Stop, End 테스트
- 24년 2월 4,5주차 : 기본 인터랙션 개발 및 테스트 / Trigger Guide 및 3D Title 개발
- 24년 3월 1주차 : LineTrace를 활용한 인터랙션 개발 및 테스트
- 24년 3월 2주차 : 1차 테스트 패키징 (+광주반도체 개발 투입)
- 24년 3월 3주차 : 피드백 적용 2차 테스트 패키징 및 VR360 시청형 촬영
- 24년 3월 4주차 : 최종 패키징 및 VR360 촬영 마무리 납품

#### 프로젝트 이슈사항 및 해결방안 :
- 해당 프로젝트는 두 가지 방식으로 납품이 되었는데, 시청형 VR360의 촬영에 어려움이 있었다.
  1. 렌더링 PC가 따로 있었다면 좀 더 수월한 촬영 및 개발이 이루어졌을 것 같다.
 
- 두 가지 프로젝트를 동시에 진행하였는데, 개발에 대한 우선순위를 정하여 중요한 부분부터 차례대로 해결을 해나갔다.

### 2311~2401 거창 승강기 CBT 승강기
#### 개발환경 : Unreal Engine 5.1 / Desktop i9-10900 RTX3070 RAM 32G 
#### 사용장비 : Vive Pro / BaseStation (2EA) 
#### 프로젝트 요약 :
#### 프로젝트 주요기능: 
#### 프로젝트 진행 : 
#### 프로젝트 이슈사항 및 해결방안

### 2309~2312 폴리텍 꿈드림공작소 
#### 개발환경 : Unreal Engine 5.1 / Desktop i9-10900 RTX3070 RAM 32G 
#### 사용장비 : Vive Pro / BaseStation (2EA) 
#### 프로젝트 요약 :
#### 프로젝트 주요기능: 
#### 프로젝트 진행 : 
#### 프로젝트 이슈사항 및 해결방안

### 2307~2309 재난 안전 체험 (지진발생 즉시대피)
#### 개발환경 : Unreal Engine 5.1 / Desktop i9-10900 RTX3070 RAM 32G 
#### 사용장비 : Vive Pro / BaseStation (2EA) 
#### 프로젝트 요약 :
#### 프로젝트 주요기능: 
#### 프로젝트 진행 : 
#### 프로젝트 이슈사항 및 해결방안

### 2305~2307 재난 안전 체험 (태풍발생 즉시대피)
#### 개발환경 : Unreal Engine 5.1 / Desktop i9-10900 RTX3070 RAM 32G 
#### 사용장비 : Vive Pro / BaseStation (2EA) 
#### 프로젝트 요약 :
#### 프로젝트 주요기능: 
#### 프로젝트 진행 : 
#### 프로젝트 이슈사항 및 해결방안

### 2303~2305 재난 안전 체험 (지진발생 실내대비)
#### 개발환경 : Unreal Engine 5.1 / Desktop i9-10900 RTX3070 RAM 32G 
#### 사용장비 : Vive Pro / BaseStation (2EA) 
#### 프로젝트 요약 :
#### 프로젝트 주요기능: 
#### 프로젝트 진행 : 
#### 프로젝트 이슈사항 및 해결방안
