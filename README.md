# Deblurring Videos Using Spatial-Temporal Contextual Transformer with Feature Propagation
[Liyan Zhang], [Boming Xu](https://github.com/xuboming8), [Jinshan Pan](https://jspan.github.io/)

<p align="center">
  <img width="800" src="./src/figs/framework.jpg">
</p>

### Abstract 
*We present a simple and effective approach to explore both local spatial-temporal contexts and non-local temporal information for video deblurring. First, we develop an effective spatial-temporal contextual transformer to explore local spatialtemporal contexts from videos. As the features extracted by the spatial-temporal contextual transformer does not model the nonlocal temporal information of video well, we then develop a feature propagation method to aggregate useful features from the long-range frames so that both local spatial-temporal contexts and non-local temporal information can be better utilized for video deblurring. Finally, we formulate the spatial-temporal contextual transformer with the feature propagation into a unified deep convolutional neural network (CNN) and train it in an end-to-end manner. We show that using the spatial-temporal contextual transformer with the feature propagation is able to generate useful features and makes the deep CNN model more compact and effective for video deblurring. Extensive  experimental results show that the proposed method performs favorably against state-of-the-art ones on the benchmark datasets in terms of accuracy and model parameters.*

## Demo Video

### Demo wiht visualization on the DVD dataset of the model (Input,  Ours and RVRT from left to right)

[https://github.com/yzb1997/STCT/raw/main/src/video/DVD.mp4](https://github.com/yzb1997/STCT/raw/main/src/video/DVD.mp4)

### Requirements
> - Python 3.8, PyTorch >= 1.11
> - BasicSR 1.4.2
> - Platforms: Ubuntu 18.04, cuda-11

### Installation
```
# Clone the repo
git clone https://github.com/yzb1997/STCT.git
# Install dependent packages
cd STCT
pip install -r requirements.txt
# Install BasicSR
python setup.py develop
```
You can also refer to this [INSTALL.md](https://github.com/XPixelGroup/BasicSR/blob/master/docs/INSTALL.md) for installation

### Training
Run the following commands for training:
```
# train STCT on the BSD dataset
python basicsr/train.py -opt options/train/Deblur/train_Deblur_BSD.yml
# train STCT on the DVD dataset
python basicsr/train.py -opt options/train/Deblur/train_Deblur_DVD.yml
# train STCT on the GOPRO dataset
python basicsr/train.py -opt options/train/Deblur/train_Deblur_GOPRO.yml
# train STCT on the REAL dataset
python basicsr/train.py -opt options/train/Deblur/train_Deblur_REAL.yml
# train STCT on the REDS dataset
python basicsr/train.py -opt options/train/Deblur/train_Deblur_REDS.yml
```
### Testing 
- Download the pretrained models.
- Download the testing dataset.
- Run the following commands:
```
# test STCT on the BSD dataset
python basicsr/test.py -opt options/train/Deblur/train_Deblur_BSD.yml
# test STCT on the DVD dataset
python basicsr/test.py -opt options/train/Deblur/train_Deblur_DVD.yml
# test STCT on the GOPRO dataset
python basicsr/test.py -opt options/train/Deblur/train_Deblur_GOPRO.yml
# test STCT on the REAL dataset
python basicsr/test.py -opt options/train/Deblur/train_Deblur_REAL.yml
# test STCT on the REDS dataset
python basicsr/test.py -opt options/train/Deblur/train_Deblur_REDS.yml
```
- The test results will be in './results'.

### Results
- **Pretrained models and visual results**

<!-- | Degradation | Model Zoo| Visual Results| 
| :----- |:-----: |:-----: |
| BI-Efficient SR | [Google Drive](https://drive.google.com/drive/folders/12O_xgwfgc76DsYbiClYnl6ErCDrsi_S9?usp=share_link)/[Baidu Netdisk](https://pan.baidu.com/s/1mKXahFifHaF14pc1pBWFOg) with code: SAFM | [Google Drive](https://drive.google.com/drive/folders/1s3vJQXDACr799khLLs1ELWL-neljx5vL?usp=share_link)/[Baidu Netdisk](https://pan.baidu.com/s/17q_OuNVTgy7QhtbFu099Jg) with code: SAFM |
| BI-Classic SR | [Google Drive](https://drive.google.com/drive/folders/12O_xgwfgc76DsYbiClYnl6ErCDrsi_S9?usp=share_link)/[Baidu Netdisk](https://pan.baidu.com/s/10jtlG-FYfB8KwYfWsQDOMA) with code: SAFM | [Google Drive](https://drive.google.com/drive/folders/1s3vJQXDACr799khLLs1ELWL-neljx5vL?usp=share_link)/[Baidu Netdisk](https://pan.baidu.com/s/1fYsZ67MNLpPs7OAS9Dn2-w) with code: SAFM |
| x4 [Real-world](https://github.com/xinntao/Real-ESRGAN) |[Google Drive](https://drive.google.com/drive/folders/12O_xgwfgc76DsYbiClYnl6ErCDrsi_S9?usp=share_link)/[Baidu Netdisk](https://pan.baidu.com/s/10jtlG-FYfB8KwYfWsQDOMA) with code: SAFM |  |

- **Efficient SR Results**
<img width="800" src="./figs/efficient_sr.png">

- **Classic SR Results**
<img width="800" src="./figs/classic_sr.png">

- **Real-world SR Results**

|Real-World Image (x4)|Real-ESRGAN  |SwinIR     | SAFMN (ours)|
|       :---          |     :---:   |  :-----:  |  :-----:    |        
| <img width="350" src="figs/real_figs/five_golden_flowers_02.png">|<img width="350" src="figs/real_figs/five_golden_flowers_02_realESRGAN.png">|<img width="350" src="figs/real_figs/five_golden_flowers_02_SwinIR.png">|<img width="350" src="figs/real_figs/five_golden_flowers_02_SAFMN.png">
| <img width="350" src="figs/real_figs/five_golden_flowers_01.png">|<img width="350" src="figs/real_figs/five_golden_flowers_01_realESRGAN.png">|<img width="350" src="figs/real_figs/five_golden_flowers_01_SwinIR.png">|<img width="350" src="figs/real_figs/five_golden_flowers_01_SAFMN.png">
| <img width="350" src="figs/real_figs/kobe_curry.png">|<img width="350" src="figs/real_figs/kobe_curry_realESRGAN.png">|<img width="350" src="figs/real_figs/kobe_curry_SwinIR.png">|<img width="350" src="figs/real_figs/kobe_curry_SAFMN.png">
| <img width="350" src="figs/real_figs/little_carp.png">|<img width="350" src="figs/real_figs/little_carp_realESRGAN.png">|<img width="350" src="figs/real_figs/little_carp_SwinIR.png">|<img width="350" src="figs/real_figs/little_carp_SAFMN.png">

[<img src="figs/real_figs/anime_results.png">](https://imgsli.com/MTkwMzE2/6/7) 


### Citation
If this work is helpful for your research, please consider citing the following BibTeX entry.
```
@inproceedings{
    
 }
 ``` -->


### Acknowledgement
This code is based on [BasicSR](https://github.com/XPixelGroup/BasicSR) toolbox. Thanks for the awesome work.
