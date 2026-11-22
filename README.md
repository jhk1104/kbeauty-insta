# kbeauty-insta

K뷰티아카데미 인스타그램 자동 게시용 이미지 저장소입니다.
Windsor.ai가 매일 오전 10시(KST)에 `schedule.csv`에서 그날의 게시물 1개를 읽어 업로드합니다.

## 폴더 구조

```
kbeauty-insta/
├── README.md            ← 이 문서 (운영 규칙)
├── schedule.csv         ← 게시 일정표 (날짜·시간·이미지 URL·캡션·상태)
├── images/
│   ├── 2026-11/         ← 월별 폴더, 파일명 = 게시일
│   └── 2026-12/
├── captions/
│   ├── 2026-11/         ← 이미지와 같은 이름의 .txt 캡션
│   └── 2026-12/
├── templates/
│   ├── hashtags.txt     ← 공통 해시태그 세트
│   └── caption-template.txt
└── archive/             ← 게시 완료된 원본·시안 보관
```

## 파일 이름 규칙

- 이미지: `images/YYYY-MM/YYYY-MM-DD.jpg` (예: `images/2026-11/2026-11-24.jpg`)
- 캐러셀(여러 장): `YYYY-MM-DD_1.jpg`, `YYYY-MM-DD_2.jpg` …
- 캡션: `captions/YYYY-MM/YYYY-MM-DD.txt`
- 영문 소문자·숫자·하이픈만 사용 (한글·공백 금지 → URL 깨짐 방지)

## 이미지 규격 (인스타그램 권장)

| 형식 | 크기 | 비율 |
|---|---|---|
| 피드 세로형 (권장) | 1080 × 1350 px | 4:5 |
| 정사각형 | 1080 × 1080 px | 1:1 |

- JPG, 8MB 이하

## Windsor.ai에 넣을 이미지 주소

저장소가 공개(Public)여야 합니다. 주소 형식:

```
https://raw.githubusercontent.com/jhk1104/kbeauty-insta/main/images/2026-11/2026-11-24.jpg
```

## schedule.csv 상태값

- `ready` 게시 대기 · `posted` 게시 완료 · `hold` 보류

## 매일 운영 순서

1. `images/YYYY-MM/`에 게시일 이름으로 이미지 업로드
2. `captions/YYYY-MM/`에 같은 이름의 캡션 작성 (`templates/` 참고)
3. `schedule.csv`에 한 줄 추가 (status = ready)
4. 게시 후 status를 posted로 바꾸고, 원본·시안은 `archive/`로 이동
