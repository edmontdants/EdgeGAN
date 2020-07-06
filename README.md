# EdgeGAN
### [Project Page](https://sysu-imsl.com/EdgeGAN/) | [Paper](https://arxiv.org/abs/2003.02683)
SketchyCOCO: Image Generation from Freehand Scene Sketches  
Chengying Gao, Qi Liu, Qi Xu, Limin Wang, Jianzhuang Liu, Changqing Zou  

**This repo is working in progress! The current version is not the final version!**

# Installation
Clone this repo.  
```
git@github.com:sysu-imsl/EdgeGAN.git
cd EdgeGAN
```
This repo requires TensorFlow 1.14.0 and python 3+.  
`conda create/activate` is suggested to manage multiple versions of tensorflow.  
After switching to proper conda environment, run `conda install --file requirements.txt`

# Dataset
Our dataset can be found in [SketchyCOCO](https://github.com/sysu-imsl/SketchyCOCO). Follow the guide and prepare the dataset.

## Directory Structure
For singleclass dataset
```
EdegGAN
└───data
    └───train
    |   |    <file00>.png
    |   |    <file01>.png
    |   |    ...
    |   
    └───test
        |    <file00>.png
        |    <file01>.png
        |    ...
```
For multiclass dataset

```
EdegGAN
└───data
    └───train
    |   └───<class label 0>
    |   |    |    <file01>.png
    |   |    |    ...
    |   └───<class label 1>
    |   |   ...
    |   
    └───test
    |   └───<class label 0>
    |   |    |    <file01>.png
    |   |    |    ...
    |   └───<class label 1>
    |   |   ...
```
## Example
### Train
![60975.png](images/dataset_example/train/60975.png?raw=true)
![60981.png](images/dataset_example/train/60981.png?raw=true)
![60987.png](images/dataset_example/train/60987.png?raw=true)
![60991.png](images/dataset_example/train/60991.png?raw=true)
![60994.png](images/dataset_example/train/60994.png?raw=true)
### Test
![14809.png](images/dataset_example/test/14809.png?raw=true)
![14810.png](images/dataset_example/test/14810.png?raw=true)
![14811.png](images/dataset_example/test/14811.png?raw=true)
![14812.png](images/dataset_example/test/14812.png?raw=true)

# Testing Using Pretrained Model
1. Download the pretrained model from the XXX, and run:
``` bash
mkdir -p outputs/edgegan/checkpoints
tar -zxvf checkpoints.tar.gz
cd ..
```
2. Generate images using pretrained model:
``` bash
python -m edgegan.test --name=edgegan --dataroot=<root of dataset> --dataset=<dataset> --gpu=<gpuid> #(with multi-classes)
python -m edgegan.test --name=edgegan --dataroot=<root of dataset> --dataset=<dataset> --nomulticlasses --gpu=<gpuid> #(with single class)
```
3. the outputs will be located at `outputs/edgegan/test_output/` by default

# Training
It will cost about fifteen hours to run on a single Nvidia RTX 2080 Ti card.

``` bash
python -m edgegan.train --name=<new_name> --dataroot=<root of dataset> --dataset=<datsaet_name> --gpu=<gpuid> #(with multi-classes)
python -m edgegan.train --name=<new_name> --dataroot=<root of dataset> --dataset=<datsaet_name> --nomulticlasses --gpu=<gpuid> #(with single class)

```

# Citation
If you use this code for your research, please cite our papers.  
```
@article{gao2020image,  
  title={Image Generation from Freehand Scene Sketches},  
  author={Gao, Chengying and Liu, Qi and Xu, Qi and Liu, Jianzhuang and Wang, Limin and Zou, Changqing},  
  journal={arXiv preprint arXiv:2003.02683},  
  year={2020}  
}
```
