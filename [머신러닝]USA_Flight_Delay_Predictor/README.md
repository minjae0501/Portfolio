> ## Preview

![](https://velog.velcdn.com/images/qnwjej/post/0c87ed74-1537-4345-9f2a-3af9fbc72569/image.webp)

>## 프로젝트 개요

- 팀 구성 및 기여도: 4명 / 25%
- 담당 역할
    - Pandas를 이용한 데이터 전처리 및 샘플링
    - EDA 및 Matplotlib, Seaborn을 이용한 데이터 시각화
    - Machine Learning Modeling
- 로그데이터를 다각도로 EDA를 활용하여 더 정확한 서비스 제공
- 항공 지연 예측 모델을 개발하여 고객의 서비스 만족도와 충성도을 향상
---

> ## 프로젝트 상세

>#### 1. 데이터

- 데이콘 항공편 지연 예측 AI경진대회 데이터 사용
    - 주소: https://dacon.io/competitions/official/236094/overview/description
- 약 1000만 개의 비행기록
    - States, 공항 코드, 비행 거리, EDT(예상 도착 시간), EAT(예상 출발 시간) 등으로 구성

> #### 2. 전처리와 EDA

- 전처리
    - EDT, EAT의 누적 데이터는 평균 비행시간을 계산하여 추론
    - 누락된 Stats와 항공사ID는 기존 데이터의 dictionary를 활용
    - 불균형 레이블(0: 비지연, 1: 지연) **언더 샘플링**
- EDA
    - 항공사 마다 다른 지연율
       - 6대 항공사(Southwest, Delta, Skywest, United, American, JetBlue)중 지연율이 가장 높은 항공사는 JetBlue항공(24.7%)
        
    ![](https://velog.velcdn.com/images/qnwjej/post/65273e4f-5787-4745-9378-62080b49a392/image.png)
    - 여름은 지연율이 가장 높은 계절
       - 데이터에 기상 조건이 명시되지 않았지만 계절적 영향이 존재</br>![](https://velog.velcdn.com/images/qnwjej/post/cf7a1742-f155-4e0a-965c-388d58e9419a/image.png)
    - 저녁-새벽(18-06)동안 지연이 높음</br>![](https://velog.velcdn.com/images/qnwjej/post/ce6b4d8f-7c17-44c3-b4f8-4f49e1e683c3/image.png)
    
> #### 3. Machine Learning Modeling

- Machine Learning을 위한 데이터 준비:
    - Feature Engineering: time_of_day, season, state_region **컬럼 생성**
    - **label-encoding, 정규화** 실행

- Modeling
   - 랜덤 포레스트, XGBoost, LightGBM중 가장 성능이 높은 모델 택
   - 하이퍼 파라미터 튜닝을 통해 정확도를 향상시키는 작업
   - **XGBoost**: 약 60-65%의 정확도를 달성하며 애플리케이션에 가장 적합한 모델로 선정

> #### 4. 모델 배포(Streamlit)

- Streamlit을 사용하여 새로운 데이터에 대한 실시간 예측을 구현
- 모델의 정밀도를 높이기 위해 결정 임계값을 보다 보수적으로 조정
- 사용자가 출발 공항, 도착 공항, 출발 시간을 입력하면 비행기의 출발 지연 확률을 제공
   

> ## 기대효과

- 비행 지연 예측기는 기계 학습, 특히 XGBoost 알고리즘의 힘을 활용하여 항공 여행의 불확실성을 관리할 수 있는 사전 예방적 솔루션을 제공

#### 적용가능한 잠재적 영역

- **승객**(User End):
   - 항공편을 예약 할 경우, 보다 더 직관적인 지연 위험도를 표시
   - 지연 위험도가 낮은 항공사를 선택하거나 시간대를 옮기는 등 정보에 입각한 결정을 내릴 수 있음
- **항공사 및 공항**(Business End):
   - 모델의 insights을 활용하여 일정, 직원 할당, 자원관리 최적화
   - 지연 예측을 통해 승객들의 전반적 고객 경험 향상, 브랜드 충성도 향상
   - 지연을 효과적으로 관리하여 **시장 경쟁력 확보**
   
