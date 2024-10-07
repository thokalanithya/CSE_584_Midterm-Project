# CSE 584 Midsem Project

# LLM Classifier

This project implements a deep learning classifier to identify which Large Language Model (LLM) was used to generate a given text completion. The classifier is based on the RoBERTa model, fine-tuned on a dataset of text pairs consisting of original truncated text and its LLM continuation.

## Features

- Custom RoBERTa-based classifier for LLM identification
- Preprocessing pipeline for text data
- Training loop with optimization techniques
- Evaluation metrics and early stopping
- Experiments with various hyperparameters and model configurations

## Requirements

- Python 3.7+
- PyTorch
- Transformers
- pandas
- scikit-learn
- numpy

## Installation

1. Clone the repository

2. Install the required packages

## Usage

1. Prepare your dataset in CSV format with columns: 'original text', 'completed text', and 'model'.
2. Update the file path in the script to point to your dataset
3. Run the training script


## Model Architecture

The classifier uses a custom RoBERTa architecture with:
- Dropout layer (30% rate) for regularization
- ReLU and Leaky ReLU activation functions
- Final linear layer for classification

## Training Process

- Optimizer: AdamW with learning rate 3e-5 and weight decay 1e-4
- Learning rate scheduler: Linear schedule with warmup
- Loss function: CrossEntropyLoss
- Gradient clipping (max norm: 1.0)
- Early stopping with patience of 3 epochs

## Results

The model achieves a validation accuracy of approximately 75% in identifying the LLM used for text completion. Detailed results and analysis can be found in the project report.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.


