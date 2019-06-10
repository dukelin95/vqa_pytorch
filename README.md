# ECE 285 VQA Project (Group DDST)

## Team Members
- Dan He
- Duke Lin 
- Sneha Kondur
- Tyler Farnan
## Requirements
1. Need python-3.6
    -Run pip install pytorch, tqdm, pickle, torchvision, h5py, scipy  
2. Optional: OpenCV for viewing glimpse maps
## Description
This project uses the network from https://arxiv.org/abs/1704.03162 to solve the visual question answering problem. We extend the paper by testing implementations of the network with the addition or ablation of batch normalization and dropout. The dataset can be downloaded from here: https://visualqa.org/download.html. This needs to be preprocessed (requires 99GB of space) so this is not a part of the repo. Also the pretrained network weights for all four experiments are not a part of the repo as they are above the 100MB limit, they can be found here: https://drive.google.com/drive/folders/1iSwnzx4nl-MU8RuQ6T--VIl32cOYuLId?usp=sharing

## To demo:
1. Download demo_weights.zip from: https://drive.google.com/drive/folders/1iSwnzx4nl-MU8RuQ6T--VIl32cOYuLId?usp=sharing  
2. Unzip demo_weight.zip 
3. Put the weight file in the same directory
4. Follow steps in demo.ipynb  

## To train:
1. Download dataset from: https://visualqa.org/download.html  
    -VQA Annotations, Input Questions, Input Images (training, validation, and testing)  
2. Unzip into ./cyanogenoid_code/data/ (make the directory)
3. In ./cyanogenoid_code/  
    -Run preprocess-images.py and preprocess-vocab.py  
    -Run train.py   
   
## Code 
```
root/cyanogenoid_code/
|
+----demo
|       |   vqaTools/vqa.py -- class to view images and questions 
|       |   demo jpgs -- images for demo.ipynb
+----resnet
|       |   -- directory for preprocessing data
|
|    config.py -- set up the parameters and paths for preprocessing and training
|    data.py -- class for loading the vocab and iamge features from processed dataset
|    model.py -- original model layout
|    model_batchnormDP0.py -- model layout with batch normalization and no dropout
|    model_batchnormDP05.py -- model layout with batch normalization and 50% dropout
|    model_dropout0.py -- model layout with no batch normalization and no dropout
|    model_dropout05.py -- model layout with no batch normalization and 50% dropout
|    preprocess-images.py -- preprocess the images through resnet, creates image filters (resnet-14x14.h5)
|    preprocess-vocab.py -- preprocess the tokens for vocab with an lstm, creates vocabulary for attention (vocab.json)
|    train.py -- trains the model, can retrain from another model by setting parameters in file
|    utils.py -- utility functions (getting transform, paths, accuracy)
|    demo.ipynb -- demo model with batch normalization and 50% dropout, randomly view 1 of 3 preset images and questions through network
|    graph_attention_QA.ipynb -- notebook used to view images, questions, network outputs, and glimpse maps
```


