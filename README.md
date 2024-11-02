# Samwoo
## 경력기술서
![image](https://github.com/user-attachments/assets/fb500b96-04cf-4e56-a14e-fb57213768a7)![image](https://github.com/user-attachments/assets/f473eefc-3e1e-42ae-bd23-1920a69c52eb)


## OneDrive 시연영상 경로
https://1drv.ms/f/c/4fc9c46aee2cb608/Ej_JjQ8lMRNOh_m4A-ARKmMBCZxQNFkPvfIEkhd_qgBh3w?e=rlM518

---
## 목차
[CPR 체험](#CPR-체험)

[광주반도체 직업체험](#광주반도체-직업체험)

[지게차 안전사고 예방체험](#부산항만연수원-지게차-안전사고-예방)

[승강기 CBT](#거창-승강기-CBT-승강기)

[폴리텍 꿈드림공작소](#폴리텍-꿈드림공작소)

[재난 안전 체험 4종](#재난-안전-체험-4종)

---
## CPR 체험
#### 1.개발기간 : 2406~2408
#### 2.개발환경 : Unreal Engine 5.3 / Desktop i9-10900 RTX3070 RAM 32G
#### 3.사용장비 : Vive XR Elite / Vive Ultimate Tracker
#### 4.프로젝트 요약 : 실제 환경에서 응급상황 시 CPR 및 제세동기 사용을 직접 할 수 있도록 VR로 학습 및 체험.
![ScreenShot00000](https://github.com/user-attachments/assets/dd99c676-6fd6-4bfb-bd7c-c99c029bd63a)
#### 5.프로젝트 주요 기능 :
  * 리듬게임 형식의 3D Widget

![CPR_WidgetTest](https://github.com/user-attachments/assets/2eb102ef-4085-4e1a-93aa-0f026e164969)

  * 실제 애니의 위치가 변경되었을 시, VR 콘텐츠 상의 위치 재조정
![image](https://github.com/user-attachments/assets/6690f086-6784-40d8-9df3-e7aa5da6a208)
![image](https://github.com/user-attachments/assets/03ffe16f-8131-46c3-929f-42742ce9611f)
![image](https://github.com/user-attachments/assets/ca36e453-a32f-4e6a-96fd-df90379b660b)
![image](https://github.com/user-attachments/assets/622869e0-d7eb-4b22-9ae8-da9d7cbb7720)
![image](https://github.com/user-attachments/assets/36bde1c3-414e-4dc9-8b71-c6812795bf2f)
![image](https://github.com/user-attachments/assets/21d4f5b0-250b-4dff-85ea-cb5b98dfd86b)

#### 6.프로젝트 진행 :
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

#### 7.프로젝트 이슈사항 및 해결방안 : 
- Vive XR Elite와 Vive Ultimate Tracker의 호환은 5.2 버전이상에서의 베타버전으로만 제공하였기 때문에 최초 프로젝트 생성 시 5.1 버전으로 진행하여 5.3으로의 버전 업 문제가 있었다.
- Vive Ultimate Tracker를 쓰는 가장 큰 이유는 Tracker 추적을 통한 CPR 애니 위치 연동이였는데, 위치값 보정 및 화면 재조정이 쉽지 않았다. (가장 오래 걸린 작업)
- CPR 압박 과정을 리듬게임 형식으로 제작하게 되어 해당 판정에 대한 범위 및 레이턴시 설정하는데에 어려움이 있었다.
  1. 언리얼 내의 메타사운드를 활용해 120bpm (CPR 압박 속도 100~120bpm) 으로 비트사운드를 개발하여 압박에 관한 타이밍을 알려주었다. 
  2. 이지투맥스, 태고의 달인 등의 리듬 게임을 참고하여 6fps의 레이턴시를 주고 해당 입력 값 들 중 최고값으로 판정하였다.판정에 관한 판정 범위 증가를 해주었다. 
     판정 범위 증가 사유 : 
     1. 애니를 직접 압박 한다는 점
     2. 실제 리듬게임 방식과 다르게 압박데이터가 틱 단위로 넘어와 그래프 형식이라 판정 체크 시 최고 점수가 아닐 수 있다는 점
     3. VR 환경에서의 60fps가 고정적이지 않다는 점을 감안 
- 일반인, CPR 자격증 보유자, 현직 119 구조대원 등의 직접적 체험 후 피드백 적용이 쉽지 않았다. 
 CPR에 관한 지식이 있고 CPR을 시행할 수 있는 전문가라고 하더라도 VR에 익숙치 않은 사람들이 다수였다. 
 해당 부분에 관하여 사전에 VR 숙련도에 관한 설문지를 먼저 작성하고 해당 부분에 관한 Case를 분류하여 난이도 조절 및 피드백을 받는 방식으로 하였다.

#### 8.기타 :
- CPR 기본 사항
[01_CPR 메인.pdf](https://github.com/user-attachments/files/17533674/01_CPR.pdf)

- Vive XR Elite 및 Vive Ultimate Tracker 사용방법
[99_Vive XR Elite 사용 방법 정리.pdf](https://github.com/user-attachments/files/17533669/99_Vive.XR.Elite.pdf)

---

## 광주반도체 직업체험
#### 1.개발기간 : 2403~2405
#### 2.개발환경 : Unreal Engine 5.1 / Desktop i9-10900 RTX3070 RAM 32G 
#### 3.사용장비 : Oculus Queset2
#### 4.프로젝트 요약 : 반도채 8대 공정의 학습을 위한 VR 체험 콘텐츠. 
#### 5.프로젝트 주요기능: 
- 반도체 공정 학습을 위한 도구 사용을 현실과 동일 시 하여 학습효과 증대

![광주반도체_ScopeCut](https://github.com/user-attachments/assets/93ef98f3-d1e6-47ac-add6-ab87736b4668)

- 학습모드 / 퀴즈모드로 나누어서 체험에서 끝이 아닌 평가 및 교육효과 증대

![image](https://github.com/user-attachments/assets/ba7825d5-9041-466a-9853-f3b2e35162d9)

#### 6.프로젝트 진행 : 
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

#### 7.프로젝트 이슈사항 및 해결방안 :
- 사용자 체험 및 내부 테스트를 통해 퀴즈 패널의 높이 및 인터랙션 위치 등 사용자 편의성 개선을 위한 피드백을 많이 받고 적용하였다.
- 누구나 해당 체험을 즐길 수 있도록 반도체 장비에 대한 간단한 pdf 제작하여 콘텐츠 내부에 정보 UI를 배치하였다.
 
---

### 2402~2403 부산항만연수원 지게차 안전사고 예방
#### 1.개발기간 : 2402~2403
#### 2.개발환경 : Unreal Engine 5.1 / Desktop i9-10900 RTX3070 RAM 32G 
#### 3.사용장비 : Vive Pro / BaseStation (2EA) 
#### 4.프로젝트 요약 : 지게차 후방 충돌 사고 예방을 위한 VR 안전체험 학습 및 시청형 VR360
#### 5.프로젝트 주요기능: 
- LineTrace를 활용환 인터랙션 제작

![ForkLift_Teleport](https://github.com/user-attachments/assets/c885c6a3-9949-469e-9fb8-4173db66207e)
![ForkLift_LineTrace](https://github.com/user-attachments/assets/ecf0e523-8b88-4bd4-b2f8-d20af8ef86d8)

- SceneCapture2D를 활용한 백미러 및 후방충돌방지 카메라 뷰

![ForkLift_BackMirror2](https://github.com/user-attachments/assets/7dddd779-6658-463e-b2b8-a9579202b2fb)
![ForkLift_BackMirror](https://github.com/user-attachments/assets/461c5790-8c28-46ae-aaa3-a7837f502bff)

- 시청형 VR360 진행 시 통신을 위한 Widget

![시청형](https://github.com/user-attachments/assets/37d5ca6f-5b8d-4692-843f-cd2d9f93d6d9)

#### 6.프로젝트 진행 : 
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

#### 7.프로젝트 이슈사항 및 해결방안 :
- 부산항만연수원 VR 학습 체험자의 연령대가 높은 편이라 해당 부분에 관한 사용자 매뉴얼 작성 및 배포하였다. 
- 해당 프로젝트는 두 가지 방식으로 납품이 되었는데, 시청형 VR360의 촬영에 어려움이 있었다. 고성능 PC 혹은 렌더링 PC가 따로 있었다면 좀 더 수월한 촬영 및 개발이 이루어졌을 것 같다.
- 두 가지 프로젝트를 동시에 진행하였는데, 개발에 대한 우선순위를 정하여 중요한 부분부터 차례대로 해결을 해나갔다.

#### 8.기타 :

![image](https://github.com/user-attachments/assets/588e75b4-f8e8-4ce0-9547-f4407c58b77f)


---

### 2311~2401 거창 승강기 CBT 승강기
#### 1.개발기간 : 2311~2402
#### 2.개발환경 : Unreal Engine 5.3 / Desktop i9-10900 RTX3070 RAM 32G 
#### 3.사용장비 : Desktop i3-12100f RTX2080 RAM 16G 
#### 4.프로젝트 요약 : 승강기 설치 및 교체 교육 및 실습을 위한 CBT 10종

![image](https://github.com/user-attachments/assets/ca9541e9-64c2-4a93-b4f9-dfe585b391dd)

#### 5.프로젝트 주요기능: 
- UI에서 장비 선택 시 마우스 포인터에 해당 장비 이미지 생성

  ![Rope_mousepointer](https://github.com/user-attachments/assets/d020b7ca-1498-4f8d-bf12-2a0abec1a8c7)
  
- 선택한 장비의 잘못된 위치 클릭 시 오답 사운드 및 UI 표출

![image](https://github.com/user-attachments/assets/f8c47b93-9d71-43f5-8cc7-2225c67e9890)
  
- 선택한 장비의 인터랙션 진행 시 아웃라인 하이라이트 생성

  ![image](https://github.com/user-attachments/assets/274104b1-430e-40b3-948d-35806abd72f3)

- 해당 절차에 나레이션 및 자막 재생
- 나레이션 및 자막 한/영 설정 가능

  ![image](https://github.com/user-attachments/assets/19c37973-6033-41ab-935d-7a67da7b7182)

- 학습모드/영상모드 두 가지 방법으로 학습효과 증대
1. 학습모드 : 사용자가 직접 공구와 부품을 선택하여 조립, 분해를 학습 할 수 있는 모드
2. 영상모드 : 모든 절차가 자동으로 진행되며 학습을 위해 기초를 다질 수 있는 모드

![image](https://github.com/user-attachments/assets/42fe0a11-105b-446a-9d95-ff91f09cf46b)

#### 6.프로젝트 진행 : 
- 23년 11월 1~3주차 : 프로젝트 생성 및 절차적 진행을 위한 GameInstance 및 GameMode 개발
  1. 해당 프로젝트는 CBT 방식의 학습모드, 영상모드 두 가지 부분을 모두 고려하여 개발.
  2. 정답에 해당 하는 부품 및 도구들을 모두 배열에 담아두고 해당 인터랙션 때, 배열에 담긴 부품 및 도구를 선택하여야 정답처리가 되게 진행.
- 23년 11월 4~5주차 : Pawn 및 시나리오를 관리하는 Sequence 및 SequenceManager / 인터랙션을 관리하는 Interactor / 사운드재생을 관리하는 SoundManager 개발
  1. SequenceManager에 Pawn 및 Sequence 들을 추가하여 해당 시나리오에 맞게 구성 
  2. 인터랙션 시작 시 해당 Sound ID를 찾아 소리 및 나레이션 재생.
  3. 인터랙션 별 상태 지정 및 상태에 따른 인터랙션 개발.

![image](https://github.com/user-attachments/assets/3918b8d1-5855-478f-86e5-8767ddadc3bb)

- 23년 12월 1~2주차 : 로프식 엘레베이터 과속조절기 로프 교체 시나리오3 인터랙션 개발
- 23년 12월 3주차 : 영상모드 테스트 및 학습모드 피드백 적용
- 23년 12월 4주차 : GameInstance의 GameMode별 시나리오 재생 및 플레이 테스트
- 24년 1월 1주차 : 로프식 엘레베이터 승강장 출입문 교체 시나리오1 인터랙션 개발
- 24년 1월 2주차 : SequenceManager에서 특정 절차 선택 시 배열이 깨지는 버그 발생하여 수정 진행 (Index가 배열 전체를 벗어난 경우)
- 24년 1월 3~4주차 : 전체 시나리오 테스트 및 패키징
- 24년 2월 1주차 : 최종 테스트 완료 후 납품

#### 7.프로젝트 이슈사항 및 해결방안 : 

---

### 폴리텍 꿈드림공작소 
#### 1.개발기간 : 2309~2310
#### 2.개발환경 : Unreal Engine 4.22, 4.26, 5.1 / Desktop i9-10900 RTX3070 RAM 32G 
#### 3.사용장비 : Oculus Quest2 
#### 4.프로젝트 요약 : 기납품된 콘텐츠 30종 폴리텍 꿈드림공작소 로고 및 영상 추가하여 재패키징
#### 5.프로젝트 주요기능: 
#### 6.프로젝트 진행 : 
- 23년 9월 2주차 : 납품 우선순위 콘텐츠부터 깃에서 내려받아 수정 시작
- 23년 9월 3주차 : 로고 및 영상 추가 큰 이슈사항 없이 10종 완료
- 23년 9월 4주차 : 기납품된 콘텐츠 중 Unreal 버전이 낮거나 Oculus Quest2로 개발되지 않는 콘텐츠 버전 업 및 Oculus Queset2 버전 추가
- 23년 10월 1~3주차 : 해당 콘텐츠 모두 수정 완료 및 재패키징 완료
- 23년 10월 4주차 : 기납품 콘텐츠 중 App 버전 콘텐츠 수정
- 23년 10월 5주차 : App 버전 모두 테스트 완료 및 재패키징, 납품완료
#### 7.프로젝트 이슈사항 및 해결방안 :
- 짧은 시간동안 30종의 콘텐츠의 코드 파악 및 수정시간이 너무 짧았고, 버전이 낮거나 Oculus Queset2로 개발되지 않았던 콘텐츠들이 많아서 수정 및 추가개밸을 하는데 시간이 많이 소요되었다.
- 회사와 관계자 및 개발자들은 차후 업데이트 및 유지보수를 고려하여 개발하는 것이 중요하다는 것을 느꼈다.
- 주기적으로 버전 업이나 매뉴얼 작성이 필요하고 인수인계 및 코드리뷰 등의 자신이 한 것을 기록하거나 남겨두는 것이 중요하다는 것을 깨닫게 되는 프로젝트였다. 

#### 8.기타 :

![image](https://github.com/user-attachments/assets/be076c72-cde7-4c83-8054-142cd6ca04eb)
![image](https://github.com/user-attachments/assets/926112c8-9948-419e-b28f-c861ff5cd02b)

---

### 재난 안전 체험 4종
#### 1.개발기간 : 2303~2309
#### 2.개발환경 : Unreal Engine 4.26 / Desktop i9-10900 RTX3070 RAM 32G 
#### 3.사용장비 : Oculus Quest2 
#### 4.프로젝트 요약 : 각종 재난 발생 시 대처방안 학습을 위한 VR 콘텐츠
#### 5.프로젝트 주요기능: 
1. 태풍
- Ultra Dynamic Weather을 활용한 날씨 구현
- 나이아가라를 활용한 스파크 및 폭발
- LineTrace를 활용한 텔레포트 개발
- Material을 활용한 전구 깜빡임 개발 

![Tythoon_Start](https://github.com/user-attachments/assets/ad63078a-6d6f-40bc-b00c-7f200d540901) ![Tythoon_Teleport](https://github.com/user-attachments/assets/2cd9d26f-ddff-444d-ad3f-c6335fef15ec)
![Tyhtoon_Teleportend](https://github.com/user-attachments/assets/0abb9461-79f2-4b22-9564-d6e52b461f2e) ![Tyhtoon_Waterup](https://github.com/user-attachments/assets/dab034c4-b4a1-4912-a005-ff6758fcf12a)

2. 지진
- Distrutable Mesh를 활용한 지진 발생 시 물건 파괴 및 붕괴 구현
- 지진 효과를 위한 Vector 및 AddForce 활용
- 나이아가라를 활용한 담벼락 붕괴 시 이펙트 구현

![Earthquake_Table](https://github.com/user-attachments/assets/5fd2b9d1-9b61-4bd3-91c3-1419aabbb316) ![Earthquake_Wall](https://github.com/user-attachments/assets/a6e23ebd-64ef-4546-8482-787801e84509)
3. 공통
- 내부 환경 라이트 수정 및 조정

![image](https://github.com/user-attachments/assets/8aa6b0e6-b066-4b0f-ac40-5bc17a3f158c)
#### 6.프로젝트 진행 : 
- 23년 3월 1~3주차 : 
#### 7.프로젝트 이슈사항 및 해결방안 :
- 사용자 테스트를 통해 VR을 착용한 상태에서 지진 체험을 멀미없이 수행할 수 있게 하기 위한 Camera Shake, Add Force, Scene Move 등을 이용하여 최적의 방법을 적용하였다.
- 사용자가 청소년이였기 때문에 대한민국 초중고 평균키 등의 통계청 자료를 활용하여 인터랙션 높이를 지정하였다. (캘리브레이션을 활용하여 키에 따른 위치 조정) 
