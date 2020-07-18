
<p><span style="font-family:georgia,serif;"><span style="font-size:36px;">VCIP Grand Challenge on NIR Image Colorization</span></span></p>

## Challenge Motivation
NIR (Near-Infrared) imaging provides a unique vision with respect to illumination and object material properties which are quite different from those in visible wavelength bands. The high sensitivity of NIR sensors and the fact that it is invisible to human vision make it an indispensable input for applications such as low-light imaging, night vision surveillance and road navigation, etc. However, the monochromatic NIR images lacks color discrimination and severely differ from the well-known RGB spectrum, which makes them unnatural and unfamiliar for both human perception and for CV algorithms.


This challenge call for development of efficient algorithms to colorize NIR images to RGB images. The correlation between the NIR and RGB domains are more ambiguous and complex which makes such task more challenging than gray scale image colorization and image style transfer. In recent years we see numerous learning-based models that explores different network architectures, supervision modes, and training strategies to tackle this challenge, however the limitations are still obvious in terms of color realism and texture fidelity. Semantic correctness and instance-level color consistency are difﬁcult to be preserved. More importantly, the demand for strictly registered NIR-RGB image pairs also restricts efﬁcient development of NIR colorization models.


In this challenge, we will provide both registered NIR-RGB image pairs as well as un-paired RGB images on several categories of scene contents for the training and testing of colorization models (as shown in Fig. 1). Both objective metrics (e.g., Peak Signal to Noise Ratio, Structural Similarity Index, Angular Color Error, etc.) and subjective evaluations (non-reference visual quality human ranking) will be carried out to comprehensively evaluate competing algorithms. The details of the dataset and the evaluation protocols will be available soon.

## Evaluation Metrics
### 1. Objective Evaluation: 50%

We are going to use Angular Error (**AE：20%**), Peak Signal-to-Noise Ratio (**PSNR：15%**) and Structural Similiarty (**SSIM：15%**) [2] as quantitative metrics to evaluate the colorization results. The PSNR value is calculated according to:

<div style="text-align: center"><img src="/projects/NIR2RGB_VCIP_Challenge/web/PSNR.jpg" width="280" /></div>

Here <img src="/projects/NIR2RGB_VCIP_Challenge/web/Iout.jpg" height="22"/> and <img src="/projects/NIR2RGB_VCIP_Challenge/web/Igt.jpg" height="22"/> represent RGB colorization results and the RGB ground truth, respectively. To provide a color similarity measure close to human color perception, we also use **AE** is according to:

<div style="text-align: center"><img src="/projects/NIR2RGB_VCIP_Challenge/web/AE.jpg" width="420" /></div>

### 2. Subjective Evaluation: 50%

As both **AE**, **PSNR** and **SSIM** can not comprehensively reflect the visual quality of the colorization performance, we will also rank the visual quality for competing algorithms. Subjective comparison will be conducted in a nonreference manner, a group of judges (10+ individuals) who do not know the ground truth RGB images are to evaluate the colorization results, and rank the algorithms based on the visual quality based on the following standards:
- **Semantic correctness and color realism: 10%** (judges will evaluate on whether the colors are conforming to the real world scenrios);
- **Boundary precision: 10%** (whether the object boudnaries are cleanly separated without "bleeding" effects);
- **Texture preservation: 10%** (how well the textures are preserved after colorization):;
- **Instance consistency: 10%** (whether the same object instance are colored consistently);
- **Color vividness: 10%**.


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

### Reference
[1] M. Brown and S. Susstrunk, “Multi-spectral SIFT for scene category recognition,” in _IEEE Conference on Computer Vision and Pattern Recognition_, 2011, pp. 177–184.
[2] Z. Wang, A. C. Bovik, H. R. Sheikh, and E. P. Simoncelli, “Image quality assessment: From error visibility to structural similarity,” _IEEE Transactions on Image Processing_, vol. 13, no. 4, pp. 600–612, 2004.
