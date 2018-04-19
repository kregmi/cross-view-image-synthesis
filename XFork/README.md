
# XFork 

Torch implementation for Crossview-Fork (XFork) model. 

Generator for X-Fork (add figure)

## Setup

### Getting Started
- Install torch and dependencies from https://github.com/torch/distro
- Install torch packages `nngraph` and `display`
```bash
luarocks install nngraph
luarocks install https://raw.githubusercontent.com/szym/display/master/display-scm-0.rockspec
```
- Clone this repo:
```bash
git clone git@github.com:kregmi/cross-view-image-synthesis.git
cd cross-view-image-synthesis/XFork
```

- Training the model
```bash
DATA_ROOT=./datasets/AB_AsBs name=sample_images which_direction=a2g phase=sample th train_fork.lua
```
- For CPU only training: 
```bash
DATA_ROOT=./datasets/AB_AsBs name=sample_images which_direction=a2g phase=sample gpu=0 cudnn=0 th train_fork.lua
```
- Testing the model:
```bash
DATA_ROOT=./datasets/AB_AsBs name=sample_images which_direction=a2g phase=sample which_epoch=35 th test_fork.lua 
```
The test results will be saved to: `./results/sample_images/35_net_G_sample/images/`.

## Train
```bash
DATA_ROOT=/path/to/data/ name=expt_name which_direction=a2g th train_fork.lua
```
Switch `a2g` to `g2a` to train in opposite direction.

Models are saved to `./checkpoints/expt_name` (can be changed by passing `checkpoint_dir=your_dir` in train_fork.lua).

See `opt` in train_fork.lua for additional training options.

## Test
```bash
DATA_ROOT=/path/to/data/ name=expt_name which_direction=a2g phase=val th test_fork.lua
```

This will run the model named `expt_name` in direction `a2g` on all images in `/path/to/data/val`.

Result images, and a webpage to view them, are saved to `./results/expt_name` (can be changed by passing `results_dir=your_dir` in test_fork.lua).

See `opt` in test_fork.lua for additional testing options.


## Datasets
The original datasets are available here:
1. [GT-CrossView](https://github.com/lugiavn/gt-crossview)
2. [CVUSA](http://cs.uky.edu/~jacobs/datasets/cvusa/)

Ground Truth semantic segmentation maps are not available for the datasets. We used RefineNet trained on CityScapes for generating semantic segmentation maps and used them as Gound Truth segmaps in our experiments.

Train/Test splits for Dayton dataset can be downloaded from here. Please cite their papers if you use the dataset.
Paper for crossview dataset and refinenet model and cityscape dataset


Download the datasets using the following script. Some of the datasets are collected by other researchers. Please cite their papers if you use the data.
```bash
bash ./datasets/download_dataset.sh dataset_name
```

## Models
Pretrained models can be downloaded from here.

[[X-Fork]](https://drive.google.com/open?id=1DsXaEJJy_iHjd819ZU_zKu8x3VzHHCYO)

Place the models in `./checkpoints/` after the download has finished.

## Setup Training and Test data
### Generating Pairs
Refer to [pix2pix](https://github.com/phillipi/pix2pix/blob/master/scripts/combine_A_and_B.py) for steps and code to generate pairs of images required for training/testing.

For XFork, first concat the streetview and aerial images followed by concatenating their segmentation maps and finally concatenating them all along the columns. Each concatenated image file in the dataset will contain {A,B,As,Bs}, 

where A=streetview image, B=aerial image, As=segmentation map for streetview image and Bs=segmentation map for aerial image.

## Citation
If you use this code for your research, please cite our paper [Cross-View Image Synthesis using Conditional GANs](https://arxiv.org/pdf/1803.03396.pdf):

```markdown
@article{regmi2018cross,
  title={Cross-View Image Synthesis using Conditional GANs},
  author={Regmi, Krishna and Borji, Ali},
  journal={arXiv preprint arXiv:1803.03396},
  year={2018}
}
```

## Acknowledgments
The code is borrowed heavily from [pix2pix](https://github.com/phillipi/pix2pix/). The data loader is modified to handle images and semantic segmentation maps.
