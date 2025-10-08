# Exploring Log RGB Data for Image Classification (Reproducibility Study)

This project reproduces and validates the results of a research study exploring how **different image representations (JPG, Linear RGB, Log RGB, and Pseudo-Log)** affect the performance of **convolutional neural networks (CNNs)** on a binary image classification task.

The experiment focuses on classifying images into **“Swedish Fish”** and **“No Fish”**, using three architectures — **FishNet64**, **Modified ResNet18**, and **DenseNet121**.  
Our goal was to verify whether *Log RGB* and *Linear RGB* transformations improve model performance compared to standard JPG images.


## Dataset and Preprocessing
The dataset consists of images split into **Train**, **Validation**, and **Test** sets, each containing:
- **SwedishFish** (positive class)
- **NoFish** (negative class)

Initially provided in standard **JPG (sRGB)** format, all images were converted to:
- **Linear RGB** — by reversing the sRGB gamma curve.
- **Log RGB** — by applying a logarithmic transformation to compress high-intensity values and enhance darker regions.


### Models 
| Model | Input Size | Epochs | Optimizer | Loss Function |
|:--|:--:|:--:|:--|:--|
| FishNet64 | 64×64 | 100 | Adam | NLLLoss (LogSoftmax) |
| ResNet18 (Modified) | 224×224 | 30 | Adam | CrossEntropyLoss |
| DenseNet121 | 224×224 | 10 | Adam | CrossEntropyLoss |


## Results Summary

| Model | JPG (sRGB) | Linear RGB | Log RGB | Pseudo-Log |
|:--|:--:|:--:|:--:|:--:|
| **FishNet64** | 86.30% | 90.70% | **90.70%** | 80.10% |
| **ResNet18 (Modified)** | 52.80% | 65.22% | **78.26%** | – |
| **DenseNet121** | **99.38%** | 98.70% | 98.50% | – |




