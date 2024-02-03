### Contents
- 1.) CNN이 무엇이고 2.) 어디에 많이 쓰이고 3.) 구조가 어떻게 되는가
- CNN 특징 맵이란
- CNN 어떻게 적용하는지

⭐️ 강추하는 영상     
- https://www.youtube.com/watch?v=YRhxdVk_sIs (CNN 전반적인 설명)
- https://www.youtube.com/watch?v=pj9-rr1wDhM (CNN 적용)
- https://www.youtube.com/watch?v=VwVg9jCtqaU (CNN 적용, 이해하기 매우 쉬움)

⭐️ 강추하는 글
- https://medium.com/@saba99/feature-map-35ba7e6c689e (특징 맵 설명)

# CNN(Convolutional Neural Network) 소개
이미지 분석에 많이 쓰임. 이미지의 패턴 인식하기 위해 쓰임(convolutional layer가 패턴 인식). 
여기서 패턴은 이미지의 경계선(edges), 모서리(corner), 동그라미(circles), 사각형(squares)등을 말함. 
네트워크의 깊은 은닉층에서는 더 정교한 것들을 인식할 수 있음
- CNN의 첫 레이어: 이미지의 제너럴한 특징 인식(경계선, 모서리, 동그라미, 사각형 등을 인식)
- CNN의 깊은 은닉층: 눈, 코, 입 인식
- CNN의 매우 깊은 은닉층/마지막: 객체 인식(강아지, 고양이 인식 가능)
<img width="529" alt="스크린샷 2024-02-03 오후 6 01 18" src="https://github.com/hanmyu/computervision_transformer_pytorch/assets/157959298/e53f2d16-d0f6-41b5-b234-e7efbbca6808">   
<img width="518" alt="스크린샷 2024-02-03 오후 6 07 07" src="https://github.com/hanmyu/computervision_transformer_pytorch/assets/157959298/7a55add9-0407-42c9-85a1-0067c9e28358">    
<img width="250" alt="스크린샷 2024-02-03 오후 6 10 29" src="https://github.com/hanmyu/computervision_transformer_pytorch/assets/157959298/055e2961-1136-44a7-8e21-e043ff5a911f">     


*CNN의 은닉층에는 convolutional layers가 있어야함. 이게 있어야 CNN이라고 말할 수 있음(아니면 앙꼬없는 찐빵, convolutional layer가 없는 CNN이 됨. 말이 안됨)


### 특징 맵 (feature map) 이란?
- CNN convolutional layer에서는 인풋 이미지 데이터에서 이미지의 특징을 추출
- convolutional layer에서는 그 전 레이어의 특징 맵에 필터(커널, kernel)를 적용하여 해당 layer의 특징 맵을 만듦.
- 첫번째 convolutional layer에서는 인풋 이미지 데이터에서 이미지의 특징 추출
- 적용된 필터 수 = 생성되는 특징 맵 수
- 그림 출처: https://www.researchgate.net/figure/Feature-maps-of-CNN-features-from-different-convolutional-layers-The-four-most_fig3_318460353
<img width="500" alt="스크린샷 2024-02-04 오전 12 03 02" src="https://github.com/hanmyu/computervision_transformer_pytorch/assets/157959298/d0bf2991-ea59-4ddb-9057-41d61e716fc6">

# Convolution 적용하는 법
<img width="500" alt="스크린샷 2024-02-04 오전 12 32 54" src="https://github.com/hanmyu/computervision_transformer_pytorch/assets/157959298/7edaef3a-9c1c-4b00-b04f-ec8ab6ca57af">
<img width="500" alt="스크린샷 2024-02-04 오전 12 33 34" src="https://github.com/hanmyu/computervision_transformer_pytorch/assets/157959298/85ca15b5-62a9-47aa-87f1-6ed3d4bc9247">     
- 그림 출처: https://www.youtube.com/watch?v=VwVg9jCtqaU

