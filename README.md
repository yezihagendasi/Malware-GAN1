# Malware-GAN
This is a realization of <a href="https://arxiv.org/abs/1702.05983">"Generating Adversarial Malware Examples for Black-Box Attacks Based on GAN"</a>.
The reaserch is done in Institute of Automation, Chinese Academy of Sciences, Summer 2018. http://english.ia.cas.cn/ with the help of my mentor XuBo.

## Introduction
The idea is to use a generative adversarial network (GAN) based algorithm to generate adversarial malware examples, which are able to bypass black-box machine learning based detection models.
![alt text](https://github.com/yanminglai/Malware-GAN/blob/master/figures/Architecture.png)


## Dependencies
 ```Tensorflow 1.80``` ```Keras 2.0```  ```Cuckoo Sandbox 2.03```

## Dataset
The original malware sample is acquired from https://virusshare.com/, I have used 3000 malware samples and 1500 benign samples for trainning and testing(will expand further).

I used the ```Cuckoo Sandbox``` to extract API features from samples. https://cuckoo.readthedocs.io/en/2.0.3/

128 API features are selcted as dimensional vectors to be input to the neutual network (API_list.txt)

## Experiments

MalGAN Architecture:
generator：128+20—256—128     
subsitite detector：128—256—1
maximum epoch：100

True positive rate (in percentage) on original samples and adversarial examples when MalGAN and the black-box detector are trained on the SAME training set

![alt text](https://github.com/yanminglai/Malware-GAN/blob/master/figures/TPR_allclassifiers.png)

MLP-TPR

![alt text](https://github.com/yanminglai/Malware-GAN/blob/master/figures/MLPTPR.png)


True positive rate (in percentage) on original samples and adversarial examples when MalGAN and the black-box detector are trained on the DIFFERENT training set

![alt text](https://github.com/yanminglai/Malware-GAN/blob/master/figures/TPR_DIF.png)

True positive rate (in percentage) on the adversarial examples after the black-box detector is retrained   (RF for example)

![alt text](https://github.com/yanminglai/Malware-GAN/blob/master/figures/retained.png)

