## Abstract
- EfficientNet을 Label이 된 ImageNet 이미지에 대해서 먼저 학습한 후, 학습된 모델을 Teacher Model로 사용하여 Unlabel 된 이미지 데이터들에 대해 Psuedo Label을 생성 (이 과정을 반복 - Teacher & Student Model)
- Psuedo Label을 생성하는 동안 Teacher Model에는 Noise(Dropout, Stochastic Depth, Data Augmentation)를 주입하지 않음
- 반면, Student Model에는 Noise Injection을 적용 -> Teacher Model보다 더 Generalize하기 위함 
- 기존 방법들 (ex. Knowledge Distillation)과의 차이점 -> Unlabeled Image를 사용하는 점과 Student Model이 Teacher Model만큼 크다는 점
- ImageNet Top-1 Accuracy 88.4%
- ImageNet Top-5 Accuracy 98.7%

***

## Noising Student
- Student Model에게 의도적으로 주는 두 가지 타입의 Noise 
1) Input Noise: Data Augmentation (RandAugment)
2) Model Noise: Dropout, Stochastic Depth

- Unlabeled Image에 Noise Injection 했을 때의 장점
1) Decision Function에서 Local Smootheness를 강화한다는 이점이 있음
2) Data Augmentation을 사용하였을 때, 예를 들어 Student가 Tranlate를 할 때의 이미지가 Tranlate 되지 않은 이미지와 동일한 Class를 가져야 함. 이 Invariant Encourages는 Student Model이 Teacher Model을 뛰어 넘어 더 어려운 이미지를 예측 가능케 함



## 작성중...
