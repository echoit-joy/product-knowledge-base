# Features

Sheetric의 현재 기능 지도를 관리하는 폴더입니다.

## feature-index.md는 무엇인가요?

[feature-index.md](feature-index.md)는 "현재 어떤 기능이 어디에 있는지"를 빠르게 확인하는 지도입니다.

기능의 자세한 동작은 XLSX 기능정의서에 있고, 왜 그렇게 결정했는지는 `decisions/`에 있습니다. feature-index는 그 둘을 연결해 주는 색인 역할을 합니다.

## decisions와 뭐가 다른가요?

| 문서 | 역할 |
| --- | --- |
| `features/feature-index.md` | 현재 기능의 위치와 상태 |
| `decisions/` | 왜 그렇게 하기로 했는지 |
| `xlsx/` | 실제 상세 동작과 검증 기준 |

## AI는 어떻게 사용하나요?

AI는 기존 기능을 추가하거나 수정할 때 feature-index를 보고 다음을 빠르게 파악합니다.

- 기능이 이미 있는지
- 어느 화면과 섹션에 연결되어 있는지
- 상태가 active, experimental, deprecated, archived 중 무엇인지
- 관련 decision이 있는지
- 현재 기능정의서에서 어떤 범위를 봐야 하는지

## 갱신 원칙

- `/spec-flow`, `/project-flow` 결과가 e2e를 통과한 뒤에만 갱신 후보가 생깁니다.
- AI가 몰래 갱신하지 않고, 변경 후보를 보여준 뒤 사용자 확인을 받아야 합니다.
- `feature_slug`는 한번 정하면 이름을 바꾸지 않습니다.
- 이름이 바뀌면 slug가 아니라 기능명을 바꿉니다.
- 결정 이유를 길게 쓰지 않습니다. 이유는 `decisions/`에 둡니다.
