
<p><span style="font-family:georgia,serif;"><span style="font-size:36px;">VCIP Grand Challenge on NIR Image Colorization</span></span></p>

## Challenge Motivation
NIR (Near-Infrared) imaging provides a unique vision with respect to illumination and object material properties which are quite different from those in visible wavelength bands. The high sensitivity of NIR sensors and the fact that it is invisible to human vision make it an indispensable input for applications such as low-light imaging, night vision surveillance and road navigation, etc. However, the monochromatic NIR images lacks color discrimination and severely differ from the well-known RGB spectrum, which makes them unnatural and unfamiliar for both human perception and for CV algorithms.


This challenge call for development of efficient algorithms to colorize NIR images to RGB images. The correlation between the NIR and RGB domains are more ambiguous and complex which makes such task more challenging than gray scale image colorization and image style transfer. In recent years we see numerous learning-based models that explores different network architectures, supervision modes, and training strategies to tackle this challenge, however the limitations are still obvious in terms of color realism and texture fidelity. Semantic correctness and instance-level color consistency are difﬁcult to be preserved. More importantly, the demand for strictly registered NIR-RGB image pairs also restricts efﬁcient development of NIR colorization models.


In this challenge, we will provide both registered NIR-RGB image pairs as well as un-paired RGB images on several categories of scene contents for the training and testing of colorization models (as shown in Fig. 1). Both objective metrics (e.g., Peak Signal to Noise Ratio, Structural Similarity Index, Angular Color Error, etc.) and subjective evaluations (non-reference visual quality human ranking) will be carried out to comprehensively evaluate competing algorithms. The details of the dataset and the evaluation protocols will be available soon.

## Challenge Dataset

The challenge dataset provides NIR and RGB images for the training and validation of models. The structure of the dataset is shown bellow. There are two types of data in the dataset:
### 1. Pixel-aligned NIR RGB Image Pairs
The subfolder **NIR** and **RGB-Resgistered** contains pixel-aligned (registered) NIR-RGB image pairs. The source of the images are from [1]. We have manually excluded ones that contain saturated regions, and temporally inconsistent contents. The images are croped and resized into 256\*256 patches

### 2. Unpaired RGB Images
The subfolder **RGB-Online** contains pixel-unaligned (unregistered) RGB images correspond to each scene category. 

### 3. Validation Datasets 
The subfolder **Validation** contains pixel-aligned (registered) NIR-RGB image pairs for the purpose of model validation. The NIR-RGB image pairs are named as "validation_nnnn_nir.png" and "validation_nnnn_rgb.png" respectively. Identical "nnnn" values indicates pairing relationships.

```bash
├── NIR_VCIP_Challenge_dataset
│   ├── NIR
│   │   ├── country_0000_nir.png
│   │   ├── country_0001_nir.png
│   │   ├── ...
│   │   ├── field_0000_nir.png
│   │   ├── ...             
│   ├── RGB-Resgistered
│   │   ├── country_0000_rgb_reg.png
│   │   ├── country_0001_rgb_reg.png
│   │   ├── ...
│   │   ├── field_0000_rgb_reg.png
│   │   ├── ...
│   ├── RGB-Online
│   │   ├── country_0000_rgb_onl.png
│   │   ├── country_0001_rgb_onl.png
│   │   ├── ...
│   │   ├── field_0000_rgb_onl.png
│   │   ├── ...
│   ├── Validation
│   │   ├── validation_0000_nir.png
│   │   ├── validation_0000_rgb.png
│   │   ├── ...
│   │   ├── validation_0009_nir.png
│   │   ├── validation_0009_rgb.png
```
The dataset contains the foloowing subfolders,  which includes both pixel aligned (registered) NIR-RGB image pairs, and un-registered RGB images.

**Terms of Use** all data provided by the VCIP challenge are freely available to the participants. The data are available only for open research and educational purposes, whithin the scope of the challenge. The conference organizing comittee makes no warranties regarding the dataset, including but not limited to warranties of non-infringement or fitness for a particular purpose. The copyright of the images remains property of their respective owners. By downloading and making use of the data, you accept full responsibility for using the data.

## Evaluation Metric
### Objective Metrics

We are going to use Angular Error (AE), Peak Signal-to-Noise Ratio (PSNR), and Structural Similiarty (SSIM) as quantitative metrics to evaluate the colorization results. The PSNR value is calculated according to:

<div style="text-align: center"><img src="/projects/NIR2RGB_VCIP_Challenge/web/PSNR.jpg" width="280" /></div>

Here <div><img src="/projects/NIR2RGB_VCIP_Challenge/web/Igt.jpg" width="36" /></div> and ![](/projects/NIR2RGB_VCIP_Challenge/web/Iout.jpg)  represents RGB colorization results and the ground truth.

AE is calculated according to the euqation below, which provides a color similarity measure close to human color perception:
<div style="text-align: center"><img src="/projects/NIR2RGB_VCIP_Challenge/web/AE.jpg" width="420" /></div>

where Iout and Igt represents RGB colorization results and the ground truth.

### Subjective Metrics

As we found both the AE and PSNR and SSIM index can not comprehensively reflect the visual quality of the colorization performance, we will also rank the subjective visual quality for the challenge. Subjective comparison will be conducted in a nonreference manner, a group of judges (approximately 10) who do not know the ground truth color
image are to compare the colorization results, and rank the them based on the visual quality (color realism, fidelity and vividness).

### Reference
[1] M. Brown and S. Susstrunk, “Multi-spectral SIFT for scene category recognition,” in _IEEE Conference on Computer Vision and Pattern Recognition_, 2011, pp. 177–184.
