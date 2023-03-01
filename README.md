# Construction_Site_Safety_Equipment_Wear_Recognition_Project
- 프로젝트 개요
  공사 현장 안전 장비 미착용으로 인한 사고 방지 (스마트 안전 통합 관제 시스템)
 
- 프로젝트 계획
  1. 데이터 다운로드 및 데이터 선택
  2. 이미지 검수 및 이미지 제거 또는 CVAT로 수정작업
  3. yolov5모델을 선택하여 training
  4. pyqt5로 GUI, 추가 기능 구현


- 데이터 구축
  AI hub 공사현장 데이터 기반\
  추가 데이터 roboflow
  
  |class|
  |--------|
  0 Safety_Belt_Used\
  1 Safety_Belt_Unused\
  2 Safety_Shoes_Used\
  3 Safety_Shoes_Unused\
  4 Safety_Helmet_Used\
  5 Safety_Helmet_Unused\
  6 person
  
  ||Dataset||
  |-----|--------|-------|
  |Train| Images | 11,495|
  |     | Labels | 11,495|
  |Valid| Images | 1,437|
  |     | Labels | 1,437|
  |Test | Images | 1,440|
  |     | Labels | 1,440|
  
  |bounding box|
  |-----|------|
  |Train|84,323|
  |Valid|11,680|
  |Test | 9,189|
  
  |Model|hyperparmeter|Batch size|epochs|optimizer|MAP 0.5|mAP 0.5 - 0.95|
  |-----|---|----------|------|---------|-------|--------------|
  |yolov5n|Hyp.scratch-low|16|100|SGD|0.83782|0.49619|
  |yolov5l|Hyp.scratch-high|16|30|SGD|0.8715|0.55632|
  |yolov5x|Hyp.scratch-high|16|60|SGD|0.88726|0.57239|
  |yolov5m|Hyp.scratch-low|32|100|SGD|0.88586|0.5667|
  
  ![Screenshot 2023-03-02 at 12 33 50 AM](https://user-images.githubusercontent.com/107936957/222186780-7eaa615a-b404-428c-ad21-eedfb6f68353.png)
  ![Screenshot 2023-03-02 at 12 34 24 AM](https://user-images.githubusercontent.com/107936957/222186942-e73b7f20-ebfb-468f-8c75-1744952b7f12.png)

- 구현 기능
1. Person 객체 내에서 다른 장구류 객체 탐색 (사람의 장구류 착용여부 체크)
    - Person 바운딩박스 안에 다른 객체의 중심값이 들어가는지 확인
2.  인식하고 싶은 객체 체크 기능 (프로그램 사용자가 작업장에 맞는 장구류 착용여부 선택)

3.  일정 시간 이상 화면 내 미착용 검출 시, 이메일 알림 서비스
![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/60f6e7ea-dcf8-440f-b34f-ac2a6d9a8681/Untitled.png)
- 개선 사항
