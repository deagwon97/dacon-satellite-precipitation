# 2020_dacon_satellite_precipitation
Dacon AI프렌즈 시즌2 위성관측 활용 강수량 산출 대회 준비를 위한 repository  

## 1. 학습한 모델
<학습모델이름_학습기(gpu, tpu)_프레임워크(tensorflow, pytorch).ipynb>
1. model_baseline_gpu_tf.ipynb
    - LB 1.59
    - Standard scale on sensor data
    - Land type: [ocean, inland water, coastal, land] = [0, 0.3, 0.7, 1.0]
    - GMI 강수량 보정 (가까운 점 2개)
    - DPR 강수량 보정 (가까운 점 2개)
    - Augmentation 8개로 한 다음, (3, 3, 3)으로 나누어서 3개 모델 앙상블
    - GoldBar님 ResNet 모델
    - No learning rate scheduler
    - Early stopping patience=4
2. ResNet_rot_transpose_cutmix_tpu_tf.ipynb
    - LB ??
    - Standard scale on sensor data
    - Land type: [ocean, inland water, coastal, land] = [0, 0.3, 0.7, 1.0]
    - GMI 강수량 보정 (가까운 점 2개)
    - DPR 강수량 보정 (가까운 점 2개)
    - Augmentation
        - 위/아래, transpose, 90도, 180도, 270도 회전 => 8배
        - cut_mix 기법으로 2배
        - 데이터를 총 16배로 증가
        - tf.Dataset을 이용하여 배치학습
    - GoldBar님 ResNet 모델
    - No learning rate scheduler
    - Early stopping x
3. ResNet_tpu_tf.ipynb
4. Unet_tpu_pytorch.ipynb
5. 

## 2. gmi_preci_generator.ipynb
## 3. EDA.ipynb
    I. 데이터 및 라이브러리 준비
        1. 필요한 라이브러리 import
        2. 데이터를 읽어서 하나의 train.numpy만들기

    II. [ land type, 위도, 경도 ] EDA
        1. [ land type, 위도, 경도 ]의 Distribution 조사
        2. Precipication(Target)과 [ land type, 위도, 경도 ] 사이의 관계 조사
            i) train_numeric 생성  
            ii) Precipitation vs GMI_latitude  
            iii) Precipitation vs GMI_longitude  
            iv) Precipitation vs Land type  

    III. 센서 데이터 EDA
        1. 센서 데이터의 Distribution 조사
        2. Precipication(Target)과 센서 데이터 사이의 관계 조사
        3. Basemap을 활용하여 센서 데이터를 지도위에 plotting  
            i) 센서 데이터 지도위에 plotting    
            ii) Precipication 데이터 지도위에 plotting    
        4. 이상치 데이터를 지도위에 plotting

    IV. 시간 데이터 EDA 및 전처리
        1. orbit 정보를 가공하여 시간 데이터 추출  
            i) orbit 정보를 가공하여 train_orbit, test_orbit 생성  
            ii) train_orbit으로 연도, 월, 날짜, 시간 데이터 추출  
        2. 시간 데이터를 활용한 EDA  
            i) Month, Day, Time vs CH  
                1) Month vs CH  
                2) May vs CH  
                3) Time vs CH  

            ii) Month(Day), Time vs Precipication  
                1) Month(Day) vs Precipication    
                2) Time vs Precipication  

        3. 훈련에 사용하기위해 시간 데이터를 삼각함수 형태로 변환
        4. 40,40,2 사이즈로 days와 times 만들기 

    V. 영역별 EDA와 Normalization
        1. Noramlization을 위한 EDA
        2. Normalization
