# ML 과정
https://colab.research.google.com/drive/1Ku_ikyOb_fVskUxu1hoNuXUbo-XZMs4L#scrollTo=2iorrUU1XtDt 참조
1. 데이터의 획득
2. 데이터 전처리
    1. 탐색적 분석 : 컬럼별 데이터 분석  
    범주형 데이터에 대한 접근 :  
        데이터의 종류 검토 df.unique()  
        데이터의 빈도 df.value_counts()  
        데이터의 비율 df.value_counts(normalize=True)  
    수치 데이터에 대한 접근 :  
        수치형 데이터가 object로 저장되었을 경우  unique()/describe()/isnull()통한 결측치 검사를 통해서 해당 데이터가 정말 범주형이 맞는지 분석   
        수치형이 맞다면 결측치로 처리함  
        astype()을 이용하여 형변환  
    결측치의 보정 :  
        dropna(), fillna() 이용해서 보정
        loc속성을 통해서 조건을 만족하는 값들을 np.nan으로 할당하여 초기화  
        결측치가 너무 많으면 학습할 데이터가 유실되므로 범주형의 경우 임의의 범주를 추가하는 등의 방법으로 보정함  
        결측치가 작다면, 버리거나 평균등으로 대체가능
3. ㅇㅇㅇ  
    1. 이상치의 제거  
    중간 값에서 Q1 - 1.5 * IQR ~ Q3 - 1.5 * IQR의 범위를 넘어가는 값들을 이상치 라고함 (평균분포에서 많이 벗어난 값들)
    상하위 25%씩을 제거
    df.describe()를 통해 획득한 값에서 min/max값과 평균값을 비교했을 때 그 값의 차가 클때 이상치로 판단 가능하다 
    **이외의 다른 방법들이 존재함** 추가 공부 필요
    
---------------------------------------------
# ML의 유형

## 지도학습
* 정답라벨이 주어진 상태에서 학습하는 방식
    * 라벨링된 학습데이터 준비
    * 학습진행하여 모델완성
    * 학습에 사용되지 않은 임의 데이터로 모델의 검증
* 분류분석
    * 예측하고자 하는 값이 범주형 데이터일 경우
    * 이미지, 문서의 분류
* 회귀분석
    * 예측하고자 하는 값이 연속형 데이터
    * 주식 가격 예측, 부동산 가격 예측

## 비지도학습
* 정답라벨이 없는 상태에서 학습하는 방식
    * 별도 라벨링 없이 데이터 준비
    * 학습진행 군집화 학습
    * 임의의 데이터 입력시 해당 데이터가 어떤 군집에 해당하는지 패턴을 찾는 학습방식
* 군집분석 Clustering
    * 데이터의 특징, 구조 등을 통해 유사한 특성을 가진 데이터끼리 그룹화 하는 과정  
    유사어, 유사 이미지, 고객분류, 추천시스템등 다양한 분야에 사용됨
* 준 지도학습 Semi-Supervised learning
    * 라벨이 있는 데이터와 라벨이 없는 데이터를 모두 사용하여 학습하는 방식
## 강화학습
* 모델이 목표를 달성할 수 있도록 보상을 기반으로 학습하는 방식
* 특정 목표를 딜성하는데 최선의 전략을 선택하도록 학습됨
* 사람이 할수 있는 다양한 분야에서 활용됨  
체스게임, 알파고, 자율주행 등

--------------------------------------------
# ML의 주요 프로세스
## 문제정의
* 해결하려는 문제를 명확하게 정의
* 문제 해결을 위한 알고리즘을 선정하는 단계
* 해결할 문제(데이터 특성)에 따라 적절한 알고리즘을 선택
## 데이터수집
* 학습/검증에 사용할 데이터를 수집하는 단계
* 데이터는 학습된 모델의 품질을 결정하는 중요 요소
    * 충분히 큰데이터.
    * 대표성을 가지는 데이터
    * 고품질의 데이터
*6
데이터전처리
특징추출
학습
검증
* 데이터 셋의 분할
    * 트레이닝 데이터 셋  
    머신러닝 모델의 학습에 사용되는 데이터 셋
    * validation 데이터 셋  
    학습된 머신러닝 모델의 성능을 평가하는데 사용되는 데이터셋으로 모델 개선의 지표가 됨
    * Testing 데이터 셋  
    학습 및 개선된 머신러닝 모델을 최종평가하는 데이터 셋
## 데이터 전처리 
* 데이터 품질을 결정하는 중요한 단계로 데이터를 정제하는 과정
* 데이터 전처리를 위한 다양한 기법이 존재 
    * 누락된 데이터 찾아 처리
    * 이상값 찾아 처리 
    * 데이터의 스케일 맞추기 
    * 데이터의 인코딩
    * 라벨링
    * 이미지, 음성등과 같은 비정형 데이터의 경우 다양한 전처리 작업이 선행됨. 
        * 사진의 크기, 명암, 중요 부분 잘라내기
        * 음성의 노이즈제거, 단위시간별 분할
        * 자연어의 경우 오타 수정등
* 가장 오래 걸리고 어려운 작업
* 도메인에 대한 전문지식, 데이터에 대한 이해가 중요함
## 특징 추출
* Feature란  
모델에 학습시킬 데이터의 특성을 의미하는 용어로, 독립변수들을 지칭함. (x값)
* Class란  
모델을 통해 판단하고자 예측 하고자하는 정답 값으로 종속변수를 지칭함 ( 결과, 정답값)
* Feature가 많다고 하여 결과 값이 좋아지는 것이 아님
* 데이터에 대한 도메인 지식을 활용하여 특징을 만들어내는 과정
* Feature Engineering이라고도 불림
    * Feature selection
    * Feature Extraction
    * Feature learning
* 모델 성능에 미치는 영향이 매우 큼
## 학습과 검증
* 전처리/ 특징 추출작업이 완료된 학습데이터 셋을 입력으로 
* 모델이 최적화 될때까지 학습이 반복됨
* 학습을 얼만큼 반복할 것인가 ?
* 모델이 최적화 되고 있음을 어떻게 판단할 것인가.?
* 학습에 노출된 적이 없는 검증 데이터 셋을 이용하여 모델 검증
* 문제의 특성에 따라서 다양한 검증지표 사용
    * 분류 : 정확도, 재현율, 정밀도...
    * 회귀 : MSE, MAE...
----------------------------------------------
# 싸이킷 런 라이브러리 
## 파이선 기반의 머신러닝 활용
* numphy : 행렬, 대규모 다차원 데이터의 분석
* pandas : 행,렬의 2차원 데이터 분석을 위한 라이브러리
* matplotlib, seaborn: 데이터 시각화 라이브러리
* scipy : 기술 통계를 위한 라이브러리
* statsmodels: 통계분석 라이브러리
* scikit-learn : 머신러닝 라이브러리
## 사이킷 런 라이브러리
* 파이썬 기반의 대표적 머신러닝 라이브러리
* 머신러닝을 위한 다양한 알고리즘 프레임워크, api제공
* 오랜기간 검증됨

------------------------------------------------
# K최근접 이웃 알고리즘
* 새로운 데이터가 주어졌을때, 가장 가까운 K개의 훈련 데이터(이웃)을 찾는 알고리즘
* 가까운 이웃의 데이터에서 많은 분류에 해당하는 쪽으로 판단하는 모델링
* 분류와 회귀 문제를 모두 다룰 수 있는 알고리즘
    * 분류 : 이웃 중 다수결로 예측 / KNN Classifier
    * 회귀 : 평균 값으로 결과 예측 / KNN Regressor
* KNN 모델 성능의 주요 이슈
    * 데이터간 거리는 어떻게 측정하는가 ? 
        * 유클리디안 거리, 두점의 직선거리
        * 맨하탄 거리 계산법, X 이동, Y이동, 즉 좌표상 직선거리
        * 민코프스키 거리 계산법, 유클리디안 + 맨하탄 거리 계산법의 복합
        * KNeighborsClassifier(파라미터를 통해서 설정가능)
    * 적절한 K값의 크기는 어떠헥 설정할 것인가 ?
        * 너무 작으면 민감도가 높아져 오류 가능
        * 너무 크면 분류가 둔감해짐
        * 답을 지정할 수 없고, 초기값 3을 기준으로 최적의 성능을 찾아가는 편
* 하이퍼 파라미터
    * 모델러가 학습전 최적의 값을 찾아서 설정해야함
    * K값이나, 거리계산 방식이 하이퍼 파라미터가 됨
* K최근접 알고리즘 특징
    * 매우 단순하고 직관적
    * 실행 시점에 K값에 의한 거리 연산 발생비용(고비용)
    * 최적의 K값 정의가 중요함
    * 데이터의 스케일이 서로 다른 경우 별도의 졍규화 과정필요

----------------------------------------------------
# 과대적합과 과소적합
* 머신러닝의 목표
    * 사람이 모든 데이터를 전수조사 할수 없기 때문에. 모집단을 대표하는 표본데이터를 추출하여 학습에 데이터로 사용함
    * 최적화 : 훈련데이터에서 최고의 성능을 내는 모델을 조정하는 과정
    * 일반화 : 모델이 이전에 학습한적 없는 데이터에서 얼마나 잘 수행되는지를 의미함
    * 서로 배타적 관계 :  
    훈련데이터에 너무 최적화 될경우 일반적인 데이터를 대상으로 모델링이 될때 정확도가 떨어질 수 있음  
    반대로 너무 일반화 된 경우, 훈련데이터에 대한 학습이 충분하지 않거나 데이터가 충분하지 않을경우 성능이 떨어질 수 있음
    * 머신러닝은 이 일반화와, 최적화의 중간값을 찾는 과정이 중요함  
    K최근점 이웃모델의 K값을 찾는 과정
* 오버피팅 (과대적합)
    * 학습용 데이터셋에 모델이 지나치게 학습에 최적화
    * 새로운데이터를 예측하지 못하는 현상
    * 일반화의 오류(최적화에 치중)
    * 모델의 복잡도가 높은상태
    * 과대적합을 해결하는 과정이 중요함
* 언더피팅 (과소적합)
    * 학습용 데이터셋에 대한 모델의 학습이 충분하지 않아 발생하는 학습의 오류
    * 새로운데이터도 충분히 설명하지 못하는 상황 발생 
    * 최적화의 오류(일반화에 치중)
    * 모델의 복잡도가 지나치게 낮은 상태
* 과대적합 피하기
    * 학습데이터 추가, 교차검증(가지고 있는 데이터를 응용하는 방법)
    * 학습데이터의 모델 노출 횟수 줄이기
    * 모델의 복잡도 줄이기 
        * Feature제거
        * 규제기법 (다음챕터)
* 과소적합 피하기
    * 학습시간을 늘림
    * 모델의 복잡도를 증가
        * Feature추가
        * 규제기법 제거
    * 모델을 새로 구출 : 알고리즘의 잘못된 선택등으로 인한 것이므로.

----------------------------------------------------
# 데이터 인코딩
데이터 전처리 기법중 하나 
통계분석에서 독립변수가 범주형인 경우, 수치형 데이터로 변환
기본적으로 사이킷럿의 머신러닝 알고리즘은 범주형 데이터 입력 불가
범주형 데이터를 수치형으로 변환화는 과정이 필요함
이를 인코딩이라고 함
* 라벨인코딩
    * 범주형데이터를 연속된 숫자로 변환시키는 전처리 기법 (enumeration)
    * 사이킷런의 LabelEncoder 사용
        * 인코딩할 대상데이터 확인
    * 연속적인 숫자로 변환된 결과는 수치를 의미하지 않지만. 그 숫자로 인하여 머신러닝에 영향을 줄 수 있음
* 원 핫 인코딩
    * 데이터가 0과 1만 가지도록 변환하는 과정
    * 라벨 인코딩 된 데이터 기반으로 원핫 인코딩 수행
    * 카테고리 개수 만큼 원소 배열 생성, 특정값의 위치는 1 모두 0으로 변환.(비트 연산과 유사)
    * 사이킷 런의 OneHotEncoder사용. 라벨인코딩 후 그 결과로 원핫인코딩 할 수 있음

----------------------------------------------------
# 데이터 스케일링
현실의 데이터들은 크기, 단위, 범위 등이 다른 데이터로 구성됨  
스케일이 다른면 ?    
    * KNN과 같은 거리기반의 알고리즘에서 오류 발생 가능
    * 큰 스케일의 특성 위주로 모델 학습이 진행됨
* Feature scaling
    * 각 데이터들의 특성(범위, 척도)을 일정 수준으로 변환하는 전처리기법
    * 머신러닝에서 모델에 영향을 주는 중요 이슈
    * 데이터가 준비되면 스케일링 필요 여부 확인 선행되어야 함
    * 대표적 기법으로 표준화와 정규화가 있음
* 표준화
    * 평균은 0, 분산이 1이 되도록 데이터의 배율을 조정하여 머신러닝 알고리즘의 인풋으로 사용
* 정규화 
    * 서로 다른 스케일의 데이터를 통일하는 기법
    * 정해진 범위 안으로 데이터를 재배치함 (ex, 0~1)
    * 최대, 최소값의 차이가 큰경우 
* 사이킷 런의 StandardScaler/ MinMaxScaler사용
* 스케일링 시 주의사항
    * 이상치에 영향을 많이 받으므로, 이상치 제거후에 스케일링 하는 것이 좋음
    * feature별 특성을 고려하여 서로 다른 스케일러를 사용하는 것도 좋음
    * fit메소드는 학습용 데이터 셋에만 적용하고 
    * transform메소드로 학습용, 테스트용 데이터셋 변환 진행
    * target(label)데이터는 별도의 스케일링 진행하지 않음
    