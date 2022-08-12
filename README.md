# Unet++ for Weizmann Horse Database



<img src=".\predict\20_0_ori.png" alt="20_0_ori" style="zoom:200%;" />

<img src=".\predict\20_0_predict.png" alt="20_0_predict" style="zoom:200%;" />

This repository uses the Weizmann Horse Database for training and semantic segmentation prediction of standard Unet++ networks.

**[UNet++: A Nested U-Net Architecture for Medical Image Segmentation](https://arxiv.org/abs/1807.10165)**

## Installation

My code has been tested on Python 3.9 and PyTorch 1.11.0. Please follow the official instructions to configure your environment. See other required packages in `requirements.txt`.

## Download the pretrained Models ##

In the project: 

### ***Please click on the hyperlinks below to get the models**.*

**_Password_：kour**

**Please place the model files in the same level as the .py file.**

**[best_model.pth](https://pan.baidu.com/s/11zPWaLTH0wvxANX_3ITuQA)** holds the network structure parameters of the best model from my training process. 

**[Unet_plus_plus.pth](https://pan.baidu.com/s/11zPWaLTH0wvxANX_3ITuQA)** holds the full structure of the best model from my training process. 

## Prepare Your Data

1. Please obtain the dataset from [Weizmann Horse Database | Kaggle](https://www.kaggle.com/datasets/ztaihong/weizmann-horse-database/metadata).
2. The dataset contains 327 images of horses and masked images.
3. In the train you need to change **"root"** to an **absolute path** to the weizmann_horse_db.
4. I used the **first 85%** of the images in the dataset for training and the **second 15%** for testing.
5. The final path structure used in my code looks like this:

````
$PATH_TO_DATASET/archive/weizmann_horse_db
├──── horse(327 images)
│    ├──── horse001.png
│    ├──── horse002.png
│    └──── ...
├──── mask(327images)
│    ├──── horse001.png
│    ├──── horse002.png
│    └──...
````

## A Quick Demo

I picked a random image from the test images and then used the pre-trained model to semantically segment it and present the results on the console.

    python demo.py

## Training

Run the following command to train Unet++ :

    python train.py

- 'root'(in train.py) should be modified to your dataset directory.
- The parameter "new_model" in train.py determines whether to train the new model or to continue training on the pre-trained model using the .pth file. **1--new model,0 -- pretrained model**
- Please see the contents of train.py for specific parameter settings. There are detailed descriptions inside. The important parameters are epochs, deep_supervision, cut, learning rate. They determine the results of training and testing.
- I have trained a model which you can use directly by setting the parameters in train.py.
- I was able to train the model on CPU(Intel(R) Core(TM) i7-10710U CPU @ 1.10GHz   1.61 GHz). The training took approximately 10 hours in 200 Epoch conditions.

## Testing ##

In the test set, the model I trained achieved about **0.908** of the MIoU, 0.699 of the Boundary IoU in the testing set.

The results can be found in the "predict" and "log" folders.

## Permission and Disclaimer

This code is only for non-commercial purposes. As covered by the ADOBE IMAGE DATASET LICENSE AGREEMENT, the trained models included in this repository can only be used/distributed for non-commercial purposes. Anyone who violates this rule will be at his/her own risk.
