# Overloaded Vehicle Detection Program
![Google Colab](https://img.shields.io/badge/Google%20Colab-%23F9A825.svg?style=for-the-badge&logo=googlecolab&logoColor=white)
![Google Drive](https://img.shields.io/badge/Google%20Drive-4285F4?style=for-the-badge&logo=googledrive&logoColor=white)

> Detectron2와 OCR 기술을 활용한 과적 차량 판별 및 정보 추출 프로그램

[프로젝트 이미지]

## Description
과적(Overloading)은 화물차에 규정된 적재중량 또는 적재용적을 넘어 화물을 싣는 법률 행위를 말한다.

국토교통부에서는 중량초과, 길이초과, 혹은 주관적 판단 기준에 의거하여 과적 차량을 구분하고 통제하고 있다. 
하지만 대부분의 경우, 경찰관이 직접 발견한 과적 차량에 대해 제재를 가하는 방식으로 단속이 이루어지고 있다. <br>이러한 방식의 경우 시간 대비 효율성이 떨어지고, 경찰관 역시 교통사고에 휘말릴 수 있다는 단점이 존재한다.
2024년 2월 실시한 화물차 적재 불량·초과 단속은 총 1064건으로, 이는 전년 3~4월 단속 실적보다 82.6% 증가한 수치다. 이에 따라 과적 화물 차량에 대한 단속을 자동화할 수 있는 프로그램의 필요성을 인식했다.

본 프로젝트는 과적 차량의 다양한 기준 중, 이미지 상으로 확인할 수 있는 적재용적 및 길이 기준에 한정하여 충족한다. 

Detectron2 모델을 사용하여 이미지에서 '정상 차량'과 '과적 차량(적재 불량)'을 정밀하게 분류하고 탐지한다. 탐지된 과적 차량 이미지는 자동으로 필터링되어 저장되며,
EasyOCR을 통해 해당 차량에 부착된 번호판 정보를 추출함으로써 관리를 자동화하는 기능을 제공한다.

## 🗓️ Period
2024-05-15 ~ 2024-06-21 (5 week)

## 👥 Members
- 장현민: Manage Github, EasyOCR 모델 연동
- 이윤우: Detectron2 모델 학습 및 성능 개선
- 황지민: Detectron2 모델 학습 및 성능 개선, 단일앱 제작

## ⚙️ Getting Started

1. Anaconda와 pytorch를 설치한다.
2. [구글 드라이브의 Training data와 Test data](https://drive.google.com/drive/folders/1sjEpVfYICoc9p9XbG2-4ivKQwat6e4cv?usp=drive_link)를 다운받는다.
3. 코드는 [detect_overload 디렉터리의 마지막 버전 파일](detect_overload/version_7.0/overload_final.ipynb)을 다운받는다.

혹은 다음 Colab 링크해서 실행할 수 있다. 

[Colab Link(클릭)](https://colab.research.google.com/drive/1g4uhNQ6se0aSSStaDk7MauDgI8h3grGb?usp=sharing)

## 🛠️ Tech Stack
- Language: Python
- Frameworks :
  - PyTorch : Detectron2와 EasyOCR의 기반
  - Detectron2 : 객체 탐지 프레임워크
- Libraries :
  - EasyOCR: 이미지에서 텍스트 추출(OCR) 라이브러리
  - OpenCV (cv2) : 이미지 처리 라이브러리
  - NumPy

## ✅ Main Features
### 과적 차량 탐지
- `Detectron2`를 사용하여 사전 학습된 `Faster R-CNN` 모델을 기반으로 과적 차량 탐지 모델을 구성하고 학습한다.
- 학습된 모델을 Validation Dataset으로 평가하여 COCO 메트릭(AP, AP50 등)을 측정하고 성능을 분석한다. 
### 과적 차량 텍스트(번호판) 추출
- 이미지의 차량이 과적 차량인지 판단하여, 과적 차량인 경우 `EasyOCR` 라이브러리를 사용해 이미지에서 텍스트(번호판)을 추출한다.
- 추출된 텍스트와 원본 이미지를 함께 시각화하여 결과를 확인한다.

## 📂 Project Structure
```
MyDrive/Data
ㄴ training         # 학습데이터
    ㄴ labeled      # 학습용 JSON 주석 파일
    ㄴ source       # 학습용 원본이미지
ㄴ validation       # 검증 데이터
    ㄴ labeled      # 검증용 JSON 주석 파일
    ㄴ source       # 검증용 원본이미지
ㄴ exported model   # Export된 최종 모델 가중치 및 설정 파일
    ㄴ model_final.pth
    ㄴ config.yaml
ㄴ overloaded_images # 과적차량으로 탐지된 이미지들 저장
```

## 💻 Architecture
이미지

## 📸 Result
페이지 이미지

## ⚖️ License
[Apache 2.0](License)

## Etc.
- 사용 데이터셋: [AI Hub 과적차량 도로 위험 데이터](https://aihub.or.kr/aihubdata/data/view.do?dataSetSn=530)
