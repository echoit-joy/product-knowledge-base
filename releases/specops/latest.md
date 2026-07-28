# SpecOps v1.3.2 — 배포 노트

배포일: 2026-07-28
ZIP: `spec-harness-kit-v1.3.2-20260728.zip`
파일 수: 52개 (.gitkeep 6개 포함)
e2e: PASS_WITH_REVIEW (fail=0)
install: CLEAN (package_release.sh 검증 완료)

---

## 주요 변경점

- **`/qa-gen` 로컬 XLSX 단독 실행 지원**
  - 이제 GitHub에 없는 프로젝트도 로컬 기능정의서 XLSX만 있으면 `/qa-gen`으로 QA TC를 만들 수 있습니다.
  - GitHub KB는 optional context입니다. KB가 없거나 gh 인증이 없어도 중단하지 않고 로컬 XLSX 기준으로 진행합니다.
  - 외부 경로(workspace/ 밖) XLSX도 직접 지정할 수 있습니다. 원본 파일은 읽기 전용으로 처리됩니다.

- **`/qa-gen` Delivery Mode 선택 (Step 0-DM)**
  - 결과는 XLSX만, Google Sheets만, 둘 다 중 선택할 수 있습니다.
  - 선택지를 표시한 뒤에만 Enter 기본값(xlsx_only)이 허용됩니다. silent default 금지.

  | 모드 | 설명 |
  |------|------|
  | `xlsx_only` | XLSX만 생성 **(기본값)** |
  | `gsheets_only` | Google Sheets에만 쓰기 — qa_auditor PASS 후 writeback, 임시 XLSX 삭제 |
  | `xlsx_and_gsheets` | XLSX 생성 + Google Sheets writeback (XLSX 경로·Sheets 기록 범위 모두 안내) |

- **QA-only Google Sheets writeback**
  - qa_auditor `fail_count=0` 통과 후에만 writeback을 실행합니다.
  - `kind: qa`를 명시해 QA-only target이 spec 시트로 오인되지 않도록 처리합니다.

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

- **Global Glossary 참고 추가**
  - 공통 UI 용어 기준(`global/glossary.md`)을 `/spec-flow`, `/project-flow`에서 참고합니다.
  - Toast, Modal, Pop-up, Popover, Button 상태값처럼 자주 흔들리던 표현은 `global/glossary.md` 기준으로 맞춥니다.
  - 기능정의서에는 불필요한 디자인 세부 조합을 기계적으로 넣지 않도록 했습니다.

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

- **Delivery Mode UX 변경 — `xlsx_only` / `gsheets_only` / `xlsx_and_gsheets` 3가지로 재편**
  - 기존 `xlsx_then_later` 옵션을 제거하고 `gsheets_only`를 추가했습니다.
  - `/spec-flow`, `/project-flow` 시작 직후 Step 0-DM에서 아래 3가지 중 하나를 선택합니다.

  <br>

  | 모드 | 설명 |
  |------|------|
  | `xlsx_only` | XLSX만 생성 **(기본값)** |
  | `gsheets_only` | Google Sheets에만 쓰기 — 내부 검증용 임시 XLSX로 e2e 후 writeback, `workspace/spec`·`qa`에 XLSX 잔류 없음 |
  | `xlsx_and_gsheets` | XLSX 생성 후 e2e gate 통과 시 Google Sheets writeback |

---

## 팀원이 해야 할 일

1. ZIP 파일(`spec-harness-kit-v1.3.2-20260728.zip`) 다운로드
2. 기존 `spec-harness-kit/` 폴더를 새 ZIP으로 교체
3. `bash install.sh` 실행 (명령어 파일 갱신)
4. Claude Code 재시작
5. Google Sheets writeback을 사용할 팀원만 최초 1회 OAuth JSON 등록:
   - 관리자가 Google Cloud OAuth 앱의 **Test users**에 팀원 Google 계정을 등록합니다.
   - 관리자가 OAuth client JSON 파일(`client_secret_...apps.googleusercontent.com.json`)을 승인된 팀원에게 안전한 내부 채널로 전달합니다.
   - 팀원은 받은 JSON 파일을 `Downloads` 등에 둔 뒤 아래 명령을 실행합니다.

     > **경로 입력 팁 (macOS)**: Finder에서 파일을 선택한 뒤 **Option+Command+C**로 경로를 복사하고, 터미널/Claude 입력창에 **Option+Command+V**로 붙여넣으세요.

     ```bash
     bash scripts/setup_gsheets_oauth.sh ~/Downloads/client_secret_...apps.googleusercontent.com.json
     ```

   - 첫 writeback 실행 시 브라우저가 열리고 Google 계정 승인을 요청합니다.
     - **"확인되지 않은 앱" 또는 "테스트 앱" 경고**가 나오면, 승인된 Test user 계정으로 로그인한 상태에서 **[계속]**을 눌러 진행합니다.
     - **[안전한 환경으로 이동]** 류 버튼은 인증을 중단하므로 누르지 마세요.
   - `403 access_denied`가 나오면 Test users 미등록 또는 다른 Google 계정으로 로그인한 가능성이 큽니다.
6. (Google Sheets 사용 시) `/spec-flow` 또는 `/project-flow` 시작 시 Step 0-DM 선택:
   - `1` — `xlsx_only`: XLSX만 생성 (기본값, Enter 입력 시 자동 선택)
   - `2` — `gsheets_only`: Google Sheets에만 쓰기 (XLSX를 workspace에 남기지 않음)
   - `3` — `xlsx_and_gsheets`: XLSX와 Google Sheets 둘 다 생성

> 팀원이 Google Cloud OAuth client를 직접 만들 필요는 없습니다.  
> `client_secret` JSON은 승인된 팀원에게만 공유하고, GitHub/ZIP/workspace에는 넣지 마세요.  
> `token.json`은 절대 공유하지 마세요.  
> Google Sheets 자체 편집 권한은 별도로 필요합니다.  
> **workspace/spec/, workspace/qa/ 내 기존 XLSX는 삭제되지 않습니다.**  
> 새 ZIP을 이전 폴더 위치에 압축 해제하면 파일이 덮어써질 수 있으니 주의하세요.

---

## 주의사항

- 이전 버전 ZIP과 함께 사용하지 마세요.
- `install.sh` 실행 전 Claude Code가 실행 중이면 종료 후 실행하세요.
- GitHub KB write 기능(`/project-flow`)은 `gh auth login`이 필요합니다.

---

_generated by publish_release_to_github.sh — v1.3.2 · 2026-07-28_