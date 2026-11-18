# boxoffice — KOBIS 박스오피스 조회 스킬

## 하는 일
날짜를 지정하면 국내 박스오피스 1위 영화 제목을 알려 준다.
날짜와 영화 제목을 지정하면 해당 영화의 당일 관객 수를 알려 준다.

## 들어 있는 파일
- .claude/skills/boxoffice/SKILL.md
- .claude/skills/boxoffice/scripts/boxoffice.py
- .claude/skills/boxoffice/LICENSE

## 필요한 것
- Python 3
- requests 패키지
- tools.py와 secret.py
- KOBIS API 키

## 설치
프로젝트 폴더의 `.claude/skills/boxoffice/`에 boxoffice 폴더를 둔다.
같은 프로젝트 폴더에 tools.py와 secret.py를 준비한다.

프로젝트 폴더에서 Claude Code를 실행하고,
`/boxoffice 20261114 박스오피스 1위 영화를 알려줘`처럼 요청한다.

## 바깥으로 요청하는 곳

- 주소 https://www.kobis.or.kr/kobisopenapi/webservice/rest/boxoffice/searchDailyBoxOfficeList.json


## 키
KOBIS API 키는 프로젝트 폴더의 secret.py에 API_KEY 변수로 저장한다.
tools.py가 이 값을 불러 사용한다.

배포하는 저장소에는 실제 키를 포함하지 않는다.
사용자가 직접 secret.py를 준비하며, 이 파일은 .gitignore로 제외한다.

## 권한

SKILL.md에 allowed-tools 설정은 없다.
스크립트 실행 시 Claude Code의 권한 설정에 따라
해당 Python 명령의 실행을 허용할지 물을 수 있다.

## 라이선스
MIT 라이선스를 사용한다. `.claude/skills/boxoffice/LICENSE`에 있다.