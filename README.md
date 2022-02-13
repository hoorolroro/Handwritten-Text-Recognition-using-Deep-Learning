# 필기체 인식기 개발
## MNIST 필기체
<img src="https://user-images.githubusercontent.com/98728682/152273731-742e6898-2efe-40fa-b434-e46d605b10e7.png" width="320" height="250">  
● Pytorch에서 제공하는 손글씨 데이터(0~9까지의 28x28 크기의 숫자)를 딥러닝을 통하여 학습시킨다.  

● 학습 데이터 수는 55,000장, 평가 데이터 수는 10,000장이다.
## Process of Learning
<img src="https://user-images.githubusercontent.com/98728682/152274850-c6958ff9-f7cf-4b14-9252-0b0597d10f4b.png" width="420" height="250">  
● 출력과 Loss는 w들의 결과로 나온 값이다.  

● Loss값을 바탕으로 각각의 w 하나 하나가 얼마나 영향을 주었는지 알 수 있다.  
● 좀 더 적절한 방향으로 w들을 변경해 나가는 것을 Back-propagation이라고 한다. 

## optimization
● Back propagation을 통해 weights를 업데이트 시키는 방법  
● 학습의 안정성 및 효율성을 위해 여러 optimization 기법들이 제안됨.  
### 종류
● Stochastic Gradient Decent (SGD) : 빠른 학습 가능, Epoch 마다 무작위 학습하면 효과 극대화 가능  
● AdaGrad : 많이 갱신된 가중치는 학습률이 낮아짐  
● RMSProp : AdaGrad의 단점 보완, Gredient가 무한정 커지는 것을 방지  
● Momentum  : Gredient decent를 통해 이동하는 과정에 관성을 주는 것  
● Adam : AdaGrad (RMSProp)와 Momentum을 융합한 기법
## Over-fitting
● 딥러닝 모델이 겪는 중요한 문제점  
● 모델이 학습(Train) 데이터에 '지나치게' 집중하면서 실제로 테스트(Test) 데이터에서 결과가 더 안좋게 나오는 현상  
● 학습 데이터로 학습하고 테스트 데이터에서 성능이 좋은 것을 Generalize(일반화)가 잘 되었다고 얘기함.  

<img src="https://user-images.githubusercontent.com/98728682/152298306-7226ad2f-6bf3-4e66-95f8-a7c93872bc1e.png" width="550" height="300">  

### 극복 방법  

Dropout  
● 네트워크의 일부를 생략하는 것  
● 학습 중 Forward 과정에서 일부 perceptron을 특정 확률(p)로 사용/미사용 함  
● p값은 hyperparameter이며 일반적으로 0.5를 사용함.  
● 평가 과정에서는 Dropout을 사용하지 않고 모든 perceptron을 사용  
<img src="https://user-images.githubusercontent.com/98728682/152300682-5328fdfa-8d2e-406c-a96b-e25ea4b9b21a.png" width="550" height="300">  

Weight decay  
● Overfitting 된 weight들은 보통 그 크기가 매우 크다.  
● weight들의 값을 너무 키우지 않는 방법으로 Overfitting을 방지한다.  

Early Stopping  
● Train loss와 Eval loss graph 상에서 최적 포인트를 자동으로 찾는다.  
● 지정한 epoch까지 모두 학습하는게 아니라 최적 포인트에서 학습 과정을 미리 멈추는 기법이다.  

<img src="https://user-images.githubusercontent.com/98728682/152306974-c0e2146a-3d20-4efa-85b0-7f97a5066c17.png" width="550" height="300">

## Hyper-parameter  

|input_size|hidden_size|num_classes|batch_size|drop_prob|weight_decay_lambda|learning_rate|weight_initialization|best_accuracy|
|---|---|---|---|---|---|---|---|---|---|
|784|600|10|10|100|0.2|0.01|0.001|Xavier|94.52%|
|784|500|10|15|150|0.2|0.01|0.001|He|94.52%|  

## 평가  
● 최적의 Hyper-parameters들을 대입하여, Test evaluation 값을 최대로 학습하는 목표를 잡는다.
