# 2020_dacon_satellite_precipitation
Dacon AI프렌즈 시즌2 위성관측 활용 강수량 산출 대회 준비를 위한 repository  

## model_baseline_gpu_tf.ipynb
- LB 1.59
- Standard scale on sensor data
- Land type: [ocean, inland water, coastal, land] = [0, 0.3, 0.7, 1.0]
- GMI 강수량 보정 (가까운 점 2개)
- DPR 강수량 보정 (가까운 점 2개)
- Augmentation 8개로 한 다음, (3, 3, 3)으로 나누어서 3개 모델 앙상블
- GoldBar님 ResNet 모델
- No learning rate scheduler
- Early stopping patience=4


## 파일 종류
- 학습모델이름_학습기(gpu, tpu)_프레임워크(tensorflow, pytorch).ipynb
    1. model_baseline_gpu_tf.ipynb
    2. ResNet_rot_transpose_cutmix_tpu_tf.ipynb
    3. ResNet_tpu_tf.ipynb
    4. Unet_tpu_pytorch.ipynb
    5. 

- EDA.ipynb
- gmi_preci_generator.ipynb
