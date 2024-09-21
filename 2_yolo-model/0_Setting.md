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

## 4. 구조 파악

<details>
    <summary>yolov5 기본 구조</summary>

```
    C:.
    │  .dockerignore
    │  .gitattributes
    │  .gitignore
    │  benchmarks.py
    │  CITATION.cff
    │  CONTRIBUTING.md
    │  data.yaml
    │  detect.py
    │  export.py
    │  hubconf.py
    │  LICENSE
    │  pyproject.toml
    │  README.md
    │  README.zh-CN.md
    │  requirements.txt
    │  train.py
    │  tutorial.ipynb
    │  val.py
    │
    ├─.github
    │  │  dependabot.yml
    │  │
    │  ├─ISSUE_TEMPLATE
    │  │      bug-report.yml
    │  │      config.yml
    │  │      feature-request.yml
    │  │      question.yml
    │  │
    │  └─workflows
    │          ci-testing.yml
    │          cla.yml
    │          codeql-analysis.yml
    │          docker.yml
    │          format.yml
    │          greetings.yml
    │          links.yml
    │          merge-main-into-prs.yml
    │          stale.yml
    │
    ├─classify
    │      predict.py
    │      train.py
    │      tutorial.ipynb
    │      val.py
    │
    ├─data
    │  │  Argoverse.yaml
    │  │  coco.yaml
    │  │  coco128-seg.yaml
    │  │  coco128.yaml
    │  │  GlobalWheat2020.yaml
    │  │  ImageNet.yaml
    │  │  ImageNet10.yaml
    │  │  ImageNet100.yaml
    │  │  ImageNet1000.yaml
    │  │  Objects365.yaml
    │  │  SKU-110K.yaml
    │  │  VisDrone.yaml
    │  │  VOC.yaml
    │  │  xView.yaml
    │  │
    │  ├─hyps
    │  │      hyp.no-augmentation.yaml
    │  │      hyp.Objects365.yaml
    │  │      hyp.scratch-high.yaml
    │  │      hyp.scratch-low.yaml
    │  │      hyp.scratch-med.yaml
    │  │      hyp.VOC.yaml
    │  │
    │  ├─images
    │  │      bus.jpg
    │  │      zidane.jpg
    │  │
    │  └─scripts
    │          download_weights.sh
    │          get_coco.sh
    │          get_coco128.sh
    │          get_imagenet.sh
    │          get_imagenet10.sh
    │          get_imagenet100.sh
    │          get_imagenet1000.sh
    │
    ├─models
    │  │  common.py
    │  │  experimental.py
    │  │  tf.py
    │  │  yolo.py
    │  │  yolov5l.yaml
    │  │  yolov5m.yaml
    │  │  yolov5n.yaml
    │  │  yolov5s.yaml
    │  │  yolov5x.yaml
    │  │  __init__.py
    │  │
    │  ├─hub
    │  │      anchors.yaml
    │  │      yolov3-spp.yaml
    │  │      yolov3-tiny.yaml
    │  │      yolov3.yaml
    │  │      yolov5-bifpn.yaml
    │  │      yolov5-fpn.yaml
    │  │      yolov5-p2.yaml
    │  │      yolov5-p34.yaml
    │  │      yolov5-p6.yaml
    │  │      yolov5-p7.yaml
    │  │      yolov5-panet.yaml
    │  │      yolov5l6.yaml
    │  │      yolov5m6.yaml
    │  │      yolov5n6.yaml
    │  │      yolov5s-ghost.yaml
    │  │      yolov5s-LeakyReLU.yaml
    │  │      yolov5s-transformer.yaml
    │  │      yolov5s6.yaml
    │  │      yolov5x6.yaml
    │  │
    │  ├─segment
    │  │      yolov5l-seg.yaml
    │  │      yolov5m-seg.yaml
    │  │      yolov5n-seg.yaml
    │  │      yolov5s-seg.yaml
    │  │      yolov5x-seg.yaml
    │  │
    │  └─__pycache__
    │          common.cpython-39.pyc
    │          experimental.cpython-39.pyc
    │          yolo.cpython-39.pyc
    │          __init__.cpython-39.pyc
    │
    ├─runs
    │  └─train
    │      └─yolo_custom_model
    │          │  events.out.tfevents.1725539357.DESKTOP-NADMO1K.25348.0
    │          │  hyp.yaml
    │          │  opt.yaml
    │          │
    │          └─weights
    ├─segment
    │      predict.py
    │      train.py
    │      tutorial.ipynb
    │      val.py
    │
    ├─utils
    │  │  activations.py
    │  │  augmentations.py
    │  │  autoanchor.py
    │  │  autobatch.py
    │  │  callbacks.py
    │  │  dataloaders.py
    │  │  downloads.py
    │  │  general.py
    │  │  loss.py
    │  │  metrics.py
    │  │  plots.py
    │  │  torch_utils.py
    │  │  triton.py
    │  │  __init__.py
    │  │
    │  ├─aws
    │  │      mime.sh
    │  │      resume.py
    │  │      userdata.sh
    │  │      __init__.py
    │  │
    │  ├─docker
    │  │      Dockerfile
    │  │      Dockerfile-arm64
    │  │      Dockerfile-cpu
    │  │
    │  ├─flask_rest_api
    │  │      example_request.py
    │  │      README.md
    │  │      restapi.py
    │  │
    │  ├─google_app_engine
    │  │      additional_requirements.txt
    │  │      app.yaml
    │  │      Dockerfile
    │  │
    │  ├─loggers
    │  │  │  __init__.py
    │  │  │
    │  │  ├─clearml
    │  │  │  │  clearml_utils.py
    │  │  │  │  hpo.py
    │  │  │  │  README.md
    │  │  │  │  __init__.py
    │  │  │  │
    │  │  │  └─__pycache__
    │  │  │          clearml_utils.cpython-39.pyc
    │  │  │          __init__.cpython-39.pyc
    │  │  │
    │  │  ├─comet
    │  │  │  │  comet_utils.py
    │  │  │  │  hpo.py
    │  │  │  │  optimizer_config.json
    │  │  │  │  README.md
    │  │  │  │  __init__.py
    │  │  │  │
    │  │  │  └─__pycache__
    │  │  │          comet_utils.cpython-39.pyc
    │  │  │          __init__.cpython-39.pyc
    │  │  │
    │  │  ├─wandb
    │  │  │  │  wandb_utils.py
    │  │  │  │  __init__.py
    │  │  │  │
    │  │  │  └─__pycache__
    │  │  │          wandb_utils.cpython-39.pyc
    │  │  │          __init__.cpython-39.pyc
    │  │  │
    │  │  └─__pycache__
    │  │          __init__.cpython-39.pyc
    │  │
    │  ├─segment
    │  │      augmentations.py
    │  │      dataloaders.py
    │  │      general.py
    │  │      loss.py
    │  │      metrics.py
    │  │      plots.py
    │  │      __init__.py
    │  │
    │  └─__pycache__
    │          augmentations.cpython-39.pyc
    │          autoanchor.cpython-39.pyc
    │          autobatch.cpython-39.pyc
    │          callbacks.cpython-39.pyc
    │          dataloaders.cpython-39.pyc
    │          downloads.cpython-39.pyc
    │          general.cpython-39.pyc
    │          loss.cpython-39.pyc
    │          metrics.cpython-39.pyc
    │          plots.cpython-39.pyc
    │          torch_utils.cpython-39.pyc
    │          __init__.cpython-39.pyc
    │
    └─__pycache__
            val.cpython-39.pyc
```

</details>

### 조금 구조가 복잡하고 사용하지 않는 파일이 있기 때문에 필요한 부분만 남기고 사용하였다.

<details>
    <summary>커스텀 구조</summary>

    ```
      C:.
      │  data.yaml
      │  detect.py # 감지 스크립트
      │  export.py
      │  requirements.txt
      │  train.py # 학습 스크립트
      │  val.py
      │
      ├─data # 학습할때 사용할 데이터
      │  ├─hyps
      │  │      hyp.no-augmentation.yaml
      │  │      hyp.Objects365.yaml
      │  │      hyp.scratch-high.yaml
      │  │      hyp.scratch-low.yaml
      │  │      hyp.scratch-med.yaml
      │  │      hyp.VOC.yaml
      │  │
      │  ├─images
      │  │  ├─train # 학습할 이미지
      │  │  │
      │  │  └─val # 검증할 이미지
      │  │
      │  └─labels
      │      │
      │      ├─train # 학습할 이미지의 객체 바운딩 박스 영역
      │      │
      │      └─val # 검증할 이미지의 객체 바운등 박스 영역
      │
      ├─models
      │  │  common.py
      │  │  experimental.py
      │  │  tf.py
      │  │  yolo.py
      │  │  yolov5l.yaml
      │  │  yolov5m.yaml
      │  │  yolov5n.yaml
      │  │  yolov5s.yaml
      │  │  yolov5x.yaml
      │  │  __init__.py
      │  │
      │  ├─hub
      │  │      anchors.yaml
      │  │      yolov3-spp.yaml
      │  │      yolov3-tiny.yaml
      │  │      yolov3.yaml
      │  │      yolov5-bifpn.yaml
      │  │      yolov5-fpn.yaml
      │  │      yolov5-p2.yaml
      │  │      yolov5-p34.yaml
      │  │      yolov5-p6.yaml
      │  │      yolov5-p7.yaml
      │  │      yolov5-panet.yaml
      │  │      yolov5l6.yaml
      │  │      yolov5m6.yaml
      │  │      yolov5n6.yaml
      │  │      yolov5s-ghost.yaml
      │  │      yolov5s-LeakyReLU.yaml
      │  │      yolov5s-transformer.yaml
      │  │      yolov5s6.yaml
      │  │      yolov5x6.yaml
      │  │
      │  ├─segment # 다양한 크기의 모델 제공
      │  │      yolov5l-seg.yaml # Large
      │  │      yolov5m-seg.yaml # Medium
      │  │      yolov5n-seg.yaml # Nano
      │  │      yolov5s-seg.yaml # Small
      │  │      yolov5x-seg.yaml # Extra Large 
      │  │
      │  └─__pycache__
      │          common.cpython-39.pyc
      │          experimental.cpython-39.pyc
      │          yolo.cpython-39.pyc
      │          __init__.cpython-39.pyc
      │
      ├─runs # 실행 결과가 저장되는 경로
      ├─utils # 필수 유틸
      │  │  activations.py
      │  │  augmentations.py
      │  │  autoanchor.py
      │  │  autobatch.py
      │  │  callbacks.py
      │  │  dataloaders.py
      │  │  downloads.py
      │  │  general.py
      │  │  loss.py
      │  │  metrics.py
      │  │  plots.py
      │  │  torch_utils.py
      │  │  triton.py
      │  │  __init__.py
      │  │
      │  ├─aws
      │  │      mime.sh
      │  │      resume.py
      │  │      userdata.sh
      │  │      __init__.py
      │  │
      │  ├─docker
      │  │      Dockerfile
      │  │      Dockerfile-arm64
      │  │      Dockerfile-cpu
      │  │
      │  ├─flask_rest_api
      │  │      example_request.py
      │  │      README.md
      │  │      restapi.py
      │  │
      │  ├─google_app_engine
      │  │      additional_requirements.txt
      │  │      app.yaml
      │  │      Dockerfile
      │  │
      │  ├─loggers
      │  │  │  __init__.py
      │  │  │
      │  │  ├─clearml
      │  │  │  │  clearml_utils.py
      │  │  │  │  hpo.py
      │  │  │  │  README.md
      │  │  │  │  __init__.py
      │  │  │  │
      │  │  │  └─__pycache__
      │  │  │          clearml_utils.cpython-39.pyc
      │  │  │          __init__.cpython-39.pyc
      │  │  │
      │  │  ├─comet
      │  │  │  │  comet_utils.py
      │  │  │  │  hpo.py
      │  │  │  │  optimizer_config.json
      │  │  │  │  README.md
      │  │  │  │  __init__.py
      │  │  │  │
      │  │  │  └─__pycache__
      │  │  │          comet_utils.cpython-39.pyc
      │  │  │          __init__.cpython-39.pyc
      │  │  │
      │  │  ├─wandb
      │  │  │  │  wandb_utils.py
      │  │  │  │  __init__.py
      │  │  │  │
      │  │  │  └─__pycache__
      │  │  │          wandb_utils.cpython-39.pyc
      │  │  │          __init__.cpython-39.pyc
      │  │  │
      │  │  └─__pycache__
      │  │          __init__.cpython-39.pyc
      │  │
      │  ├─segment
      │  │      augmentations.py
      │  │      dataloaders.py
      │  │      general.py
      │  │      loss.py
      │  │      metrics.py
      │  │      plots.py
      │  │      __init__.py
      │  │
      │  └─__pycache__
      │          augmentations.cpython-39.pyc
      │          autoanchor.cpython-39.pyc
      │          autobatch.cpython-39.pyc
      │          callbacks.cpython-39.pyc
      │          dataloaders.cpython-39.pyc
      │          downloads.cpython-39.pyc
      │          general.cpython-39.pyc
      │          loss.cpython-39.pyc
      │          metrics.cpython-39.pyc
      │          plots.cpython-39.pyc
      │          torch_utils.cpython-39.pyc
      │          __init__.cpython-39.pyc
      │
      └─__pycache__
              export.cpython-39.pyc
              val.cpython-39.pyc
  ```

</details>
