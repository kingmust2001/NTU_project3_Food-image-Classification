# NTU_project3_Food image classification

## 專案介紹
Using self-defined CNN to do food image classification. The images are collected from the food-11 dataset classified into 11 classes.

## 專案目標
* Solve image classification with convolutional neural networks.
* Improve the performance with data augmentations.
* Understand how to utilize unlabeled data and how it benefits.
## 軟硬體配置
* CPU: Intel(R) Xeon(R) (6-cores)
* GPU: Tesla K80 (11.44GB)
* OS： Window10
* Pytorch: 1.10.0
* keras: 2.7.0
* tensorflow: 2.7.0
* Memory: 12.69GB
## 資料來源
food-11 dataset

link: https://mega.nz/file/zt1TTIhK#ZuMbg5ZjGWzWX1I6nEUbfjMZgCmAgeqJlwDkqdIryfg
## 資料基本資訊
* Training set: 280 * 11 labeled images + 6786 unlabeled images
* Validation set: 60 * 11 labeled images
* Testing set: 3347 images

## Data augmentations
* resize image to (128,128)
* 隨機調整圖片的亮度(brightness)、對比(contrast)、飽和度(saturation)和色調(hue)
* normalize in model layer
## 模型
3 layers of convolution & maxpooling + 2 layers of fully-connected layer
## Metrics
CROSSENTROPYLOSS (default softmax)

![image](https://user-images.githubusercontent.com/77257138/149958939-32579188-252f-4b12-8a86-459ebfb48422.png)

Note:This criterion combines LogSoftmax and NLLLoss in one single class.
## 成果
* epoch:10 batch size:128

  Train: loss = 1.25415, acc = 0.58594
  
  Valid: loss = 1.66544, acc = 0.42865

* epoch:10 batch size:16 (only revise batch size)

  Train: loss = 0.78096, acc = 0.74223
  
  Valid: loss = 1.66736, acc = 0.48214
  
conclusion: A greater batch size usually gives a more stable gradient. But the GPU memory is limited, so please adjust it carefully.
## Reference
https://speech.ee.ntu.edu.tw/~hylee/ml/2021-spring.html

https://pytorch.org/

http://pytorch.org/vision/stable/index.html

https://chih-sheng-huang821.medium.com/03-pytorch-dataaug-a712a7a7f55e

## Other 
* Improve the performance with additional unlabeled images. 
  * method: semi-supervised learning, self-supervised learning.
![image](https://user-images.githubusercontent.com/77257138/149956555-31a16df8-a4fb-45b9-9a63-4403f827570a.png)

* logits = not normalized; probability = normalized
![image](https://user-images.githubusercontent.com/77257138/149957107-3734efc9-1314-48bd-bea6-2c70359c142a.png)

* dataset folder

![image](https://user-images.githubusercontent.com/77257138/150145669-8f37d64e-75e1-43b6-ae86-80f4a388d17a.png)
