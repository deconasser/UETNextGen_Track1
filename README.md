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
## Prepare dataset
```
data
└── soict2024_hackathon
    ├── train_img
    │   ├── cam_01_00001.jpg
    │   ├── cam_01_00001_aug.jpg
    │   └── ...
    ├── train.json
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
 - Checkpoints được lưu tại Co-DETR/nextgen
 - Public test được lưu tại Co-DETR/test_data

Mở file `Dockerfile` và sửa dòng lệnh CMD như sau:
  ```bash
  CMD bash infer.sh && tail -f /dev/null
  ```
Tiến hành inference:
```
cd sources/Co-DETR
docker compose up --build 
```
