# Setting

## 1. 모델 훈련에 필요한 라이브러리와 도구를 설치한다.

* PyTorch
* Torchvision
* numpy
* opencv-python
* matplotlib
* pandas
등..

## 2. GPU 사용을 위해 CUDA를 설치하고, PyTorch의 GPU 버전을 설치한다.

```
  pip install torch torchvision numpy opencv-python matplotlib pandas
```

## 3. YOLO 모델 다운로드

### PyTorch에서 사용할 YOLOv5, YOLOv7 등의 모델을 다운로드 한다.

### 예시로는 YOLOv5를 다운로드 하였음.

```
  git clone https://github.com/ultralytics/yolov5.git
  cd yolov5
  pip install -r requirements.txt
```
