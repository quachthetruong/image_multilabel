# Multi-Label Image Classification

This project develops a multi-label classification model to assign up to 10 location labels to images from a Hanoi tourist dataset, focusing on landmarks like Ho Guom (Sword Lake) and Ho Tay (West Lake). It fine-tunes pre-trained **VGG16, GoogleNet, ResNet50, and ViT**, achieving high accuracy on a small dataset through data augmentation and a weighted binary cross-entropy loss.

![plot](https://github.com/quachthetruong/image_multilabel/blob/main/asset/hoguom.jpg?raw=true)

## Loss function

A **weighted binary cross-entropy loss** is used to address class imbalance and optimize multi-label predictions. The loss function is shown below:

![plot](https://github.com/quachthetruong/image_multilabel/blob/main/asset/weighted_binary_crossentrpy_loss.png?raw=true)

## Methodology

### Dataset

- Size: 200 images with up to 10 labels.
- Data Augmentation:
  - Horizontal flipping.
  - Random adjustments to brightness, saturation, and contrast.
- Purpose: Enhance the small dataset to improve model generalization.

### Model Architecture

The project fine-tunes pre-trained models for multi-label classification:

- Convolutional Base: Reused pre-trained ConvNet layers (frozen or with a low learning rate) to adapt to the dataset.
- Classifier: Replaced the original classifier with new fully connected layers for 10-label output.
- Models:

  - VGG16: Deep 16-layer convolutional network.
  - GoogleNet: Inception-based model for efficient feature extraction.
  - ResNet50: 50-layer residual network for robust performance.
    ![plot](https://github.com/quachthetruong/image_multilabel/blob/main/asset/resnet.jpg?raw=true)
  - ViT: Vision Transformer leveraging transformer architecture.
    ![plot](https://github.com/quachthetruong/image_multilabel/blob/main/asset/vit.jpg?raw=true)

## Result

Training and test loss curves for the models:![plot](https://github.com/quachthetruong/image_multilabel/blob/main/asset/train_test_lost.jpg?raw=true)

The models were evaluated on binary accuracy, overall accuracy, training time, inference time, and parameter count. Results are summarized below:

| Model     | Binary Accuracy | Accuracy | Training Time (s) | Inference Time (s) | Number of Parameters |
| --------- | --------------- | -------- | ----------------- | ------------------ | -------------------- |
| VGG16     | 94%             | 70%      | 485.7             | 0.017              | 134,301,514          |
| GoogleNet | 95%             | 74%      | 219.7             | 0.012              | 26,620,586           |
| ResNet50  | 97%             | 82%      | 413.8             | 0.014              | 48,723,018           |
| ViT       | 95%             | 70%      | 400.0             | 0.0153             | 90,072,586           |
