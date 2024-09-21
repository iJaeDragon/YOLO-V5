# detect

## 실행

```
python detect.py --weights ./runs/train/yolo_custom_model3/weights/best.pt --img 650 --conf 0.6 --source C:\Users\rhkgk\Desktop\OO\2_yolo-model\data\images\train\cat5.jpg --save-txt --save-conf --project ./runs/detect --name test_results
```

## 파라미터 의미

```
  --weights ./runs/train/yolo_custom_model3/weights/best.pt # 가중치 파일 경로이며, 모델이 사용할 사전 학습된 가중치 파일의 경로이다.
  --img 650 # 이미지 크기이며, 입력 이미지의 가로와 세로 길이를 650 픽셀로 조정한다는 의미이다.
  --conf 0.6 # 신뢰도 임계값을 의미하며, 모델이 탐지한 객체가 유효하다고 판단하기 위한 최소 신뢰도 값이다. 여기서는 0.6로 설정되어 있으며, 탐지된 객체의 신뢰도가 60% 이상인 경우에만 결과로 출력된다.
  --source C:\Users\rhkgk\Desktop\OO\2_yolo-model\data\images\train\cat5.jpg # 입력 소스를 의미하며, 탐지할 이미지 또는 비디오 파일의 경로를 지정한다. 이 경로에 있는 파일을 사용해 객체 탐지를 수행한다.
  --save-txt # 결과 저장(텍스트) : 이 옵션을 사용하면 탐지 결과(바운딩 박스와 클래스 정보)를 .txt파일로 저장한다. 결과는 YOLO포맷으로 저장되며, 각 객체에 대한 클래스와 좌표 정보가 포함된다.
  --save-conf # 신뢰도 값 저장 : 이 옵션을 활성화하면 탐지된 객체의 신뢰도 값도 함께 저장된다. 이는 결과 텍스트 파일에 추가되어 탐지된 각 객체의 신뢰도를 확인할 수 있다.
  --project ./runs/detect # 프로젝트 경로를 의미하며 탐지 결과를 저장할 티렉토리 경로이다. 각 탐지 결과는 `--name` 파라미터로 지정된 이름 하위 폴더에 저장된다.
  --name test_results # 결과 저장 폴더 이름을 의미하며, 탐지 결과를 저장할 폴더의 이름을 지정한다.
```

![IMG_0264_JPG rf 67ec2a63bc2de6709559c9d458b18733](https://github.com/user-attachments/assets/2769f3e5-f4c2-45f1-b5f9-0585be7f68a7)
