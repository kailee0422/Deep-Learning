# Experiment Report

## Introduction

This project develops a simple **ResNet model** for classifying the
**Flowers102 dataset** (102 flower categories). Images were resized for
consistent input, and experiments tested different architectures,
optimizers, schedulers, and preprocessing methods. The report is divided
into failed and successful experiments.

## Failed Experiments

### Augmentation & Normalization

  Setting               Accuracy
  --------------------- ----------
  ResNet18 + Aug        66.47%
  ResNet18 + No Aug     66.08%
  Normalization (Yes)   48.43%
  Normalization (No)    2.94%

### Image Size & Optimizers (with errors)

  Model      Image Size   Optimizer   Accuracy
  ---------- ------------ ----------- ----------
  ResNet18   224x224      SGD         65.88%
  ResNet18   224x224      Adam        73.14%
  ResNet18   320x320      SGD         73.63%
  ResNet18   320x320      Adam        72.16%
  ResNet34   224x224      SGD         61.86%
  ResNet34   224x224      Adam        74.71%
  ResNet50   224x224      SGD         44.12%
  ResNet50   224x224      Adam        76.37%

## Successful Experiments

### Optimizers

  Model      SGD      Adagrad    RMSprop    Adam     AdamW
  ---------- -------- ---------- ---------- -------- --------
  ResNet18   83.33%   75.78%     79.90%     83.43%   85.39%
  ResNet34   80.69%   77.55%\*   77.65%\*   80.78%   88.04%
  ResNet50   81.67%   \-         \-         82.55%   85.59%

### Learning Rate Schedulers (AdamW)

  Model      StepLR   CosineAnnealingLR   ReduceLROnPlateau
  ---------- -------- ------------------- -------------------
  ResNet18   85.39%   83.73%              89.22%
  ResNet34   88.04%   \-                  88.63%
  ResNet50   85.59%   \-                  90.98%

### Class Balancing

  Model      Without Balance   With Balance
  ---------- ----------------- --------------
  ResNet18   85.39%            86.67%
  ResNet34   88.04%            89.02%
  ResNet50   85.59%            88.63%

### Image Size (AdamW + ReduceLROnPlateau)

  Model      224x224   512x512
  ---------- --------- ----------
  ResNet18   89.22%    89.71%
  ResNet34   88.63%    93.04%\*
  ResNet50   90.98%    91.76%\*

### Activation Functions (ResNet50 + AdamW + ReduceLROnPlateau)

  Activation   Accuracy
  ------------ ----------
  ReLU         90.98%
  LReLU        90.20%
  EReLU        89.51%
  PReLU        89.41%

## Discussion

-   ResNet outperformed simple CNN due to skip connections (avoids
    vanishing gradients).\
-   ReLU performed best due to simplicity, sparsity, and stable
    gradients.

## Conclusion

-   **Best result**: ResNet34 (512x512) + AdamW + ReduceLROnPlateau →
    **93.04%**.\
-   Key factors: augmentation, optimizer, scheduler, and image size.\
-   Larger images + class balancing → improved accuracy.

## Acknowledgment

Thanks to **206 Lab members and seniors** for their support.

