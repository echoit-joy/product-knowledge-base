# SpecOps 릴리즈 이력

---
## v1.3.3 (2026-08-24)

ZIP: `spec-harness-kit-v1.3.3-20260824.zip` · 파일 수: 52개

- **모달 닫기 문구 산출물 혼입 방지**
  - 모달 템플릿에서 별도 닫기 아이콘 부재 설명을 제거했습니다.
  - 기능정의서/QA TC에 `X 버튼 없음`, `X 버튼 기본 제공 아님` 같은 문구가 들어가면 FAIL로 잡습니다.
  - 외부 클릭·ESC 닫힘은 기존처럼 정상 모달 기본 동작으로 유지합니다.

---

## v1.3.2 (2026-08-19)

ZIP: `spec-harness-kit-v1.3.2-20260819.zip` · 파일 수: 52개

- **GitHub KB 문서 참조 안정성 개선**
  - `spec-harness-kit` 폴더가 git 저장소가 아니어도 정상으로 처리합니다.
  - decisions/meetings는 `workspace/reference/existing/`가 아니라 GitHub KB에서 읽는다고 명확히 했습니다.
  - 기존 프로젝트에서 decisions/meetings를 읽지 못하면 Draft를 만들기 전에 사용자 확인을 받습니다.

---

## v1.3.2 (2026-07-28)

ZIP: `spec-harness-kit-v1.3.2-20260728.zip` · 파일 수: 52개

- **`/qa-gen` 단독 실행 지원**
  - GitHub에 없는 프로젝트도 로컬 기능정의서 XLSX만 있으면 QA TC를 만들 수 있습니다.
  - GitHub KB는 있으면 참고하고, 없으면 로컬 XLSX 기준으로 진행합니다.

- **산출물 수령 방식 정리**
  - `/spec-flow`, `/project-flow`, `/qa-gen`에서 `xlsx_only` / `gsheets_only` / `xlsx_and_gsheets` 중 선택할 수 있습니다.
  - 중복 안내를 줄이고, 시작 직후 Step 0-DM에서 한 번만 선택하도록 정리했습니다.

- **Google Sheets writeback 안정화 + 한 탭 병합 정책**
  - 여러 `기능정의_` 시트를 병합해 Google Sheets에 씁니다.
  - 실제 행/열 범위를 다시 읽어 검증합니다.
  - QA TC만 Google Sheets에 쓰는 `kind: qa` 흐름도 지원합니다.
  - QA TC writeback은 기본 한 target tab에 전체를 병합해 기록합니다. URL만 받은 경우 화면명 기반 탭 자동 분리 금지.
  - dry-run 리포트에 `source_sheets`, `merged_sheet_count`, `merged_row_count`, `target_tab`을 명시합니다.

- **source-backed QA 원칙 추가**
  - `/qa-gen`은 기능정의서 XLSX 기반 downstream 흐름입니다.
  - source 기능정의서에 X 버튼이 명시되어 있으면 harness 정책 충돌 여부와 무관하게 TC를 생성합니다.
  - "harness 정책상 X 버튼 TC 금지인데 제외할까요?" 재질문 금지.
  - `qa_auditor --source-spec` 옵션: source-backed X 버튼 TC는 FAIL 대신 WARN으로 처리합니다.

- **기능정의서·QA TC 품질 가드 강화**
  - 질문 3개 제한으로 기획 구멍이 남는 문제를 방지합니다.
  - 삭제 decision을 과하게 해석해 정상 기능까지 막는 문제를 줄였습니다.
  - `global/glossary.md` 기준으로 UI 용어를 참고합니다.
  - Action 컬럼의 결과형 문구와 Modal X 버튼 오기재를 FAIL로 잡습니다.

- **운영 편의 개선**
  - 팀원용 Google OAuth 등록 스크립트와 인증 안내를 보강했습니다.
  - 한글 decision 파일 fetch 안정성을 높였습니다.
  - 새 실행 시 이전 `.reports/latest/` 리포트를 정리합니다.

---

## v1.3.2 (2026-07-23)

ZIP: `spec-harness-kit-v1.3.2-20260723.zip` · 파일 수: 52개

- **Google Sheets 여러 시트 한 번에 읽기 (hotfix)**
  - `기능정의_A`, `기능정의_B` 등 여러 시트가 있을 때 첫 번째 시트만 쓰던 버그를 수정했습니다.
  - 이제 `기능정의_` 접두사가 있는 시트를 전부 병합해서 Google Sheets에 씁니다.

- **Google Sheets 검증 범위 정확도 개선 (hotfix)**
  - 검증 단계에서 데이터 범위를 `ZZ9999` 같은 열린 범위로 조회하던 문제를 수정했습니다.
  - 이제 실제 행·열 수에 맞는 정확한 범위로 조회해 검증 오류가 줄었습니다.

- **Google Sheets OAuth 팀 배포 스크립트 추가**
  - 팀원이 Google Sheets 연동을 위해 직접 Google Cloud 프로젝트를 만들 필요가 없습니다.
  - 관리자가 만든 `client_secret.json`을 `scripts/setup_gsheets_oauth.sh`로 간편하게 등록합니다.

- **Step 1 인터뷰 질문 수 제한 금지 규칙 추가**
  - 질문이 많을 때 3개만 묻고 나머지를 누락한 채 Draft를 진행하는 문제를 방지합니다.
  - 질문 backlog(`remaining_question_count`)를 소진한 후에만 Draft로 넘어갑니다.

- **FORBIDDEN_DOMAINS 오탐 방지 규칙 추가**
  - "파일 기능 삭제" decision에서 "파일", "폴더"를 금지어로 등록하면 "폴더 색상 변경" 같은 무관한 기능도 차단되던 문제를 예방합니다.
  - 삭제된 기능의 구체적인 동작만 금지어로 쓰도록 규칙과 회귀 사례를 추가했습니다.

- **Delivery Mode UX 변경 — `xlsx_then_later` 제거, `gsheets_only` 추가**
  - `xlsx_only` / `gsheets_only` / `xlsx_and_gsheets` 3가지로 재편했습니다.
  - `gsheets_only` 모드: 내부 검증용 임시 XLSX로 e2e를 수행하고, PASS 후 Google Sheets에만 writeback합니다. workspace/spec·qa에 XLSX가 남지 않습니다.

- **Global Glossary 참고 추가**
  - 공통 UI 용어 기준(`global/glossary.md`)을 `/spec-flow`, `/project-flow`에서 참고합니다.
  - Toast, Modal, Pop-up, Popover, Button 등 자주 흔들리던 용어는 glossary 기준으로 보정합니다. 용어 불일치는 기본 WARN.

- **Action 컬럼 품질 검증 강화 (check 24 FAIL)**
  - Action 컬럼에 `(변경 사항 미적용)`, `변경 전 상태로 유지` 같은 결과/상태 설명이 들어가면 FAIL로 잡습니다.
  - Action은 동작만 적고, 결과/기대 상태는 Property, Note, QA 기댓값으로 분리합니다.

- **Modal 닫기 규칙 보정**
  - X 버튼은 기본 닫기 수단이 아닙니다.
  - X 버튼만 사용자 요청/reference/decisions에 명시된 경우에만 기능정의서·QA TC에 기재합니다. 외부 클릭·ESC 닫힘은 기본 동작으로 유지됩니다.

- **한글 decision 파일 fetch 안정화**
  - `파일 기능 삭제.md` 같은 한글 파일명 decision은 GitHub Contents API의 `download_url` 기준으로 읽습니다.
  - raw URL 직접 조합으로 생기던 404 가능성을 줄였습니다.

- **Google OAuth 안내 보강**
  - client_secret JSON 경로는 Finder에서 **Option+Command+C**로 복사하고, 터미널/Claude 입력창에 **Option+Command+V**로 붙여넣을 수 있습니다.
  - Google 인증 화면에서 "확인되지 않은 앱"/"테스트 앱" 경고가 나오면 승인된 Test user 계정으로 **[계속]**을 눌러 진행합니다. **[안전한 환경으로 이동]** 류 버튼은 인증을 중단합니다.

- **`.reports` 정리 정책 추가**
  - 새 `/spec-flow` / `/project-flow` 시작 시 이전 `latest/` 리포트를 자동 정리하고, 이번 실행 결과만 남깁니다.

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