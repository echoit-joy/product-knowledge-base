# SpecOps 릴리즈 이력

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
- HTML 프로토타입을 만들 때 임시 링크만 남기지 않고 KB에 반영하도록 흐름을 강화했습니다.
- 배포 ZIP을 만들고 GitHub Release에 올리는 기본 배포 흐름이 추가됐습니다.

---