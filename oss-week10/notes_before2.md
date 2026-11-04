# oss-week9/tools.py 함수 정리

`tools.py`는 영화진흥위원회(KOBIS) 오픈 API의 **일별 박스오피스** 정보를 가져오는 도구 모음이다.

## 공통 사항

- `BASE_URL`: KOBIS 일별 박스오피스 조회 API 주소 (`searchDailyBoxOfficeList.json`)
- `API_KEY`: `secret.py`에서 불러오는 API 키
- 두 함수 모두 `requests.get(BASE_URL, params={"key": API_KEY, "targetDt": date}, timeout=10)`으로 요청하고,
  응답 JSON의 `boxOfficeResult.dailyBoxOfficeList`에서 영화 목록을 꺼낸다.

## 함수 목록

### 1. `get_boxoffice_rank_1(date)`

그 날짜의 박스오피스 **1위 영화 제목**을 알려준다.

| 구분 | 내용 |
|---|---|
| 입력 | `date` (문자열) — 8자리 날짜, 예: `"20260824"` |
| 출력 | (문자열) 1위 영화 제목 |

- 동작: 영화 목록의 첫 번째 항목(`movies[0]`)의 `movieNm`을 반환한다.

### 2. `get_movie_audience(date, title)`

그 날짜 박스오피스 순위에서 특정 영화의 **당일 관객 수**를 알려준다.

| 구분 | 내용 |
|---|---|
| 입력 | `date` (문자열) — 8자리 날짜, 예: `"20260824"`<br>`title` (문자열) — 영화 제목, 예: `"오디세이"` |
| 출력 | (문자열) 쉼표와 '명'을 붙인 관객 수, 예: `"186,587명"`<br>순위에 없으면 `"'<title>' 은(는) <date> 순위에 없습니다."` |

- 동작: 영화 목록을 돌면서 `movieNm`이 `title`과 정확히 일치하는 영화의 `audiCnt`를 찾아 형식을 맞춰 반환한다.
