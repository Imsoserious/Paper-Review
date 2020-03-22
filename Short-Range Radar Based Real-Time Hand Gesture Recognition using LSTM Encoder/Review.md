# Short-Range Radar Based Real-Time Hand Gesture Recognition using LSTM Encoder 

### Introduction

- 비전과 비교했을 때 레이더의 장점(레이더로 제스처 인식을 한 이유)
  - 조명 영향(외부 환경의 영향)을 받지 않는 점
  - 갇힌 공간에서도 작동하기에 외부에 카메라 같은 장비가 노출될 필요가 없는 점
  - Hci 관점에서 물체를 투사하는 경우 디자인이 더 깔끔해지는 점
  
  
- 과거 연구 사례

    솔리 프로젝트, 레이더+광학+깊이 카메라를 사용한 사례 등 제스처 인식을 위한 시도들이 있었으나 
    움직임의 범위나 스피드, 손의 형태 등 달라지는 상황에 따라 성능 차가 큰 한계가 있었다.
    또한, 정확도가 약 90% 즈음에 그쳐 상용화하기엔 부족한 수준이다.

### Section 2 : Radar System for Gesture Recognition

- 해당 논문
    
    해당 논문에서는 위의 단점을 극복한 실시간 제스처 분류 모델을 소개할 것이며 그 과정은 크게 아래와 같다.
    
    - 2D FFT로 Range-Doppler-map을 생성하고, 
    - clutter로 배경을 제거하고, 
    - 제스처는 CFAR를 통해 인식되어 RDM sequence로 데이터가 재정립된다. 
    - 그 이후 모션 프로파일을 추출하여 데이터 크기를 줄이고,
    - lstm 모델을 통해 제스처를 분류한다.
![그림1](https://github.com/Imsoserious/Paper-Review/blob/master/Short-Range%20Radar%20Based%20Real-Time%20Hand%20Gesture%20Recognition%20using%20LSTM%20Encoder/img/radar_capture1.PNG)

### Section 3 : Hand gesture recognition

RDM sequcne를 바로 3D-CNN이나 convolutional LSTM에 쓸 수는 있으나 컴퓨팅 시간이 오래 걸려 실시간 예측애는 적합하지 않다. 
해당 논문에서는 RDM에서 range profile과 Doppler profile을 추출하여 데이터 특징을 1차로 뽑아내서 모델 계산량을 줄였다.

최종 모델로는 LSTM encoder을 사용했다. 다양한 길이의 데이터를 바로 쓸 수 있는 장점이 있다. 분류 결과에서도
2D CNN(95.39%), RNN encoder(92.90%)보다 높은 정확도(99.10%)를 보였다.

### 결론(내 결론!)
- 필요한 부분만 추려서 리뷰했음
- 딥러닝 모델 부분보다는 신호처리 쪽에 더 중점이 있는 논문이라 생소했음
  - 신호처리 관련 개념들을 개론 수준에서 찬찬히 살펴볼 필요가 있음(2D FFT, RDM, Chirp 등)
