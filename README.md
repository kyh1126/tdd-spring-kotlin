# TDD with Spring Kotlin API


## Wright Flyer 프로젝트

- 받았던 기획서 중 하나 선택해볼까 하다가 저작권(?) 같은게 있으면 어쩌지 하는 고민이 들었다.
- 고민이 너무 길어지는군!! 정말로 생각을 해볼 때이다.
- TDD 를 익숙하게 만들어 줄 프로젝트이니, 이름은 라이트 형제들이 발명한 세계 최초 동력비행기 프로젝트로 한다!
    - 자전거 수리공을 하며 꿈을 키웠던 라이트 형제들처럼 TDD 에 익숙해지길 바라며.


## 뭘 만들어 볼까나?
  
### 내가 필요한게 뭐가 있을까?
    1. 스터디 관련 API 를 만들면 좋겠다
        - 스터디는 앞으로도 계속 할거란 포부와 함께!!
    2. 보통 스터디는 매주 리볼빙 스터디로 진행되니 종료 시점이 정해져있다.
        - 목표 달성치를 챕터 별 기준으로 퍼센티지로 보여주고,
        - 달성한 후에는 Complete 표시, 
        - 이슈가 생겨서 미뤄지는 날은 Pending 표시하면 어떨까?
    3. 그 후 세세한 기능들은 Optional 로 하자.


# 필요한 API 를 정의해보자

## 1. POST /goals/add

- 목표를 저장한다.
    - 주제명
    - 시작일
        - 종료일은 자동 계산된다. - `Optional`
    - 총 목표 (챕터 갯수 / 페이지 수 선택)
    - 달성 단위 (1회당 몇 챕터 / 페이지)
    - 진행 상태 (작성중 / 중단 / 진행중 / 완료)
    - 진행 날짜 (월요일 ~ 일요일 중 멀티 선택 / 선택안함) - `Optional`
    - 기타 - `Optional`
    - 생성일시
    - 수정일시
- 히스토리를 남긴다.


## 2. GET /goals

- 목표 리스트를 조회한다.
    - 주제명 
    - 시작일
    - 종료일
    - 진행 상태
    - 진행 날짜 기반 `정기 / 수시` 표시
    - 달성 퍼센티지
    - 수정일시


## 3. GET /goals/{id}

- 목표를 조회한다.
- 히스토리를 보여준다.


## 4. PUT /goals/{id}

- 목표를 수정한다.
    - 주제명
    - 총 목표
    - 달성 단위
    - 진행 날짜
    - 기타
    - 수정일시
- 히스토리를 남긴다.


## 5. DELETE /goals/{id}

- 목표를 삭제한다.
- 히스토리를 남긴다.
