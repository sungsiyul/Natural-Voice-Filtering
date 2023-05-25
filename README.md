# Natural-Voice-Filtering
KCC2023 :: 음성 기반 상황 분류 모델의 학습 효율 향상을 위한 데이터셋 정제 기법

## Summary
![image](https://github.com/sungsiyul/Natural-Voice-Filtering/assets/86465983/2c2a5af2-5166-4f28-a6b7-874642227081)

## 연구 배경
- 음성 인식 기반 인공지능 모델은 다양한 분야에서 놀라운 성과를 보이고 있지만, 그 성능은 대부분 학습 데이터의 질과 양에 크게 의존
- 현실에서는 학습 데이터가 부자연스러운 형태로 제공되는 경우가 많음.
- 이러한 요소는 모델의 성능을 크게 저하시키는 문제로 작용하기 때문에 이를 해결하고자 감정 정보를 활용하여 자연스러운 음성을 정제하는 데이터 정제 기법을 제시함.

## 데이터 셋
![image](https://github.com/sungsiyul/Natural-Voice-Filtering/assets/86465983/3abde99a-1b13-4faf-a3cd-697a9a388064)
- 위급상황 (AI hub ‘위급상황 음성/음향 데이터셋’)
- 일상대화 (ETRI ‘한국어 멀티모달 감정 데이터셋 2020’)

## 감정 분류 모델(TIM-Net)
- 음성 데이터를 TIM-Net을 활용하여 7가지 감정(angry, disgust, fear, happy, neutral, sad, surprise)의 확률로 예측한다.
- 각 감정에 대한 확률을 감정 정보로 활용하여 자연스러운 음성을 구분하는 모델을 구축한다.

## 데이터 정제 모델(Semi-Supervised Learning)
![image](https://github.com/sungsiyul/Natural-Voice-Filtering/assets/86465983/6d246433-54be-49c1-a93e-ad8beef32bbd)
- 데이터 정제를 위한 모델은 준지도 학습을 활용하여 보다 많은 데이터를 학습한다.
- ① ~ ⑤의 과정을 순차적으로 반복한다. (전체 데이터의 80%를 Merge할 때까지)
- 예측 신뢰도가 낮은 하위 20% (2,421개)의 데이터는 학습에서 제외한다.

## 상황 분류 모델(CNN)
- 데이터 정제 모델의 성능을 평가하기 위해 상황 분류 모델을 활용한다.

![image](https://github.com/sungsiyul/Natural-Voice-Filtering/assets/86465983/c5faea52-b722-424f-9633-4c2f5a28f6b5)
- 5가지 위급 상황에 대해 상황별 2,000개의 데이터(총 10,000개)를 본 연구에서 제안하는 데이터 정제모델을 통해 자연스러운 모델만을 확보한다.

![image](https://github.com/sungsiyul/Natural-Voice-Filtering/assets/86465983/a2e12c92-f116-4285-9843-7eaa4c43beef)
- 정제된 데이터 7,632개와 정제하지 않은 10,000개의 데이터를 같은 조건의 상황 분류 모델에 학습시키고, 그 결과를 비교한다.

## 결과
- 학습 데이터가 감소되었기 때문에, 학습 시간이 단축되는 효과를 보였다.
- 적은 학습 데이터임에도 성능을 유지하며, 학습에 필요하지 않은 데이터가 잘 정제되었음을 증명한다.
- 결론적으로 본 연구에서 제안하는 데이터 정제 모델을 통해 상황 분류 모델의 학습 효율을 향상시키는 결과를 확인할 수 있다.

