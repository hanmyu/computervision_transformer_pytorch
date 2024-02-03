### Contents
- SSD란?

⭐️ 강추하는 영상
- https://www.youtube.com/watch?v=F-irLP2k3Dk (SSD 간단 정리)
- https://www.youtube.com/watch?v=F-irLP2k3Dk (SSD 심층 정리)

# SSD(Single Shot Detector)
<img width="594" alt="스크린샷 2024-02-03 오후 2 51 19" src="https://github.com/hanmyu/computervision_transformer_pytorch/assets/157959298/71c4cfef-ff3f-4a4f-b9bb-d91bc9e3beea">
</br>

- SSD는 다양한 객체 탐지를 위해 쓰임. 따라서 다양한 크기의 특징 맵 사용. 
- Input 데이터 넣어줄 때 Ground Truth(객체 레이블 해놓은 것) 표시해서 넣어줘야함.  
- VGG16에서 특징 맵 추출       
- SSD는 6개의 레이어로 이루어져있음: 하나의 객체당 8732개 bounding boxes(예측)을 줌     
- 하나의 레이어당 38*38 bounding box 만듦. 
- 이후, Non Max Suppression 적용-> 객체를 제대로 탐지한 200개의 것들만 뽑기  
- 이미지 출처: https://www.youtube.com/watch?v=NUEim5bF0_0

## 왜 SSD를 사용하는가?
- 객체 탐지를 위해 indiscriminate sliding window를 통해 객체 탐지하면 너무 리소스가 많이 소요.        
- RCNN에서는 그래서 region proposal 사용, 하지만 RCNN에서는 Selective Search, Alexnet, SVM 다 따로 따로 진행하여 한번에 모델 트레이닝하기 어려움/번거롭고
느림.
  - 그래서 Faster RCNN, YOLO, SSD가 탄생. 우리는 그래서 여기서 SSD 살펴볼 것임.
  - SSD는 RCNN보다 훨씬 빠름. 영역 제안을 안하고 바로 객체 인식을 하기 때문에.
