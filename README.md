# 🤔 Learning from Pattern Completion: Self-supervised Controllable Generation

Inspired by the cortical modularization and hippocampal pattern completion, we propose a self-supervised controllable generation (**SCG**) framework to achieve pattern completion and generate images.

[![Project Page](https://img.shields.io/badge/Project-Page-Green.svg)](https://qizekun.github.io/shapellm/)
[![Paper PDF](https://img.shields.io/badge/Paper-PDF-orange.svg)](https://arxiv.org/abs/2402.17766)
[![Code License](https://img.shields.io/badge/Code%20License-Apache_2.0-green.svg)](https://github.com/tatsu-lab/stanford_alpaca/blob/main/LICENSE)
[![Data License](https://img.shields.io/badge/Data%20License-CC%20By%20NC%204.0-red.svg)](https://github.com/tatsu-lab/stanford_alpaca/blob/main/DATA_LICENSE)

![img](docs/intro.png)

## News

- 🍾 Sep, 2024: [**SCG**](https://qizekun.github.io/shapellm/) is accepted by NeurIPS 2024, congratulations! We will release offical version as soon, please check in homepage.
- 🎉 Apr, 2024: For those interested, we update a [pre-release code](https://gitee.com/chenzq/control-net-main) in Gitee.


## 📄 Intro

Our model is built upon our trained modular Hypercolumn-like features and ControlNet. The hypercolumn-like features are trained using a self-supervised method. Based on these features, we train several ControlNets. This approach utilizes a comprehensive modular feature set that is automatically learned and differentiated, resulting in robustness and generalization transfer capabilities. By configuring and combining appropriate control modules, it can effectively transfer to features without prior learning. We exclusively train them on the COCO dataset, yet they demonstrate the ability to generalize across various image styles, including those generated from ancient rock paintings, Chinese monochromes, oil paintings, scribbles, and more. Notably, it maintains strong performance even when dealing with lower-quality ancient rock paintings and oil paintings. 

## 🛠️ Installation

Cause our work is based on ControlNet, please refer to [ControlNet Docs](https://github.com/lllyasviel/ControlNet?tab=readme-ov-file#production-ready-pretrained-models) to install environment.


## 🚀 Quickstart

```python
python tutorial_train.py
```

## 🔧 Setting

You can modify model and dataset in `tutorial_train.py`:
```python
modelarch_path = './models/cldm_v15.yaml'
resume_path = './image_log/checkpoint_deconv_down2_3/last.ckpt'
logger_path = 'shuimo_deconv2_3_test'
dataset_name = 'MyDatasetShuimo'
```

To select different hypercolumn, refer to `./models/cldm_v15.yaml`:
```yaml
hyperconfig:
  target: cldm.cldm.HyperColumnLGN
  params: 
    hypercond: [0]
    size: 512
```

## 🖼️ Results

**To find more result, please refer to our papers.**

The first line are the origin image and the prompt. The second line are conditions of multiple hypercolumn and canny. The last line are the generated images

![img](docs/hc.png)

### Specific hypercolumn

#### Hypercolumn 0
![img](docs/img0.png)

#### Hypercolumn 1
![img](docs/img1.png)

#### Hypercolumn 2
![img](docs/img2.png)

#### Hypercolumn 3
![img](docs/img3.png)

#### Hypercolumn 4
![img](docs/img4.png)

#### Hypercolumn 5
![img](docs/img5.png)

### Painting

#### Ancient rock painting
![img](docs/bihua.png)

Oil painting. The first line are the origin images. The second line are the conditions. The last line are the generated images.

- Canny
![img](docs/youhua1.png)

- Hypercolumn
![img](docs/youhua2.png)

- Scribble
![img](docs/scribble.png)

#### Chinese monochromes. 

The first line are the origin images. The second line are the conditions by hypercolumn. The last two line are the generated images.
![img](docs/shuimo1.png)

![img](docs/shuimo2.png)

## 📌 Citation
If you find our work helpful for your research. Please consider citing our paper.

```
@article{point-gcc,
  title={Learning from Pattern Completion: Self-supervised Controllable Generation},
  author={Zhiqiang Chen, Guofan Fan, Jinying Gao, Lei Ma, Bo Lei, Tiejun Huang, Shan Yu},
  journal={arXiv preprint arXiv:2305.19623},
  year={2023}
}
```

## 📕 Acknowledgement and License

Our code is based on ControlNet. Thanks for their wonderful work!

SCG is licensed under the Apache License. See the LICENSE file for more details.
