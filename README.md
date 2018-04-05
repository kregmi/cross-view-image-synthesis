## cross-view-image-synthesis
[[Project](https://kregmi.github.io/cross-view-synthesis)]
[[Arxiv](https://arxiv.org/pdf/1803.03396.pdf)]

Cross-View Image Synthesis using Conditional GANs, 

Krishna Regmi, [Ali Borji](http://aliborji.xyz/aliborji.html)

CVPR 2018.

## Abstract
Learning to generate natural scenes has always been a challenging task in computer vision. It is even more painstaking when the generation is conditioned on images with drastically different views. This is mainly because understanding, corresponding, and transforming appearance and semantic information across the views is not trivial. In this paper, we attempt to solve the novel problem of cross-view image synthesis, aerial to street-view and vice versa, using conditional generative adversarial networks (cGAN). Two new architectures called Crossview Fork (X-Fork) and Crossview Sequential (X-Seq) are proposed to generate scenes with resolutions of 64x64 and 256x256 pixels. X-Fork architecture has a single discriminator and a single generator. The generator hallucinates both the image and its semantic segmentation in the target view. X-Seq architecture utilizes two cGANs. The first one generates the target image which is subsequently fed to the second cGAN for generating its corresponding semantic segmentation map. The feedback from the second cGAN helps the first cGAN generate sharper images. Both of our proposed architectures learn to generate natural images as well as their semantic segmentation maps. The proposed methods show that they are able to capture and maintain the true semantics of objects in source and target views better than the traditional image-to-image translation method which considers only the visual appearance of the scene. Extensive qualitative and quantitative evaluations support the effectiveness of our frameworks, compared to two state of the art methods, for natural scene generation across drastically different views.

## Code
Our code is borrowed from [pix2pix](https://github.com/phillipi/pix2pix).
We will release the code soon.


## Models
Pretrained models can be downloaded here.

[[X-Pix2pix]](https://drive.google.com/open?id=1y5E4XNWiYz5s80Yb9TwVyqFqnZJ3byoJ)   [[X-Fork]]()   [[X-Seq](https://drive.google.com/open?id=11VA_ipbSv6Y_cqNG0BouQwK8LbiJEgiX)]


## Datasets
We used the following datasets:
1. [GT-CrossView](https://github.com/lugiavn/gt-crossview)
2. [CVUSA](http://cs.uky.edu/~jacobs/datasets/cvusa/)

## Results

Some qualitative results on Dayton of GT-CrossView Dataset.
![alt tag](https://github.com/kregmi/cross-view-image-synthesis/blob/master/test_256.jpg)


## Citation
If you find our work useful in your research, please cite our paper 
[Cross-View Image Synthesis using Conditional GANs](https://arxiv.org/pdf/1803.03396.pdf): 

```markdown
@article{regmi2018cross,
  title={Cross-View Image Synthesis using Conditional GANs},
  author={Regmi, Krishna and Borji, Ali},
  journal={arXiv preprint arXiv:1803.03396},
  year={2018}
}
```

## Questions

Please contact: 'krishna.regmi7@gmail.com'
