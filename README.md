# SOICT_HACKATHON2024_Track1


## Team: UET NextGen  
### mAP@50: 0.9017

### Team Members:
  - [Nguyễn Bá Thịnh](https://www.facebook.com/profile.php?id=61559925006655)
  - [Nguyễn Quang Huy](https://www.facebook.com/hmon2k4)
  - [Đỗ Trí Dũng](https://www.facebook.com/dtdungggggggg)
    


---

## 1. Training: 
Hãy thực hiện các bước sau để train mô hình:
### Download Dataset
```
soict2024_hackathon(Yolo format): !gdown https://drive.google.com/uc?id=147erElYLdhHiH49fu2iz-5T3M3gegFaJ
co_dino_5scale_swin_large_22e_o365.pth: !gdown https://drive.google.com/uc?id=1U6Mexf23-VzebMY7LL87C29Zi0Eapdtg
```

## Prepare dataset
Sử dụng utils/cvtCocoFormat.py để convert YOLO format sang COCO format.
```
data
└── soict2024_hackathon
    ├── train_img
    │   ├── cam_01_00001.jpg
    │   ├── cam_01_00001_aug.jpg
    │   └── ...
    ├── train.json
    ├── test_img
    ├── test.json  
```

 Kiểm tra thư mục Co-DETR/models:
 ```
models
└── co_dino_5scale_swin_large_22e_o365.pth
```
Mở file `Dockerfile` và chắc chắn dòng lệnh sau đã được cấu hình:
  ```bash
  CMD bash train.sh && tail -f /dev/null
  ```
Tiến hành training:
```
cd sources/Co-DETR
docker compose up --build 
```
## 2. Inference: 
### Download Checkpoints
```
Epoch 2: !gdown https://drive.google.com/uc?id=1--elr04W-ktPi3FuHERJ_L545QifUaqT
Epoch 6: !gdown https://drive.google.com/uc?id=1-B533mVm6WUt5Bdcfjtinm8V__KbjSLu
Epoch 8: !gdown https://drive.google.com/uc?id=1-C_exQbO-yrYtM2L5yDVI2rKW248mpe7
Epoch 10: !gdown https://drive.google.com/uc?id=1-FtEs4eIpHV5O30Vl8-vzXt30JztPql6
Epoch 8_night: !gdown https://drive.google.com/uc?id=108S8b_CUn75MbLPz-BtCdJYeaX5xSJ3r
Epoch 12_day: gdown https://drive.google.com/uc?id=1Kwnqnk2IN-fmDDhU7Q5qIp3t6RxonSRu
```
 - Checkpoints đặt tại Co-DETR/nextgen
``` 
Co-DETR
└── nextgen
    ├── epoch_2.pth
    ├── ...
    ├── epoch_8_night.pth
    ├── epoch_12_day.pth
```
 - Public test đặt tại Co-DETR/test_data
``` 
Co-DETR
└── test_data
    ├── public test
    │   ├── cam_08_00500_jpg.rf.5ab59b5bcda1d1fad9131385c5d64fdb.jpg
```

Mở file `Dockerfile` và sửa dòng lệnh CMD như sau:
  ```bash
  CMD bash infer.sh && tail -f /dev/null
  ```
Kiểm tra đường dẫn tại: infer.py
Tiến hành inference:
```
cd sources/Co-DETR
docker compose up --build 
```
