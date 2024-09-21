## YOLO 모델 사용

## YOLO 모델 사용을 위한 프레임워크

`PyTorch`와 `TensorFlow`중 `PyTorch`를 채택하여 학습을 진행했음.

### 1. PyTorch
  특징:
    PyTorch는 동적 그래프 구조를 사용하여 직관적이고 유연한 코딩이 가능합니다.
    PyTorch에서 YOLOv3, YOLOv4, YOLOv5, 그리고 YOLOv7 등의 다양한 버전이 공식적으로 또는 커뮤니티에서 지원됩니다.
    PyTorch는 디버깅이 용이하고, 코드가 Pythonic하여 배우고 사용하기 쉬운 편입니다.
  장점:
    직관적이고 유연한 개발: 개발자 친화적이며, 연구와 개발 모두에 적합합니다.
    커뮤니티 지원: PyTorch는 빠르게 성장하는 커뮤니티를 가지고 있으며, 다양한 튜토리얼과 오픈 소스 코드가 제공됩니다.
    ONNX 지원: PyTorch는 ONNX로 모델을 내보내고, 다양한 플랫폼에서 배포할 수 있습니다.
  단점:
    모델 배포: TensorFlow에 비해 모바일 및 엣지 디바이스에서의 배포 지원이 상대적으로 적습니다. 다만 PyTorch Mobile과 TorchServe를 통해 이를 해결할 수 있습니다.
    추천 상황:
    연구 및 개발 초기 단계에서 프로토타이핑을 빠르게 수행하고자 하는 경우.
    Python 친화적이고 디버깅이 쉬운 환경을 원하는 경우.
    YOLOv5, YOLOv7과 같은 최신 YOLO 버전을 사용하려는 경우.
   
### 2. TensorFlow
  특징:
    TensorFlow는 정적 그래프를 사용하여 대규모 배포 및 최적화에 강점을 가지고 있습니다.
    TensorFlow에서 YOLOv3, YOLOv4 등이 지원되며, YOLOv5와 같은 최신 버전도 비공식적으로 지원됩니다.
    TensorFlow는 모바일, 웹, 엣지 디바이스에서의 배포에 최적화된 다양한 도구(TensorFlow Lite, TensorFlow.js 등)를 제공합니다.
  장점:
    광범위한 배포 옵션: TensorFlow Lite, TensorFlow.js 등을 통해 다양한 환경에서 모델을 배포할 수 있습니다.
    에코시스템: TensorFlow Extended(TFX), TensorFlow Hub, 모델 서빙 등을 통한 강력한 에코시스템을 제공합니다.
    기업 지원: Google이 후원하는 프로젝트로서, 산업에서 널리 사용되며, 대규모 배포에 적합합니다.
  단점:
    코딩 복잡성: PyTorch에 비해 다소 복잡하고 덜 직관적일 수 있습니다.
    학습 곡선: 처음 배우기에는 PyTorch보다 학습 곡선이 가파를 수 있습니다.
  추천 상황:
    대규모 배포를 고려하고 있으며, 다양한 플랫폼에서의 실행을 원하는 경우.
    산업 현장에서 신뢰할 수 있는 프레임워크를 사용하고자 하는 경우.
    이미 TensorFlow 기반의 프로젝트를 진행 중이거나, Google Cloud Platform(GCP)과 같은 서비스와 통합하려는 경우.


## 데이터셋

직접 이미지를 구해서 데이터 라벨링 작업을 할 수 있지만 너무 오래걸리고 귀찮기 때문에 공개 데이터셋을 활용해서 모델을 훈련했다.

이용한 사이트 : https://universe.roboflow.com/

이용한 데이터셋 : https://universe.roboflow.com/the-pennsylvania-state-university/apple-detection-only/dataset/8

해당 사이트에서 사과 데이터셋을 다운로드 받아 사용하였다.
