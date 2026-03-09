# 00. 전체 화면 목록 (Screen Inventory)

> **문서 목적**: 모바일 앱(U00~U23)과 관리자 웹(A01~A10) 전체 화면의 번호, 이름, 한줄 설명, 와이어프레임 파일 링크를 한곳에서 확인할 수 있도록 정리한 화면 인벤토리.
> **기준 문서**: [`06-glossary.md`](../01-prd/06-glossary.md) 3절 화면 번호 ↔ 기능 매핑 테이블
> **총 화면 수**: 37개 (앱 27개 + 관리자 웹 10개)

---

## 1. 모바일 앱 화면 (U00~U23)

> 온보딩(U00 계열), 순찰(U02~U08), 공통(U09/U21~U23), 커뮤니티(U10~U13), 랭킹(U14), 마이페이지(U15~U20)

| 번호 | 화면명 | 기능 영역 | 한줄 설명 | 와이어프레임 |
|------|--------|-----------|-----------|-------------|
| U00 | 스플래시 | 온보딩 | 앱 로고 표시 및 로그인 토큰 확인 후 자동 전환 | [app/01-onboarding.md](app/01-onboarding.md#u00-스플래시) |
| U00a | 온보딩 슬라이드 | 온보딩 | 앱 소개 3장 슬라이드 (최초 실행 시만 표시) | [app/01-onboarding.md](app/01-onboarding.md#u00a-온보딩-슬라이드) |
| U00b | 로그인 | 온보딩 | 이메일/비밀번호 및 소셜 로그인(카카오/네이버/Google/Apple) | [app/01-onboarding.md](app/01-onboarding.md#u00b-로그인) |
| U00c | 회원가입 | 온보딩 | 이메일·비밀번호·닉네임·휴대폰 번호 입력 및 약관 동의 | [app/01-onboarding.md](app/01-onboarding.md#u00c-회원가입) |
| U00d | 비밀번호 찾기 | 온보딩 | 이메일 입력 후 비밀번호 재설정 링크 발송 | [app/01-onboarding.md](app/01-onboarding.md#u00d-비밀번호-찾기) |
| U02 | 순찰 대기 (홈) | 순찰 | 현재 위치 지도 + 최근 순찰 요약 카드 + 순찰 시작 버튼 | [app/02-home-patrol.md](app/02-home-patrol.md#u02-순찰-대기-홈) |
| U03 | 순찰 진행 중 | 순찰 | 실시간 경로(Route) 렌더링 + 타이머·거리·속도 표시 + 마킹/신고/종료 버튼 | [app/02-home-patrol.md](app/02-home-patrol.md#u03-순찰-진행-중) |
| U04 | 순찰 일시정지 | 순찰 | 타이머 정지 상태 표시 + 재개/종료 버튼 | [app/02-home-patrol.md](app/02-home-patrol.md#u04-순찰-일시정지) |
| U05 | 현장 마킹 | 순찰 | 바텀시트 형태로 사진·메모·유형(일반/신고) 입력하여 PatrolMark 생성 | [app/03-patrol-detail.md](app/03-patrol-detail.md#u05-현장-마킹-바텀시트) |
| U06 | 신고 작성 | 순찰 | 카테고리·상세 설명·사진 입력 후 Report(submitted) 생성 | [app/03-patrol-detail.md](app/03-patrol-detail.md#u06-신고-작성) |
| U07 | 순찰 결과 | 순찰 | 순찰 완료 요약(거리·시간·마킹수·포인트) + 활동 일지(Patrol.note) 입력 | [app/03-patrol-detail.md](app/03-patrol-detail.md#u07-순찰-결과) |
| U08 | 순찰 기록 상세 | 순찰 | 과거 순찰 경로 지도 + PatrolMark 핀 목록 + 활동 일지 열람 | [app/03-patrol-detail.md](app/03-patrol-detail.md#u08-순찰-기록-상세) |
| U09 | 알림 목록 | 공통 | 수신 PushNotification 목록 + 읽음/미읽음 표시 + 전체 읽음 처리 | [app/07-settings-notifications.md](app/07-settings-notifications.md#u09-알림-목록) |
| U10 | 피드 (커뮤니티) | 커뮤니티 | 게시글 목록 (활동인증/정보공유/자유 카테고리 탭 + 무한 스크롤) | [app/04-community.md](app/04-community.md#u10-피드-커뮤니티) |
| U11 | 게시글 상세 | 커뮤니티 | 본문·이미지·좋아요·댓글 열람 및 댓글 작성 | [app/04-community.md](app/04-community.md#u11-게시글-상세) |
| U12 | 게시글 작성 | 커뮤니티 | 게시판 선택·제목·본문·이미지(최대 5장) 입력 후 Post 생성 | [app/04-community.md](app/04-community.md#u12-게시글-작성) |
| U13 | 영상 목록/재생 | 커뮤니티 | 영상 썸네일 그리드 목록(U13-A) + YouTube/Vimeo 인앱 재생(U13-B) | [app/04-community.md](app/04-community.md#u13-영상-목록재생) |
| U14 | 랭킹 (리더보드) | 랭킹 | 실시간·주간·월간 탭별 순찰 거리 순위 + 내 순위 하단 고정 표시 | [app/05-ranking.md](app/05-ranking.md#u14-랭킹-리더보드) |
| U15 | 프로필 (마이페이지) | 마이페이지 | 프로필 이미지·닉네임·통계 요약(순찰수·거리·포인트) + 메뉴 목록 | [app/06-mypage.md](app/06-mypage.md#u15-프로필-마이페이지) |
| U16 | 활동 내역 | 마이페이지 | 순찰 이력 텍스트 목록 (날짜·거리·시간·포인트·마킹수, 최신순) | [app/06-mypage.md](app/06-mypage.md#u16-활동-내역) |
| U17 | 순찰 기록 목록 | 마이페이지 | 월별 그룹 + 미니 경로 지도 썸네일로 순찰 기록 시각적 비교 | [app/06-mypage.md](app/06-mypage.md#u17-순찰-기록-목록) |
| U18 | 포인트 내역 | 마이페이지 | 현재 보유 포인트 + 적립·차감 이력 (초록/빨강 색상 구분) | [app/06-mypage.md](app/06-mypage.md#u18-포인트-내역) |
| U19 | 프로필 편집 | 마이페이지 | 프로필 사진·닉네임·휴대폰 번호 변경 (이메일 변경 불가) | [app/06-mypage.md](app/06-mypage.md#u19-프로필-편집) |
| U20 | 설정 | 마이페이지 | 알림 ON/OFF 토글·위치 권한 상태·로그아웃·회원 탈퇴·앱 버전 | [app/07-settings-notifications.md](app/07-settings-notifications.md#u20-설정) |
| U21 | 위치 권한 요청 | 공통 | GPS 위치 권한(항상 허용) 요청 팝업 — 순찰 시작 시 트리거 | [app/02-home-patrol.md](app/02-home-patrol.md) |
| U22 | 카메라/갤러리 권한 | 공통 | 카메라·사진 라이브러리 접근 권한 요청 팝업 — 마킹·게시글 사진 첨부 시 트리거 | [app/03-patrol-detail.md](app/03-patrol-detail.md) |
| U23 | 에러 화면 | 공통 | 네트워크·서버 오류 안내 + 재시도 버튼 | [app/02-home-patrol.md](app/02-home-patrol.md) |

> **비고**: U01은 정의되지 않음 (glossary 기준). U21·U22·U23은 독립 전체 화면이 아닌 시스템 팝업/공통 화면으로, 별도 와이어프레임 파일 없이 관련 화면 파일 내에 인터랙션으로 기술됨.

---

## 2. 관리자 웹 화면 (A01~A10)

> 사이드바 네비게이션 기반 SPA. 로그인(A09) → 대시보드(A01) → 각 관리 화면

| 번호 | 화면명 | 기능 영역 | 한줄 설명 | 와이어프레임 |
|------|--------|-----------|-----------|-------------|
| A01 | 대시보드 | 관리자 메인 | KPI 카드 4개(총 대원·금일 순찰·미처리 신고·금주 신규가입) + 라인/바 차트 + 최근 활동 목록 | [admin/02-dashboard.md](admin/02-dashboard.md) |
| A02 | 대원 관리 | 대원 관리 | 대원 목록 검색·필터·정렬·CSV 다운로드 + 대원 상세(순찰 이력·포인트 내역·상태 변경) | [admin/03-member-management.md](admin/03-member-management.md) |
| A03 | 신고 관리 | 신고 관리 | 신고 목록 상태 탭(submitted/in_progress/resolved) + 사이드 패널 상세 및 상태 전이 | [admin/04-report-management.md](admin/04-report-management.md) |
| A04 | 이벤트 관리 | 이벤트 관리 | 이벤트 CRUD + 보너스 배율(bonus_multiplier) 설정 + 진행중·예정·종료 상태 뱃지 | [admin/05-event-management.md](admin/05-event-management.md) |
| A05 | 포인트 관리 | 포인트 관리 | 대원 검색 후 포인트 수동 지급/차감 + 사유 입력 + 수동 조정 이력 조회 | [admin/06-point-management.md](admin/06-point-management.md) |
| A06 | Push 알림 관리 | 알림 관리 | Push 발송 이력 목록 + 새 알림 작성(전체/그룹 대상·제목·내용·미리보기) + 발송 | [admin/07-push-management.md](admin/07-push-management.md) |
| A07 | 통계 | 통계 | 기간 선택 + 요약 KPI 4개 + 일별 추이·시간대별·카테고리별 차트 + 지역별 히트맵 + CSV 내보내기 | [admin/08-statistics.md](admin/08-statistics.md) |
| A08 | 콘텐츠 관리 | 콘텐츠 관리 | 영상 URL CRUD(YouTube/Vimeo) + 게시판 카테고리 관리 + 신고된 게시글 처리(유지/숨김/삭제) | [admin/09-content-management.md](admin/09-content-management.md) |
| A09 | 로그인 | 관리자 인증 | 이메일/비밀번호 로그인 전용 화면 (사이드바 없음, role=admin 검증) | [admin/01-login.md](admin/01-login.md) |
| A10 | 설정 | 관리자 설정 | 관리자 계정 관리·포인트 정책(공식·상한)·어뷰징 임계값 설정 | _(와이어프레임 미작성)_ |

> **비고**: A10(설정) 화면은 glossary·IA·화면전환도에 정의되어 있으나 와이어프레임 파일이 아직 작성되지 않았음.

---

## 3. 화면 수 요약

| 구분 | 화면 수 | 비고 |
|------|---------|------|
| 모바일 앱 (U00~U23) | 27개 | U00 계열 5개(U00/a/b/c/d) + U02~U23 22개. U01 미정의. |
| 관리자 웹 (A01~A10) | 10개 | A10 와이어프레임 미작성 |
| **합계** | **37개** | |
