# 반려견 순찰대 GPS 트래킹 & 커뮤니티 앱

## 프로젝트 개요

반려견주와 방범 활동 대원이 함께 참여하는 GPS 기반 산책/순찰 트래킹 앱의 기획 문서입니다.

---

## 산출물 목차

### 📋 01-PRD (기획서)

| 파일 | 내용 |
|------|------|
| [01-project-overview.md](01-prd/01-project-overview.md) | 프로젝트 개요, 배경, 목적 |
| [02-personas.md](01-prd/02-personas.md) | 사용자 페르소나 4개 |
| [03-feature-specs.md](01-prd/03-feature-specs.md) | 기능 명세 (우선순위 P0/P1/P2) |
| [04-information-architecture.md](01-prd/04-information-architecture.md) | 정보 구조 (IA) |
| [05-entity-model.md](01-prd/05-entity-model.md) | 엔티티 모델 (9개) |
| [06-glossary.md](01-prd/06-glossary.md) | 용어 사전 — 화면 번호 기준 문서 |

### 🎨 02-UX (UX 설계)

| 파일 | 내용 |
|------|------|
| [01-user-journey-map.md](02-ux/01-user-journey-map.md) | 사용자 여정 맵 (5개 시나리오) |
| [02-task-flows.md](02-ux/02-task-flows.md) | 태스크 플로우 (기능별 상세) |
| [03-screen-transition.md](02-ux/03-screen-transition.md) | 화면 전환 다이어그램 |

### 📱 03-UI 와이어프레임

#### 화면 전체 목록

| 파일 | 내용 |
|------|------|
| [03-ui-wireframes/00-screen-inventory.md](03-ui-wireframes/00-screen-inventory.md) | 전체 화면 인벤토리 (번호·이름·설명·파일 링크) |

#### 사용자 앱 (U00~U23, 27개 화면)

| 파일 | 화면 번호 | 화면명 |
|------|----------|--------|
| [01-onboarding.md](03-ui-wireframes/app/01-onboarding.md) | U00, U00a, U00b, U00c, U00d | 스플래시, 온보딩 슬라이드, 로그인, 회원가입, 비밀번호 찾기 |
| [02-home-patrol.md](03-ui-wireframes/app/02-home-patrol.md) | U02, U03, U04 | 순찰 대기(홈), 순찰 진행 중, 순찰 일시정지 |
| [03-patrol-detail.md](03-ui-wireframes/app/03-patrol-detail.md) | U05, U06, U07, U08 | 현장 마킹, 신고 작성, 순찰 결과, 순찰 기록 상세 |
| [04-community.md](03-ui-wireframes/app/04-community.md) | U10, U11, U12, U13 | 커뮤니티 피드, 게시글 상세, 게시글 작성, 영상 목록/재생 |
| [05-ranking.md](03-ui-wireframes/app/05-ranking.md) | U14 | 랭킹 (리더보드) |
| [06-mypage.md](03-ui-wireframes/app/06-mypage.md) | U15, U16, U17, U18, U19 | 프로필, 활동 내역, 순찰 기록 목록, 포인트 내역, 프로필 편집 |
| [07-settings-notifications.md](03-ui-wireframes/app/07-settings-notifications.md) | U20, U09 | 설정, 알림 목록 |

> U21(위치 권한), U22(카메라/갤러리 권한), U23(에러 화면)은 공통 팝업/시스템 화면으로 관련 파일 내 인터랙션으로 기술됨.

#### 관리자 웹 (A01~A10, 10개 화면)

| 파일 | 화면 번호 | 화면명 |
|------|----------|--------|
| [01-login.md](03-ui-wireframes/admin/01-login.md) | A09 | 관리자 로그인 |
| [02-dashboard.md](03-ui-wireframes/admin/02-dashboard.md) | A01 | 대시보드 |
| [03-member-management.md](03-ui-wireframes/admin/03-member-management.md) | A02 | 대원 관리 |
| [04-report-management.md](03-ui-wireframes/admin/04-report-management.md) | A03 | 신고 관리 |
| [05-event-management.md](03-ui-wireframes/admin/05-event-management.md) | A04 | 이벤트 관리 |
| [06-point-management.md](03-ui-wireframes/admin/06-point-management.md) | A05 | 포인트 관리 |
| [07-push-management.md](03-ui-wireframes/admin/07-push-management.md) | A06 | Push 알림 관리 |
| [08-statistics.md](03-ui-wireframes/admin/08-statistics.md) | A07 | 통계 |
| [09-content-management.md](03-ui-wireframes/admin/09-content-management.md) | A08 | 콘텐츠 관리 |
| _(미작성)_ | A10 | 관리자 설정 |

### 🔧 04-기술 스택

| 파일 | 내용 |
|------|------|
| [01-comparison-table.md](04-tech-stack/01-comparison-table.md) | 기술 스택 비교표 (6개 항목) |
| [02-system-architecture.md](04-tech-stack/02-system-architecture.md) | 시스템 아키텍처 |

---

## 읽는 순서

1. 프로젝트 개요 → 2. 페르소나 → 3. 기능 명세 → 4. IA → 5. 엔티티 모델 → 6. 용어 사전
7. 사용자 여정 맵 → 8. 태스크 플로우 → 9. 화면 전환도
10. 화면 인벤토리 → 와이어프레임 (앱 → 어드민)
11. 기술 스택 비교표 → 시스템 아키텍처

---

## 프로젝트 정보

- 총 화면 수: 37개 (사용자 앱 27개 + 관리자 웹 10개)
- 산출물 형식: 마크다운 + ASCII 와이어프레임
- 기술 스택: 비교표만 제시 (결정은 개발사와 협의)

---

## Known Issues (일관성 검증 결과)

전체 산출물을 교차 검증한 결과 아래 불일치 사항이 확인되었습니다.

### Issue 1: 화면 수 불일치 — 중요

| 위치 | 주장 | 실제 (glossary 기준) |
|------|------|---------------------|
| `03-screen-transition.md` 서두 | "전체 34개 화면" | 앱 27개 + 관리자 10개 = **37개** |
| 해당 README 초안 (task 지시) | "사용자 앱 24개, 관리자 10개 = 34개" | 앱 27개, 관리자 10개 = **37개** |

**원인 분석**: glossary의 모바일 앱 화면 목록에는 U00/U00a/U00b/U00c/U00d(5개) + U02~U23(22개) = **27개**가 정의되어 있음. U01은 정의되지 않음. 일부 문서에서 U00 계열(스플래시~비밀번호 찾기)을 1개로 묶어 계산한 결과 "24개"로 표기된 것으로 추정됨.

**권고**: glossary(06-glossary.md) 3.1절이 기준 문서이므로, 해당 테이블에 정의된 27개(앱) + 10개(관리자) = 37개를 공식 수치로 확정하거나, 또는 U00 계열 집계 방식을 팀 내에서 합의하여 모든 문서에 동일하게 적용 필요.

---

### Issue 2: A10 관리자 설정 — 와이어프레임 미작성

| 위치 | 내용 |
|------|------|
| `06-glossary.md` 3.2절 | A10 설정 화면 정의됨 (관리자 계정·포인트 정책·어뷰징 임계값) |
| `04-information-architecture.md` | A10 설정 화면 IA 정의됨 |
| `03-screen-transition.md` | A10 설정 화면 전환 정의됨 |
| `03-ui-wireframes/admin/` | **A10 와이어프레임 파일 없음** |

**권고**: `03-ui-wireframes/admin/10-settings.md` 파일 작성 필요. 포인트 정책(1km=100pt, 일일 상한 1,000pt 등)과 어뷰징 임계값(속도 기준 3단계) 설정 폼이 핵심 내용.

---

### Issue 3: 관리자 파일 번호와 화면 번호 불일치

관리자 와이어프레임 파일의 순서 번호(01~09)가 화면 번호(A01~A09)와 일치하지 않음.

| 파일명 | 실제 화면 번호 |
|--------|--------------|
| `admin/01-login.md` | A09 (로그인) |
| `admin/02-dashboard.md` | A01 (대시보드) |
| `admin/03-member-management.md` | A02 (대원 관리) |
| `admin/04-report-management.md` | A03 (신고 관리) |
| `admin/05-event-management.md` | A04 (이벤트 관리) |
| `admin/06-point-management.md` | A05 (포인트 관리) |
| `admin/07-push-management.md` | A06 (Push 알림 관리) |
| `admin/08-statistics.md` | A07 (통계) |
| `admin/09-content-management.md` | A08 (콘텐츠 관리) |

**원인**: 로그인(A09)이 사용자 경험 상 가장 먼저 접하는 화면이므로 파일 순서 `01`에 배치된 것으로 보임. 논리적으로 타당하나, 파일명만 보고 화면 번호를 유추하기 어려울 수 있음.

**권고**: 현재 파일 구조 유지 (사용자 흐름 기준 정렬)는 수용 가능. 단, 각 파일 상단의 `> 화면 번호: AXX` 메타데이터가 이미 명시되어 있으므로 혼동 위험은 낮음. 파일명에 화면 번호를 병기하는 방안 검토 가능 (예: `01-login-A09.md`).

---

### Issue 4: U01 화면 번호 공백

glossary 3.1절 테이블에서 U00 계열(U00/U00a~d) 다음이 바로 U02로 시작하여 **U01이 정의되지 않음**. 다른 모든 문서도 동일하게 U01을 건너뜀.

**권고**: 의도적 공백인지 확인 필요. 향후 기능 추가(예: 프로필 초기 설정 화면) 시 U01을 예약 번호로 활용하거나, 공식적으로 "미사용"으로 glossary에 명시하는 것을 권고.

---

### 일관성 확인 항목 (문제 없음)

| 항목 | 결과 |
|------|------|
| glossary 용어(Patrol, PatrolMark, Report, Points, Ranking 등) → 와이어프레임 사용 | 일관성 확인됨 |
| Report.status 값(submitted/in_progress/resolved) | glossary ↔ A03 와이어프레임 일치 |
| Patrol.status 값(ready/active/paused/completed) | glossary ↔ U02~U04 와이어프레임 일치 |
| Post.board_type 값(activity/info/free) | glossary ↔ U10/U12/A08 와이어프레임 일치 |
| PushNotification.target_type(all/group) | glossary ↔ A06 와이어프레임 일치 |
| 포인트 공식(1km=100pt) | glossary ↔ U02/U03/U07 와이어프레임 일치 |
| 사진 최대 장수(마킹 3장, 게시글 5장) | glossary ↔ U05/U06/U12 와이어프레임 일치 |
| 닉네임 길이(2~10자) | glossary 암묵적 기준 ↔ U00c/U19 와이어프레임 일치 |
| 화면 전환 관계(U03→U05→U06, U07→U08 등) | task-flows ↔ 와이어프레임 인터랙션 노트 일치 |
