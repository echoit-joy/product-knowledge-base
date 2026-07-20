# Sheetric — Feature Index

> 현재 어떤 기능이 어느 화면/섹션에 있는지 확인하는 지도입니다.  
> 결정 이유 → `decisions/` | 상세 동작 → `xlsx/Sheetric 프로젝트.xlsx`

_updated: 2026-07-20 · source: xlsx/Sheetric 프로젝트.xlsx_

---

## 화면 요약

| 화면 | 상태 | 비고 |
|------|------|------|
| 로그인 / 회원가입 | active | |
| 메인 페이지 | active | |
| 즐겨찾기 | active | |
| 내 드라이브 | active | |
| 휴지통 | active | |
| 노트 | active | |
| 파일 | deprecated | decisions/파일 기능 삭제.md — 파일 업로드·조회 스펙아웃 |

---

## Feature Index

| feature_slug | 기능명 | 상태 | primary_screen | primary_section | related_screens | related_sections | source_xlsx | related_decisions | note |
|---|---|---|---|---|---|---|---|---|---|
| email-auth | 이메일 로그인 / 회원가입 | active | 로그인 | 이메일·비밀번호·로그인·회원가입 | 회원가입 | 비밀번호 재설정·인증 메일 | 기능정의_회원가입, 로그인 | — | 이메일 인증, 비밀번호 찾기·재설정 포함 |
| sidebar-nav | 사이드바 네비게이션 | active | 메인 페이지 | Sidebar | 즐겨찾기·내 드라이브·휴지통·노트 | Sidebar | 기능정의_MainPage | 추가 팝오버 미제공 메뉴 제거.md · 키보드 포커스 및 단축키.md | 새 시트·파일 업로드·폴더 업로드 메뉴 제거됨 |
| create-menu | 새로 만들기 팝오버 | active | 메인 페이지 | 새로 만들기 팝오버 | 내 드라이브·즐겨찾기 | Sidebar | 기능정의_MainPage | 추가 팝오버 미제공 메뉴 제거.md | 새 노트·새 폴더만 제공. 새 시트 제거됨 |
| tab-bar | 탭 바 / 탭 관리 | active | 메인 페이지 | Navbar | 노트·내 드라이브 | Navbar | 기능정의_MainPage | 모바일 단일 노트 모드.md | 모바일 정책은 decisions 참조 |
| home-favorites-section | 메인 즐겨찾기 섹션 | active | 메인 페이지 | 즐겨찾기 | — | — | 기능정의_MainPage | 즐겨찾기 최대 10개 표시.md | 최신 수정일 기준 최대 10개 노출 |
| home-recent-section | 최근 작업 섹션 | active | 메인 페이지 | 최근 작업 | — | — | 기능정의_MainPage | — | |
| account-settings | 계정 설정 | active | 메인 페이지 | 설정 모달·프로필 메뉴 팝오버 | — | — | 기능정의_MainPage | — | 이름 변경·비밀번호 변경·계정 탈퇴 포함 |
| favorites-list | 즐겨찾기 리스트 | active | 즐겨찾기 | 파일 리스트·액션 바·브레드크럼 | — | — | 기능정의_즐겨찾기 | — | 다운로드·삭제·즐겨찾기 해제·공유 링크 복사 포함. 기존 XLSX 섹션명 기준 |
| favorites-tag-filter | 즐겨찾기 태그 필터 | active | 즐겨찾기 | 태그 필터 | — | — | 기능정의_즐겨찾기 | 태그 필터 노출 및 정렬.md | 즐겨찾기 노트의 태그만 노출. 항목 수↓ → 최신 생성순 |
| list-search | 리스트 검색 | active | 즐겨찾기 | 좌측 패널·검색 결과 | 내 드라이브·휴지통 | 좌측 패널·검색 결과 | 기능정의_즐겨찾기·기능정의_내드라이브·기능정의_휴지통 | 검색바 리스트 상단 이동.md · 검색 결과 현재 페이지 표시.md | 검색바는 리스트 헤더 상단 배치. 결과는 현재 페이지 내 표시 |
| table-row-selection | 테이블 행 선택 동작 | active | 즐겨찾기 | 파일 리스트 | 내 드라이브·휴지통 | 파일 리스트 | 기능정의_즐겨찾기 | 테이블 행 선택 동작.md | 우클릭 선택·Shift+클릭 범위 선택·드래그 선택. 기존 XLSX 섹션명 기준 |
| item-move-modal | 항목 이동 모달 | active | 즐겨찾기 | 항목 이동 모달 | 내 드라이브·노트 | 항목 이동 모달 | 기능정의_즐겨찾기 | 항목 이동 모달 드릴다운 방식.md | 드릴다운 방식. 한 번에 최대 8개 노출 |
| tag-management | 태그 관리 모달 | active | 즐겨찾기 | 태그 관리 모달 | 내 드라이브·노트 | 태그 관리 모달 | 기능정의_즐겨찾기 | — | 태그 추가·제거·AI 추천 태그·현재 태그 목록 표시 |
| drive-list | 내 드라이브 파일 리스트 | active | 내 드라이브 | 파일 리스트·액션 바·브레드크럼 | — | — | 기능정의_내드라이브 | — | 폴더·노트 생성, 다운로드·삭제·이동·공유 링크 복사 |
| folder-tree | 폴더 트리 | active | 내 드라이브 | 좌측 패널 | — | — | 기능정의_내드라이브 | 폴더 트리 동작 정책.md · 폴더 공유 제외.md | 이름순 고정. 폴더 공유 메뉴 없음 (삭제 결정) |
| trash-list | 휴지통 리스트 | active | 휴지통 | 파일 리스트·액션 바·브레드크럼 | — | — | 기능정의_휴지통 | — | 기존 XLSX 섹션명 기준 |
| trash-restore | 복원 / 영구 삭제 | active | 휴지통 | 항목 복원 모달·영구 삭제 모달·휴지통 비우기 모달 | — | — | 기능정의_휴지통 | — | |
| note-editor | 노트 에디터 | active | 노트 | 노트 에디터 | — | — | 기능정의_노트 | 노트 붙여넣기 블록 분리.md | 블록 기반 편집. 붙여넣기 시 Markdown 구조 유지하여 블록 분리 |
| note-header | 노트 헤더 액션 | active | 노트 | 노트 헤더·버전 기록 팝오버 | — | — | 기능정의_노트 | 새 노트 제목 자동 포커스.md | 제목 자동 포커스·전체 선택. 즐겨찾기·공유·더보기·오프라인 포함 |
| note-version-history | 버전 기록 | active | 노트 | 버전 기록·버전 기록 팝오버 | — | — | 기능정의_노트 | 버전 기록 프리뷰 읽기 전용.md | 수동/Altio 자동 저장 버전. 복원·Diff MVP 미제공 |
| note-share | 노트 공유 링크 | active | 노트 | 노트 헤더 | 즐겨찾기·내 드라이브 | 파일 리스트 | 기능정의_노트·기능정의_즐겨찾기·기능정의_내드라이브 | 공유 링크 OG 메타 노출.md · 공유 링크 별도 읽기 전용 URL.md · 삭제된 노트 링크 접근 처리.md | 링크 복사 버튼. 리스트 더보기 메뉴에서도 공유 링크 복사 가능 |
| note-download | 노트 다운로드 | active | 노트 | 노트 액션 | — | — | 기능정의_노트 | 노트 다운로드 Markdown 정책.md | 더보기(⋯) 팝오버 내 다운로드. 개별 .md 파일. 다중: 폴더명 기준 ZIP |
| altio-assistant | Altio AI 어시스턴트 | active | 노트 | Altio | 즐겨찾기 | 알티오 | 기능정의_노트·기능정의_즐겨찾기 | — | 인라인 제안 위젯 + 사이드바 |
| file-viewer | 파일 뷰어 | deprecated | 파일 | 파일 미리보기·파일 헤더 | — | — | 기능정의_파일 | 파일 기능 삭제.md | 파일 업로드·조회 스펙아웃 |
