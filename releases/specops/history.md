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

- **Feature Index 자동 갱신 안정화** — `/spec-flow` Step 7-FI 및 `/project-flow` Step 10-B의 feature-index writeback 흐름 안정화
- **`/spec-flow` Step 7-FI**: e2e PASS 후 `kb-writeback.json` 저장 명세 추가 (10개 필드: feature_index_source·changed_rows·appended_rows·updated_rows·skipped_rows·e2e_gate·write_mode·branch·commit_sha·rollback_command). GitHub write 전 변경 예정 diff 사용자 확인 필수.
- **`/project-flow` kb-writeback.json**: 누락 6개 필드 추가 (feature_index_source·changed_rows·appended_rows·updated_rows·skipped_rows·e2e_gate). single 모드 전체 e2e fail_count=0 게이트 명문화. split-by-feature 모드 기능별 PASS/FAIL 분기 규칙 추가.
- **package_release.sh 검증 5개 추가**: feature-index 갱신 후보 단계 존재·split-by-feature 규칙·feature_slug rename 금지·spec-flow kb-writeback feature_index_source·project-flow kb-writeback feature_index_source
- **harness_version v1.2.0** bump

---
## v1.1.0 (2026-07-15)

ZIP: `spec-harness-kit-v1.1.0-20260715.zip` · 파일 수: 49개

- **macOS-only 패키지 전환** — Windows/PowerShell 스크립트 전량 제거 (install.ps1, run_all_harness.ps1, run_e2e_harness.ps1, run_repair_loop.ps1, harness/*.ps1 등 11개), 문서도 macOS 기준으로만 정리
- **Feature Index Schema v1.1 추가** — `features/feature-index.md`를 AI 참조 기능 지도로 정의하고, feature_slug 안정성·primary/related 화면·e2e 기반 writeback 규칙 추가

---
## v1.0.0 (2026-07-14)

ZIP: `spec-harness-kit-v1.0.0-20260714.zip` · 파일 수: 61개

- **v1.0.0 공식 릴리즈** — beta 표기 전면 제거 (ZIP/MANIFEST/README/quick-start)
- **Feature Index Schema v1.1 추가** — `features/feature-index.md`를 AI 참조 기능 지도로 정의하고, feature_slug 안정성·primary/related 화면·e2e 기반 writeback 규칙 추가
- **prototype 저장 규칙 강화** — modal/partial 화면도 `workspace/prototype/{project}/` 로컬 저장 필수, Artifact-only 완료 금지
- **prototype-summary.json 고정 경로** — `workspace/.reports/spec-flow/latest/prototype-summary.json`
- **package_release.sh [3B/4] 강화** — 정적 JSON 확인 → 실제 파일 생성(HTML + JSON) 후 구조 검증
- **release-zip-manifest.md 개선** — 현재 배포 버전 섹션 분리, v0.x 과거 기록 아카이브
- **SpecOps publish 기능 추가** — `scripts/publish_release_to_github.sh` (dry-run/publish 모드)

---