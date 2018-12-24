# <center>Predicting Cancer metastates </center>


## The Problem

#### Dataset: Biopsy images at 8 level(0-7) magnification, with corresponding masks
#### Goal: Assisting doctors by detecting regions that likely have metastatis (at level 7)

## Methodology(compelte work done on google colab):

1. Extract data: 
    
    a. Extract few images and corresponding masks by 
    
    b. Extract cropped patches from slides from levels 5, 6, 7
   
    c. Generate labels by looking at mask of the center region
    
2. Train model

3. Test on one image

## Built-in Functions
* **read_slide**(slide, x, y, level, width, height, as_float=False) - Reads slides
* **positive_samples_from_image**(image_slide, mask_slide, number=100, level=5, patch_size=(100, 100)) - outputs 'number' of samples with tumor for a given patch size
* **negative_samples_from_image**(image_slide, mask_slide, number=100, level=5, patch_size=(100, 100)) - outputs 'number' of samples without tumor for a given patch size
* **test_image**(image_slide, model= model_vgg, level=7, patch_size=(100, 100))- output predicted mask for given image

## Dataset used
* xpos, xng, ypos, yneg - .npy files containing positive and negative patches extracted from 5 slides at (5, 6, 7) levels. y are the associated labels

## Models
* **vgg_model.h5** (best performing, with 0.96 ROC AUC)
* **inception_model.h5**

## Model Results (test accuracy, precision, recall, roc auc)
* **VGG: 90%, 87%, 87%, 0.956
* **Inception: 84%, 80%, 75%, 0.905 
