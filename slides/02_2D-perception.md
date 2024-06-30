---
marp: true
title: 24 Jun 2024
size: 16:9
math: mathjax
theme: am_dark
paginate: true
headingDivider: [2,3]
footer: Kashu Yamazaki, 2024
# backgroundImage: url('https://marp.app/assets/hero-background.svg')
---

<!-- _class: cover_b -->
<!-- _header: "" -->
<!-- _footer: "" -->
<!-- _paginate: "" -->
<!-- _backgroundImage: url('https://marp.app/assets/hero-background.svg') -->

# Robot Perception and Control

###### Robot Perception in 2D

Last updated: Jul / 25 /2024
Kashu Yamazaki
kyamazak@andrew.cmu.edu

## Image Classification

<!-- _class: trans -->
<!-- _footer: "" -->
<!-- _paginate: "" -->

## ImageNet

ImageNet is a large-scale dataset for image classification, known for its use in Large Scale Visual Recognition Challenge (ILSVRC). 

- (2009): ImageNet was released by Dr. *Li Fei-Fei* team.
- (2012): **AlexNet** made a breakthrough achieving 16% top-5 error rate - kickstarting the boom in deep learning.
- (2017): 95% accuracy reached and ILSVRC concluded.

<!-- _class:  bq-blue -->
> After ILSVRC Challenge 
> 
> ImageNet continues to be a valuable resource for researchers for pre-training image encoder (backbone) models.

![bg right:40% w:95%](https://blog.acolyer.org/wp-content/uploads/2016/04/imagenet-fig4l.png)

## AlexNet

AlexNet is a **convolutional neural network** (CNN) architecture, designed by Alex Krizhevsky that contains eight layers: the first five are convolutional layers, some of them followed by max-pooling layers, and the last three are fully connected layers.

![#center w:650](https://miro.medium.com/v2/resize:fit:1400/1*bD_DMBtKwveuzIkQTwjKQQ.png)

<!-- _class:  bq-blue -->
> Influence
> 
> AlexNet is considered one of the most influential papers published in computer vision, having spurred many more papers published employing CNNs and GPUs to accelerate deep learning.

## ResNet



## ViT

## CLIP

Learning directly from raw text about images **can leverage a much broader source of supervision** than using a fixed set of predetermined object categories [[1](https://arxiv.org/pdf/2103.00020.pdf)] [[code](https://github.com/openai/CLIP)]. 

![#center](img/clip.png)

## CLIP

Sample implementation:

```python
# extract feature representations of each modality
I_f = image_encoder(I) #[n, d_i]
T_f = text_encoder(T)  #[n, d_t]
# joint multimodal embedding [n, d_e]
I_e = l2_normalize(np.dot(I_f, W_i), axis=1)
T_e = l2_normalize(np.dot(T_f, W_t), axis=1)
# scaled pairwise cosine similarities [n, n]
logits = np.dot(I_e, T_e.T) * np.exp(t)
# symmetric loss function
labels = np.arange(n)
loss_i = cross_entropy_loss(logits, labels, axis=0)
loss_t = cross_entropy_loss(logits, labels, axis=1)
loss = (loss_i + loss_t)/2
```

![bg right:30% h:70%](img/clip_.png)

## Object Detection

<!-- _class: trans -->
<!-- _footer: "" -->
<!-- _paginate: "" -->

##

## Segmentation

<!-- _class: trans -->
<!-- _footer: "" -->
<!-- _paginate: "" -->

## SAM