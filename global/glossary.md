# Global Glossary

## 목적

이 문서는 모든 프로젝트에서 공통으로 사용하는 UI/기획 용어의 기준입니다.
사람은 기능정의서, L10N, QA TC, decisions를 같은 용어로 읽을 수 있고, AI는 같은 개념을 다른 기능으로 오해하지 않도록 이 문서를 먼저 참고합니다.

## 기본 원칙

- 기능정의서 본문은 한글 용어를 우선 사용한다.
- 디자인 시스템 컴포넌트명은 영문 표준명을 병기하거나 메타 정보로 사용한다.
- 상태값은 영어 표준값을 그대로 사용한다. 예: `Default`, `Hover`, `Focused`, `Selected`, `Disabled`.
- `팝업`이라는 일반 표현은 피하고, `Modal`, `Pop-up`, `Popover` 중 하나로 구체화한다.
- 별도 `Context Menu` 용어는 사용하지 않는다. 우클릭, 더보기, 항목 작업 메뉴는 `Popover`로 정리한다.
- 프로젝트 고유 화면명, 기능명, 도메인 용어는 global이 아니라 각 프로젝트의 references 또는 decisions에 둔다.
- 용어 불일치는 가능한 한 output에서 표준 용어로 보정하되, 의미가 애매하면 사용자 확인이 필요하다.

## Component Names

### Foundation

| 표준 한글 용어 | 디자인 컴포넌트 | 설명 |
|---|---|---|
| 색상 | `Colors` | 제품 전반의 색상 토큰 |
| 그리드 | `Grid` | 레이아웃 격자 기준 |
| 반경 | `Radius` | 모서리 둥글기 기준 |
| 그림자 | `Shadow` | elevation 또는 shadow 기준 |
| 간격 | `Spacing` | margin, padding, gap 기준 |
| 타이포그래피 | `Typography` | 글꼴, 크기, 행간 등 텍스트 기준 |

### Atomic

| 표준 한글 용어 | 디자인 컴포넌트 | 설명 |
|---|---|---|
| 배지 | `Badge` | 상태, 개수, 라벨을 작게 표시 |
| 버튼 | `Button` | 사용자가 클릭해 명령을 실행하는 요소 |
| 체크박스 | `Checkbox` | 복수 선택 또는 on/off 선택 |
| 칩 | `Chip` | 선택값, 필터, 태그 등을 작은 단위로 표시 |
| 구분선 | `Divider` | 영역을 시각적으로 분리 |
| 입력창 | `Input` | 텍스트를 입력하는 필드 |
| 라벨 | `Label` | 입력값이나 항목의 이름 |
| 라디오 버튼 | `Radio` | 여러 옵션 중 하나만 선택 |
| 슬라이더 | `Slider` | 연속값을 조절하는 입력 |
| 토글 | `Toggle` | 설정을 켜고 끄는 스위치 |
| 태그 | `Tag` | 콘텐츠 분류 또는 메타 정보 표시 |

### Composite

| 표준 한글 용어 | 디자인 컴포넌트 | 설명 |
|---|---|---|
| 아코디언 | `Accordion` | 접고 펼치는 영역 |
| 말풍선 | `Bubble` | 대화형 또는 안내형 말풍선 UI |
| 캘린더 | `Calendar` | 날짜를 달력 형태로 표시하는 UI |
| 카드 | `Card` | 관련 정보를 묶어 보여주는 컨테이너 |
| 캐러셀 | `Carousel` | 여러 콘텐츠를 넘겨 보는 UI |
| 날짜 선택기 | `Date Picker` | 날짜를 입력하거나 선택하는 UI |
| 모달 | `Modal` | 배경을 막고 사용자 응답을 요구하는 창 |
| 페이지네이션 | `Pagination` | 페이지 단위 이동 UI |
| 팝업 | `Pop-up` | 광고, 공지, 프로모션 등 독립 안내 UI |
| 프로그레스 | `Progress` | 작업 진행률 또는 진행 상태 표시 |
| 스크롤 바 | `Scroll bar` | 스크롤 가능 영역의 위치 표시 |
| 스테퍼 | `Stepper` | 단계별 진행 또는 단계형 입력 UI |
| 탭 | `Tab` | 같은 화면 안에서 콘텐츠를 전환하는 UI |
| 툴팁 | `Tooltip` | hover 또는 focus 시 보조 설명을 제공 |

### Data Display

| 표준 한글 용어 | 디자인 컴포넌트 | 설명 |
|---|---|---|
| 빈 상태 | `Empty State` | 표시할 데이터가 없을 때의 안내 상태 |
| 리스트 | `List` | 항목을 나열하는 UI |
| 프로필 | `Profile` | 사용자 정보 표시 |
| 평점 | `Rating` | 별점 등 평가값 표시 |
| 테이블 | `Table` | 행과 열 구조의 데이터 목록 |

### Feedback

| 표준 한글 용어 | 디자인 컴포넌트 | 설명 |
|---|---|---|
| 백드롭 | `Backdrop` | 모달 등 오버레이 뒤의 dim 영역 |
| 스켈레톤 | `Skeleton` | 콘텐츠 로딩 전 자리 표시 |
| 스낵바 | `Snackbar` | 화면 하단 중심의 알림 또는 액션 안내 |
| 스피너 | `Spinner` | 처리 중임을 나타내는 로딩 표시 |
| 토스트 | `Toast` | 짧게 나타났다 사라지는 상태/결과 알림 |

### Navigation & Overlay

| 표준 한글 용어 | 디자인 컴포넌트 | 설명 |
|---|---|---|
| 바텀시트 | `BottomSheet` | 모바일 하단에서 올라오는 패널 |
| 브레드크럼 | `Breadcrumb` | 현재 위치 경로 표시 |
| 플로팅 버튼 | `Floating Button` | 화면 위에 떠 있는 주요 액션 버튼 |
| GNB | `GNB` | 전역 또는 상단 주요 내비게이션 |
| 내비게이션 | `Navigation` | 화면 이동 구조 전반 |
| 오버플로 메뉴 | `Overflow Menu` | 더보기 또는 추가 작업 진입점 |
| 팝오버 | `Popover` | 대상 근처에 뜨는 메뉴 또는 보조 패널 |
| LNB | `LNB` | 좌측 또는 지역 내비게이션 |

## States

상태값은 기능정의서, L10N, QA TC에서 영어 표준값을 그대로 사용합니다.

| 표준 상태 | 의미 | 사용 예 |
|---|---|---|
| `Default` | 기본 상태 | Button Default |
| `Hover` | 마우스를 올린 상태 | Button Hover |
| `Pressed` | 누르고 있는 상태 | Button Pressed |
| `Focused` | 키보드 또는 입력 포커스가 있는 상태 | 검색 결과 Focused |
| `Selected` | 항목이 선택된 상태 | Table row Selected |
| `Disabled` | 클릭 또는 입력이 불가능한 상태 | Button Disabled |
| `Loading` | 처리 중인 상태 | Button Loading, Spinner |
| `Error` | 오류 상태 | Error Toast, Input Error |
| `Success` | 성공 상태 | Success Toast |
| `Warning` | 경고 상태 | Warning Toast |
| `Information` | 정보 안내 상태 | Information Toast |

## Toast Types

Toast는 아래 5가지 타입을 표준으로 사용합니다. L10N의 `기능 요소`에도 동일한 값을 사용합니다.

| Toast 타입 | L10N 기능 요소 | 사용 기준 |
|---|---|---|
| `Normal` | `Normal Toast` | 일반 상태 또는 중립 안내 |
| `Success` | `Success Toast` | 저장, 생성, 변경 등 성공 결과 |
| `Information` | `Information Toast` | 참고 정보 또는 상태 안내 |
| `Error` | `Error Toast` | 실패, 오류, 접근 불가 |
| `Warning` | `Warning Toast` | 주의, 되돌리기 어려운 작업 전 경고 |

### Toast 작성 규칙

- `Toast Normal`은 사용하지 않고 `Normal Toast`로 단일화한다.
- `토스트 모달`, `toast modal`은 사용하지 않는다.
- 사용자의 액션 결과를 짧게 알리는 경우는 `Toast`를 우선 검토한다.
- 확인, 취소, 입력처럼 사용자의 응답이 필요한 경우는 `Toast`가 아니라 `Modal`을 사용한다.

## Modal / Pop-up / Popover

| 표준 용어 | 컴포넌트 | 사용 기준 | 닫기/동작 기준 |
|---|---|---|---|
| 모달 | `Modal` | 확인, 취소, 입력 등 사용자의 명시적 응답이 필요한 창 | X 버튼 없음이 기본. `취소`, `확인`, 단일 버튼 등 명시 버튼으로 처리 |
| 팝업 | `Pop-up` | 광고, 공지, 프로모션, 다시 보지 않기 안내 | X 버튼과 `다시 보지 않기` 사용 가능 |
| 팝오버 | `Popover` | 버튼, 아이콘, 선택 항목 근처에 뜨는 메뉴 또는 보조 패널 | 외부 클릭, Esc, 항목 선택 등으로 닫힘 |

### 구분 규칙

- `팝업`이라는 일반 표현만 단독으로 쓰지 않는다.
- 업무 액션 확인 창은 `Modal`이다.
- 광고나 공지처럼 업무 흐름과 분리된 노출 창은 `Pop-up`이다.
- 우클릭 메뉴, 더보기 메뉴, 텍스트 편집 메뉴, URL 붙여넣기 선택 메뉴는 `Popover`이다.
- `Context Menu`, `우클릭 메뉴`를 컴포넌트명처럼 쓰지 않는다. 필요한 경우 `우클릭 시 Popover 노출`로 쓴다.

## Button Naming

Button을 상세히 지정할 때는 아래 값을 사용합니다.

| 구분 | 표준값 |
|---|---|
| variant | `Primary`, `Alternative`, `Secondary`, `Link` |
| size | `Lg`, `Md`, `Sm` |
| content type | `Label`, `LabelIcon`, `IconOnly`, `Underline` |
| state | `Default`, `Hover`, `Pressed`, `Disabled` |

예시:

- `Primary Button / Md / Label / Default`
- `Link Button / Md / Underline / Hover`
- `IconOnly Button / Sm / Disabled`

## 자주 혼동되는 표현

| 피해야 할 표현 | 표준 표현 | 이유 |
|---|---|---|
| 팝업 | `Modal`, `Pop-up`, `Popover` 중 하나 | 목적과 동작이 서로 다름 |
| 토스트 모달 | `Toast` | Toast는 사용자 응답을 요구하지 않음 |
| 컨텍스트 메뉴 | `Popover` | 별도 Context Menu 컴포넌트를 사용하지 않음 |
| 우클릭 메뉴 | 우클릭 시 `Popover` | 동작은 우클릭, 컴포넌트는 Popover |
| 더보기 메뉴 | `Overflow Menu` 또는 더보기 버튼 클릭 시 `Popover` | 진입점과 노출 패널을 구분 |
| 하단 팝업 | `BottomSheet` | 모바일 하단 패널은 BottomSheet로 통일 |
| Calender | `Calendar` | 오타 방지 |
| disbled | `Disabled` | 오타 방지 |
| toast success | `Success Toast` | L10N 기능 요소 표준 유지 |

## AI 사용 규칙

- `/spec-flow`, `/project-flow`는 산출물 작성 전 이 glossary를 참고한다.
- 산출물에는 가능한 표준 용어를 사용한다.
- 사용자 입력에 비표준 용어가 있어도 의미가 명확하면 표준 용어로 보정한다.
- 의미가 애매한 용어는 임의로 확정하지 않고 질문한다. 예: `팝업`이 Modal인지 Pop-up인지 Popover인지 불명확한 경우.
- 용어 불일치는 기본적으로 FAIL이 아니라 WARN으로 다룬다. 단, 동일 산출물 안에서 서로 다른 의미로 섞이면 사용자 확인이 필요하다.
- 프로젝트 고유 용어는 각 프로젝트의 references, features, decisions를 우선한다.
