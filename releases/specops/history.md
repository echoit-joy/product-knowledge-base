# SpecOps 릴리즈 이력

---

## v1.3.2 (2026-07-23)

ZIP: `spec-harness-kit-v1.3.2-20260723.zip` · 파일 수: 52개

### 산출물 전달 방식

- **Google Sheets로 바로 보낼 수 있습니다**
  - `/spec-flow`, `/project-flow` 시작 직후 산출물을 어떻게 받을지 선택합니다.
  - `xlsx_only` / `gsheets_only` / `xlsx_and_gsheets` 중에서 고를 수 있습니다.

- **여러 화면으로 나뉜 기능정의서도 Google Sheets에 함께 반영됩니다**
  - `내 드라이브`, `즐겨찾기`처럼 기능정의서가 여러 시트로 나뉘어도 Google Sheets에는 이어진 표처럼 넣을 수 있습니다.

### 팀원 설정

- **Google Sheets 연동 준비가 쉬워졌습니다**
  - 팀원이 Google Cloud OAuth client를 직접 만들 필요가 없습니다.
  - 관리자가 공유한 `client_secret` JSON을 한 번만 등록하면 됩니다.
  - 파일 경로는 Finder에서 **Option+Command+C**로 복사해 붙여넣을 수 있습니다.

### 산출물 품질

- **질문을 빠뜨리지 않고 확인합니다**
  - 확인할 질문이 많을 때 일부만 묻고 넘어가지 않도록 했습니다.

- **기능정의서 문장이 더 깔끔해집니다**
  - Action 컬럼에는 동작만 적고, 결과나 기대 상태는 Property, Note, QA 기댓값으로 분리합니다.
  - 모달의 X 버튼, 외부 클릭, ESC 닫힘은 명시된 경우에만 포함합니다.

- **공통 UI 용어를 더 일관되게 씁니다**
  - Toast, Modal, Pop-up, Popover, Button 상태값처럼 자주 흔들리던 표현은 `global/glossary.md` 기준으로 맞춥니다.

### 작업 폴더 관리

- **리포트 폴더가 덜 쌓이도록 정리됩니다**
  - 새 `/spec-flow` 또는 `/project-flow`를 시작하면 이전 `latest/` 리포트를 정리하고 이번 실행 결과만 남깁니다.

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