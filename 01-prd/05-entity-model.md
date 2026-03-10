# 05. 엔티티 모델

> **문서 목적**: 앱의 핵심 데이터 엔티티, 필드, 관계, 상태값을 정의하여 백엔드 설계와 UI 데이터 바인딩의 기준을 제공한다.
> **대상 독자**: 백엔드 개발자, 프론트엔드 개발자, 기획자
> **참조**: 엔티티 상태값 정의 및 용어 매핑은 `06-glossary.md` 참조

---

## 1. 엔티티 목록

| # | 엔티티 | 설명 |
|---|--------|------|
| 1 | User | 회원 (대원, 관리자 포함) |
| 2 | Patrol | 순찰 기록 |
| 3 | PatrolMark | 순찰 중 현장 기록 (마킹) |
| 4 | Report | 신고 |
| 5 | Post | 커뮤니티 게시글 |
| 6 | Comment | 게시글 댓글 |
| 7 | Ranking | 랭킹 집계 |
| 8 | Event | 이벤트 |
| 9 | PushNotification | Push 알림 |
| 10 | Dog | 반려견 |

---

## 2. 엔티티 상세 정의

### 2.1 User (회원)

| 필드 | 타입 | 필수 | 설명 |
|------|------|------|------|
| id | UUID | O | 고유 식별자 |
| email | String | O | 이메일 (로그인 ID) |
| password_hash | String | O | 암호화된 비밀번호 |
| name | String | O | 닉네임 |
| phone | String | O | 휴대폰 번호 |
| profile_img | String | X | 프로필 이미지 URL |
| role | Enum | O | 사용자 역할: `user`, `admin` |
| points | Integer | O | 현재 보유 포인트 (기본값: 0) |
| total_distance_km | Float | O | 누적 순찰 거리 (km, 기본값: 0) |
| total_patrols | Integer | O | 누적 순찰 횟수 (기본값: 0) |
| push_token | String | X | FCM/APNs 토큰 |
| created_at | Timestamp | O | 가입일시 |
| updated_at | Timestamp | O | 수정일시 |

**관계**:
- has many → Patrol
- has many → Post
- has many → Comment
- has many → Report
- has one → Ranking (기간별)
- has many → Dog

---

### 2.2 Patrol (순찰)

| 필드 | 타입 | 필수 | 설명 |
|------|------|------|------|
| id | UUID | O | 고유 식별자 |
| user_id | UUID (FK) | O | 순찰 수행 사용자 |
| status | Enum | O | 순찰 상태: `ready`, `active`, `paused`, `completed` |
| start_time | Timestamp | X | 순찰 시작 시각 (active 전환 시) |
| end_time | Timestamp | X | 순찰 종료 시각 (completed 전환 시) |
| duration_seconds | Integer | X | 순찰 순수 소요 시간 (정지 시간 제외, 초) |
| route | GeoJSON | X | 이동 경로 (LineString 좌표 배열) |
| distance_km | Float | X | 총 이동 거리 (km, 소수점 2자리) |
| avg_speed_kmh | Float | X | 평균 속도 (km/h) |
| points_earned | Integer | X | 이번 순찰로 획득한 포인트 |
| dog_id | UUID (FK) | X | 순찰 대상 반려견 (미선택 시 null) |
| note | String | X | 활동 일지 (최대 500자) |
| created_at | Timestamp | O | 레코드 생성일시 |
| updated_at | Timestamp | O | 수정일시 |

**관계**:
- belongs to → User
- belongs to → Dog
- has many → PatrolMark

**상태 전이**:
```
ready → active → paused → active (재개)
                         → completed
         active → completed (직접 종료)
```

---

### 2.3 PatrolMark (현장 기록 / 마킹)

| 필드 | 타입 | 필수 | 설명 |
|------|------|------|------|
| id | UUID | O | 고유 식별자 |
| patrol_id | UUID (FK) | O | 소속 순찰 |
| lat | Float | O | 위도 |
| lng | Float | O | 경도 |
| photo_urls | String[] | X | 사진 URL 목록 (최대 3장) |
| note | String | X | 메모 (최대 200자) |
| type | Enum | O | 유형: `normal`, `report` |
| created_at | Timestamp | O | 생성일시 |

**관계**:
- belongs to → Patrol
- has one → Report (type = 'report'인 경우)

---

### 2.4 Report (신고)

| 필드 | 타입 | 필수 | 설명 |
|------|------|------|------|
| id | UUID | O | 고유 식별자 |
| patrol_mark_id | UUID (FK) | O | 연관 마킹 |
| user_id | UUID (FK) | O | 신고자 |
| category | String | O | 신고 카테고리 (예: 불법투기, 시설파손, 안전위험, 기타) |
| description | String | O | 신고 내용 (최대 500자) |
| status | Enum | O | 처리 상태: `submitted`, `in_progress`, `resolved` |
| admin_note | String | X | 관리자 처리 메모 |
| resolved_at | Timestamp | X | 처리 완료 시각 |
| created_at | Timestamp | O | 신고 접수일시 |
| updated_at | Timestamp | O | 수정일시 |

**관계**:
- belongs to → PatrolMark
- belongs to → User

**상태 전이**:
```
submitted → in_progress → resolved
```

---

### 2.5 Post (게시글)

| 필드 | 타입 | 필수 | 설명 |
|------|------|------|------|
| id | UUID | O | 고유 식별자 |
| user_id | UUID (FK) | O | 작성자 |
| title | String | O | 제목 (최대 100자) |
| content | String | O | 본문 (최대 2000자) |
| images | String[] | X | 이미지 URL 목록 (최대 5장) |
| board_type | Enum | O | 게시판 유형: `activity`, `info`, `free` |
| likes_count | Integer | O | 좋아요 수 (기본값: 0) |
| comments_count | Integer | O | 댓글 수 (기본값: 0) |
| is_reported | Boolean | O | 신고 여부 (기본값: false) |
| created_at | Timestamp | O | 작성일시 |
| updated_at | Timestamp | O | 수정일시 |

**관계**:
- belongs to → User
- has many → Comment

---

### 2.6 Comment (댓글)

| 필드 | 타입 | 필수 | 설명 |
|------|------|------|------|
| id | UUID | O | 고유 식별자 |
| post_id | UUID (FK) | O | 소속 게시글 |
| user_id | UUID (FK) | O | 작성자 |
| content | String | O | 댓글 내용 (최대 500자) |
| is_reported | Boolean | O | 신고 여부 (기본값: false) |
| created_at | Timestamp | O | 작성일시 |

**관계**:
- belongs to → Post
- belongs to → User

---

### 2.7 Ranking (랭킹)

| 필드 | 타입 | 필수 | 설명 |
|------|------|------|------|
| id | UUID | O | 고유 식별자 |
| user_id | UUID (FK) | O | 대상 사용자 |
| period_type | Enum | O | 집계 기간: `daily`, `weekly`, `monthly` |
| period_key | String | O | 기간 키 (예: "2026-W10", "2026-03") |
| distance_total | Float | O | 해당 기간 총 거리 (km) |
| points_total | Integer | O | 해당 기간 총 포인트 |
| patrol_count | Integer | O | 해당 기간 순찰 횟수 |
| rank | Integer | O | 순위 |
| updated_at | Timestamp | O | 마지막 갱신일시 |

**관계**:
- belongs to → User

**갱신 정책**:
- daily: 매일 자정 집계
- weekly: 매주 월요일 자정 집계
- monthly: 매월 1일 자정 집계
- 실시간 탭은 순찰 종료 시 즉시 갱신

---

### 2.8 Event (이벤트)

| 필드 | 타입 | 필수 | 설명 |
|------|------|------|------|
| id | UUID | O | 고유 식별자 |
| title | String | O | 이벤트 제목 |
| description | String | O | 이벤트 설명 |
| start_date | Date | O | 시작일 |
| end_date | Date | O | 종료일 |
| bonus_multiplier | Float | X | 포인트 보너스 배율 (예: 1.5 = 150%) |
| is_active | Boolean | O | 활성 여부 |
| created_by | UUID (FK) | O | 등록 관리자 |
| created_at | Timestamp | O | 등록일시 |
| updated_at | Timestamp | O | 수정일시 |

**관계**:
- belongs to → User (admin)

---

### 2.9 PushNotification (Push 알림)

| 필드 | 타입 | 필수 | 설명 |
|------|------|------|------|
| id | UUID | O | 고유 식별자 |
| title | String | O | 알림 제목 |
| body | String | O | 알림 본문 |
| target_type | Enum | O | 대상: `all`, `group` |
| target_group | String | X | 그룹 지정 시 대상 조건 |
| deep_link | String | X | 탭 시 이동할 화면 경로 |
| sent_by | UUID (FK) | O | 발송 관리자 |
| sent_at | Timestamp | O | 발송일시 |
| read_count | Integer | O | 읽음 수 (기본값: 0) |
| created_at | Timestamp | O | 생성일시 |

**관계**:
- belongs to → User (admin, sent_by)

---

### 2.10 Dog (반려견)

| 필드 | 타입 | 필수 | 설명 |
|------|------|------|------|
| id | UUID | O | 고유 식별자 |
| user_id | UUID (FK) | O | 반려견 보호자 |
| photo | String | X | 반려견 사진 URL |
| name | String | O | 반려견 이름 (최대 20자) |
| breed | String | O | 견종 |
| gender | Enum | O | 성별: `male`, `female` |
| birthday | Date | X | 생년월일 |
| is_neutered | Boolean | O | 중성화 여부 (기본값: false) |
| is_vaccinated | Boolean | O | 예방접종 여부 (기본값: false) |
| personality | String | X | 성격/특이사항 (최대 200자) |
| created_at | Timestamp | O | 등록일시 |
| updated_at | Timestamp | O | 수정일시 |

**관계**:
- belongs to → User

---

## 3. 엔티티 관계 다이어그램 (텍스트 기반 ER)

```
┌──────────┐       1:N        ┌──────────┐       1:N       ┌─────────────┐
│   User   │─────────────────▶│  Patrol  │───────────────▶│ PatrolMark  │
│          │                  │          │                 │             │
│ id       │                  │ id       │                 │ id          │
│ email    │                  │ user_id  │                 │ patrol_id   │
│ name     │                  │ dog_id   │                 │ lat, lng    │
│ role     │                  │ status   │                 │ type        │
│ points   │                  │ route    │                 │ photo_urls  │
└──────────┘                  │ distance │                 └─────────────┘
     │                        └──────────┘                      │
     │ 1:N                         ▲                            │ 1:1
     │                             │ 1:N                        │ (type='report')
     ▼                             │                            ▼
┌──────────┐                  ┌──────────┐                ┌──────────┐
│   Dog    │─────────────────▶│  Patrol  │                │  Report  │
│          │  1:N             │          │                │          │
│ id       │                  └──────────┘                │ id       │
│ user_id  │                                              │ mark_id  │
│ name     │                                              │ user_id  │
│ breed    │                                              │ category │
│ gender   │                                              │ status   │
└──────────┘                                              └──────────┘

┌──────────┐                                              ┌──────────┐
│   Post   │                                              │ Comment  │
│          │       1:N       ┌──────────┐                 │          │
│ id       │────────────────▶│ Comment  │                 │ id       │
│ user_id  │                 │          │                 │ post_id  │
│ board_ty │                 │ id       │                 │ user_id  │
│ likes_ct │                 │ post_id  │                 └──────────┘
└──────────┘                 │ user_id  │
                             └──────────┘

┌──────────┐                 ┌──────────────────┐
│ Ranking  │                 │ PushNotification │
│          │                 │                  │
│ user_id  │                 │ id               │
│ period   │                 │ title, body      │
│ distance │                 │ target_type      │
│ rank     │                 │ sent_by (admin)  │
└──────────┘                 └──────────────────┘

┌──────────┐
│  Event   │
│          │
│ id       │
│ title    │
│ dates    │
│ bonus    │
│ admin_id │
└──────────┘
```

**관계 요약**:

| 관계 | 유형 | 설명 |
|------|------|------|
| User → Patrol | 1:N | 한 사용자가 여러 순찰을 수행 |
| User → Dog | 1:N | 한 사용자가 여러 반려견을 등록 |
| Dog → Patrol | 1:N | 한 반려견이 여러 순찰에 참여 |
| Patrol → PatrolMark | 1:N | 한 순찰에 여러 마킹이 생성됨 |
| PatrolMark → Report | 1:1 | 마킹 유형이 'report'이면 신고 연결 |
| User → Report | 1:N | 한 사용자가 여러 신고를 접수 |
| User → Post | 1:N | 한 사용자가 여러 게시글을 작성 |
| Post → Comment | 1:N | 한 게시글에 여러 댓글이 달림 |
| User → Comment | 1:N | 한 사용자가 여러 댓글을 작성 |
| User → Ranking | 1:N | 한 사용자의 기간별 랭킹 레코드 |
| User (admin) → Event | 1:N | 관리자가 이벤트를 등록 |
| User (admin) → PushNotification | 1:N | 관리자가 알림을 발송 |

---

## 4. 상태값(Status) 상세 정의

### 4.1 Patrol.status

| 상태 | 값 | 설명 | 전이 가능 상태 |
|------|----|------|---------------|
| 대기 | `ready` | 순찰이 생성되었으나 아직 시작되지 않음 | → `active` |
| 진행 중 | `active` | GPS 트래킹이 활성 상태 | → `paused`, → `completed` |
| 일시정지 | `paused` | GPS 수집이 일시 중단됨 | → `active`, → `completed` |
| 완료 | `completed` | 순찰이 종료되어 기록이 확정됨 | (최종 상태) |

### 4.2 Report.status

| 상태 | 값 | 설명 | 전이 가능 상태 |
|------|----|------|---------------|
| 접수됨 | `submitted` | 사용자가 신고를 접수한 초기 상태 | → `in_progress` |
| 처리 중 | `in_progress` | 관리자가 신고를 확인하고 처리 진행 중 | → `resolved` |
| 처리 완료 | `resolved` | 신고가 처리 완료됨 | (최종 상태) |

### 4.3 User.role

| 역할 | 값 | 설명 | 권한 |
|------|----|------|------|
| 일반 사용자 | `user` | 순찰, 커뮤니티, 랭킹 이용 가능 | 모바일 앱 전체 기능 |
| 관리자 | `admin` | 대원/신고/이벤트/포인트/통계 관리 | 모바일 앱 + 관리자 웹 전체 기능 |
