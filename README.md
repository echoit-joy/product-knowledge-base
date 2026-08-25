# Product Knowledge Base

팀이 제품을 만들면서 생기는 기준 문서, 회의록, 확정 결정, 현재 기능정의서를 모아 두는 곳입니다.

사람은 이 저장소를 보고 "왜 이렇게 정했는지"와 "현재 제품 기능이 어디에 있는지"를 빠르게 확인합니다. AI는 `/spec-flow`, `/project-flow`를 실행할 때 이 저장소를 먼저 참고해 기존 결정과 기능정의서와 충돌하지 않게 작업합니다.

## 먼저 볼 문서

1. [00-index.md](00-index.md)  
   전체 프로젝트와 공통 문서로 이동하는 첫 화면입니다.
2. [projects/sheetric/README.md](projects/sheetric/README.md)  
   Sheetric 프로젝트 문서의 입구입니다.
3. [releases/specops/latest.md](releases/specops/latest.md)  
   SpecOps 최신 배포 버전과 ZIP 다운로드 기준을 확인합니다.

## 폴더 역할

| 위치 | 역할 |
| --- | --- |
| `global/` | 모든 프로젝트에 공통으로 적용되는 용어와 제품 규칙 |
| `projects/{project}/` | 프로젝트별 문서 모음 |
| `projects/{project}/decisions/` | 이미 확정된 결정만 기록 |
| `projects/{project}/features/` | 현재 기능 지도. 기능이 어느 화면/섹션에 있는지 확인 |
| `projects/{project}/meetings/` | 회의록과 논의 기록. 확정 결정으로 보지는 않음 |
| `projects/{project}/xlsx/` | 현재 기능정의서 XLSX. AI가 기능 ID와 정책을 확인할 때 사용 |
| `projects/{project}/references/` | 외부 링크, 참고 자료 |
| `templates/` | decision, meeting note 작성 양식 |
| `releases/specops/` | SpecOps 배포 노트 |

## 가장 중요한 원칙

- `decisions/`에는 확정된 결정만 넣습니다.
- 회의에서 나온 의견이나 아직 논의 중인 내용은 `meetings/`에 둡니다.
- `features/feature-index.md`는 현재 기능의 지도입니다. 결정 이유를 길게 쓰지 않습니다.
- 현재 기능정의서 XLSX는 상세 기준입니다. 기능 ID, L10N ID, QA 기준과 충돌하지 않도록 AI가 참고합니다.

## AI가 참고하는 순서

AI는 보통 다음 순서로 문서를 봅니다.

1. `decisions/`에서 이미 확정된 결정 확인
2. `features/feature-index.md`에서 현재 기능 위치와 상태 확인
3. `xlsx/`의 현재 기능정의서에서 상세 ID와 정책 확인
4. `meetings/`에서 관련 맥락 참고

회의록은 참고 자료일 뿐입니다. 회의록에 적힌 내용이 자동으로 확정 결정이 되지는 않습니다.
