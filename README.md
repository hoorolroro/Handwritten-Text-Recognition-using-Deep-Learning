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
