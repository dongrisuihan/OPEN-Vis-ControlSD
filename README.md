# Model architecture of OPEN-Vis-ControlSD

Our model is based our trained Hypercolumn-like features and ControlNet. The hypercolumn-like features are trained by a self-supervised method. Basing on the hypercolumn-like features, we train several controlnets and it can generalize to multiple tasks such as 

The Hypercolumn-like features are shown as following:

![img](github_page/hypercolumn.png)

The whole architecture is:

![img](github_page/Vis_Control.png)

Issues about ControlNet refer to (https://github.com/lllyasviel/ControlNet/blob/main/docs/train.md).

The checkpoint will be released soon.

# Run the network, set model archtecture file, checkpoint file, logger file and dataset

In file tutorial_train.py

modelarch_path = './models/cldm_v15.yaml'
resume_path = './image_log/checkpoint_deconv_down2_3/last.ckpt'
logger_path = 'shuimo_deconv2_3_test'
# dataset_name_list = ['MyDatasetCOCO','MyDatasetCOCO_canny','MyDatasetCOCO_val','MyDatasetCOCO_val_canny','MyDatasetBihua','MyDatasetBihuaCanny','MyDatasetShuimo','MyDatasetShuimoCanny']
dataset_name = 'MyDatasetShuimo'

# Set the selected hypercolumn

In file ./models/cldm_v15.yaml

        hyperconfig:
          target: cldm.cldm.HyperColumnLGN
          params: 
            hypercond: [0]
            size: 512

# Run

python tutorial_train.py 

# Results

The first line are the origin image and the prompt. The second line are conditions of multiple hypercolumn and canny. The last line are the generated images

![img](github_page/hc.png)

hypercolumn 0
![img](github_page/img0.png)

hypercolumn 1
![img](github_page/img1.png)

hypercolumn 2
![img](github_page/img2.png)

hypercolumn 3
![img](github_page/img3.png)

hypercolumn 4
![img](github_page/img4.png)

hypercolumn 5
![img](github_page/img5.png)

Ancient murals
![img](github_page/bihua.png)

Oil painting. The first line are the origin images. The second line are the conditions. The last line are the generated images.

Canny:
![img](github_page/youhua1.png)

Hypercolumn:
![img](github_page/youhua2.png)

Scribble:
![img](github_page/scribble.png)

Ink painting. The first line are the origin images. The second line are the conditions by hypercolumn. The last two line are the generated images.
![img](github_page/shuimo1.png)

![img](github_page/shuimo2.png)


