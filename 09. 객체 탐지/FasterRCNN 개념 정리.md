Faster R-CNN이 나온 배경을 이해하기 위해 R-CNN과 Fast R-CNN을 알아보자.

# R-CNN
**R-CNN: Clearly Explained 영상은 정말 좋은 영상입니다. 추천합니다!**     
(영상: https://www.youtube.com/watch?v=nJzQDpppFj0)       

R-CNN (Region Based Convolutional Neural Networks)은
- 🔸**영역제안(Regional Proposal)**: 선택적 탐색 알고리즘(Selective Search)을 이용해 객체가 있을만한 영역을 찾음
    - 선택적 탐색 알고리즘은 이미지의 인접 픽셀들이 비슷한 색상, 밝기 등을 가지는지 확인하여 비슷하면 군집화하는 것.
- 🔸**합성곱 모델을 이용한 특징 추출(Feature Extraction Using Convolution Model)**: 영역에서 특징을 추출해서 진짜 영역 안에 객체 있는지 확인 용이하도록 함.
- 🔸**서포트 벡터머신(Support Vector Machine)**: 클래스 분류를 위해 사용되는데, 여기서 **영역들의 클래스와 해당 클래스에 속할 확률값 계산함.**
    - 서포트 벡터머신을 통해 클래스와 해당 클래스에 속할 확률 구해서 비최댓값 억제(Non-Maximum Suppression, NMS) 수행함
        - NMS는 IoU, Intersection over Union(= proposed region ∩ ground truth)/(proposed region ∪ ground truth)로 구함
        - 아래 그림은 R-CNN: Clearly Explained 영상 캡쳐입니다. 12/25가 3/20보다 크기 때문에 NMS에서 12/25가 객체가 있을만한 영역으로 선택됨(R-CNN: Clearly Explained 영상 캡쳐)       
            <img width="500" alt="스크린샷 2024-01-30 오후 6 14 06" src="https://github.com/hanmyu/computervision_transformer_pytorch/assets/157959298/92309145-e635-4ec6-af12-7285556ffa2f">      
로 이루어져 있음.

- **R-CNN 모델 평가는 평균 정밀도(Mean Average Precision, mAP) 이용함.**
    - IoU가 0.5 이상일 때, 우리가 예측한 영역 (predicted bounding boxes)가 제대로 예측했다고 말함.
    - IoU가 0.5 이하이면, 우리가 예측한 영역 (predicted bounding boxes)가 제대로 예측못한 것.
    - 아래 그림의 Precision은 IoU 0.5 이상/전체이고 Recall은 사진에서 개가 두마리인데 하나만 객체 탐지 했으므로 1/2임(R-CNN: Clearly Explained 영상 캡쳐)       
        <img width="600" alt="스크린샷 2024-01-30 오후 6 21 54" src="https://github.com/hanmyu/computervision_transformer_pytorch/assets/157959298/058ece0b-3b1c-45b9-9527-7ab06aea361e">    

VGG 논문 소개:
[https://medium.com/@msmapark2/vgg16-논문-리뷰-very-deep-convolutional-networks-for-large-scale-image-recognition-6f748235242a](https://medium.com/@msmapark2/vgg16-%EB%85%BC%EB%AC%B8-%EB%A6%AC%EB%B7%B0-very-deep-convolutional-networks-for-large-scale-image-recognition-6f748235242a)

Convolution: 설명 적기.
[But what is a convolution?](https://www.youtube.com/watch?v=KuXjwB4LzSA)

**교차 검증(Cross Validation)**:      
테스트 데이터셋을 따로 고정하지 않고 데이터의 모든 부분을 다 이용하여 모델을 테스팅한다. 모델 정확도(=성능)은 모든 데이터를 다 이용해 테스팅 후 나온 정확도들의 평균 값이다.      
이후, 다양한 머신러닝 방법들(Logistic Regression, Support Vector Machine, K-nearest neighbors)을 비교하여 어떤 걸 쓰는 게 좋을지 정한다.       
*참고: https://m.blog.naver.com/ckdgus1433/221599517834

**서포트 벡터머신(Support Vector Machine, SVM)**: 서로 다른 클래스들을 나누는 점, 선, 면을 찾는 것.  

- SVM의 결정 경계(Decision Boundary, 클래스들을 나누는 경계)들은 서로 가장 멀리 떨어져있어야한다(=margin이 크면 클수록 좋음).
- Support vector은 decision boundary에 있는 것들이다. 딱 그 경계선에 있는 것들이다.
- 커널을 이용하여 감마 값을 조정하면 SVM의 선을 곡선으로 만들 수 있음(아래 The Kernel Trick in Support Vector Machine (SVM) 영상 참고).
    - 감마 값이 높을수록 선이 더 구불거림
- 소프트 마진 방식을 많이 씀. 하드 마진 방식은 이상치들이 있는 실제 데이터에 적용하기 힘듦.
    - 아래 그림은 Support Vector Machines : Data Science Concepts 영상 스크린샷임. 하드 마진 방식은 하나의 클래스에 속하는 데이터들이 무조건 decision boundary 안에 위치해야함. 하지만 소프트 마진 방식은 하나의 클래스에 속하는 데이터들이 무조건 decision boundary 안에 위치해야하는 건 아님. 오차 허용함.
    <img width="219" alt="스크린샷 2024-01-30 오후 5 02 55" src="https://github.com/hanmyu/computervision_transformer_pytorch/assets/157959298/a99ddc55-53ec-4808-8851-e175cff472d9">

***아래의 Support Vector Machines : Data Science Concepts 영상은 매우 매우 좋으니 보시길 바랍니다 :)**

[Support Vector Machines : Data Science Concepts](https://www.youtube.com/watch?v=iEQ0e-WLgkQ)

[The Kernel Trick in Support Vector Machine (SVM)](https://www.youtube.com/watch?v=Q7vT0--5VII)

+**+시간이 있다면 SVM 수식 공부, SVM에 커널 적용하는 부분을 더 공부해봐도 좋을 것 같음.**
