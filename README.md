# MNIST Neural Network Lab

An experimental handwritten-digit classification project built with Keras. The notebook covers the complete workflow from dataset exploration and preprocessing to training, evaluation, and error analysis.

> This project uses a fully connected neural network (MLP), not a convolutional neural network (CNN). Each `28 × 28` image is flattened into a 784-dimensional vector before being passed to the model.

## Project Overview

The project uses the MNIST dataset to classify handwritten digits from `0` to `9`.

It demonstrates:

- Loading and inspecting the MNIST dataset
- Visualizing random training samples
- Examining class distribution
- Flattening images from `28 × 28` into 784-dimensional vectors
- Normalizing pixel values from `[0, 255]` to `[0, 1]`
- One-hot encoding class labels
- Building and training a dense neural network with Keras
- Monitoring validation loss with early stopping
- Evaluating the model on unseen test data
- Creating a confusion matrix
- Visualizing misclassified samples

## Dataset

[MNIST](https://keras.io/api/datasets/mnist/) contains 70,000 grayscale images of handwritten digits.

| Split | Number of Images | Image Shape |
|---|---:|---|
| Training | 60,000 | `28 × 28` |
| Testing | 10,000 | `28 × 28` |

## Preprocessing

The notebook applies three main preprocessing steps.

### Image Flattening

Each `28 × 28` image is converted into a one-dimensional vector:

```text
28 × 28 → 784
```

### Pixel Normalization

Pixel values are converted to `float32` and normalized:

```text
[0, 255] → [0.0, 1.0]
```

### Label Encoding

Class labels are converted into one-hot encoded vectors.

For example:

```text
5 → [0, 0, 0, 0, 0, 1, 0, 0, 0, 0]
```

## Model Architecture

The model is a fully connected neural network, also known as a Multilayer Perceptron (MLP).

```text
Input: 784 features
        ↓
Dense: 784 units, ReLU
        ↓
Dense: 512 units, ReLU
        ↓
Dense: 10 units, Softmax
```

The output layer produces a probability distribution over the ten digit classes.

## Training Configuration

| Setting | Value |
|---|---|
| Optimizer | RMSprop |
| Loss Function | Categorical Cross-Entropy |
| Evaluation Metric | Accuracy |
| Batch Size | 256 |
| Maximum Epochs | 15 |
| Validation Split | 10% |
| Early Stopping | `val_loss`, patience = 5 |

## Results

The current notebook run achieved the following results:

| Metric | Result |
|---|---:|
| Test Accuracy | **98.4%** |
| Test Loss | **0.0708** |

The training history shows that training accuracy continues to increase while validation loss eventually stops improving. Early stopping prevents unnecessary training after this point.

## Evaluation and Error Analysis

The notebook evaluates the model using more than test accuracy.

The evaluation section includes:

- Training and validation accuracy curves
- A confusion matrix for all ten digit classes
- Visualization of twelve misclassified test images

These analyses help identify which handwritten digits the model tends to confuse instead of relying only on a single accuracy value.

## Running the Project

### Google Colab

1. Open Google Colab.
2. Upload `mnist_neural_network_lab.ipynb`.
3. Select **Runtime → Run all**.

## License

This project is intended for educational and experimental use.
