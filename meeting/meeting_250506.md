# 서비스 설계

- 회의일자: 25.05.06(화)
- 참석자: 김동혁, 김태형, 엄세훈

### Summary

- 이번 주는 설계에 집중, 그 후 개발 시작
    - WBS, API 명세서, 데이터 양식 작성
- 데이터 수집 같이 진행
- 발표 자료 제작

---

## 서비스 설계

- Git이 얼마나 잘 관리가 되느냐가 관건
    
    → 설계에 비중을 두고 관리하는 게 중요하다고 생각
    
- WBS(Work Breakdown Structure) 작성
    - 사용자를 기준으로, 각 기능별로 사용자가 어떤 기능을 사용할 수 있는가
    - 크게 백테스트 기능, 클러스터링 기능, ETF 데이터 수집이 있는데, 이 추상적인 기능에서 세부적 즉, 단위로 쪼개야 함 (Use Case)
        - Use Case를 뽑아 각각에 고유 번호를 붙여 명세를 하고 나면 브랜치 관리, 이슈 관리 등 매우 간편해짐
    - WBS 작성 시 기능을 계속 추가하게 되는 경향이 있는데, 더 추가하지 말고 지금 정의했던 최소 기능으로만 정의
        - 메인 3개 먼저 MVP 형식으로 짧게 정의 후 우선 빠르게 개발 시작
        - 생각나는 아이디어들은 추가 기능 쪽으로 분류
- API 명세서 작성
    - Pront - Back에서 실제로 요청하는 명세 작성
    - Use Case에 End Point를 잡아 Front - Back 연결
- API 명세서 작성 후 데이터 양식 작성

→ 설계 과정 마무리 후 개발 시작

## 데이터 수집

- 데이터 수집도 미리 하는 것이 좋을 거 같음
    - 요청 단위로 비용이 들거나 하루 수집량 제한 등이 있을 수 있음
    - DB나 텍스트 파일로라도 저장을 해두고 확인을 해서 사용할 예정
    - 가격 지표부터 뽑을 것
- 필요한 데이터를 요청하더라도 데이터 수집이 어려울 수 있음
    - 데이터 양도 많고 수집이 제한될 수 있기 때문에 모든 지표를 수집하기는 어려울 수 있음
    
    → 다양한 지표를 이용한 클러스터링 방식을 우선으로 하되, 정 안될 시 가격 자표만으로 클러스터링
    

## 발표 자료 제작

- 설계가 완벽하게 마무리 되면 이것만 들어가도 OK
- 자료 부가 설명들은 GitHub에서 캡쳐해 보여주면 좋아 보임
- 컨벤션 내용 - 설계 - 와이어프레임 & API 명세 순으로 구성
- 내용 부족하면 데이터 수집 내용 정도 추가

## 그 외

- 기능 중 클러스터별 대표 N개 ETF 추천 or 특정 클러스터 추천?
    - 특정 클러스터 추천 방식으로 우선 개발
- GitHub 마지막 검토자가 승인 후 merge 진행
    - merge 이름은 GitHub에서 default로 생성되는 것으로
    - branch 삭제는 판단 하에 재사용 할 거 같으면 남겨두고, 아니라면 삭제
- 발표 자료도 GitHub docs에 올려 진행 상황 관리
- GitHub - Slack 연동

---

### To-do

- WBS 작성(김동혁 : 최대한 빠르게)
- API 명세서 작성(엄세훈 : ~5/10)
- 발표 자료 제작(김동혁, 엄세훈 : ~5/11)
- 프론트 개발(김태형)
- 데이터 수집(김태형, 엄세훈)