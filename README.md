# Dacon Jeju Specialty Product Price Prediction AI Competetion (Private 91th/2002)
<img width="1192" alt="image" src="https://github.com/DanDanHeeWorld/Dacon-Jeju-Product-Price-Prediction-AI-/assets/143466233/eaf360af-9497-4bd8-b2b5-b483cd76b339">


<https://dacon.io/competitions/official/236176/overview/description>
***

1. 실험을 통해서 알아낸 것들
- CR(당근)은 1,2,3,4,5,11,12월에만 공급이 존재함.
- TG(감귤)은 일년 내내
- RD(무)는 9,10빼고
- CB(양배추)는 7,8,9,10빼고 여름에 생산 X
- BC(브로콜리)는 6,7,8,9 빼고 여름생산 X
> 결국 금액대가 가장 큰 TG를 잘 맞추는 것이 핵심이 될 것

- 일요일과 신정 등 다양한 공휴일이 있으며 해당일에는 무조건 값이 0이지만 다소 불규칙한 경향을 보임.
- 여러가지 모델들을 실험해보았지만 대회에서 제시한 feature들은 target에 유의미한 영향을 주지못했다.
> 결국 feature들이 유의미한 영향을 주지못한다면 target으로만 예측할 수 있는 LSTF 모델을 사용하는 것이 적합하다고 판단했고, SOTA모델인 N_linear 모델을 활용하여 예측을 한 결과 성능이 크게 향상되었다.


![newplot (28)](https://github.com/DanDanHeeWorld/Dacon-Jeju-Product-Price-Prediction-AI-/assets/143466233/b70f5ee0-3d35-407e-86ce-f73123e1ef43)

- 하지만, 다른 경험을 비추어보았을 때 LSTF 모델들은 예측기간이 길어짐에 따라서 성능이 크게 낮아지는 것을 알 수 있었다. 특히, 시간상 앞부분은 다소 잘 맞추지만 뒤의 기간을 못맞추는 경향을 보였는데, 이는 향후 private 공개 시 큰 shake up을 불러일으킬 것이라고 판단했다. 이를 해결하기 위해서 다양한 모델들을 앙상블 해줄 수 있는 방안에 대해 고민하였고 autogluon을 통해서 해결할 수 있었다.
### 실제로 ensembled을 통해서 public보다 private에서 순위가 향상된 것을 경험할 수 있었다. 다만, public에서 부족한 성능을 보였던 모델들에 대해서 ensemble하는 것을 망설였는데, 실제로 대회가 종료한 이후 public에서 아쉬운 성능을 보였던 모델들을 ensemble하였을 때 더 좋은 결과를 보여 아쉬움이 남는다.

### 📌이번 대회는 feature engineering을 다소 활용하지 못한 것 같은 아쉬움이 남는다. 하지만, 부족한 시간과 자원 내에서 빠르게 판단 내리고 다양한 모델들을 실험하고 해결방안에 대해서 모색한 것은 나름대로의 성과라고 생각한다.
