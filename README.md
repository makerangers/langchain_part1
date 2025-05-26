# LangChain 기반 AI 투자 보고서 생성기

이 프로젝트는 Streamlit 웹 애플리케이션을 통해 주식 종목의 기본 정보와 재무제표를
조회하고, OpenAI 모델을 활용하여 한글 투자 보고서를 생성해 주는 예제입니다.
MeiliSearch 검색 엔진으로 종목을 찾고, yfinance에서 데이터를 가져와 LangChain 체인으로
AI 리포트를 작성합니다.

## 주요 기능

- **종목 검색**: MeiliSearch 인덱스(`nsdaq`)를 이용해 회사명을 검색합니다.
- **기본 정보 및 재무제표 조회**: yfinance 라이브러리로 기본 정보와 분기 재무제표를
  가져와 Markdown 형식으로 보여 줍니다.
- **AI 투자 보고서 생성**: OpenAI `gpt-4o-mini` 모델을 호출해 종목 투자 의견을
  요약한 보고서를 생성합니다.

## 설치 및 실행 방법

1. Python 3.11 이상을 권장합니다.
2. 의존성 설치:

   ```bash
   pip install -r requirements.txt
   ```
3. 프로젝트 루트에 `.env` 파일을 만들고 다음 환경 변수를 설정합니다.

   ```ini
   OPENAI_API_KEY=YOUR_OPENAI_KEY
   MEILISEARCH_URL=http://localhost:7700
   MEILISEARCH_API_KEY=YOUR_MEILISEARCH_KEY
   ```
4. Streamlit 앱 실행:

   ```bash
   streamlit run app.py
   ```

## 파일 구조

- `app.py` – Streamlit 애플리케이션 진입점입니다.
- `search.py` – MeiliSearch 클라이언트로 종목을 검색합니다.
- `stock_info.py` – yfinance에서 기본 정보와 재무제표를 가져옵니다.
- `report_service.py` – LangChain을 사용해 AI 투자 보고서를 생성합니다.
- `requirements.txt` – 필요한 파이썬 패키지 목록입니다.

## 참고 사항

- MeiliSearch에 `nsdaq` 인덱스가 이미 구축되어 있어야 검색이 동작합니다.
- 외부 API 호출이 많으므로 실행 시 인터넷 연결이 필요합니다.
- 예제 수준의 코드이며 테스트나 배포 스크립트는 포함되어 있지 않습니다.

