# SpecOps 릴리즈 이력

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