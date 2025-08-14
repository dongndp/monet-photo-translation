# Introduction to Deep Learning Week 5: GANs

## 1. Brief description of the problem and data

In this week's assignment, we will participate in the Kaggle competition [I’m Something of a Painter Myself](https://www.kaggle.com/competitions/gan-getting-started), which challenges participants to build generative adversarial models (GANs) that can generate images of artworks that resemble images of famous painters like Monet.

### Dataset Description
The dataset contains four directories: monet_tfrec, photo_tfrec, monet_jpg, and photo_jpg. The monet_tfrec and monet_jpg directories contain the same painting images, and the photo_tfrec and photo_jpg directories contain the same photos.

- The monet directories contain Monet paintings. These images are used to train our GAN models.
- The photo directories contain photos. These photos are used to generate images for submission.

**Files**
- monet_jpg - 300 Monet paintings sized 256x256 in JPEG format
- monet_tfrec - 300 Monet paintings sized 256x256 in TFRecord format
- photo_jpg - 7028 photos sized 256x256 in JPEG format
- photo_tfrec - 7028 photos sized 256x256 in TFRecord format

**Submission Format**
- The submision must be named as images.zip and contain 7,000-10,000 generated images sized 256x256.

**Evaluation**
- Submissions are evaluated on MiFID (Memorization-informed Fréchet Inception Distance), which is a modification from [Fréchet Inception Distance (FID)](https://arxiv.org/abs/1706.08500).

### Summary of Tasks:
- Load monet/photo datasets
- Explore the dataset, perform data cleaning, data analysis, preprocess image data
- Build and test models: Build, evaluate, and test our GAN models (CycleGAN). 
- Summarize and discuss the results.

## References

Here are some great papers and articles that helped and inspired me.

[1] Amy Jang, Monet CycleGAN Tutorial. [https://www.kaggle.com/code/amyjang/monet-cyclegan-tutorial](https://www.kaggle.com/code/amyjang/monet-cyclegan-tutorial)

[2] Keras CycleGAN Turtorial. [https://keras.io/examples/generative/cyclegan/](https://keras.io/examples/generative/cyclegan/)

[3] TensorFlow Tutorial, CycleGAN. [https://www.tensorflow.org/tutorials/generative/cyclegan](https://www.tensorflow.org/tutorials/generative/cyclegan)

[4] Generative Adversarial Networks. [arXiv:1406.2661](https://arxiv.org/abs/1406.2661)

[5] Jun-Yan Zhu, Taesung Park, Phillip Isola, Alexei A. Efros, "Unpaired Image-to-Image Translation using Cycle-Consistent Adversarial Networks”, 2017. [arXiv:1703.10593](https://arxiv.org/abs/1703.10593)

[6] Emami, Hajar, "Image-To-Image Translation With Deep Neural Networks" (2022). Wayne State University Dissertations. 3733.
[https://digitalcommons.wayne.edu/oa_dissertations/3733](https://digitalcommons.wayne.edu/oa_dissertations/3733)

[7] How CycleGAN Works? [https://developers.arcgis.com/python/latest/guide/how-cyclegan-works/](https://developers.arcgis.com/python/latest/guide/how-cyclegan-works/)

[8] CycleGAN: How AI Creates Stunning Image Transformations. [https://viso.ai/deep-learning/cyclegan/](https://viso.ai/deep-learning/cyclegan/)

[9] U-Net Architecture [https://en.wikipedia.org/wiki/U-Net](https://en.wikipedia.org/wiki/U-Net)

[10] U-Net Architecture Explained [https://www.geeksforgeeks.org/machine-learning/u-net-architecture-explained/](https://www.geeksforgeeks.org/machine-learning/u-net-architecture-explained/)

## NOTES

This notebook is configured to run directly on Kaggle with GPU. If you want to try out on your own machine, you need to download the data from Kaggle and adjust the paths to the data. Please see section 2. Import Library and Setup of the notebook.

RUN_LOCAL = False <= Change to False

if RUN_LOCAL:

    BASE_DIR = './' <= Change to your local path

else:

    BASE_DIR = '/kaggle/input/'

MONET_DIR = f'{BASE_DIR}gan-getting-started/monet_tfrec/'

PHOTO_DIR = f'{BASE_DIR}gan-getting-started/photo_tfrec/'

if RUN_LOCAL:

    OUTPUT_DIR = f'{BASE_DIR}/working/images/'

    SUBMISSION_FILE = f'{BASE_DIR}/images'

else:

    OUTPUT_DIR = '../tmp/'

    SUBMISSION_FILE = '/kaggle/working/images'

