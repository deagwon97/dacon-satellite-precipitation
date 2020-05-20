# 2020_dacon_satellite_precipitation
Dacon AI프렌즈 시즌2 위성관측 활용 강수량 산출 대회 준비를 위한 repository  
Branch naming rule - 전처리-기법/모델

## Dacon_satellite_baseline.ipynb
- LB 1.59
- Standard scale on sensor data
- Land type: [ocean, inland water, coastal, land] = [0, 0.3, 0.7, 1.0]
- GMI 강수량 보정 (가까운 점 2개)
- DPR 강수량 보정 (가까운 점 2개)
- Augmentation 8개로 한 다음, (3, 3, 3)으로 나누어서 3개 모델 앙상블
- GoldBar님 ResNet 모델
- No learning rate scheduler
- Early stopping patience=4
