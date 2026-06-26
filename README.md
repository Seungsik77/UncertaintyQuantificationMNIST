Dataset: MNIST dataset of handwritten digits

My goal for this project was to Create a 2D Convolutional Neural Network to classify handwritten digits from the MNIST dataset. These digits would then be grouped by digit class, while tracking loss and accuracy.

Libraries Used:
PyTorch, random, numpy, matplotlib, torch, torchvision

**STEPS**
1. Loaded the Dataset (MNIST Dataset)
- Initialized number of epochs, learning rate, and rate of weight decay
- With torch.device, activated the GPU for faster training

2. Normalized the Dataset
- This has the effect of reducing overfitting
- Split the dataset into Train/Test sets
- Output number of classes, number of input channels, and initial tensor shape

3. Exploratory Data Analysis/Diagnostics
- Used matploylib to plot class weight distributions of the Train set
- Returned maximum and minimum class counts

4. Quality Assurance
- Output a sample of digits from the dataset, denormalized to preserve original input (before being turned into tensors)
- Output sample labels (should be digits from 0-9)
- Output batch tensor shape

5. Initialized Baseline Convolutional Neural Network Model
- Used nn.Module to define the BaselineCNN class
- Shrinks original tensor using these steps:
  Convolution Block Steps:
  1. nn.Conv2d (2D Convolution, extracts low-level features, then patterns, then deep feature extraction)
  2. nn.BatchNorm2d (Normalizes each feature channel, improves stability, speeds up training)
  3. nn.ReLU (Zeros negative values to introduce Non-Linearity, while keeping positive activations)
  4. nn.MaxPool2d (Reduces height and width of original tensor)
- Defined forward pass method

6. Tracked Loss and Accuracy of Model
- defined accuracy method (extracted from resulting logits, turned into probabilties with SoftMax function)
- defined epoch training method
- Used torch.no_grad() to disable gradient tracking for model evaluation

7. Run training on Baseline
- Trained the model for 14 epochs
- Listed best validation accuracy, test accuracy, and loss
- Best val_acc=0.9892
- Test acc=0.9886
- Test loss=0.0355

8. Learning Curves
- Loss curve showed training loss steadily decreasing for each epoch, while validation loss decreased sporadically
- Accuracy curve showed training accuracy steadily increasing for each epoch, with validation accuracy increasing sporadically

9. Results
- Output a list of most confident wrong predictions
- Returned a confusion matrix to show tendency of each class to return confident wrong predictions
- Listed out uncertain digits and their predictions, as well as their confidences












