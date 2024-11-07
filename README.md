# Image Classification Model Comparison

This project explores the training, validation, and testing performance of four different convolutional neural network architectures on an image classification dataset. The architectures include the classic **LeNet5**, **LeNet5 with Batch Normalization (BN)**, **LeNet5 with L2 Regularization**, and a deeper network, **ResNet9**. Each model was evaluated based on training loss, validation loss, validation accuracy, test accuracy, test loss, and a detailed examination of their misclassified examples.

## Models Overview

1. **LeNet5**: A classic CNN model with three convolutional layers followed by fully connected layers, serving as a baseline in this experiment.
2. **LeNet5 with Batch Normalization (BN)**: An enhanced version of LeNet5 that includes batch normalization layers to stabilize the training process and potentially improve generalization.
3. **LeNet5 with L2 Regularization**: This variant applies L2 regularization to control overfitting, helping the model generalize better.
4. **ResNet9**: A deeper network that includes residual connections, designed to capture more complex patterns and enable better feature extraction.

## Training Results Summary

The models were trained on the CINC-10 dataset, and their performance was recorded over the training epochs. Refer to this [paper](https://arxiv.org/pdf/1810.03505) for in-depth information on the dataset.

- **LeNet5** shows a steady decline in training loss with some variability, achieving a final validation accuracy of around **50%**. This indicates limited capacity in the base model for complex feature extraction.
- **LeNet5 with BN** has a smoother training loss curve, achieving slightly higher validation accuracy at **52%**, which shows that batch normalization aids stability and generalization.
- **ResNet9** significantly outperforms all LeNet5 variants, reaching a validation accuracy of around **70%**. Its deeper architecture with residual connections allows it to capture complex patterns effectively, resulting in the best performance.
- **LeNet5 with L2 Regularization** provides a modest boost over the base LeNet5, achieving around **52%** validation accuracy. L2 regularization reduces overfitting but does not enhance accuracy substantially.

## Testing Results Summary

The models were tested on a separate test set to evaluate their generalization.

- **LeNet5** achieved a test accuracy of **50.7%** with a test loss of **1.4627**, with confusion in distinguishing similar classes, such as airplanes vs. ships.
- **LeNet5 with BN** showed slight improvement, with a test accuracy of **52.7%** and a test loss of **1.3715**. The batch normalization layer provides some improvement in stability but still struggles with certain class distinctions.
- **ResNet9** performed the best on the test set with a test accuracy of **69.8%** and a test loss of **0.8814**. This model accurately handles complex classes and minimizes misclassifications, as evident in its confusion matrix.
- **LeNet5 with L2 Regularization** scored **53.0%** in test accuracy with a test loss of **1.3250**. It slightly outperformed the base LeNet5 but still lacks the generalization power of ResNet9.

## Misclassification Analysis

Across all models, the most common misclassification involved images labeled as airplane, which were often confused with classes like ship, automobile, frog, and occasionally bird. This confusion suggests that the models rely on low-level features such as color and shape, which can overlap across these categories, particularly in low-resolution or blurry images. ResNet9 showed fewer of these confusions, though it was not immune, reflecting its improved, but not perfect, capacity to handle visual ambiguities.

## Conclusion

This experiment demonstrates that **ResNet9** significantly outperforms all LeNet5 variants due to its deeper architecture and residual connections, making it more suitable for complex classification tasks. While batch normalization and L2 regularization provide slight improvements to LeNet5, they fall short compared to the architectural enhancements in ResNet9. This project highlights the importance of model complexity and the use of residual learning for tackling challenging image classification tasks, especially when dealing with classes that have subtle visual similarities.

## Project Structure

- `cnn_analysis.py`: Code for loading dataset, training each model, recording training/validation/test metrics, and analyzing misclassified examples.
