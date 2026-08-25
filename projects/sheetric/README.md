# Sheetric

Sheetric 프로젝트의 기준 문서를 모아 둔 곳입니다.

기능을 추가하거나 수정할 때 사람과 AI가 모두 이 폴더를 참고합니다.

## 어디를 보면 되나요?

| 보고 싶은 것 | 위치 |
| --- | --- |
| 프로젝트 개요와 현재 맥락 | [project-context.md](project-context.md) |
| 현재 기능 목록과 위치 | [features/README.md](features/README.md) |
| 확정된 제품 결정 | [decisions/README.md](decisions/README.md) |
| 회의록과 논의 기록 | [meetings/README.md](meetings/README.md) |
| 현재 기능정의서 XLSX | [xlsx/README.md](xlsx/README.md) |
| 외부 링크와 참고 자료 | [references/README.md](references/README.md) |

## 폴더별 의미

- `decisions/`  
  확정된 결정만 들어갑니다. 예를 들어 "폴더 공유 권한 전파", "공유 링크 별도 읽기 전용 URL"처럼 이후 작업에서 반드시 지켜야 하는 기준입니다.

- `features/`  
  현재 기능 지도입니다. 어떤 기능이 어느 화면/섹션에 있고 상태가 무엇인지 빠르게 확인합니다.

- `meetings/`  
  회의록입니다. 논의 맥락을 남기는 곳이며, 여기에 적힌 내용이 곧바로 확정 결정이 되지는 않습니다.

- `xlsx/`  
  현재 기준 기능정의서입니다. AI가 기능 ID, L10N ID, QA 기준, 현재 정책을 확인할 때 사용합니다.

- `references/`  
  외부 링크나 참고 자료를 둡니다.

## AI 작업 시 기준

`/spec-flow`나 `/project-flow`를 실행하면 AI는 이 프로젝트 폴더를 참고합니다.

AI는 먼저 `decisions/`를 확인해 이미 정해진 정책과 충돌하지 않는지 봅니다. 그 다음 `features/feature-index.md`로 현재 기능 위치를 확인하고, `xlsx/`의 현재 기능정의서로 상세 ID와 정책을 대조합니다. 필요한 경우 `meetings/`를 참고하지만, 회의록은 확정 결정으로 취급하지 않습니다.
