# Deblurring Videos Using Spatial-Temporal Contextual Transformer with Feature Propagation
[Liyan Zhang], [Boming Xu](https://github.com/xuboming8), [Jinshan Pan](https://jspan.github.io/)

<p align="center">
  <img width="800" src=".src/figs/framework.png">
</p>

### Abstract 
*We present a simple and effective approach to explore both local spatial-temporal contexts and non-local temporal information for video deblurring. First, we develop an effective spatial-temporal contextual transformer to explore local spatialtemporal contexts from videos. As the features extracted by the spatial-temporal contextual transformer does not model the nonlocal temporal information of video well, we then develop a feature propagation method to aggregate useful features from the long-range frames so that both local spatial-temporal contexts and non-local temporal information can be better utilized for video deblurring. Finally, we formulate the spatial-temporal contextual transformer with the feature propagation into a unified deep convolutional neural network (CNN) and train it in an end-to-end manner. We show that using the spatial-temporal contextual transformer with the feature propagation is able to generate useful features and makes the deep CNN model more compact and effective for video deblurring. Extensive  experimental results show that the proposed method performs favorably against state-of-the-art ones on the benchmark datasets in terms of accuracy and model parameters.*


### Requirements
> - Python 3.8, PyTorch >= 1.11
> - BasicSR 1.4.2
> - Platforms: Ubuntu 18.04, cuda-11

### Installation
```
# Clone the repo
git clone https://github.com/sunny2109/SAFMN.git
# Install dependent packages
cd SAFMN
pip install -r requirements.txt
# Install BasicSR
python setup.py develop
```
You can also refer to this [INSTALL.md](https://github.com/XPixelGroup/BasicSR/blob/master/docs/INSTALL.md) for installation

### Training
Run the following commands for training:
```
# train SAFMN for x4 effieicnt SR
python basicsr/train.py -opt options/train/SAFMN/train_DF2K_x4.yml
# train SAFMN for x4 classic SR
python basicsr/train.py -opt options/train/SAFMN/train_L_DF2K_x4.yml
```
### Testing 
- Download the pretrained models.
- Download the testing dataset.
- Run the following commands:
```
# test SAFMN for x4 efficient SR
python basicsr/test.py -opt options/test/SAFMN/test_benchmark_x4.yml
# test SAFMN for x4 classic SR
python basicsr/test.py -opt options/test/SAFMN/test_L_benchmark_x4.yml
# test SAFMN for x4 real-world SR (without ground-truth)
python basicsr/test.py -opt options/test/SAFMN/test_real_img_x4.yml
# test SAFMN for x4 real-world SR (large input)
python inference/inference_real_safmn.py --input test_demo --output results/test_demo --scale 4 --large_input 
```
- The test results will be in './results'.

### Results
- **Pretrained models and visual results**

| Degradation | Model Zoo| Visual Results| 
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
@inproceedings{sun2023safmn,
    title={Spatially-Adaptive Feature Modulation for Efficient Image Super-Resolution},
    author={Sun, Long and Dong, Jiangxin and Tang, Jinhui and Pan, Jinshan},
    booktitle={Proceedings of the IEEE/CVF International Conference on Computer Vision},
    year={2023}
 }
 ```


### Acknowledgement
This code is based on [BasicSR](https://github.com/XPixelGroup/BasicSR) toolbox. Thanks for the awesome work.