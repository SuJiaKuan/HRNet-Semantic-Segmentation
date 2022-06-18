# Defects Segmentation by HRNet

The repository is based on [HRNets for Semantic Segmentation (PyTorch version)](https://github.com/HRNet/HRNet-Semantic-Segmentation/tree/pytorch-v1.1), to support defects segmentation.

## Prerequisites

You need a computer with Nvidia GPU and you already installed:
- Ubuntu 18.04 or Ubuntu 20.04
- Pyhton 3
- Anaconda or Miniconda

## Installation

* Create a conda environment `hrnet`.

```bash
conda create -n hrnet
```

* Activate the envrionment.

```bash
conda activate hrnet
```

* Install PyTroch related packages.

```bash
conda install pytorch==1.1.0 torchvision==0.3.0 cudatoolkit=10.0 -c pytorch
```

* Install other packages.

```bash
pip3 install -r requirements.txt
```

* Create folders: `pretrained_models` and `datasets`.

```bash
mkdir -p pretrained_models datasets
```

* Download the pretrained model: [hrnet_w18_small_model_v2.pth](https://1drv.ms/u/s!Aus8VCZ_C_33gRv2PI1vjJyn2g7G?e=i8Rdzx), and put it under folder `pretrained_models` (i.e., its path should be `pretrained_models/hrnet_w18_small_model_v2.pth`).

* Put your [generated dataset](https://github.com/SuJiaKuan/defects_segmentation_tools) under `datasets` with folder name `defects_segmentation` (i.e., its path should be `datasets/defects_segmentation`).

## Training and Testing

* Run the training script. You will get results on directory `output/cityscapes/defects_segmentation` after training.

```bash
python3 tools/train.py --cfg experiments/cityscapes/defects_segmentation.yaml
```

* Run the testing script. You will get results (images about detected defects) on directory `output/cityscapes/defects_segmentation/test_results` after training.

```bash
python3 tools/test.py --cfg experiments/cityscapes/defects_segmentation.yaml DATASET.TEST_SET list/test.lst TEST.MODEL_FILE output/cityscapes/defects_segmentation/best.pth TEST.SCALE_LIST 0.5,0.75,1.0,1.25,1.5,1.75 TEST.FLIP_TEST True
```
