# Fashion-MNIST Clothing Classification

A PyTorch CNN that classifies Fashion-MNIST images into 10 categories. The notebook also examines which classes the model confuses and displays examples of correct and incorrect predictions.

## Dataset and model

[Fashion-MNIST](https://github.com/zalandoresearch/fashion-mnist) contains 60,000 training images and 10,000 test images. Each image is a 28 × 28 grayscale image of a clothing item, shoe, or bag.

The model uses three convolutional layers with ELU activations, two max-pooling layers, and a linear layer that produces 10 class scores. It was trained for 10 epochs with cross-entropy loss and Adam, using a batch size of 32 and a learning rate of 0.001.

## Results

The model correctly classified **9,029 of 10,000 test images**. Average training loss decreased from **0.3985** in epoch 1 to **0.1267** in epoch 10.

| Test metric | Score |
| --- | ---: |
| Accuracy | **90.29%** |
| Macro precision | 90.33% |
| Macro recall | 90.29% |
| Macro F1 | 0.903 |

### Performance by class

The test set contains 1,000 images per class.

| Class | Precision | Recall | F1 |
| --- | ---: | ---: | ---: |
| T-shirt/top | 0.851 | 0.815 | 0.832 |
| Trouser | 0.989 | 0.985 | 0.987 |
| Pullover | 0.810 | 0.881 | 0.844 |
| Dress | 0.918 | 0.875 | 0.896 |
| Coat | 0.814 | 0.894 | 0.852 |
| Sandal | 0.982 | 0.980 | 0.981 |
| **Shirt** | **0.756** | **0.692** | **0.723** |
| Sneaker | 0.964 | 0.963 | 0.963 |
| Bag | 0.988 | 0.976 | 0.982 |
| Ankle boot | 0.961 | 0.968 | 0.965 |

### Error analysis

`Shirt` had the lowest F1 score. The model correctly identified 692 of 1,000 shirts. The most frequent errors in the confusion matrix were:

| Actual class | Predicted class | Images |
| --- | --- | ---: |
| T-shirt/top | Shirt | 133 |
| Shirt | Coat | 99 |
| Shirt | Pullover | 90 |
| Shirt | T-shirt/top | 85 |

The notebook shows correct and incorrect predictions for `Shirt` and `T-shirt/top` side by side. Several misclassified examples have similar silhouettes, and details such as collars and sleeves can be difficult to distinguish at 28 × 28 pixels.

## Running the notebook

Install the dependencies and open [notebook.ipynb](./notebook.ipynb).

```bash
python -m pip install notebook torch torchvision torchmetrics numpy matplotlib scikit-learn
jupyter notebook notebook.ipynb
```

Run the cells from top to bottom. Fashion-MNIST downloads automatically to `./data` on the first run.
