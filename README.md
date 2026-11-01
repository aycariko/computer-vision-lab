# mnist-neural-network-lab
MNIST Neural Network Lab

An experimental handwritten-digit classification project built with Keras. The notebook covers the complete workflow from dataset exploration and preprocessing to training, evaluation, and error analysis.

This project uses a fully connected neural network (MLP), not a convolutional neural network (CNN). Each 28 × 28 image is flattened into a 784-dimensional vector before being passed to the model.

Project overview

The project uses the MNIST dataset to classify handwritten digits from 0 to 9. It demonstrates:

Loading and inspecting the MNIST dataset

Visualizing random training samples

Examining class distribution

Flattening images from 28 × 28 to 784-dimensional vectors

Normalizing pixel values from [0, 255] to [0, 1]

One-hot encoding class labels

Building and training a dense neural network with Keras

Monitoring validation loss with early stopping

Evaluating the model on unseen test data

Creating a confusion matrix

Visualizing misclassified samples

Dataset

MNIST contains 70,000 grayscale images of handwritten digits:

Split

Images

Image shape

Training

60,000

28 × 28

Testing

10,000

28 × 28

Preprocessing

The notebook applies two main preprocessing steps:

Each image is flattened:

28 × 28 → 784

Pixel values are converted to float32 and normalized:

[0, 255] → [0.0, 1.0]

The labels are converted to one-hot encoded vectors for use with categorical cross-entropy.

Model architecture

Input: 784 features
        ↓
Dense: 784 units, ReLU
        ↓
Dense: 512 units, ReLU
        ↓
Dense: 10 units, Softmax

The output layer produces a probability distribution over the ten digit classes.

Training configuration

Setting

Value

Optimizer

RMSprop

Loss function

Categorical cross-entropy

Metric

Accuracy

Batch size

256

Maximum epochs

15

Validation split

10%

Early stopping

val_loss, patience = 5

Results

The current notebook run achieved:

Metric

Result

Test accuracy

98.4%

Test loss

0.0708

The training history shows that training accuracy continues to increase while validation loss eventually stops improving. Early stopping limits unnecessary training after this point.

Evaluation and error analysis

In addition to test accuracy, the notebook includes:

A training-versus-validation accuracy plot

A confusion matrix for all ten classes

A visualization of twelve misclassified test images

These analyses help identify which handwritten digits the model tends to confuse instead of relying only on a single accuracy value.

Run the notebook

Google Colab

Upload mnist_neural_network_lab.ipynb to Google Colab and select Runtime → Run all.

Local environment

Clone the repository and install the dependencies:

git clone <repository-url>
cd mnist-neural-network-lab
pip install numpy matplotlib scikit-learn tensorflow keras jupyter
jupyter notebook mnist_neural_network_lab.ipynb

Repository structure

mnist-neural-network-lab/
├── mnist_neural_network_lab.ipynb
└── README.md

Planned improvements

Restore the best weights when early stopping is triggered

Add loss curves alongside accuracy curves

Compare different optimizers and learning rates

Add dropout and L2 regularization experiments

Report precision, recall, and F1-score

Compare the MLP baseline with a CNN

Test robustness using shifted, rotated, or noisy digits

Add reproducible random seeds and experiment tracking

Acknowledgment

The initial workflow was inspired by DataCamp's Mastering Backpropagation notebook and was adapted and extended with revised preprocessing, model training, early stopping, confusion-matrix evaluation, and misclassification analysis.
