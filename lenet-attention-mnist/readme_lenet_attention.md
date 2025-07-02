# LeNet vs. AttentionLeNet on MNIST

## Overview

We compare two CNN architectures on MNIST:

- **Standard LeNet**: Classic LeNet-5 variant with:
  - Conv1: 6 filters, 5×5, padding=2 → ReLU → AvgPool 2×2
  - Conv2: 16 filters, 5×5, padding=0 → ReLU → AvgPool 2×2
  - FC layers: 120 → 84 → 10 units

- **AttentionLeNet**: LeNet augmented with CBAM (Convolutional Block Attention Module) blocks after each convolutional layer to provide channel and spatial attention.

## Experimental Setup

- **Optimizer**: Adam, learning rate 0.001
- **Batch size**: 16
- **Epochs**:
  - LeNet: 30
  - AttentionLeNet: 30 (initial), then extended to 40
- **Loss**: CrossEntropyLoss
- **Device**: CUDA (GPU)

## Results

### LeNet (30 epochs)

- Training Accuracy: 97.07%  
- Testing Accuracy: 95.67%

### AttentionLeNet

- **30 epochs**:
  - Training Accuracy: 94.48%  
  - Testing Accuracy: 92.00%
- **40 epochs**:
  - Training Accuracy: 97.93%  
  - Testing Accuracy: 95.33%

| Model              | Epochs | Train Acc | Test Acc |
|--------------------|--------|-----------|----------|
| LeNet              | 30     | 97.07%    | 95.67%   |
| AttentionLeNet     | 30     | 94.48%    | 92.00%   |
| AttentionLeNet     | 40     | 97.93%    | 95.33%   |

## Analysis

- **Attention training curve**: AttentionLeNet underperforms initially but catches up with extended epochs, indicating that the CBAM blocks require more time to learn effective attention weights.
- **Generalization**: After 40 epochs, AttentionLeNet nearly matches LeNet’s test performance, demonstrating attention’s potential when fully trained.

## Insights

- Adding attention does not guarantee immediate gains on a simple task like MNIST.
- **Training duration** is critical—attention mechanisms often need more epochs to converge.
- **Hyperparameters** (e.g., CBAM reduction ratio) significantly affect performance.

## Usage

1. Clone the repo:

  ```bash
  git clone [https://github.com/Omarkhaled711/deep-learning-projects.git](https://github.com/Omarkhaled711/deep-learning-projects.git);
  cd lenet-attention-mnist
  ```

2. Install dependencies:

```bash
pip install -r requirements.txt
```
