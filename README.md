# Matrix Factorization을 이용한 추천시스템 알고리즘 구현

2021년 대학원 계산특론 수업의 Final Project로 진행하였다.
<br> 전반적인 내용은 [발표 자료](https://github.com/jihye0115/2021-Recommendation-System-Project/blob/main/Project%20Presentation.pdf)를, 구체적인 내용은 [보고서](https://github.com/jihye0115/2021-Recommendation-System-Project/blob/main/Project%20Report.pdf)와 코드를 참고할 수 있다.

<br/> <br> 
## Data
![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/43ce35c0-435a-4070-8cdc-8a858d1d28cd/Untitled.png)
- 출처 : Netflix Prize 영화 평점 데이터로, 각 고객이 시청한 작품에 대한 평점
- 구조 : 고객, 작품, 평점 3열로 이루어진 데이터를, 고객 by 작품 행렬 형태로 바꾸어, 각 고객이 이미 시청한 작품은 알고있는 평점으로 채우고, 그렇지 않은 작품은 NA로 채운다.
![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5000365e-9ef8-4fe7-b814-7d2f88d75af1/Untitled.png)
이 행렬을 R로 두면, 고객의 내재적 특성에 해당하는 행렬 U와 작품의 내재적 특성에 해당하는 행렬 V의 곱으로 나타낼 수 있다. 이때, U와 V를 찾아 R의 빈 칸을 채우는 것이 기본적인 추천시스템 구조이다.

<br/> <br> 
## 모델 구조
### MF (Matrix Factorization)
기본적인 행렬 분해 방법론이다. R을 U와 V로 분해하되, 람다 규제항을 추가하여 과적합을 막는다. 추정한 U, V로 계산한 R과 실제 R의 차이를 최소화하는 방향으로 R을 찾아나간다. 단, 차이를 계산할 때는 알고있는 데이터에 대해서만 계산하여 데이터에 왜곡을 줄이고 계산 비용을 줄인다.
![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/96a68180-f77f-4bc1-bdeb-4695918d958f/Untitled.png)

### PMF (Probabilistic Matrix Factorization)
MF 모델에 U와 V에 대한 사전 분포를 가정하여 베이지안 방법으로 계산하는 모델이다. MF와 target function 형태가 달라지고, 다른 최적화 방법을 사용한다.
![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/1ff71c05-402c-4538-8c22-87d056e04bf8/Untitled.png)

### BPMF (Bayesian Probabilistic Matrix Factorization)
BPMF는 PMF의 사전 분포의 하이퍼파라미터에 대해서도 분포 가정을 추가하는 모델이다. 구조가 더 복잡해지되, 분포를 전부 가정하였으므로 MCMC 방법으로 샘플을 생성하여 최적화한다. Gibbs sampling을 사용하였다.

## 결과
BPMF의 성능이 가장 우수하다.
![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7d1d314c-6391-4cd2-af75-8d9db67f2a03/Untitled.png)
![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/bd2baeec-d95c-481d-b1a4-8a5a88f5e5ea/Untitled.png)


<br/> <br> 
## Reference Paper
:page_with_curl: Y. Koren, R. Bell, and C. Volinsky, Matrix factorization techniques for recommender systems, IEEE Computing, 2009. 
<br>:page_with_curl: Salakhutdinov, R., & Mnih, A., Probabilistic matrix factorization, Advances in Neural Information Processing Systems 20, 2008
<br>:page_with_curl: Salakhutdinov, R., & Mnih, A. Bayesian probabilistic matrix factorization using MCMC. ICML’08.
<br/> <br> 

## Project Object
추천시스템의 협업 필터링 방법(Collaborative Filtering) 중 하나인 잠재 요인 모델(Latent Factor Model)을 **MF, PMF, BPMF**을 이용하여 구현하고 넷플릭스 데이터에 적용하여 성능을 비교한다.
<br/> <br>

## Project Result
| |**MF**|**PMF**|**BPMF**|
|----|----|----|----|
|train RMSE|0.90|0.80|0.80|
|test RMSE|0.94|0.96|0.89|
|epoch|50|100|40|
|time|25m 51s|15m 5s|55m 35s|
