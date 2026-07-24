# SpecOps 릴리즈 이력

---

## v1.3.2 (2026-07-23)

ZIP: `spec-harness-kit-v1.3.2-20260723.zip` · 파일 수: 52개

### Google Sheets 연동

- **산출물 받는 방식 선택 개선**
  - `xlsx_only` / `gsheets_only` / `xlsx_and_gsheets` 3가지로 재편했습니다.
  - `gsheets_only` 모드에서는 내부 검증용 임시 XLSX로 e2e를 수행하고, PASS 후 Google Sheets에만 writeback합니다. `workspace/spec`·`qa`에 XLSX가 남지 않습니다.

- **여러 기능정의 시트도 한 번에 Google Sheets로 보냅니다**
  - XLSX 안에 기능정의 시트가 여러 개 있어도 첫 번째 시트만 쓰지 않습니다.
  - `기능정의_`로 시작하는 시트를 모아 하나의 표처럼 Google Sheets에 씁니다.

- **Google Sheets에 제대로 써졌는지 더 정확히 확인합니다**
  - 쓰기 후 검증할 때 실제로 쓴 행과 열만 다시 읽습니다.
  - 빈 영역까지 넓게 읽어서 실패처럼 보이던 문제를 줄였습니다.

- **팀원용 OAuth 등록 스크립트 추가**
  - 팀원이 Google Sheets 연동을 위해 직접 Google Cloud 프로젝트를 만들 필요가 없습니다.
  - 관리자가 공유한 `client_secret` JSON을 `scripts/setup_gsheets_oauth.sh`로 한 번만 등록하면 됩니다.

### 작업 흐름 안정성

- **질문이 3개에서 끊기지 않도록 보강**
  - 확인해야 할 질문이 많을 때 일부만 묻고 Draft로 넘어가지 않도록 했습니다.
  - 남은 질문 목록을 끝까지 처리한 뒤에만 기능정의서 작성을 진행합니다.

- **삭제된 기능 판단을 더 정확하게 보정**
  - 기존에는 `파일 기능 삭제` 같은 결정을 너무 넓게 해석해 `폴더 색상 변경`처럼 실제 삭제 대상이 아닌 기능까지 막을 수 있었습니다.
  - 이제는 삭제하기로 한 구체적인 동작만 충돌 기준으로 보고, 일반 화면명이나 객체명만으로는 요청을 막지 않도록 했습니다.

### 용어 기준

- **Global Glossary 참고 추가**
  - 공통 UI 용어 기준(`global/glossary.md`)을 `/spec-flow`, `/project-flow`에서 참고합니다.
  - Toast, Modal, Pop-up, Popover, Button 등 자주 흔들리던 용어는 glossary 기준으로 보정합니다. 용어 불일치는 기본 WARN.

---
## v1.3.1 (2026-07-21)

ZIP: `spec-harness-kit-v1.3.1-20260721.zip` · 파일 수: 51개

- **Step 0-DM 항상 질문**: Delivery Mode 선택을 매 실행마다 묻도록 변경했습니다. 이전 세션 설정이 잘못 이어지던 문제를 방지합니다.
- **GitHub write 여부 자동 감지**: gh CLI 인증 상태를 자동으로 확인해 write 가능 여부를 사전에 알려줍니다. 인증이 없으면 dry-run으로 전환합니다.
- **Step 6 완료 조건 강화**: e2e PASS 없이 Step 6 완료 선언이 불가하도록 게이트를 추가했습니다.

---
## v1.3.0 (2026-07-21)

ZIP: `spec-harness-kit-v1.3.0-20260721.zip` · 파일 수: 51개

- **Google Sheets writeback MVP** — XLSX 생성 후 선택적으로 Google Sheets에 writeback. XLSX는 항상 유지되며 Sheets writeback은 추가 배포 경로.
- **Step 0-DM (Delivery Mode 선택)**: `/spec-flow` · `/project-flow` 시작 직후 xlsx_only / xlsx_and_gsheets / xlsx_then_later 선택. 기본값: xlsx_only. 기존 플로우와 동일하게 동작.
- **`/spec-flow` Step 7-GS**: e2e gate 통과 후 Google Sheets writeback — target 입력 → parse 미리보기 → dry-run → 사용자 승인 → write → verify → report 저장.
- **`/project-flow` Step 11-GS**: cascade Step 11 완료 후 Google Sheets writeback (동일 흐름).
- **`scripts/gsheets_writeback.py` 신규**: OAuth 2.0 인증(macOS Keychain 우선), dry-run(읽기 전용), write 3분기(write/safe-write/overwrite approve), verify, report 저장(URL/ID 마스킹).
- **`workspace/gsheets-target.local.yaml.template` 신규**: 팀원이 복사·수정하여 사용하는 target 설정 템플릿.
- **package_release.sh 검증 10개 추가**: gsheets_writeback.py 존재·template 존재·local.yaml 혼입 금지·token 혼입 금지·URL 평문 노출 금지·Step 7-GS·0-DM·11-GS 섹션 존재·마스킹 키워드 존재.
- **EXPECTED_COUNT=51** (v1.2.0: 49 → v1.3.0: 51, +2 파일)
- **harness_version v1.3.0** bump

---
## v1.2.0 (2026-07-15)

ZIP: `spec-harness-kit-v1.2.0-20260715.zip` · 파일 수: 49개

- 기능이 추가되거나 변경될 때 `feature-index.md`를 더 안정적으로 갱신하도록 정리했습니다.
- 검증이 통과한 내용만 GitHub KB에 반영하도록 흐름을 강화했습니다.
- 반영 전 변경 예정 내용을 먼저 보여주고, 사용자가 확인한 뒤에만 기록하도록 안전장치를 추가했습니다.
- 여러 기능을 한 번에 처리할 때도 실패한 기능이 섞이지 않도록 기준을 명확히 했습니다.

---
## v1.1.0 (2026-07-15)

ZIP: `spec-harness-kit-v1.1.0-20260715.zip` · 파일 수: 49개

- macOS 기준으로만 사용할 수 있게 정리했습니다.
- Windows/PowerShell 전용 파일을 제거해서 ZIP이 더 가벼워졌고, 문서도 macOS 기준으로 헷갈리지 않게 정리했습니다.
- `features/feature-index.md` 기준을 추가해서 AI가 프로젝트의 현재 기능 목록을 더 쉽게 파악할 수 있게 했습니다.

---
## v1.0.0 (2026-07-14)

ZIP: `spec-harness-kit-v1.0.0-20260714.zip` · 파일 수: 61개

- 첫 공식 배포 버전입니다.
- 기능정의서, L10N, QA TC를 만들고 검증하는 기본 흐름을 팀에 공유할 수 있게 됐습니다.
- HTML 프로토타입을 만들 때 임시 링크만 남기지 않고 `workspace/prototype/` 폴더에 로컬 파일로 저장하도록 강화했습니다.
- 배포 ZIP을 만들고 GitHub Release에 올리는 기본 배포 흐름이 추가됐습니다.

---