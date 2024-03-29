# 웹 접근성 점검 퀵 가이드 

본 문서는 웹 페이지의 웹접근성 준수 여부를 확인하는 방법을 기술하고 있습니다.

웹접근성관련 기초 지식은 이미 습득한 상태라고 가정하고 진행합니다.

전문적인 지식이 필요한 경우에는 표준 문서를 확인해주시기 바랍니다.



## 표준

- [@W3C - WCAG 2.1](https://www.w3.org/TR/WCAG/)
- [@W3C/WAI - WAI-ARIA 1.1](https://www.w3.org/TR/wai-aria/)
- [@미래창조과학부 - 한국형 웹 콘텐츠 접근성 지침 (KWCAG 2.1)](https://www.wah.or.kr:444/Participation/guide.asp)
- [@미래창조과학부 - 모바일 애플리케이션 콘텐츠 접근성 지침 2.0](https://www.wah.or.kr:444/board/boardView.asp?page=1&brd_sn=4&brd_idx=1014)
- [@과학기술정보통신부 - KWCAG2.2 개정예정 분석 보고서](https://www.wah.or.kr:444/board/boardView.asp?brd_sn=5&brd_idx=1032)



> WCAG2.0 ≒ KWCAG 2.1 (상호호환)

> 미래창조과학부 - 현,  과학기술정보통신부



## 점검 범위

### 법적 개념

국가정보화기본법 제 32조 (장애인•고령자 등의 정보접근 및 이용 보장)

**인터넷을 통하여 정보나 서비스를 제공할 때 장애인·고령자 등이 쉽게 웹사이트**와 이동통신단말장치( 「전파법」에 따라 할당받은 주파수를 사용하는 기간통신역무를 이용하기 위하여 필요한 단말장치를 말한다. 이하 같다)에 설치되는 응용 소프트웨어를 **이용할 수 있도록 접근성을 보장하여야한다.**



### 실무 개념

불특정 다수를 클라이언트에게 판매되거나 운영되는 모든 웹사이트 & 페이지

단, 특정 사용자만 접근할 수 있는 인트라넷의 경우, 제외할 수 있다.

=> 다음 Top  O

=> 광고운영툴 X

  \- 고객사 이용대상이면 △ 

  \- 운영사 관리자만 이용하는 폐쇠적인 툴이라면 X





### 사내 운영툴은 웹접근성 준수 대상일까?

전사직원대상 서비스라면 준수하는 게 맞음

단, 사내 장애인 직원이 없다면 > 예외할 수 있음

사내 장애인 직원이 있는데 개선할 생각이 없다면, 국가인권위원회에 진정 > 법적 대응, 노동부 신고 GO

**결론. 실제 장애인 사용자가 접근할 가능성이 있는 서비스는 모두 대상**



### 점검 방법

웹접근성 점검 방법은 크게 코드 검사(리뷰), 기능 검사, 사용성 검사로 나눌 수 있다. (그냥 제가 맘대로 정한거라 통용되는 건 아님)

- 코드 검사(리뷰)는 HTML이나 CSS, JS 코드를 확인하여 문제점을 찾는 방법이다. 보통 웹 브라우저의 개발자 도구나, 오픈왁스, HTML Validate와 같은 툴을 이용한다.
- 기능 검사는 키보드나, 마우스 등의 입력도구나 보조기기를 이용하여 기능 동작 상 문제점을 찾는 방법이다. 예를들면 마우스로 동작 가능한 기능을 키보드로도 사용이 가능한지 확인하는 것이 여기에 해당된다.
- 사용성 검사는 사용자 입장에서 서비스를 실제 이용하면서 문제점을 찾는 방법이다. 스크린리더와 같은 보조공학기기를 이용하여 테스트를 하는 것이 여기에 해당된다.



**진행 순서**

<img src="/Users/gio/Documents/workspace/문서/qa1.png" alt="qa1" style="zoom:100%;" />





## 체크리스트

### 요약

| 검사항목                          | 체크 | 주요 유형                                                    |
| --------------------------------- | :--: | ------------------------------------------------------------ |
| 1.1.1 (적절한 대체 텍스트 제공)   | ***  | - img alt <br>- background-image IR                          |
| 1.2.1 (자막 제공)                 |      | - 자막, 수화, 대본 유무                                      |
| 1.3.1 (색에 무관한 콘텐츠 인식)   |  *   | - 색상으로만 구분 (그래프, 범례, 페이지네이션)               |
| 1.3.2 (명확한 지시 사항 제공)     |  *   | - 지시어(여기, 저기), 색상, 방향 등 한가지 감각 정보         |
| 1.3.3 (텍스트 콘텐츠의 명도 대비) | ***  | - 명도차 3:1 이상                                            |
| 1.3.4 (자동 재생 금지)            |      | - 렌더링 후, 영상/음악 재생                                  |
| 1.3.5 (콘텐츠 간의 구분)          |      | - 영역 구분                                                  |
| 2.1.1 (키보드 사용 보장)          | ***  | - 마우스 의존기능 유무<br/>- 마우스 == 키보드 기능 구현      |
| 2.1.2 (초점 이동)                 | ***  | - Tab / shift+Tab<br/>- Focus Outline                        |
| 2.1.3 (조작 가능)                 |  *   | - 컨트롤 영역 최소 18px 이상                                 |
| 2.2.1 (응답시간 조절)             |      | - 일정 시간 후 자동전환 회피                                 |
| 2.2.2 (정지 기능 제공)            |      | - 움직이는 콘텐츠 제어                                       |
| 2.3.1 (깜빡임과 번쩍임 사용 제한) |      | - 피카츄! 광과민성유발                                       |
| 2.4.1 (반복 영역 건너뛰기)        |  *   | - 본문 바로가기 유무<br>- 바로가기 목적지 연결               |
| 2.4.2 (제목 제공)                 |  **  | - 페이지 title 요소<br/>- 프레임 title 속성<br/>- Heading 제목 |
| 2.4.3 (적절한 링크 텍스트)        |  *   | - 링크 목적지                                                |
| 3.1.1 (기본 언어 표시)            |  *   | - html lang                                                  |
| 3.2.1 (사용자 요구에 따른 실행)   |  **  | - 새창알림 target="\_blank"<br>- 새창 레이어 열림<br>- 옵션 선택에 onchange로 페이지 전환 |
| 3.3.1 (콘텐츠의 선형구조)         |  **  | - 사용자 흐름<br>- 구조화(조직도)                            |
| 3.3.2 (표의 구성)                 |  **  | - caption, summary<br>- th, td 구분<br>- scope, id-headers   |
| 3.4.1 (레이블 제공)               | ***  | - 입력서식의 label, title, aria-label<br/>- label for, id 연결 |
| 3.4.2 (오류 정정)                 |  *   | - alert, notification, toast<br/>- 입력폼 오류시 적절성, 초점 |
| 4.1.1 (마크업 오류 방지)          |  *   | - 열고 닫기<br>- 중첩<br>- ID 중복, 속성 중복                |



### 세부내용

#### 1.1.1 (적절한 대체 텍스트 제공)

> 텍스트 아닌 콘텐츠는 그 의미나 용도를 인식할 수 있도록 대체 텍스트를 제공해야 한다.

`코드검사` > [open-wax](https://chrome.google.com/webstore/detail/openwax/bfahpbmaknaeohgdklfbobogpdngngoe?hl=ko), 개발자도구

- HTML
  - \<img\>, \<input type="image"\>, \<area\>, \<applet\> 요소에 alt 속성 제공 유무 확인
  - 제공된 alt 속성 값이 의미나 용도를 이해할 수 있는지 확인
    - 의미와 내용이 다르거나, 내용의 일부가 누락되거나 요약되었다면 오류
    - 장식용(꾸밈) 이미지에 대체텍스트를 제공하였다면 오류 (예, 도트, 점, 블릿)
  - 링크, 버튼 등의 역할을 하는지 확인 > 핵심 기능에 대한 설명이 포함되었는지 확인
- CSS
  - 텍스트, 픽토그램 등 의미가 포함된 이미지를 배경이미지(background-image)를 이용하여 의미있는 이미지를 제공하고 ir(image replacement) 정보 유무 확인
    - 참고 : 대체콘텐츠를 display:none; 이나 visibility:hidden; 등을 이용하여 숨길 경우, 화면낭독프로그램에서 인식할 수 없으므로 이용하지 않아야 한다.



#### 1.2.1 (자막 제공)

> 동영상, 음성 등 멀티미디어 콘텐츠를 이해할 수 있도록 자막, 대본 또는 수화를 제공해야 한다.

`사용성검사`  > 시각, 청각

- 멀티미디어 콘텐츠 뷰
  - 청각 정보
    - 멀티미디어 콘텐츠에 포함된 음성과 소리에 대한 대체 수단 제공(자막, 대본 또는 수화) 유무 확인
    - 대체 수단을 통해 동등하게 내용을 이해할 수 있는 지 확인 (내용적절성 판단)
  - 시각 정보
    - 멀티미디어 콘텐츠에 포함된 텍스트에 대한 대체 수단 제공(화면해설) 유무 확인
    - 대체 수단을 통해 동등하게 내용을 이해할 수 있는 지 확인
- 멀티미디어 콘텐츠 운영
  - 멀티미디어 콘텐츠 등록/운영 툴에서 대체수단을 제공할 수 있는 기능의 제공 유무 확인



#### 1.3.1 (색에 무관한 콘텐츠 인식)

> 콘텐츠는 색에 관계없이 데이터를 구분하여 인식될 수 있어야 한다.

`사용성검사` > 시각

`코드검사` > Win-CCA(old ver) 

- 콘텐츠(이미지, 그래프, 차트, 지도 등)를 색상만으로 구분하는지 확인
- 페이지 내비게이션, 메뉴, 현재 위치, 필수 항목, 선택 상태, 버튼 등을 색상만으로 구분하는지 확인
- 오류 발견시 CCA(Colour Contrast Analyser)를 활용해 색각이상 시뮬레이션을 진행하여 재확인



#### 1.3.2 (명확한 지시 사항 제공)

> 지시사항은 모양, 크기, 위치, 방향, 색, 소리 등에 관계없이 인식할 수 있어야 한다.

`사용성검사` > 시각, 청각

- 평가 대상 콘텐츠에서 한 가지 감각으로만 인식 가능한 지시사항이나 콘텐츠가 있는지 확인
  - 모양, 크기, 위치, 방향, 색, 소리 등 한 가지 감각만으로 인식할 수 있는 경우, 오류



#### 1.3.3 (텍스트 콘텐츠의 명도 대비)

> 텍스트 콘텐츠와 배경 간의 명도 대비는 3대 1 이상이어야 한다.

`사용성검사` > 시각

`코드검사` > [CCA](https://developer.paciellogroup.com/resources/contrastanalyser/), 개발자 도구

- 텍스트, 링크, 버튼 등에서 콘텐츠와 배경 간의 명도 대비가 기준 이상인지 확인

  - 그라데이션이나 테두리효과로 인해 전체 혹은 일부 영역이 기준치보다 낮은 경우
  - 밝은 배경을 제공하거나, 투명한 글자색상으로 인해 기준치보다 낮은 경우
  - 의미를 갖는 아이콘이나 픽토그램의 명도대비가 기준치보다 낮은 경우

- 텍스트 : css > color, background-color 값

- 텍스트 이미지 : CCA 찍어봄

  

- 참고 : 일반적으로 CCA(Colour Contrast Analyser)를 이용하여 측정

  - 최소 기준 4.5:1, 확대 가능한 콘텐츠의 경우 **3:1**로 완화
  - 중요도가 높은 콘텐츠는 7:1 이상, 주요 콘텐츠에 대해서는 사용성까지 고려하여 4.5:1 이상을 권장



#### 1.3.4 (자동 재생 금지)

> 페이지 로딩 시 자동으로 재생되는 소리를 사용하지 않아야 한다.

`사용성검사` > 시각

- 사용자의 조작없이 자동으로 재생되는 3초 이상의 소리가 있는지 확인
- 소리를 제어할 수 있는 수단을 제공하고 있는지 확인
- 제어수단이 정상적으로 동작하는지 확인
- 특정 영역에서 마우스 오버 혹은 키보드 초점 접근에 의해 소리가 자동으로 재생되는지 확인



- 예외조건
  - 자동으로 재생되는 소리는 3초 내에 멈추는 경우, PASS
  - 사전 경고한 경우, PASS
  - 페이지 전환 후, 바로 중단할 수 있는 수단(예, ESC, Enter 키로 정지) 제공시 PASS



#### 1.3.5 (콘텐츠 간의 구분)

> 이웃한 콘텐츠는 구별될 수 있어야 한다.

`사용성검사` > 시각

이웃한 콘텐츠간 경계를 구분할 수 있는지 확인

- 테두리를 이용하여 구분하고 있는가?
- 콘텐츠 사이에 시각적인 구분선을 삽입하고 있는가?
- 서로 다른 무늬를 이용하여 구분하고 있는가?
- 콘텐츠 배경색 간의 명도대비(채도)를 달리하여 구분하고 있는가?
- 줄 간격, 글자 간격 등 충분한 여백을 제공하여 콘텐츠 간 구분할 수 있는가?



#### 2.1.1 (키보드 사용 보장)

> 모든 기능은 키보드만으로도 사용할 수 있어야 한다.

`기능검사` > 키보드

`코드검사` > 개발자도구

- 대상 페이지를 Tab, Shift+Tab 키만 이용하여 모든 요소에 접근할 수 있는지 확인
- 기능을 가지는 요소에서 Enter, Spacebar, 방향키 등 키보드만 이용하여 동작할 수 있는지 확인
- 마우스 오버, 드래그 앤 드롭 등 마우스 이벤트 사용된 요소를 키보드로 동등한 수준으로 이용할 수 있는지 확인



- 예외 조건
  - 위치 지정 도구의 커서 궤적이 중요한 역할을 하는 콘텐츠(붓질 기능이 필요한 콘텐츠, 시뮬레이션 콘텐츠, 지리정보 응용 콘텐츠, 가상현실 콘텐츠 등), 움직임 측정 센서를 이용하는 콘텐츠는 이 검사 항목의 예외 콘텐츠로 간주한다. 그러나 예외 콘텐츠의 경우에도 위치 지정 도구나 움직임 측정 센서를 이용하는 기능을 제외한 나머지 사용자 인터페이스는 키보드만으로 사용할 수 있어야 한다.
  - 서비스 내부 단축키를 포함하고 있거나, 옵션으로 제공하고 있을 경우
    - 단축키으로만 해당 기능을 구현했는지 확인 (대체기능 제공여부 확인)



#### 2.1.2 (초점 이동)

> 키보드에 의한 초점은 논리적으로 이동해야 하며, 시각적으로 구별할 수 있어야 한다.

`기능검사` > 키보드

- 대상 페이지를 Tab, Shift+Tab 키만 이용하여 기능 요소에 접근할 수 있는지 확인
- 대상 페이지를 Tab, Shift+Tab 키만 이용하여 기능 요소에 초점(focus)이 시각화(outline)되는 지 확인
- 기능 요소가 아님에도 초점이 시각화되는 지 확인
  - 문맥상 접근이 필요없다면 오류
- 대상 페이지 내 tabindex 속성 사용 유무 확인
  - 접근성 향상/대응을 의도가 아닌 경우, tabindex 속성 사용 금지
- 초점의 이동 순서가 콘텐츠의 흐름에 맞는지 확인



#### 2.1.3 (조작 가능)

> 사용자 입력 및 컨트롤은 조작 가능하도록 제공되어야 한다.

`코드검사` > 개발자도구

- 사내 CSS Guide의 링크/버튼 영역 최소 크기 기준에 맞는 지 확인
  - PC : 18x18 

- KWCAG 2.1
  - 사용자 입력 및 컨트롤의 대각선 방향 길이가 6.0mm 이상되는지 확인
  - 사용자 입력 및 컨트롤의 조작 가능 영역은 15x15px 이상인지 확인
  - 링크, 사용자 입력 및 기타 컨트롤은 조작 영역 바깥 1픽셀 이상의 여백을 지공하고 있는지 확인
  -  [a11y inspector](https://chrome.google.com/webstore/detail/kwcag-a11y-inspector/ngcmkfaolkgkjbddhjnhgoekgaamjibo?hl=ko) 툴 이용 > 17inch, 1280 x 1024 설정



#### 2.2.1 (응답시간 조절)

> 시간제한이 있는 콘텐츠는 응답시간을 조절할 수 있어야 한다.

`사용성검사` > 시각, 청각

- 대표적인 콘텐츠 유형 : 입력시간제한, 자동 갱신, 자동 페이지 이동 등

- 시간제한이 있는 콘텐츠는 제공 유무 확인
- 시간제한을 조절할 수 있는 수단을 제공 유무 확인
  - 시간제한을 연장 또는 취소할 수 있는 수단이 있는지 확인
  - 시간제한 연장 또는 취소 수단의 동작 여부를 확인
  - 보조공학기기, 키보드 등에서도 동일한 기능이 동작하는 지 확인
  - 시간제한에 따른 남은 시간을 인식할 수 있는 정보가 제공되었는지 확인



- 예외 조건
  - 온라인 경매, 실시간 게임 등과 같이 반응 시간의 조절이 허용되지 않은 경우 예외
  - 다만 이 경우에도 사용자에게 시간제한이 있다는 것을 미리 알리고, 종료되었을 때 이를 알려야 함
  - 세션 만료시간이 20시간 이상인 경우 예외



#### 2.2.2 (정지 기능 제공)

> 자동으로 변경되는 콘텐츠는 움직임을 제어할 수 있어야 한다.

`사용성검사` > 시각

`기능검사` > 마우스 & 키보드



- 자동으로 변경되는 콘텐츠 제공 유무 확인
- 콘텐츠의 움직임을 제어할 수 있는 수단 제공 유무 확인
  - 재생, 정지, 이전, 다음 등
- 제어 수단 미제공된 경우, focus, mouseover 시 움직임을 정지할 수 있는 대체 기능을 제공하였는지 확인





#### 2.3.1 (깜빡임과 번쩍임 사용 제한)

> 초당 3~50회 주기로 깜빡이거나 번쩍이는 콘텐츠를 제공하지 않아야 한다.

`사용성검사` > 시각

- 깜빡이거나 번쩍이는 콘텐츠는 제공 유무 확인
  - 초당 3~50회 주기
- 깜빡이거나 번쩍이는 콘텐츠를 제공시, 사전에 경고나, 회피할 수 있는 수단을 제공하였는지 확인
- 깜빡이거나 번쩍이는 콘텐츠 발견시, Trace Center Photosensitive Epilepsy Analysis Tool (PEAT)을 이용하여 정밀 확인



#### 2.4.1 (반복 영역 건너뛰기)

> 콘텐츠의 반복되는 영역은 건너뛸 수 있어야 한다.

`사용성검사` > 시각

`기능검사` > 키보드

- 반복되는 영역(GNB, LNB 등)을 건너뛸 수 있는 링크 제공 유무 확인
- 반복 영역 건너뛰기 링크의 위치 확인
- 반복 영역 건너뛰기 링크에 초점 접근시 시각적으로 노출되는 지 확인
- 반복 영역 건너뛰기 링크 외 불필요한 링크가 있는지 확인
- 반복영역 건너뛰기 링크 텍스트의 적절성 확인
- 반복영역 건너뛰기 링크 정상 동작 확인



#### 2.4.2 (제목 제공)

> 페이지, 프레임, 콘텐츠 블록에는 적절한 제목을 제공해야 한다.

`사용성검사` > 시각

`코드검사` > [open-wax](https://chrome.google.com/webstore/detail/openwax/bfahpbmaknaeohgdklfbobogpdngngoe?hl=ko), [HeadingsMap](https://chrome.google.com/webstore/detail/headingsmap/flbjommegcjonpdmenkdiocclhjacmbi?hl=ko), 개발자도구

- \<title\>
  - \<title\> 요소 및 값 제공 유무 확인
  - 제공된 페이지 제목이 적절한지 확인
    - [HTML Convention - Page Infomation]([https://wiki.daumkakao.com/display/dktdev/%5BHTML+Convention%5D+Page+Infomation](https://wiki.daumkakao.com/display/dktdev/[HTML+Convention]+Page+Infomation)) 기준
    - 꾸밈을 위해 특수기호를 반복적으로 사용하였는지 확인
    - 같은 서비스 내에 같은 제목을 사용하고 있는지 확인
    - 서비스내 페이지 제목이 일관성이 있게 제공하고 있는지 확인

- frame
  - \<iframe\>, \<frame\> 등 프레임 요소에 title 속성 제공 유무 확인
  -  각 프레임의 콘텐츠를 설명할 수 있는 제목을 제공하고 있는지 확인
  - 빈 프레임에 프레임 제목을 적절히 제공하였는지 확인

- Heading
  - 문서 내 콘텐츠의 구조적 관계를 이해할 수 있는지 확인
  - 콘텐츠의 제목, 소제목, 단락 제목 등 단락이 나뉘는 경우, Heading 요소를 이용하고 있는지 확인
    - [HTML Convention - Contents]([https://wiki.daumkakao.com/display/dktdev/%5BHTML+Convention%5D+HTML+Contents](https://wiki.daumkakao.com/display/dktdev/[HTML+Convention]+HTML+Contents)) 기준
  - 콘텐츠 내용 상 동일 레벨의 제목이지만, Heading이 누락되거나 레벨이 잘못 제공한 경우가 있는지 확인 



#### 2.4.3 (적절한 링크 텍스트)

> 링크 텍스트는 용도나 목적을 이해할 수 있도록 제공해야 한다.

`코드검사` > [open-wax](https://chrome.google.com/webstore/detail/openwax/bfahpbmaknaeohgdklfbobogpdngngoe?hl=ko), 개발자도구

- \<a\> 요소의 값이 제공되었는지 확인

- \<a\> 요소의 값이 링크 목적지 정보를 대표하고 있는지 적절성 확인

- 기능을 제어 할 수 있는 요소 (\<button\>, \<input tyep="button | submit\">)에서 용도나 목적을 이해할 수 있는지 확인

  

- 예외 조건

  - WAI-ARIA (aria-expanded, role 등) 를 이용하여 대체 정보를 제공하고 있는 경우

- 권장

  - 목적지가 동일한 연속된 링크는 하나의 링크로 구현하는 것을 권장

  - 콘텐츠가 접히거나 펼쳐지는 경우 그 상태나 기능을 명확히 인식할 수 있는 정보를 제공함
    - 현재 상태(선택/해제)를 표시하거나 상태 변경(사용하기/해제하기)기능을 가지는 경우, 단순 명사형(설정, 사용 등)으로 제공하지 말고 동작이나 상태를 나타낼 수 있는 표현 (설정하기, 설정됨, 사용하기, 사용 중, 선택됨)과 같이 제공

  - 링크 텍스트가 탭(Tab)형태일 경우 탭 구조 임을 알 수 있도록 "탭"에 대한 정보를 제공을 권장



#### 3.1.1 (기본 언어 표시)

> 주로 사용하는 언어를 명시해야 한다.

`코드검사` > [open-wax](https://chrome.google.com/webstore/detail/openwax/bfahpbmaknaeohgdklfbobogpdngngoe?hl=ko), 개발자도구

- HTML
  - 대상 페이지의 HTML DTD(문서 형식 정의)와 \<html\>요소의 lang 속성 확인
  - HTML DTD에 따른 lang 속성 값이 적절한지 확인

- 프레임으로 연결된 페이지
  - 동일 서비스의 페이지로 연결되는 경우, 수정 권장
  - 연결된 페이지에 마크업 내용이 없는 경우, 예외
  - 외부 API 페이지로 연결되는 경우, 예외



#### 3.2.1 (사용자 요구에 따른 실행)

> 사용자가 의도하지 않은 기능 (자동 새 창 열림, 초점 자동 이동에 의한 맥락 변화 등)은 실행되지 않아야 한다.

`사용성검사` > 시각

`코드검사` > [open-wax](https://chrome.google.com/webstore/detail/openwax/bfahpbmaknaeohgdklfbobogpdngngoe?hl=ko), 개발자도구

`기능검사` > 키보드



- 사용성
  - 대상 페이지 로딩 시에 자동으로 새창(new window)이 열리는지 확인
  - 대상 페이지 로딩 시에 주요 콘텐츠 영역을 덮는 레이어(layer)가 제공되었는지 확인
  - 사용자가 예상할 수 없는 상태에서 실행되어 콘텐츠 탐색을 방해하는 문제가 있는지 확인

- HTML
  - window.open 이벤트를 통해 새창이 열리는지 확인
    - a 요소에 target="_blank" 속성이 제공되었는지 확인
    - button 요소와 같이 target 속성 사용이 어려운 경우, title이나, 숨김 텍스트로 대체정보를 제공하고 있는지 확인
      예) title="새창열림", \<span class="screen_out"\>새창\</span\>
  - \<select\>, \<input type="checkbox\">, \<input type="radio"\> 등에 onchange 이벤트를 제공 유무 확인
    - 옵션을 수정하는 것만으로 페이지가 이동되거나, 초기화되는 문제가 있는지 확인



#### 3.3.1 (콘텐츠의 선형구조)

> 콘텐츠는 논리적인 순서로 제공해야 한다.

`코드검사` > [Web Developer](https://chrome.google.com/webstore/detail/web-developer/bfbameneiokkgbdmiekhjnmfkcnldhhm?hl=ko), 개발자도구

`사용성검사` > 시각

- CSS를 disable한 상태에서 콘텐츠의 접근 순서, 구조 등이 적절한지 확인
- 계층 구조를 가지는 콘텐츠에서 semantic element 사용 여부 확인
  - semantic element (구조적 마크업) : Sectioning(article, aside, nav, section), Heading(h1~h6), ul(ol)-li, dl-dt-dd, landmark 등



#### 3.3.2 (표의 구성)

> 표는 이해하기 쉽게 구성해야 한다.

`코드검사` > [open-wax](https://chrome.google.com/webstore/detail/openwax/bfahpbmaknaeohgdklfbobogpdngngoe?hl=ko), 개발자도구

- \<caption>, summary
  - \<caption> 요소 값 제공 유무 확인
  - \<caption> 요소 값이 표를 대표할 수 있는지 적절성 확인
  - \<caption> 요소에 display:none, visibility:hidden,  hidden Attribute 등으로 숨김 처리되었는지 확인
  - HTML5 미만인 경우, \<table> 요소의 summary 속성 값이 적절히 포함되었는지 확인
  - HTML5 이상인 경우, 표의 요약정보가 \<caption>에 포함하여 포함되었는지 확인 

- th, td
  - 표의 제목셀과 내용셀을 마크업으로 구분하고 있는지 확인
    - \<thead>, \<tbody>, \<tfoot>, \<th>, \<td>
  - 제목 행이나 제목 열에 \<th> 요소가 용도에 맞게 사용되었는지 확인

- 복잡한 구조의 표
  - 다층 데이터용 표(Layered tables)인지 확인 
    - 테이블 > 테이블 > 테이블 중첩한 경우
    - 시각적으로 하나의 표를 여러 개의 table로 나누어 제공한 경우
  - 병합된 표에서 id와 headers 속성 제공하고 있는 지 확인
  - 제공된 id와 headers 속성의 연결 관계가 적절한지 확인
  - 단순 데이터용 표(Simple tables)는 \<th> 요소, scope 속성을 제공하고 있는지 확인
  - 제공된 scope 속성 값이 적절한지 확인

- 배치용 테이블
  - 표 안의 콘텐츠가 구조적 정보를 가지지 않는 단순 배치용테이블 (Layout table)에 \<caption>, summary, \<th>, scope, id, headers 등의 값을 제공하고 있는지 확인



#### 3.4.1 (레이블 제공)

> 사용자 입력 서식에는 대응하는 레이블을 제공해야 한다.

`코드검사` > [open-wax](https://chrome.google.com/webstore/detail/openwax/bfahpbmaknaeohgdklfbobogpdngngoe?hl=ko), 개발자도구

- 사용자 입력 서식에 대응하는 레이블 제공 유무 확인
  - 사용자입력서식 : \<input>, \<textarea>, \<select> 요소 등
    - \<input type="image | hidden | submit | button | reset"> 제외
  - 레이블 : \<label>, title (attribute), aria-label
- 사용자 입력 서식에 대응하는 레이블이 입력서식의 용도와 목적에 적절한지 확인
- 사용자 입력 서식에 대응하는 레이블의 연결관계가 적절한지 확인
  - \<label for> 속성 값과 \<input id> 속성 값을 동일 여부
- \<label> 요소에 숨김 속성(display:none, visibility:hidden 등)을 사용하고 있는 지 확인
  - 스크린 리더에서 접근이 불가능한 속성 해당



- 참고 : 시각적으로 노출된 레이블이 없이 placeholder와 같이 입력폼 내부에 안내 문구를 대체한 경우, 사용자가 내용을 지우지 않고 입력할 가능성이 높으므로 삭제 안내 또는 상황에 따라 적절하게 삭제할 수 있는 기능을 같이 구현하는 것을 권장



#### 3.4.2 (오류 정정)

> 입력 오류를 정정할 수 있는 방법을 제공해야 한다.

`기능검사` 

- 입력된 값에 오류가 있거나 필수 항목을 누락한 경우 사용자에게 오류에 대한 안내 메시지를 제공한다.
- 입력서식에 값을 누락하거나 잘못된 값을 입력하여 오류를 발생시킨 후, 사용자에게 안내 메시지가 적절하였는지 반복 확인
- 오류 발생시, 오류가 발생한 입력서식으로 초점 이동이 되는지 확인
- 오류 안내는 장애인 보조 기기에서 인지할 수 있는지 확인



#### 4.1.1 (마크업 오류 방지)

> 마크업 언어로 작성된 문서는 요소의 열고 닫음, 중첩 관계 및 속성 선언에 오류가 없어야 한다.

`코드검사` > [Web Developer](https://chrome.google.com/webstore/detail/web-developer/bfbameneiokkgbdmiekhjnmfkcnldhhm?hl=ko), Lint, 개발자도구

- W3C 유효성 검사도구를 사용하여 마크업 오류 확인
- 마크업 문서의 DOCTYPE이 적절히 제공되었는지 확인
- 태그가 적절히 열고 닫혔는지 확인
- 태그간 중첩 관계가 올바르게 선언되었는지 확인
- 한 요소에 중복된 속성이 선언되었는지 확인
- 한 페이지에 id 속성 값이 중복 제공되었는지 확인

