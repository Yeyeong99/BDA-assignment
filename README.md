## 디렉토리 구조
```
├── Basic Statistics/            # 통계적 추론과 가설 검정에 관한 실습 파일
│   ├── Binomial distribution.ipynb             # 이항분포
│   ├── correlation coefficient.ipynb           # 상관계수 분석
│   ├── Correlation.ipynb                       # 상관관계 분석
│   ├── Population Ratio Estimation.ipynb       # 모비율 추정
│   ├── Population Ratio Estimation2.ipynb      # 모비율 추정 추가
│   ├── t-test.ipynb                           # t-검정
│   ├── Chi-squared Test.ipynb                 # 카이제곱 검정
│   ├── Chi-squared Test&Degree of Freedom.ipynb # 카이제곱 검정과 자유도
│   ├── Quartile.ipynb                         # 사분위수
│   ├── scipy stats Basic.ipynb                # scipy.stats 기초
│   ├── Estimation Basic.ipynb                 # 추정 기초
│   └── statistical hypothesis test.pdf        # 통계적 가설검정 이론
│
├── DataFrame/                   # pandas DataFrame을 다루는 방법에 대한 실습 파일
│   ├── Data_Frame_Basic.ipynb              # DataFrame 기초
│   ├── DataFrame Handling.ipynb            # DataFrame 조작 방법
│   ├── DataFrame Handling 2.ipynb          # DataFrame 조작 방법 심화
│   └── DataFrame Handling 3.ipynb          # DataFrame 조작 방법 고급
│
├── Data Visualization/          # 데이터 시각화에 관한 실습 파일
│   ├── Data Visualization Basic.ipynb      # matplotlib과 seaborn을 활용한 기본적인 시각화
│   └── Data Visualization Basic2.ipynb     # 심화 데이터 시각화
│
└── Practice/                    # 학습한 내용을 실제로 적용해보는 실습 파일
    ├── statistical hypothesis test practice.ipynb    # 통계적 가설검정 실습
    ├── Estimation Practice.ipynb                     # 추정 실습
    └── Practice.ipynb                               # 종합 실습
```

## 1. 통계적 추정 (Statistical Estimation)

### 추정이란
- 모집단에 대한 정보가 거의 없는 상황에서 표본 데이터를 활용하여 모수(모평균, 모비율, 모분산 등)를 추정하는 방법

### 점추정 (Point Estimation)  
- 모수를 하나의 특정 값으로 추정

### 구간추정 (Interval Estimation)  
- 모수가 존재할 것으로 예상되는 구간을 특정 신뢰수준 하에서 추정

### 신뢰구간 (Confidence Interval)

- **모분산을 아는 경우 (Z-분포 활용)**  
  - 주어진 모표준편차(σ)와 표본 데이터를 사용하여 모집단 평균을 특정 신뢰수준(예: 95%, 99%)으로 추정
  - Z-critical 값을 활용하여 오차 한계(Margin of Error = z_critical × σ/√n)를 계산하고,  
  - 신뢰구간 = (sample_mean ± margin_of_error) 로 도출

- **모분산을 모르는 경우 (t-분포 활용)**  
  - 표본 표준편차(sample_std)를 사용하여 모집단 평균을 특정 신뢰수준으로 추정
  - t-critical 값을 활용하며 자유도 (n-1)를 고려

## 2. 가설 검정 (Hypothesis Testing)

### 가설 설정  
- **귀무가설 (H0):** 기존에 받아들여지는 사실 또는 차이가 없다는 가설  
  (예: p_A = p_B, μ = 70)  
- **대립가설 (H1):** 연구자가 증명하려는 가설 또는 차이가 있다는 가설  
  (예: p_A ≠ p_B, μ ≠ 70)  

### 가설 유형  
- **단측가설 (One-tailed):** 특정 방향으로 차이 (예: ~는 적다, ~는 높다)  
- **양측가설 (Two-tailed):** 차이 방향이 특정되지 않음 (예: ~는 같지 않다)  

### 유의수준 (α)  
- 귀무가설이 참인데도 기각할 확률  
- 일반적으로 0.05 또는 0.01로 설정  

### 검정통계량 및 기각역 결정  
- Z-검정, t-검정, 카이제곱(χ²) 검정 등 적절한 검정 통계량 선택  
- 기각역 결정 (귀무가설 기각 기준)  

### p-value  
- 귀무가설이 참일 때 관측된 데이터 또는 더 극단적인 데이터가 나올 확률  
- p-value < α이면 귀무가설 기각, 대립가설 채택  

### 오류 유형  
- **제1종 오류 (α 오류):** 귀무가설이 참인데 기각하는 오류  
- **제2종 오류 (β 오류):** 귀무가설이 거짓인데 채택하는 오류  

### 다양한 가설 검정 방법

| 검정 종류           | 설명                                              | 
|---------------------|---------------------------------------------------|
| 단일 표본 t-검정      | 주어진 데이터셋 평균이 모집단 평균과 다른지 검정    | 
| 독립 표본 t-검정      | 두 독립 표본 평균 간 유의미한 차이 검정             |
| 대응 표본 t-검정      | 동일 개체 두 번 측정된 데이터 간 차이 검정          |
| 카이제곱 검정         | 범주형 변수 간 관련성 검정                          | 
| 두 모비율의 차이 검정 | 두 모집단 비율 간 차이 검정                          |

## 3. 데이터 전처리 및 시각화

### 데이터 로드 및 확인  
- pandas를 사용하여 데이터 로드  
- `.head()` 등으로 데이터 구조 및 내용을 확인  

### 결측치 처리  
- `dropna()`를 사용하여 결측치가 있는 행 제거  

### 데이터 시각화  
- matplotlib.pyplot, seaborn 라이브러리 활용  
- `sns.histplot(data, kde=True)`로 데이터 분포를 히스토그램과 커널 밀도 추정(KDE)으로 시각화  
- 분포 확인은 통계 분석의 중요한 첫 단계임  

## 4. 확률 분포 (Probability Distributions)

### 이항분포 (Binomial Distribution)
- n번의 독립적인 베르누이 시행에서 성공 횟수의 분포
- 주요 매개변수:
  - n: 시행 횟수
  - p: 각 시행의 성공 확률
- 주요 함수:
  - PMF (확률질량함수): 특정 성공 횟수의 확률
  - CDF (누적분포함수): 특정 횟수 이하의 누적 확률
  - SF (생존함수): 특정 횟수 이상의 누적 확률
- 통계적 특성:
  - 평균: np
  - 분산: np(1-p)
  - 왜도: (1-2p)/√(np(1-p))
  - 첨도: (1-6p(1-p))/(np(1-p))

### 정규분포 (Normal Distribution)
- 자연계에서 가장 흔히 관찰되는 연속확률분포
- 주요 매개변수:
  - μ (mu): 평균, 분포의 중심
  - σ (sigma): 표준편차, 분포의 퍼짐 정도
- 특징:
  - 종 모양의 대칭적 분포
  - 평균, 중앙값, 최빈값이 모두 같음
  - 68-95-99.7 규칙
    - μ ± 1σ: 약 68%의 데이터 포함
    - μ ± 2σ: 약 95%의 데이터 포함
    - μ ± 3σ: 약 99.7%의 데이터 포함

### 상관계수 (Correlation Coefficient)
- 두 변수 간의 선형적 관계의 강도를 나타내는 지표
- 종류:
  - 피어슨 상관계수: 연속형 변수 간의 선형 관계
  - 스피어만 상관계수: 순서형 변수나 비선형 관계
  - 켄달 타우: 순위 상관계수
- 특징:
  - -1에서 1 사이의 값
  - 1: 완벽한 양의 상관관계
  - 0: 상관관계 없음
  - -1: 완벽한 음의 상관관계

### 카이제곱 분포 (Chi-square Distribution)
- 표본의 분산이나 범주형 변수의 독립성 검정에 사용
- 특징:
  - 항상 양의 값을 가짐
  - 자유도(df)에 따라 형태가 달라짐
  - 자유도가 증가할수록 정규분포에 가까워짐
- 주요 용도:
  - 적합도 검정
  - 독립성 검정
  - 동질성 검정
  - 분산 분석

## 5. 통계적 검정의 실제 적용

### 검정 선택 가이드
1. 단일 표본 검정
   - 정규성 검정: Shapiro-Wilk 검정
   - 평균 검정: 단일표본 t-검정
   - 비율 검정: 이항검정

2. 두 표본 검정
   - 독립표본: 독립표본 t-검정
   - 대응표본: 대응표본 t-검정
   - 비모수: Mann-Whitney U 검정

3. 세 개 이상 표본 검정
   - 일원배치 분산분석(ANOVA)
   - Kruskal-Wallis 검정(비모수)

### 검정력 분석
- 제2종 오류(β)를 범하지 않을 확률(1-β)
- 고려사항:
  - 표본 크기
  - 유의수준(α)
  - 효과 크기
  - 검정력(Power)

### 신뢰구간
- 모수의 참값이 있을 것으로 추정되는 구간
- 계산 방법:
  - 표본통계량 ± (임계값 × 표준오차)
- 해석:
  - 95% 신뢰구간: 동일한 방법으로 표본을 100번 추출할 때, 약 95번은 모수가 이 구간에 포함됨



