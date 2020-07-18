# VCIP Grand Challenges on NIR Image Colorization

## Challenge Motivation
NIR (Near-Infrared) imaging provides a unique vision with respect to illumination and object material properties which are quite different from those in visible wavelength bands. The high sensitivity of NIR sensors and the fact that it is invisible to human vision make it an indispensable input for applications such as low-light imaging, night vision surveillance and road navigation, etc. However, the monochromatic NIR images lacks color discrimination and severely differ from the well-known RGB spectrum, which makes them unnatural and unfamiliar for both human perception and for CV algorithms.


This challenge call for development of efficient algorithms to colorize NIR images to RGB images. The correlation between the NIR and RGB domains are more ambiguous and complex which makes such task more challenging than gray scale image colorization and image style transfer. In recent years we see numerous learning-based models that explores different network architectures, supervision modes, and training strategies to tackle this challenge, however the limitations are still obvious in terms of color realism and texture fidelity. Semantic correctness and instance-level color consistency are difﬁcult to be preserved. More importantly, the demand for strictly registered NIR-RGB image pairs also restricts efﬁcient development of NIR colorization models.


In this challenge, we will provide both registered NIR-RGB image pairs as well as un-paired RGB images on several categories of scene contents for the training and testing of colorization models (as shown in Fig. 1). Both objective metrics (e.g., Peak Signal to Noise Ratio, Structural Similarity Index, Angular Color Error, etc.) and subjective evaluations (non-reference visual quality human ranking) will be carried out to comprehensively evaluate competing algorithms. The details of the dataset and the evaluation protocols will be available soon.

## Challenge Dataset
We are going to provide two datasets for the training/validation of the colorization models. The EPFL RGB-NIR Scene Dataset [1] which contains 477 image pairs with resolution of 1024680 (some might vary) captured from 9 categories of scenes including: country, field, forest, indoor, mountain, old building, street, urban, and water. The pixels are registered and aligned. We have already received consent from the EPFL image dataset authors [1] to use the dataset for our
challenge.
On top of paired data, we also provide a RGB image dataset that fall under 4 image categories for the challenge in Track 2. The NIR and RGB images are targeted at different scenes without pixel alignments. The thumbnails for the two datasets are shown in Fig. 1 and Fig. 2.

## Evaluation Metric
### Objective Metrics

We are going to use Angular Error (AE) and Peak Signal-to-Noise Ratio (PSNR) as quantitative metrics to evaluate the colorization results. AE provides a color similarity measure instead of absolute intensity values (measured by PSNR), which is closer to human color perception. AE is defined as:

![alt text](https://github.com/adam-p/markdown-here/raw/master/src/common/images/icon48.png "Logo Title Text 1")

![](https://github.com/jchenhkg/jchenhkg.github.io/blob/master/projects/NIR2RGB_VCIP_Challenge/web/AE.jpg)

<p><img style="display: block; margin-left: auto; margin-right: auto;" src="https://github.com/jchenhkg/jchenhkg.github.io/blob/master/projects/NIR2RGB_VCIP_Challenge/web/AE.jpg" width="500" /></p>

where (Io(i; j)) represents pixels in colorized images, and Ig(i; j)) represents RGB ground truth.
 stands for dot product, and Io Ig stand for normalized vectors for Io and Io respectively.
### Subjective Metrics

As we found both the AE and PSNR and SSIM index can not comprehensively reflect the visual quality of the colorization performance, we will also rank the subjective visual quality for the challenge. Subjective comparison will be conducted in a nonreference manner, a group of judges (approximately 10) who do not know the ground truth color
image are to compare the colorization results, and rank the them based on the visual quality (color realism, fidelity and vividness).

### Reference
[1] M. Brown and S. Susstrunk, “Multi-spectral SIFT for scene category recognition,” in _IEEE Conference on Computer Vision and Pattern Recognition_, 2011, pp. 177–184.
