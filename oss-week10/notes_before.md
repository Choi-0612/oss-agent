# tools.py 함수 정리 (week09)

`oss-week9/tools.py`는 영화진흥위원회(KOBIS) 오픈 API로 **일별 박스오피스** 정보를 가져오는 도구 모음입니다.

- API 키: `secret.py`의 `API_KEY`를 불러와 사용
- 요청 주소(`BASE_URL`): `searchDailyBoxOfficeList.json` (일별 박스오피스 목록)
- 두 함수 모두 `requests.get(..., timeout=10)`으로 요청하고, 응답의 `boxOfficeResult.dailyBoxOfficeList`를 사용

## 1. `get_boxoffice_rank_1(date)`

그 날짜의 박스오피스 **1위 영화 제목**을 알려준다.

| 구분 | 내용 |
|------|------|
| 받는 것 | `date` (문자열) – 8자리 날짜. 예: `"20260824"` |
| 돌려주는 것 | (문자열) 1위 영화 제목 |

동작: 목록의 첫 번째 항목(`movies[0]`)의 `movieNm`을 돌려준다.

## 2. `get_movie_audience(date, title)`

그 날짜 박스오피스 순위에서 특정 영화의 **당일 관객 수**를 알려준다.

| 구분 | 내용 |
|------|------|
| 받는 것 | `date` (문자열) – 8자리 날짜. 예: `"20260824"`<br>`title` (문자열) – 영화 제목. 예: `"오디세이"` |
| 돌려주는 것 | (문자열) 쉼표와 '명'을 붙인 관객 수. 예: `"186,587명"`<br>순위에 없으면 `"'{title}' 은(는) {date} 순위에 없습니다."` |

동작: 목록을 하나씩 돌며 `movieNm`이 `title`과 정확히 같은 영화를 찾고, `audiCnt`를 숫자로 바꿔 천 단위 쉼표를 붙여 돌려준다.
