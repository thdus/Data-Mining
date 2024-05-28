# Seoul Senior Welfare Center Analysis Project for Event Hosting

## DataMining Team Project 4team

## 행사 주최를 위한 서울시 노인복지센터 분석 프로젝트

---

## Summary
- 서울시에 존재하는 동마다의 인구 밀도 및 노인 밀도 등의 인구 통계학적 데이터를 기반하여 경로당의 설립장소 추천
- 경로당이 존재하는 동에 통계학적 데이터를 기반하여 어떠한 행사를 주최하는 가에 대한 분석

## Data PreProcessing
### 데이터 수집 및 분석
1. **서울시 주민등록인구 (연령별/동별) 통계**  
   *https://data.seoul.go.kr/dataList/10727/S/2/datasetView.do*
2. **서울시 독거노인 현황 (연령별/동별) 통계**  
   *https://data.seoul.go.kr/dataList/10176/S/2/datasetView.do*
3. **서울시 장애인 현황 (연령별/동별) 통계**  
   *https://data.seoul.go.kr/dataList/10580/S/2/datasetView.do*
4. **서울시 경로당 정보**  
   *https://data.seoul.go.kr/dataList/OA-15052/S/1/datasetView.do*
5. **서울시 국민기초생활 수급자 동별 현황**  
    *https://data.seoul.go.kr/dataList/OA-22227/F/1/datasetView.do*

*Data Source: [서울 열린데이터광장](https://data.seoul.go.kr/)*

### 데이터 전처리
1. 결측치 제거 및 필요하지 않는 Feature 제거
2. 데이터의 각 행의 내용 정렬 및 일치작업
3. 전체 데이터에 필요한 Feature 확인
4. 경로당이 존재하는 동의 Feature 생성
5. 모든 동의 Feature 생성

---

### 시각화(EDA) - 서울시 동별

---

## 모델링

### K-means Clustering
- 데이터를 K개의 군집으로 나누기 위한, 거리 기반 Clustering 알고리즘.
- 같은 집단 내 데이터들은 비슷한 특징을 가지고 있고, 다른 집단의 데이터와는 데이터적으로 상반된 특징을 가지고 있다는 것을 가정한다. 즉, 동일 집단의 군집화를 고려하는 것 뿐만 아니라, 타집단과의 관계도 고려.
- 매우 좋은 알고리즘임에도 불구하고, 가장 큰 단점이 있다면, Cluster 개수를 미리 알아야한다는 것 (PCA 사용으로 해결)

![k-means-clustering-algorithm-in-machine-learning](https://github.com/Kyle1113/DataMining_Project/assets/168116920/24b99b95-b08b-41a5-86db-f67d68b16c28)  

##### PCA
- 데이터 집합 내에 존재하는 각 데이터의 차이를 가장 잘 나타내 주는 요소를, 데이터를 잘 표현 할 수 있는 특성을 찾아내는 방법
- 서로 상관성이 높은 여러 변수들의 선형조합으로 만든 새로운 변수들로 요약 및 축약하는 기법.
- 데이터의 분산(variance)를 최대한 보존하면서 직교하는 새 기저(축)을 찾아 고차원 공간의 표봄들을 선형 연관성이 없는 저차원 공간으로 변환해 준다.

![PCA](https://github.com/Kyle1113/DataMining_Project/assets/168116920/fc54f5d2-6841-4059-b99f-26cc28168787)  

##### Silhouette 계수
- 각각의 데이터가 해당 데이터와 같은 군집 내의 데이터와는 얼마나 가깝게 군집화가 되었고, 다른 군집에 있는 데이터와는 얼마나 멀리 분포되어 있는지를 나타내는 지표
- -1에서 1 사이의 값을 가지며 1에 가까울 수록 근처 군집과 멀리 떨어져 있음을, 0에 가까울수록 근처 군집과 가까움을 의미

<img width="1100" alt="Silhoutte" src="https://github.com/Kyle1113/DataMining_Project/assets/168116920/9ce5728d-664e-4480-aece-842955dd954c">

---

### 시각화(EDA) - 경로당 존재 동별
