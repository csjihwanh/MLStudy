# Kaggle MNIST competition


## lrdecay

### model

![image](https://user-images.githubusercontent.com/19871043/159160021-dee7815a-5352-44f9-9c7c-de7ebbf877b7.png)

### hyperparameters

* learning rate = 1e-3

* learning rate decay : 0.1 mutliplied per 20000 step

### loss graph

![lrdecay_epoch20](https://user-images.githubusercontent.com/19871043/159159997-138f8471-4a8c-4219-af71-7c63633cf7ff.jpg)

---

## 2xCNN
### model

<div id ="1"></div>


![image](https://user-images.githubusercontent.com/19871043/159192088-037cf3f5-a054-4ec8-8089-a26c076066a7.png) 

### hyperparameters

* learning rate = 1e-3 (no learning rate decay)

### loss graph

![2xCNN](https://user-images.githubusercontent.com/19871043/159192122-66810c20-dfd1-474b-ae42-1154e66e9224.jpg)

---

## 2xCNN_LrDecay

### model
same to <a href ="#1">2xCNN</a>

### hyperparameters

* learning rate = 1e-3 (decayed to 0.1 per every 10000 steps)

### loss graph

![2xCNN_LrDecay](https://user-images.githubusercontent.com/19871043/159196137-2be7215e-4c61-44d7-b7c1-f185f34ec66a.jpg)


---

## 2xCNN_NoSoftmax

### model

![image](https://user-images.githubusercontent.com/19871043/159203170-53cf29af-2320-43b3-a648-626eebb9604d.png)\


### hyperparameters

* learning rate = 1e-2 (multiplied 0.1 times per every 2500 steps (each epoch))

* epoch = 11

### optimizer 

`torch.optim.SGD`

### loss graph

![2xCNN_NoSoftmax](https://user-images.githubusercontent.com/19871043/159203242-ddc485be-e750-4edd-8e25-15dc38dde9e2.jpg)

maximum accuracy in validation : 98.4%

---

## 2xCNN_BN_lr1e-2

### model

![image](https://user-images.githubusercontent.com/19871043/159218026-46354deb-9d60-40ef-b345-f379d4d338c4.png)

### hyperparameters

* learning rate = 1e-2 (multiplied 0.1 times per every 10000 steps)

--> when 1e-3 is used as the learning rate, the final accuracy is dropped drastically

* epoch = 16

### optimizer 

`torch.optim.SGD`

### loss graph

| ![2xCNN_BN_lr1e-2](https://user-images.githubusercontent.com/19871043/159218140-6b9e6e4c-3173-49f5-b953-752905acdee1.jpg) |
|:--:| 
| *when 1e-2 is used for initial learning rate* |
| maximum accuracy in validation set : 99.4% |


| ![2xCNN_BN_lr1e-3](https://user-images.githubusercontent.com/19871043/159219195-a6c2c887-223a-4394-a7ab-cd4bea288a6e.jpg) |
|:--:| 
| *when 1e-3 is used for initial learning rate* |


---

## 2xCNN_dropout0.7

```
HongNet(
(seq_module): Sequential(
(0): Conv2d(1, 10, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1))
(1): BatchNorm2d(10, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
(2): ReLU()
(3): Conv2d(10, 10, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1))
(4): BatchNorm2d(10, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
(5): ReLU()
(6): Conv2d(10, 10, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1))
(7): ReLU()
(8): MaxPool2d(kernel_size=3, stride=1, padding=1, dilation=1, ceil_mode=False)
(9): Conv2d(10, 10, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1))
(10): BatchNorm2d(10, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
(11): ReLU()
(12): Conv2d(10, 10, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1))
(13): BatchNorm2d(10, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
(14): ReLU()
(15): Conv2d(10, 10, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1))
(16): ReLU()
(17): MaxPool2d(kernel_size=3, stride=2, padding=0, dilation=1, ceil_mode=False)
)
(classifier): Sequential(
(0): Dropout(p=0.7, inplace=True)
(1): Linear(in_features=1690, out_features=1024, bias=True)
(2): ReLU()
(3): Dropout(p=0.7, inplace=True)
(4): Linear(in_features=1024, out_features=512, bias=True)
(5): ReLU()
(6): Linear(in_features=512, out_features=10, bias=True)
(7): ReLU()
)
)
```

### hyperparameters

* learning rate = 1e-2 (multiplied 0.1 times per every 15000 steps)

* epoch = 20

* dropout p = 0.7 (almost same accuracy when p = 0.5 is used)

### optimizer 

`torch.optim.SGD`

### loss graph

|![2xCNN_dropout_p=0 7](https://user-images.githubusercontent.com/19871043/159390699-631d06ce-c8d8-480e-80fd-fc17453943c5.jpg) |
|:--:| 
| *when 1e-2 is used for initial learning rate* |
| maximum accuracy in validation set : 99.2% |
