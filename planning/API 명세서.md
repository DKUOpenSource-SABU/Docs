|기능 분류  |기능 설명       |HTTP Method|Endpoint                            |pid    |Request                                              |Response               |
|-------|------------|-----------|------------------------------------|-------|-----------------------------------------------------|-----------------------|
|[클러스터링]|ETF 종목 코드 검색|GET        |/etfs/search?q={ticker}             |CLU-001|ticker                                             |ticker, name           |
|       |ETF 종목 코드 검색|GET        |/etfs/search?cluster={ticker}            |CLU-002|ticker                                             |ticker, name           |
|       |클러스터 실행     |POST       |/clustering/run                     |CLU-003|ets, n_clusters                                      |message, clusters   |
|       |클러스터 추천     |GET        |/clustering/recommendation          |CLU-005|                                                     |recommended_etfs       |
|[백테스팅] |백테스트 실행     |POST       |/backtest/run                       |BTE-001|etfs, start_date, end_date, initial_capital, fee_rate|message, backtest_id   |
|       |백테스트 결과 조회  |GET        |/backtest/results?backtest_id={id}  |BTE-002|                                                     |                       |
|       |자산 변동 추이 조회 |GET        |/backtest/variation?backtest_id={id}|BTE-003|                                                     |dates, estimated_assets|
