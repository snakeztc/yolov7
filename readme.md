
<div align="center">

<img src="https://s4.ax1x.com/2022/02/01/Hk2dtP.png">

<h1>YOLOv7 - Framework Beyond Detection</h1>


[Documentation](https://github.com/jinfagang/yolov7) •
[Installation Instructions](https://github.com/jinfagang/yolov7) •
[Deployment](#deploy) •
[Contributing](.github/CONTRIBUTING.md) •
[Reporting Issues](https://github.com/jinfagang/yolov7/issues/new?assignees=&labels=&template=bug-report.yml)


[![PyPI - Python Version](https://img.shields.io/pypi/pyversions/yolort)](https://pypi.org/project/yolort/)
[![PyPI version](https://badge.fury.io/py/yolort.svg)](https://badge.fury.io/py/yolort)
[![PyPI downloads](https://static.pepy.tech/personalized-badge/alfred-py?period=total&units=international_system&left_color=grey&right_color=blue&left_text=pypi%20downloads)](https://pepy.tech/project/yolort)
[![Github downloads](https://img.shields.io/github/downloads/jinfagang/yolov7/total?color=blue&label=downloads&logo=github&logoColor=lightgrey)](https://img.shields.io/github/downloads/jinfagang/yolov7/total?color=blue&label=Downloads&logo=github&logoColor=lightgrey)

[![codecov](https://codecov.io/gh/zhiqwang/yolov5-rt-stack/branch/main/graph/badge.svg?token=1GX96EA72Y)](https://codecov.io/gh/zhiqwang/yolov5-rt-stack)
[![license](https://img.shields.io/github/license/zhiqwang/yolov5-rt-stack?color=dfd)](LICENSE)
[![Slack](https://img.shields.io/badge/slack-chat-aff.svg?logo=slack)](https://join.slack.com/t/yolort/shared_invite/zt-mqwc7235-940aAh8IaKYeWclrJx10SA)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-pink.svg)](https://github.com/jinfagang/yolov7/issues?q=is%3Aopen+is%3Aissue+label%3A%22help+wanted%22)


</div>


>  **`YOLO family variant with transformers!`**, Instance Segmentation in YOLO, DETR, AnchorDETR all supported!

update: we also provide a private version of yolov7, please visit: https://manaai.cn for more details. Our latest update will appear on mana first.

🔥🔥🔥 Just another yolo variant implemented based on **`detectron2`**. Be note that **YOLOv7 doesn't meant to be a successor of yolo family, 7 is just my magic and lucky number**. In our humble opinion, a good opensource project must have these features:

- It must be reproduceble;
- It must be simple and understandable;
- It must be build with the weapon of the edge;
- It must have a good maintainance, listen to the voice from community;

However, we found many opensource detection framework such as YOLOv5, Efficientdet have their own weakness, for example, YOLOv5 is very good at reproduceable but really over-engineered, too many messy codes. What's more surprisingly, there were at least 20+ different version of re-implementation of YOLOv3-YOLOv4 in pytorch, 99.99% of them were totally **wrong**, either can u train your dataset nor make it mAP comparable with origin paper.(However, *doesn't mean this work is totally right, use at your own risk*.)

That's why we have this project! It's much more simpler to experiment different ARCH of YOLO build upon detectron2 with YOLOv7! Most importantly, more and more decent YOLO series model merged into this repo such as YOLOX (most decent in 2021). We also **welcome any trick/experiment PR on YOLOv7, help us build it better and stronger!!**. Please **star it and fork it right now!**.

The supported matrix in YOLOv7 are:

- [x] YOLOv4 contained with CSP-Darknet53;
- [x] YOLOv7 arch with resnets backbone;
- [ ] YOLOv7 arch with resnet-vd backbone (likely as PP-YOLO), deformable conv, Mish etc;
- [x] GridMask augmentation from PP-YOLO included;
- [x] Mosiac transform supported with a custom datasetmapper;
- [x] YOLOv7 arch Swin-Transformer support (higher accuracy but lower speed);
- [ ] YOLOv7 arch Efficientnet + BiFPN;
- [ ] YOLOv5 style positive samples selection, new coordinates coding style;
- [x] RandomColorDistortion, RandomExpand, RandomCrop, RandomFlip;
- [x] CIoU loss (DIoU, GIoU) and label smoothing (from YOLOv5 & YOLOv4);
- [ ] YOLOF also included;
- [x] YOLOv7 Res2net + FPN supported;
- [x] Pyramid Vision Transformer v2 (PVTv2) supported;
- [ ] WBF (Weighted Box Fusion), this works better than NMS, [link](https://github.com/ZFTurbo/Weighted-Boxes-Fusion);
- [ ] YOLOX like head design and anchor design, also training support;
- [x] YOLOX s,m,l backbone and PAFPN added, we have a new combination of YOLOX backbone and pafpn;
- [x] YOLOv7 with Res2Net-v1d backbone, we **found res2net-v1d** have a better accuracy then darknet53;
- [x] Added PPYOLOv2 PAN neck with SPP and dropblock;
- [x] YOLOX arch added, now you can train YOLOX model (**anchor free yolo**) as well;
- [x] DETR: transformer based detection model and **onnx export supported, as well as TensorRT acceleration**;
- [x] AnchorDETR: Faster converge version of detr, now supported!

what's more, there are some features awesome inside repo:

- [x] Almost all models can export to onnx;
- [x] Supports TensorRT deployment for DETR and other transformer models;
- [ ] It will integrate with [wanwu](https://github.com/jinfagang/wanwu_release), a torch-free deploy framework run fastest on your target platform.


**Help wanted!** If you have spare time or if you have GPU card, then help YOLOv7 become more stronger! Here is the guidance of contribute:

1. **`Claim task`**: I have some ideas but do not have enough time to do it, if you want implement it, claim the task, **I will give u fully advise on how to do, and you can learn a lot from it**;
2. **`Test mAP`**: When you finished new idea implementation, create a thread to report experiment mAP, if it work, then merge into our main master branch;
3. **`Pull request`**: YOLOv7 is open and always tracking on SOTA and **light** models, if a model is useful, we will merge it and deploy it, distribute to all users want to try.

Here are some tasks need to be claimed:

- [ ] VAN: Visual Attention Network, [paper](https://arxiv.org/abs/2202.09741), [VAN-Segmentation](https://github.com/Visual-Attention-Network/VAN-Segmentation), it was better than Swin and PVT and DeiT:
  - [ ] D2 VAN backbone integration;
  - [ ] Test with YOLOv7 arch;
- [ ] ViDet: [code](https://github.com/naver-ai/vidt), this provides a realtime detector based on transformer, Swin-Nano mAP: 40, while 20 FPS, it can be integrated into YOLOv7;
  - [ ] Integrate into D2 backbone, remove MSAtten deps;
  - [ ] Test with YOLOv7 or DETR arch;
- [ ] DINO: 63.3mAP highest in 2022 on coco. https://github.com/IDEACVR/DINO
  - [ ] waiting for DINO opensource code.
- [ ] ConvNext: https://github.com/facebookresearch/ConvNeXt, combined convolution and transformer.



## 💁‍♂️ Results

| YOLOv7 Instance             |  Face & Detection |
:-------------------------:|:-------------------------:
![](https://z3.ax1x.com/2021/09/08/hHPhUx.png)  |  ![](https://z3.ax1x.com/2021/07/19/WGVhlj.png)
![](https://z3.ax1x.com/2021/09/08/hHP7xe.png)  |  ![](https://z3.ax1x.com/2021/07/22/WDr5V0.png)
![](https://s1.ax1x.com/2022/03/25/qN5zp6.png)  |  ![](https://s2.loli.net/2022/03/25/MBwq9YT7zC5Sd1A.png)


## 🆕 News!

- **2022.04.15**: Now, we support the `SparseInst` onnx expport!
- **2022.03.25**: New instance seg supported! 40 FPS @ 37 mAP!! Which is fast;
- **2021.09.16**: First transformer based DETR model added, will explore more DETR series models;
- **2021.08.02**: **YOLOX** arch added, you can train YOLOX as well in this repo;
- **2021.07.25**: We found **YOLOv7-Res2net50** beat res50 and darknet53 at same speed level! 5% AP boost on custom dataset;
- **2021.07.04**: Added YOLOF and we can have a anchor free support as well, YOLOF achieves a better trade off on speed and accuracy;
- **2021.06.25**: this project first started.
- more


## 🧑‍🦯 Installation && Quick Start

- See [docs/install.md](docs/install.md)



## 🤔 Features

Some highlights of YOLOv7 are:

- A simple and standard training framework for any detection && instance segmentation tasks, based on detectron2;
- Supports DETR and many transformer based detection framework out-of-box;
- Supports easy to deploy pipeline thought onnx.
- **This is the only framework support YOLOv4 + InstanceSegmentation** in single stage style;
- Easily plugin into transformers based detector;

We are strongly recommend you send PR if you have any further development on this project, **the only reason for opensource it is just for using community power to make it stronger and further**. It's very welcome for anyone contribute on any features!

## 🧙‍♂️ Pretrained Models

| model | backbone | input | aug | AP<sup>val</sup> |  AP  | FPS | weights |
| :---- | :------  | :---: | :-: |:--------------: | :--: | :-: | :-----: |
| [SparseInst](configs/sparse_inst_r50_base.yaml) | [R-50]() | 640 | &#x2718; | 32.8 | - | 44.3 | [model](https://drive.google.com/file/d/12RQLHD5EZKIOvlqW3avUCeYjFG1NPKDy/view?usp=sharing) |
| [SparseInst](sparse_inst_r50vd_base.yaml) | [R-50-vd](https://github.com/rwightman/pytorch-image-models/releases/download/v0.1-weights/resnet50d_ra2-464e36ba.pth) | 640 | &#x2718; | 34.1 | - | 42.6 | [model]()|
| [SparseInst (G-IAM)](configs/sparse_inst_r50_giam.yaml) | [R-50]() | 608 | &#x2718; | 33.4 | - | 44.6 | [model](https://drive.google.com/file/d/1pXU7Dsa1L7nUiLU9ULG2F6Pl5m5NEguL/view?usp=sharing) |
| [SparseInst (G-IAM)](configs/sparse_inst_r50_giam_aug.yaml) | [R-50]() | 608 | &#10003; | 34.2 | 34.7 | 44.6 | [model](https://drive.google.com/file/d/1MK8rO3qtA7vN9KVSBdp0VvZHCNq8-bvz/view?usp=sharing) |
| [SparseInst (G-IAM)](configs/sparse_inst_r50_dcn_giam_aug.yaml) | [R-50-DCN]() | 608 | &#10003;| 36.4 | 36.8 | 41.6 | [model](https://drive.google.com/file/d/1qxdLRRHbIWEwRYn-NPPeCCk6fhBjc946/view?usp=sharing) |
| [SparseInst (G-IAM)](configs/sparse_inst_r50vd_giam_aug.yaml) | [R-50-vd](https://github.com/rwightman/pytorch-image-models/releases/download/v0.1-weights/resnet50d_ra2-464e36ba.pth) | 608 | &#10003;| 35.6 | 36.1 | 42.8| [model](https://drive.google.com/file/d/1dlamg7ych_BdWpPUCuiBXbwE0SXpsfGx/view?usp=sharing) |
| [SparseInst (G-IAM)](configs/sparse_inst_r50vd_dcn_giam_aug.yaml) | [R-50-vd-DCN](https://github.com/rwightman/pytorch-image-models/releases/download/v0.1-weights/resnet50d_ra2-464e36ba.pth) | 608 | &#10003; | 37.4 | 37.9 | 40.0  | [model](https://drive.google.com/file/d/1clYPdCNrDNZLbmlAEJ7wjsrOLn1igOpT/view?usp=sharing)|
| [SparseInst (G-IAM)](sparse_inst_r50vd_dcn_giam_aug.yaml) | [R-50-vd-DCN](https://github.com/rwightman/pytorch-image-models/releases/download/v0.1-weights/resnet50d_ra2-464e36ba.pth) | 640 | &#10003; | 37.7 | 38.1 | 39.3 |  [model](https://drive.google.com/file/d/1clYPdCNrDNZLbmlAEJ7wjsrOLn1igOpT/view?usp=sharing)| 


## 🥰 Demo

Run a quick demo would be like:

```
python3 demo.py --config-file configs/wearmask/darknet53.yaml --input ./datasets/wearmask/images/val2017 --opts MODEL.WEIGHTS output/model_0009999.pth
```

Run SparseInst:

```
python demo.py --config-file configs/coco/sparseinst/sparse_inst_r50vd_giam_aug.yaml --video-input ~/Movies/Videos/86277963_nb2-1-80.flv -c 0.4 --opts MODEL.WEIGHTS weights/sparse_inst_r50vd_giam_aug_8bc5b3.pth
```

**an update based on detectron2 newly introduced LazyConfig system, run with a LazyConfig model using**:

```
python3 demo_lazyconfig.py --config-file configs/new_baselines/panoptic_fpn_regnetx_0.4g.py --opts train.init_checkpoint=output/model_0004999.pth
```

## 😎 Train

For training, quite simple, same as detectron2:

```
python train_net.py --config-file configs/coco/darknet53.yaml --num-gpus 8
```

If you want train YOLOX, you can using config file `configs/coco/yolox_s.yaml`. All support arch are:

- **YOLOX**: anchor free yolo;
- **YOLOv7**: traditional yolo with some explorations, mainly focus on loss experiments;
- **YOLOv7P**: traditional yolo merged with decent arch from YOLOX;
- **YOLOMask**: arch do detection and segmentation at the same time (tbd);
- **YOLOInsSeg**: instance segmentation based on YOLO detection (tbd);


## 😎 Rules

There are some rules you must follow to if you want train on your own dataset:

- Rule No.1: Always set your own anchors on your dataset, using `tools/compute_anchors.py`, this applys to any other anchor-based detection methods as well (EfficientDet etc.);
- Rule No.2: Keep a faith on your loss will goes down eventually, if not, dig deeper to find out why (but do not post issues repeated caused I might don't know either.).
- Rule No.3: No one will tells u but it's real: *do not change backbone easily, whole params coupled with your backbone, dont think its simple as you think it should be*, also a Deeplearning engineer **is not an easy work as you think**, the whole knowledge like an ocean, and your knowledge is just a tiny drop of water...
- Rule No.4: **must** using pretrain weights for **transoformer based backbone**, otherwise your loss will bump;

Make sure you have read **rules** before ask me any questions.


## 🔨 Export ONNX && TensorRTT && TVM

1. `detr`:

  ```
  python export_onnx.py --config-file detr/config/file
  ```

  this works has been done, inference script included inside `tools`.

2. `AnchorDETR`:

  anchorDETR also supported training and exporting to ONNX.

3. `SparseInst`:
   Sparsinst already supported exporting to onnx!!

  ```
  python export_onnx.py --config-file configs/coco/sparseinst/sparse_inst_r50_giam_aug.yaml --video-input ~/Videos/a.flv  --opts MODEL.WEIGHTS weights/sparse_inst_r50_giam_aug_2b7d68.pth INPUT.MIN_SIZE_TEST 512
  ```
  Then you can have `weights/sparse_inst_r50_giam_aug_2b7d68_sim.onnx` generated, this onnx can be inference using ORT without any unsupported ops.



## 🤒️ Performance

Here is a dedicated performance compare with other packages. 

tbd.



## 🪜 Some Tiny Object Datasets supported

- **Wearmask**:
  support VOC, Yolo, coco 3 format. You can using coco format here. Download from: 链接: https://pan.baidu.com/s/1ozAgUFLqfTXLp-iOecddqQ 提取码: xgep . Using `configs/wearmask` to train this dataset.
- **more**:
  to go.



## 👋 Detection Results

![](https://z3.ax1x.com/2021/07/22/WDs9PO.png)
![](https://z3.ax1x.com/2021/07/22/WDr5V0.png)
![](https://z3.ax1x.com/2021/07/19/WGVhlj.png)
![](https://z3.ax1x.com/2021/07/26/WWBxi9.png)



## 😯 Dicussion Group

| Wechat             |  QQ |
:-------------------------:|:-------------------------:
![image.png](https://s2.loli.net/2022/03/14/9uxaEnDA6vdByr2.png)  |  ![image.png](https://s2.loli.net/2022/02/28/C4gjf6DcwdHvnO8.png)

* if wechat expired, please contact me update via github issue. group for general discussion, not only for yolov7.

## 🀄️ Some Exp Visualizations

1. GridMask

   ![](https://z3.ax1x.com/2021/06/27/RYeJkd.png)
   ![](https://z3.ax1x.com/2021/07/06/Roj5dg.png)

   Our GridMask augmentation also supports 2 modes.



2. Mosaic

   ![](https://z3.ax1x.com/2021/07/06/RIX1iR.png)
   ![](https://z3.ax1x.com/2021/07/06/Roq97d.png)

   Our Mosaic support any size and any any image numbers!

   **new**:
   we merged another mosiac implementation from YOLOX, this version will do random pespective:

   ![](https://z3.ax1x.com/2021/08/06/futTte.png)
   ![](https://z3.ax1x.com/2021/08/06/futv0f.png)
   ![](https://z3.ax1x.com/2021/08/07/fKEPvd.png)





## ©️ License

Code released under GPL license. Please pull request to this source repo before you make your changes public or commercial usage. All rights reserved by Lucas Jin.

