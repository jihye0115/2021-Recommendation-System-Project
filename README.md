# **Matrix Factorization을 이용한 추천시스템 알고리즘 구현**

2021년 대학원 계산특론 수업의 Final Project로 진행

<br/>
<br>

## **Project Object**
추천시스템의 협업 필터링 방법(Collaborative Filtering) 중 하나인 잠재 요인 모델(Latent Factor Model)을 Matrix Factorization, Probabilistic Matrix Factorization, Bayesian Probabilistic Matrix Factorization을 이용하여 구현하고 성능을 비교한다.

<br/>
<br>

## **Project Result**
| |**MF**|**PMF**|**BPMF**|
|----|----|----|----|
|train RMSE|0.90|0.80|0.80|
|test RMSE|0.94|0.96|0.89|
|epoch|50|100|40|
|time|25m 51s|15m 5s|55m 35s|
