# AOD-Net by Pytorch 该Readme就是翻译他的

这是[AOD-Net : All-in-One Network for Dehazing](https://arxiv.org/abs/1707.06543)的一个实现在Python3上，Pytorch。该模型可以去除雾霾、烟雾甚至水的杂质。

The repository includes:
*AOD网络的源代码
*基于[NYU Depth V2]的合成模糊图像构建代码，下面可以下载
*hazy数据集的训练代码
*AOD网络的预训练模型

# Requirements
Python 3.6, Pytorch 0.4.0 and other common packages

## NYU Depth V2
用来构建雾霾图像，我这里上传百度云了:
* 下载 [NYU Depth V2 labeled dataset](https://pan.baidu.com/s/1_wtUSDDgy-Vai40H5c4pwg)
提取码：6xho

这里不提供我修改的代码了，源代码需要的话直接去[人家Github](https://github.com/weber0522bb/AODnet-by-pytorch)上找吧.以下是我可以运行的命令行参数更改。可以下他的源码然后用我命令行参数。然后他还有有几个包有问题需要更新，先建个Repo占个坑吧。但是最近搞得太忙了，自己的训练当时用一半数据集跑出来效果太差了。(老板不给服务器，用1060 6G跑的，TAT)

# Training Part
## Dateset Setup
1. Clone this repository
2. Create dataset from the repository root directory
    ```bash
    $ cd make_dataset
    $ python create_train.py --nyu {Your NYU Depth V2 path} --dataset {Your trainset path}
    ``` 
3. Random pick 3,169 pictures as validation set
    ```bash
    $ python random_select.py --trainroot {Your trainset path} --valroot {Your valset path}
    ```
## Start to training
4. training AOD-Net
    ```bash
    $ python train.py --dataroot {Your trainset path} --valDataroot {Your valset path} --cuda
    ```
# Testing Part
5. test hazy image on AOD-Net
    ```bash
    $ python test.py --input_image /test/canyon1.jpg  --model /model_pretrained/AOD_net_epoch_relu_10.pth --output_filename /result/canyon1_dehaze.jpg --cuda
    ```
