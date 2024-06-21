# OpenSourceProgramming final project
---
## 시각 장애인을 위한 보행 안내서비스, 시야
object detection deeplearning model인 YOLO(You Only Look Once) version 8을 사용하여 시각장애인이 보행 중 위협 요소가 되는 각종 장애물을 피할 수 있도록 돕는 Android 기반 애플리케이션입니다.
---
## 목차
+ 프로젝트 소개
+ 프로그램 설명
+ YOLOv8을 활용한 모델과 UI 설명
+ 활용 방법 설명(각 소스 코드 파일 설명)
+ 한계점과 보안
---
## 프로젝트 소개
+ 숙명여자대학교 IT공학전공(현 인공지능공학부) 오픈소스프로그래밍 수업의 기말 팀 프로젝트
+ 팀원: 김민지, 김진솔, 박세희
+ 개발 기간: 2024.05.19 ~ 2024.06.20
+ 주요 기능: 장애물 인식 후 TTS 및 진동으로 회피 방향 안내(단, 진동 모드는 화면 왼쪽을 터치하려 ON 시켜야 햐며, 진동 모드 ON시 TTS와 함께 진동 1번(왼쪽 회피)/2번(오른쪽 회피) 울림)
+ 사용 툴: Android Studio Jellyfish, Colab, GitHub
+ 설치 및 실행 방법: Android Sudio를 설치하고 Code-clone한 후 Front-end/AndroidProject를 실행합니다. 안드로이드 기반 스마트폰의 설정-휴대전화 정보-소프트웨어 정보에서 빌드 번호 5번을 누르면 개발자 옵션이 생기는데, 이 옵션에서 USB 디버깅을 켜고 휴대폰과 컴퓨터를 USB 선으로 연결합니다. Android Studio에서 run을 누르면 휴대폰에서 앱이 실행됩니다.
+ 라이선스: MIT license
---
## YOLOv8을 활용한 모델과 UI 설명
1. YOLOv8 모델
   - YOLOv8은 2023년 1월 발표된 버전으로, 현재 YOLOv10까지 발표되었으나 자료가 풍부한 YOLOv8을 채택했습니다. (2024.06.21 기준)
   - YOLO는 실시간 객체 검출 알고리즘으로, 객체 검출을 단 한번의 순전파만으로 수행하는 효율적인 방법입니다.
   - AI-Hub의 인도보행 영상 Bounding Box 데이터셋을 활용해 모델을 훈련시켰습니다.(데이터셋 링크: https://www.aihub.or.kr/aihubdata/data/view.do?currMenu=&topMenu=&aihubDataSe=data&dataSetSn=189)
   - 데이터를 저장햘 용량 문제와 GPU 문제로 약 4000개의 데이터밖에 활용 못했지만, 성능 향상을 위해 훨씬 더 많은 데이터를 사용할 것을 권장드립니다.
   - YOLOv8 CLI를 통해 모델을 train, validation, test 하였습니다.
2. UI
   - 화면 상단의 좌측에는 진동 모드 ON/OFF 버튼, 우측에는 종료 버튼을 배치했습니다.
   - 사용자가 시각장애인임을 고려하여 꼭 버튼이 아니더라도 화면 왼쪽/오른쪽만 터치해도 버튼 기능이 작동하도록 하였습니다.
   - 애플리케이션이 잘 실행되는지 확인하기 위해 화면 중앙에 카메라 화면을 띄웠습니다.
   - 음성과 함꼐 팝업창으로 위험요소 회피 문구 안내하도록 했습니다. (팝업창은 애플리케이션이 잘 실행되는지 확인하기 위해 띄움)
---
## 활용 방법 설명(각 소스 코드 파일 설명)
1. YOLOv8 폴더 설명
   - Colab의 GPU와 Google Drive을 사용해 YOLOv8 모델을 학습시켰습니다.
   - xmlToyolo.ipynb 파일

     XML 형식의 라벨링 format을 YOLO format으로 변경해 저장하는 소스코드입니다.
     
   - checkData.ipynb
   - data.yaml
   - yolov8.ipynb


