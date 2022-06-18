# 0. IOT 작업 전체 가이드라인

- 해당 프로젝트는 크게 Classification 과 Object Detection 두개로 구분되어 있음
- 각 파트는 데이터 수집 - 라벨링 - 학습 - web 적용 순으로 진행 됨
- 웹캠을 활용하며 로컬과 colab 환경에서 진행 됨

# 1. Classification

## 파일 구조

<aside>
💡 자세한 파일 설명은 진행 과정에서 설명

</aside>

- html (모델 web 구동 용 폴더)
    - mobilenet (weights 파일)
    - results (결과 출력 이미지)
    - hand.json (라벨 인코더)
    - index.html (html 파일)
- thumb (학습용 데이터)
- 1_Data_collecting.ipynb (데이터 수집,로컬환경)
- 2_Classification.ipynb (데이터 학습, 코랩환경)

## 진행 과정

### 1. 데이터 수집

<aside>
💡 데이터 수집에선 1_Data_collecting.ipynb를 사용 함

- 노트북에 있는 웹캠을 활용 해 직접 데이터를 수집
- 데이터는 크게 Train 과 Test로 나누어 수집
- 수집할 이미지는 손 이미지 이며 라벨은 손가락 up / 손가락 down
</aside>

1. **빈 폴더에 1_Data_collecting.ipynb 다운로드** 
2. **Train , test 그리고 라벨 별로 데이터를 저장하기 위해 아래 디렉토리 처럼 폴더 생성** 
    1. thumb
        1. train
            1. up
            2. down
        2. test
            1. up
            2. down

![디렉토리](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2d4a3a45-7b69-4e5e-b201-8e1f5ef28521/Untitled.png)

디렉토리

1. **vscode에서 1_Data_collecting.ipynb 실행**
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/80b94c91-3de7-4114-802b-5116bc01bb24/Untitled.png)
    
    - 해당 코드는 GUI 라이브러리인 tkinter와 이미지 라이브러리 cv2를 이용함
2. **실행을 하게 되면 아래와 같은 GUI 화면이 실행 되며 아래 버튼을 누를 수 있음** 
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3713c60f-96cb-48f5-9925-084e72eb57f3/Untitled.png)
    
3. **버튼에 따라 저장되는 디렉토리가 다름** 
4. **아래 이미지 처럼 이미지들이 저장 됨** 

![버튼 클릭 시 다음과 같이 이미지가 저장 됨 ](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d5c86075-f3bf-44e0-8eed-adeffe7e7a5d/Untitled.png)

버튼 클릭 시 다음과 같이 이미지가 저장 됨 

1. **저장 한 이미지의 폴더 thumb를 구글 드라이브에 업로드**

### 2. 데이터 학습

<aside>
💡 데이터 학습에선 **2_Classification.ipynb** 파일을 사용, **코랩 환경**에서 진행

- 데이터 수집 과정에서 모은 이미지를 이용해 학습을 진행 함
- Pretrained model 로 mobilnet을 사용 함
- Input 이미지가 Up | Down을 분류하는 모델
- **코드 및 과정 설명은 ipynb 노트북 파일에 주석으로 작성 함**
</aside>

### 3. Git repositary for html

<aside>
💡 웹에서 분류 모델을 실행 시키기 위해서는 4개가 필요 함 
- index.html
- 모델 weights 파일 
- 라벨 json 파일 
- 결과 출력 이미지

</aside>

1. **Github 빈 Repositary 생성** 
    - tensorflow weights파일이 local에서는 사용이 불가하기 때문에 github pages를 이용함
    - Github에서 빈 Repositary를 만듬 (이름은 자유)
2. **Repositary를 만든 뒤 로컬에서 clone → 폴더 생성** 
3. **파일 복사** 
    - results, hand_json, index.html 파일을 다운 받은 뒤 앞서 clone 한 repositary 폴더에 넣음
    - 데이터 학습 단계에서 다운 받은 weights 파일을 mobilenet 폴더에 넣음 (이 때 model.json 뿐만 아니라 .bin 파일 모두 넣어야 함)
4. **Git push** 
    - git push를 이용해 github에 업로드 함
        
        ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/8305b31a-655b-4b85-b6e7-50546269c698/Untitled.png)
        

### 4. web page 만들기 in github

- 깃허브의 pages 기능을 사용하면 index.html로 web page로 만들 수 있음
1. **pages 만들기** 
    - 앞서 push 한 git repositary로 들어가 setting → pages를 들어 감
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/359cd111-dc97-415a-a57c-a22b0ea91cc6/Untitled.png)
    
2. Source 지정 
    - source 탭에서 main - root 로 설정 하고 save를 누름
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/16301723-6322-4faf-8d2d-793e87bf6256/Untitled.png)
    
3. **web page 링크 확인** 
    - SAVE를 누를 경우 자동으로 WEBPAGE 링크가 생성 됨
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/bf1c3999-29b8-41f1-98cd-183dbc5b79cb/Untitled.png)
    
    - 다만 웹페이지 링크가 생성되었다 하더라도 바로 웹페이지가 생성되지는 않음
    - 웹 페이지가 생성 완료 되었을 때 code 탭 오른쪽 하단에 다음과 같은 표시가 뜸
        
        ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d0ef9dbb-ef0e-4daf-9f37-dbd5a0d2d156/Untitled.png)
        
4. **웹페이지 실행** 
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/20b64e2d-09e0-4ee1-a79a-d92c1e9a3e0e/Untitled.png)
    
    - 상단에는 웹캠이 실시간으로 실행 되며 Capture를 누르면 사진이 찍힘
    - 왼쪽 하단에 찍힌 사진이 출력 되며 이 사진이 input image가 되어 분류 모델이 실행 됨
    - 분류 결과에 따라 Up 또는 Down 이미지가 출력 됨
    

# 2. Object Detection
