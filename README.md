# IOT_education

# 프로젝트 목적

- IOT (노트북 카메라)를 활용한 AI 사용
- 노트북 카메라로 하여금 학생들이 AI를 체험할 수 잇게
- AI 체험 사항 : 포즈추출, 분류, 물체 탐지(Object Detection), Face Recognition

# 파일 디렉토리

- 각 폴더 및 파일은 AI 종류 별로 구성되어 있습니다
- 주요 출처는 기존 학습 자료 + YOLOv5 기반 모델들 입니다

<aside>
💡 폴더 디렉토리는 다음과 같으며 파일 설명은 밑에 추가되어 있습니다.

</aside>

1. Face emotion classification & Detection 
    1. 1-1 Face_emotion_classification.ipynb
    2. 1-2 Real time Emotion Detection Using Yolo-V5 and RepVGG.ipynb
2. Object Detection
    1. 2-1 Object_detection_YOLOv5.ipynb
    2. mask_x_trained.pt
    3. people.png 
3. Pose extraction 
    1. open_pose_using_template.ipynb
    2. tf-pose-estimation_with_webcam.ipynb
4. Face recognition 
    1. Face_Recognition.ipynb
    2. Face Recognition_library.ipynb

# 각 항목 별 설명

## 1. Face Emotion Classification & Detection

- 사진 or 영상 or 웹캠의 실시간 영상을 이용해 얼굴에서 나타나는 감정을 분류 또는 탐지합니다

### 1-1 Face_emotion_classification

- 바닐라 CNN을 이용해 감정을 분류하는 모델입니다
- 학습한 모델을 이용해 사진 그리고 웹캠을 활용해 실시간으로 얼굴 감정을 분류합니다
- 웹캠 모듈은 기존에 Open-Pose 파일에 있는 코드를 활용했습니다
- 웹캠으로 부터 이미지를 받고 이를 모델에 넣어 감정을 분류합니다

### 1-2 Face_emotion_Detection

- 해당 노트북은 실시간 웹캠을 이용한 감정 탐지를 위한 노트북입니다
- 얼굴의 감정을 탐지하고 분류하기 위해 YOLOv5 모델을 활용했습니다
- YOLOv5는 자체적으로 웹캠을 활용한 탐지를 지원하지만 로컬에서만 가능하기 때문에 로컬에서 진행됩니다
- 특정 가상 환경, 라이브러리가 요구되기 때문에 이를 위한 과정들을 작성 해 두었습니다
- 예시


<img src="https://user-images.githubusercontent.com/92499881/172298509-0c4561f6-ad08-45af-8121-a59f64c885f1.png" width="400" height="400"/>

<img src="https://user-images.githubusercontent.com/92499881/172298562-407f7cb1-fc99-4739-a2e6-218dfaac9baa.png" width="400" height="400"/>








## 2. Object Detection

### 2-1 Object_detection_YOLOv5.ipynb

- Object Detection은 YOLOv5 모델 기반으로 구성하였습니다
- 기존에 만들어진 Datasets, weights를 이용한 학습, Predict 과정이 있으며 새로운 데이터(커스텀 데이터)를 이용한 학습 과정 및 추론 과정 또한 포함되어 있습니다
- 그리고 이렇게 학습한 것을 이용해 웹캠으로 실시간 탐지를 하는 과정 또한 포함되어 있습니다

### mask_x_trained.pt

- mask_x_trained.pt는 커스텀 데이터 셋(마스크 데이터)를 미리 학습시켜 놓은 weights 파일입니다.
- 학습의 경우 가장 큰 YOLOv5x 모델을 Pretrained model로 사용하여 학습하였으며 학습 시간이 1시간 정도 소요되기 떄문에 미리 학습 시켜 두고 따로 저장 해 두었습니다.

### people.png

- mask detection을 위한 샘플 이미지 입니다.

## 3. Pose extraction

- 해당 파일들은 기존 Pose extraction 파일들 입니다
- 추가 사항 없습니다

## 4. Face recognition

- 얼굴을 인식하고 그 이외의 응용으로 구성되어 있습니다
- 두개의 노트북으로 구성되어 있으며 첫번째 노트북은 기존의 파일이며 두번째 노트북은 Face_recognition 라이브러리를 활용했습니다

### 1. Face_recognition.ipynb

- 기존의 Face recognition과 동일합니다

### 2. Face_recognition_library.ipynb

- Face_recognition 라이브러리를 활용하여 얼굴 탐지, 얼굴 인식, 자동 메이크업 등을 할 수 있습니다.
1. 얼굴 탐지 : 말 그대로 사진 ,영상 속 얼굴을 탐지하여 박스로 표시합니다 
2. 얼굴 특징 : 사진 속 얼굴의 윤곽을 표시하거나 자동 메이크업을 진행 합니다 
3. 얼굴 인식 : 사진 속 이미지에서 얼굴을 탐지하고 이를 레퍼런스 이미지와 비교해 사진 속 인물이 누구인지 표시합니다 
4. Webcam 활용 
    - 위에서 진행한 얼굴 탐지, 인식, 자동 메이크업을 웹캠으로 실시간으로 진행합니다
    - 이 경우 로컬에서 진행되어야 하며 가상 환경, 라이브러리를 위한 과정이 따로 필요 합니다.
