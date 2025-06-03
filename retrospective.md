# 🧠 SABU 프로젝트 회고 및 문제 해결

## ✅ 잘한 점

- **API 명세서의 체계적 정리**
  - 클러스터링, 백테스트, ETF 데이터 수집 등 기능을 프로세스 ID 기반으로 체계적으로 분류함.
  - Swagger 연동을 통한 테스트 환경 구축이 효율적이었음.

- **프론트-백 협업 효율성**
  - 공통 API 스펙 기준 문서를 바탕으로 프론트와 백엔드 간 명확한 역할 분리가 가능했음.
  - 클러스터링/백테스트 결과 시각화를 위한 라벨 설계가 일관적이었음.

- **캐시 처리 및 성능 최적화**
  - Diskcache를 도입하여 동일 요청에 대한 반복 처리 비용을 절감.
  - 백테스트 결과 및 클러스터링 데이터를 로컬 캐시에 저장하여 API 속도 개선.

- **시각화 중심의 데이터 제공**
  - 클러스터링 결과를 Chart.js 기반 시각화로 제공함으로써 사용자의 이해도 상승.
  - 사용자 중심의 인터랙티브한 분석 경험 제공.


## ❌ 아쉬운 점

- **CORS 및 리다이렉션 문제**
  - HTTPS와 HTTP 간 리다이렉트 충돌 문제 발생 (특히 `/backtest` API).
  - `OPTIONS` 프리플라이트 요청에서 307 Redirect 발생 → CORS 오류로 연결 차단됨.

- **디스크 공간 부족**
  - Docker 빌드 중 HDF5 및 PyTorch 관련 패키지 설치 시 공간 부족 오류 발생 (`[Errno 28]`).
  - 임시로 `/mnt/data`를 저장소로 지정해 해결했지만, 루트 디스크 용량 관리 필요성 확인.

- **메트릭 데이터 API 설계 초기 혼란**
  - `pod_stats`, `node_stats` 등의 리소스 조회 API에서 GROUP BY 구문 누락으로 SQL 오류 빈번 발생.
  - 데이터 집계 기준(`timestamp`, `pod_name`, `namespace`)에 대한 명확한 설계가 필요했음.


## 🛠 문제 해결

- **CORS 문제 해결**
  - Nginx에서 HTTP 요청을 모두 308 permanent redirect로 강제하여 HTTPS로 유도.
  - FastAPI에서 `allow_redirects=False` 설정과 `CORSMiddleware` 재구성.

- **디스크 부족 대응**
  - Docker 빌드 캐시 최소화 (`--no-cache`, `apt clean` 등).
  - `/mnt/data` 볼륨으로 pip 패키지 저장 경로 지정하여 공간 분산.

- **SQL 오류 개선**
  - Postgres의 집계함수와 GROUP BY 규칙 확인 후 쿼리 수정.
  - ORM 대신 raw SQL 사용 시, 쿼리 리팩토링 패턴 정립.

- **시각화 문제**
  - Chart.js의 label 겹침 → x축 제한, fontSize 축소, legend custom 처리로 해결.
  - 클러스터 산점도에서 데이터 라벨 중복 → 데이터셋별 map 분리 및 색상 파스텔화 적용.


## 💡 다음 단계

- 알림 조건 설정 기능의 정교화 및 경고 시스템 고도화
- 시계열 데이터에 대한 주기적 업데이트 및 리프레시 성능 개선
- ETF 뉴스 감정 분석 정확도 향상을 위한 모델 개선


> 작성자: 김태형  
> 프로젝트 기간: 2025년 5월 ~ 6월  
> 주요 기술: FastAPI, React, Chart.js, PostgreSQL, Docker, Diskcache
