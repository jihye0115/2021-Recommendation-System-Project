# Matrix Factorization을 이용한 추천시스템 알고리즘 구현

2021년 대학원 계산특론 수업의 Final Project로 진행하였다.
<br> 전반적인 내용은 [발표 자료](https://github.com/jihye0115/2021-Recommendation-System-Project/blob/main/Project%20Presentation.pdf)를, 구체적인 내용은 [보고서](https://github.com/jihye0115/2021-Recommendation-System-Project/blob/main/Project%20Report.pdf)와 코드를 참고하기 바란다.

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
