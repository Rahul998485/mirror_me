# mirror_me

source code: drive link :- https://drive.google.com/drive/folders/1FsbiyhjEZoX3sCQAK_DVM2kP9bYp-rUv?usp=sharing

dataset :- drive link :- https://drive.google.com/file/d/1t2N9kBLzZItjAe5K_UD5MX8eJEBbDtou/view?usp=sharing


## instruction to run	

This pipeline is a combination of consecutive training and testing of GMM + TOM. GMM generates the wraped clothes according to the target human. Then, TOM blends the wraped clothes outputs from GMM into the target human properties, to generate the final try-on output.

1) Install the requirements
2) Download/Prepare the dataset
3) Train GMM network
4) Get wraped clothes for training set with trained GMM network, and copy wraped clothes & masks inside `data/train` directory
5) Train TOM network
6) Test GMM for testing set
7) Get wraped clothes for testing set, copy wraped clothes & masks inside `data/test` directory
8) Test TOM testing set

## Installation
This implementation is built and tested in PyTorch 0.4.1.
Pytorch and torchvision are recommended to install with conda: `conda install pytorch=0.4.1 torchvision=0.2.1 -c pytorch`
<br/>For all packages, run `pip install -r requirements.txt`

## Training
Run `python train.py`

## Testing
Run 'python test.py'

### Testing with custom images
to run the model with custom internet images, make sure you have the following:

1) image (image of a person, crop/resize to 192 x 256 (width x height) pixels)
2) image-parse (you can generate with CIHP_PGN or Graphonomy pretrained networks from the person image. 
3) cloth (in-shop cloth image, crop/resize to 192 x 256 (width x height) pixels)
4) cloth-mask (binary mask of cloth image, you can generate it with simple pillow/opencv function)
5) pose (pose keypoints of the person, generate with openpose COCO-18 model (OpenPose from the official repository is preferred))
6) Also, make a test_pairs.txt file for your custom images. (accordingly).
