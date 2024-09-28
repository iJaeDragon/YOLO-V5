# train

## 학습 데이터

```
  data:
    ├─hyps
    ├─images 
    │  ├─train # 학습할 이미지
    │  └─val # 검증(validation)을 위한 이미지 - 이미지들은 학습 과정에서 사용되지 않으며, 학습된 모델이 새로운 데이터에서 얼마나 잘 예측하는지를 측정하기 위해 사용
    └─labels 
        ├─train # 학습할 이미지의 바운딩 박스 영역 정보
        └─val # 검증 이미지의 바운딩 박스 영역 정보
```

## 학습 시작

```
  python train.py --img 650 --batch 16 --epochs 75 --data ./data.yaml --cfg ./models/yolov5s.yaml --weights '' --name yolo_custom_model
```

## 파리미터 의미

```
  --img 650  # 이미지 크기 : 입력 이미지의 크기를 설정하는것이며, 여기서 650은 입력 이미지의 가로와 세로 길이가 각각 650 픽셀이 된다는 뜻이다. YOLOv5는 이미지의 크기를 정사각형으로 처리한다.
  --batch 16 # 배치 크기 : 한 번에 모델에 입력으로 넣을 이미지의 개수이다. `16`은 한 배치에 16개의 이미지를 사용한다는 의미이며, 배치 크기가 클수록 학습이 빠르지만, 더 많은 GPU 메모리를 필요로 한다.
  --epochs 75 # 에포크 수 : 전체 학습 데이터를 몇 번 반복해서 학습할지 설정한다. 여기서는 75번 반복하며, 에포크 수가 많을수록 더 많은 학습이 이루어지지만, 학습 시간이 길어질 수 있다.
  --data ./data.yaml # 데이터 구성 파일 경로 설정
  --weights '' # 가중치 파일 경로이며, 빈 문자열은 가중치 없이 처음부터 모델을 학습하겠다는 뜻이다. 만약 사전 학습된 가중치를 사용하고 싶다면 해당 경로를 입력할 수 있다.
  --name yolo_custom_mode # 실험 이름이며, 학습된 모델과 로그 파일이 저장될 디렉토리 이름이다.
```

## 결과

```
  C:.
  │  events.out.tfevents.1726746187.DESKTOP-NADMO1K.15212.0 # TensorBoard 로그 파일: TensorBoard에서 학습 과정을 시각화할 수 있는 로그 파일
  │  hyp.yaml # 하이퍼파라미터 설정 파일: 학습에 사용된 하이퍼파라미터 설정을 기록한 파일
  │  labels.jpg # 학습 데이터의 클래스 분포 시각화: 학습 데이터셋의 클래스 레이블 분포를 보여주는 이미지
  │  labels_correlogram.jpg # 레이블 상관도 이미지: 각 클래스 간의 상관관계를 시작적으로 나타낸 이미지
  │  opt.yaml # 옵션 파일: 모델 학습에 사용된 옵션(파라미터) 설정을 기록한 파일
  │  results.csv # 성능 결과 파일
  │
  └─weights
          best.pt # 최고 성능 가중치 파일
          last.pt # 최종 가중치 파일
```

## 참고
  https://docs.ultralytics.com/modes/train/#resuming-interrupted-trainings
  
  patience - epoch early stop 정리
