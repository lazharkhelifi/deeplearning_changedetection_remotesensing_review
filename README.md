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

![reviewHSI](https://github.com/mhaut/hyperspectral_deeplearning_review/blob/master/images/paviaclasf.png)

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
```
# Training from scratch
python <algorithm>.py --dataset IP 
# Example:
python svm.py --dataset IP --tr_percent 0.15

# Fine-tuning (not recommended) <DENSENET121, MOBILENET, RESNET50, VGG16, VGG19>:
python pretrained_cnn.py --dataset IP --arch <architecture>
# Example:
python pretrained_cnn.py --dataset IP --arch VGG16

# Transfer learning <CNN1D, CNN2D, CNN2D40bands, CNN3D>, two steps:
python transfer_learning.py --dataset1 IP --dataset2 SV --arch <algorithm> --search_base_model
python transfer_learning.py --dataset1 IP --dataset2 SV --tr_samples 2 --use_val --arch <algorithm> --use_transfer_learning
# Example:
python transfer_learning.py --dataset1 IP --dataset2 SV --arch CNN2D40bands --search_base_model
python transfer_learning.py --dataset1 IP --dataset2 SV --tr_samples 2 --use_val --arch CNN2D40bands --use_transfer_learning
```

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
