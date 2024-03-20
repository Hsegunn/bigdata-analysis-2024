## 9일차 학습

### 빅데이터 실습
#### OpenAPI 기반 크롤링 실습
- [공공데이터포털]https://data.go.kr
    - 국가 공공기관에서 무료로 제공하는 데이터 API 서비스 포털
    - 한국관광공사 관광빅데이터 API 사용
    - http 프로토콜로 요청해야함. https로 요청시 ssl 오류 발생

    ```python
    ## 반복문으로 처리
    totalList = []
    year = 2023
    month = 12

    for day in tqdm(range(1,32)):
        reqYmd = f'{year}{month}{day:02d}'
        data = getTouristDataService(reqYmd)
        if xmltodict.parse(data)['response']['body']['items'] == None: # 해당 날짜에 데이터가 없을 수 있음
            resList = []
        else:
            resList = xmltodict.parse(data)['response']['body']['items']['item']
        totalList = totalList + resList
    ```
    100%|██████████| 31/31 [01:23<00:00,  2.70s/it]

#### 통계 분석 리뷰
- 그래프를 사용한 기술 통계 분석
- 히트맵을 사용한 상관 분석

#### 와인 품질 분석
- [캘리포니아 어바인 대학 연구소](https://archive.ics.uci.edu/dataset/186/wine+quality)