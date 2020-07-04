## Deep Learning for Change Detection in Remote Sensing Images: Comprehensive Review and  Meta-Analysis
  
The references and materials for "Deep Learning for Change Detection in Remote Sensing Images: Comprehensive Review and  Meta-Analysis".  
[https://arxiv.org/abs/2006.05612]
```
L. Khelifi and M. Mignotte.
Deep Learning for Change Detection in Remote Sensing Images: Comprehensive Review and  Meta-Analysis
IEEE Access
DOI: xxxx/ACCESS.2020.xxxx
vol. xx, pp. xxx-xxx, July 2020.
```

![reviewDCR](lazharkhelifi/deeplearning_changedetection_remotesensing_review/images/fig-1.png)
![reviewDCR](lazharkhelifi/deeplearning_changedetection_remotesensing_review/images/fig-2.png)


![reviewDCR](/images/fig-1.png)
![reviewDCR](/images/fig-2.png)
### Example of use
```
# Without datasets
git clone https://github.com/mhaut/hyperspectral_deeplearning_review/

# With datasets
git clone --recursive https://github.com/mhaut/hyperspectral_deeplearning_review/
cd HSI-datasets
python join_dsets.py
```

### Run code
Go to algorithms folder and run



<h2 id="1">1.Bounding box supervision</h2>

* [Box-driven Class-wise Region Masking and Filling Rate Guided Loss for Weakly Supervised Semantic Segmentation](https://arxiv.org/abs/1904.11693), CVPR 2019 

* [Learning to Segment Every Thing](https://arxiv.org/abs/1711.10370), CVPR 2018

	:Learning weight transfer from well-annotated subset, transfer class-specific weights(output layers) from detection and classification branch, based on Mask-RCNN

* [Pseudo Mask Augmented Object Detection](https://arxiv.org/abs/1803.05858), CVPR 2018

	:State-of-art weakly supervised instance segmentation with bounding box annotation. EM optimizes pseudo mask and segmentation parameter like Boxsup. Graphcut on superpixel is employed to refine pseudo mask. 

* [Simple Does It: Weakly Supervised Instance and Semantic Segmentation](https://arxiv.org/abs/1603.07485), CVPR 2017 \[[web](https://www.mpi-inf.mpg.de/departments/computer-vision-and-multimodal-computing/research/weakly-supervised-learning/simple-does-it-weakly-supervised-instance-and-semantic-segmentation/)\] \[[ref-code](https://github.com/philferriere/tfwss)\]\[[supp](http://openaccess.thecvf.com/content_cvpr_2017/supplemental/Khoreva_Simple_Does_It_2017_CVPR_supplemental.pdf)\]

	:Grabcut+(HED bounday) and MCG , train foreground segmentation network directly with generated mask semantic segmentaion, sensitive to env(quality) of training images. 

* [Weakly- and Semi-Supervised Learning of a DCNN for Semantic Image Segmentation](https://arxiv.org/abs/1502.02734), ICCV 2015

	:Based on CRF refine, EM seems not work

* [BoxSup: Exploiting Bounding Boxes to Supervise Convolutional Networks for Semantic Segmentation](https://arxiv.org/abs/1503.01640), ICCV 2015

	:Iteratively update parameters and region proposal labels, proposals are selected by network output masks

* [Deepcut: Object segmentation from bounding box annotations using convolutional neural networks](https://pdfs.semanticscholar.org/9732/f55c55512309e24a88ae4f0728cc763b626f.pdf), TMI 2017

* [Adversarial Learning for Semi-Supervised Semantic Segmentation](https://arxiv.org/abs/1802.07934), BMVC 2018, \[[code](https://github.com/hfslyc/AdvSemiSeg)\]



#### Other parameters
Dimensionality reduction **- - components** [number]
```
python <algorithm>.py --dataset IP --components 40
```
You can change the proposed parameters  **- - set_parameters** [parameters]
```
python svm.py --dataset IP --set_parameters --C 2 --g 0.01
```
You can use validation set  **- - use_val** by default is 10%, you can change it **- -use_val - -val_percent** [percent]
```
python cnn1d.py --dataset IP --use_val --val_percent 0.10
```
Example:
```
python cnn1d.py --dataset IP --components 40  --set_parameters --epochs 100 --batch_size 32--use_val --val_percent 0.10
```
