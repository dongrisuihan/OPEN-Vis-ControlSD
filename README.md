# OPEN-Vis-ControlSD

Our model is built upon our trained modular Hypercolumn-like features and ControlNet. The hypercolumn-like features are trained using a self-supervised method. Based on these features, we train several ControlNets. This approach utilizes a comprehensive modular feature set that is automatically learned and differentiated, resulting in robustness and generalization transfer capabilities. By configuring and combining appropriate control modules, it can effectively transfer to features without prior learning. We exclusively train them on the COCO dataset, yet they demonstrate the ability to generalize across various image styles, including those generated from ancient rock paintings, Chinese monochromes, oil paintings, scribbles, and more. Notably, it maintains strong performance even when dealing with lower-quality ancient rock paintings and oil paintings. 

The modular Hypercolumn-like features are shown as following:

![img](github_page/hypercolumn.png)

The whole architecture is:

![img](github_page/Vis_Control.png)
<!-- ![alt text](image.png) -->

Issues about ControlNet refer to (https://github.com/lllyasviel/ControlNet/blob/main/docs/train.md).

The checkpoint will be released soon.

# Setting

In file tutorial_train.py

modelarch_path = './models/cldm_v15.yaml'
resume_path = './image_log/checkpoint_deconv_down2_3/last.ckpt'
logger_path = 'shuimo_deconv2_3_test'
dataset_name = 'MyDatasetShuimo'

# Select Hypercolumn

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

Ancient rock painting:
![img](github_page/bihua.png)

Oil painting. The first line are the origin images. The second line are the conditions. The last line are the generated images.

Canny:
![img](github_page/youhua1.png)

Hypercolumn:
![img](github_page/youhua2.png)

Scribble:
![img](github_page/scribble.png)

Chinese monochromes. The first line are the origin images. The second line are the conditions by hypercolumn. The last two line are the generated images.
![img](github_page/shuimo1.png)

![img](github_page/shuimo2.png)

