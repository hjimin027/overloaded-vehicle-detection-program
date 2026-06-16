# Overloaded Vehicle Detection Program
![Google Colab](https://img.shields.io/badge/Google%20Colab-%23F9A825.svg?style=for-the-badge&logo=googlecolab&logoColor=white)
![Google Drive](https://img.shields.io/badge/Google%20Drive-4285F4?style=for-the-badge&logo=googledrive&logoColor=white)

> An overloaded vehicle detection and information extraction program utilizing Detectron2 and OCR technology

## Description
Overloading refers to the illegal act of loading cargo onto a truck exceeding its regulated load weight or volume capacity.

The Ministry of Land, Infrastructure and Transport (MOLIT) (South Korea) classifies and controls overloaded vehicles based on excess weight, excess length, or subjective judgment criteria. 
However, in most cases, enforcement is carried out by police officers who manually spot and penalize these vehicles. <br>This method is inefficient in terms of time and poses a risk of traffic accidents for the officers involved.

In February 2024, a total of 1,064 crackdowns on improperly loaded or overloaded trucks were conducted, an 82.6% increase compared to the enforcement performance in March and April of the previous year. Accordingly, there is a recognized need for a program that can automate the enforcement of overloaded freight vehicles. 

Among the various criteria for overloaded vehicles, this project strictly focuses on the load volume and length criteria that can be visually identified through images. 

Using the Detectron2 model, the program precisely classifies and detects 'normal vehicles' and 'overloaded vehicles (improperly loaded)' from images. The detected images of overloaded vehicles are automatically filtered and saved, and it provides an automated management feature by extracting the license plate information attached to the vehicle using EasyOCR.

## 🗓️ Period
2024-05-15 ~ 2024-06-21 (5 weeks)

## 👥 Members
- **Hyunmin Jang**: GitHub Management, EasyOCR model integration 
- **Yunwoo Lee**: Detectron2 model training and performance improvement 
- **Jimin Hwang**: Detectron2 model training and performance improvement, Standalone app development

## ⚙️ Getting Started
1. Install Anaconda and PyTorch. 
2. Download the [Training data and Test data from Google Drive](https://drive.google.com/drive/folders/1sjEpVfYICoc9p9XbG2-4ivKQwat6e4cv?usp=drive_link). 
3. Download the [latest version code file in the detect_overload directory](detect_overload/version_7.0/overload_final.ipynb). 

Alternatively, you can run it via the following Colab link. 

[Colab Link (Click)](https://colab.research.google.com/drive/1g4uhNQ6se0aSSStaDk7MauDgI8h3grGb?usp=sharing)
## 🛠️ Tech Stack
- Language: Python 
- Frameworks : 
	- PyTorch: Base for Detectron2 and EasyOCR 
	- Detectron2: Object detection framework 
- Libraries : 
	- EasyOCR: Image text extraction (OCR) library 
	- OpenCV (cv2): Image processing library 
	- NumPy
## ✅ Main Features
### 1. Overloaded Vehicle Detection 
* Developed and trained a custom object detection model utilizing the pre-trained `Faster R-CNN` architecture via the `Detectron2` framework. 
* Evaluated model performance using a dedicated Validation Dataset, analyzing standard COCO metrics (e.g., AP, AP50) to ensure high detection accuracy. 
### 2. Automated License Plate Extraction (OCR) 
* Implemented a filtering pipeline that identifies overloaded vehicles and triggers the `EasyOCR` library to extract license plate text from the specific regions of interest. 
* Generated visual outputs combining the original images, bounding boxes, and extracted text for reliable verification and record-keeping.

## 📂 Project Structure
```
MyDrive/Data/ 
├── training/ # Training dataset 
│   ├── labeled/ # JSON annotation files 
│   └── source/ # Original training images 
├── validation/ # Validation dataset 
│   ├── labeled/ # JSON annotation files 
│   └── source/ # Original validation images 
├── exported_model/ # Final model weights and configurations 
│   ├── model_final.pth 
│   └── config.yaml 
└── overloaded_images/ # Output directory for detected overloaded vehicles
```

## 💻 Architecture
<img width="1002" height="459" alt="Overloaded_EN drawio" src="https://github.com/user-attachments/assets/e69611fd-b1a0-4f94-9f5d-8114c4c0b4d0" />

## 📸 Result
<img width="1662" height="385" alt="image" src="https://github.com/user-attachments/assets/ee32cd7e-3fb1-41d0-aaaa-95674f48684f" />
Result for Detecting overloaded vehicles: AP 75.031

<img width="720" alt="image" src="https://github.com/user-attachments/assets/10057632-11d8-414e-b77e-095f5a0c656d" />
<img width="720" alt="image" src="https://github.com/user-attachments/assets/3b1cdecb-a348-4d51-a75b-d4662ae8c698" />

## ⚖️ License
[Apache 2.0](License)

## Etc.
- Dataset Used : [AI Hub - 과적차량 도로 위험 데이터](https://aihub.or.kr/aihubdata/data/view.do?dataSetSn=530)
