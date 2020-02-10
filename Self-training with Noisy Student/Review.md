## Abstract
- EfficientNet을 Label이 된 ImageNet 이미지에 대해서 먼저 학습한 후, 학습된 모델을 Teacher Model로 사용하여 Unlabel 된 이미지 데이터들에 대해 Psuedo Label을 생성 (이 과정을 반복 - Teacher & Student Model)
- Psuedo Label을 생성하는 동안 Teacher Model에는 Noise(Dropout, Stochastic Depth, Data Augmentation)를 주입하지 않음
- 반면, Student Model에는 Noise Injection을 적용 -> Teacher Model보다 더 Generalize하기 위함 

