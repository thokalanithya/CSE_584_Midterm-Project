# CSE 584 Midterm Project
CSE 584 Midterm Project

## LLM Output Classification Project

This project aims to classify which large language model (LLM) generated given output texts. Two distinct models were used:

1. Stella Embeddings with a Neural Network Classifier
2. Fine-tuned BERT Model with its Tokenizer

## Project Overview

The main goal of this project was to create models capable of distinguishing the outputs generated by different LLMs. The dataset used contained LLM outputs paired with the corresponding prompts. To solve this problem, two approaches were adopted: a custom embedding-based neural network classifier using Stella embeddings, and a transformer-based classifier leveraging a fine-tuned BERT model.

### 1. Stella Embeddings + Neural Network Classifier

- **Embedding Generation**: Used the pre-trained dunzhang/stella_en_1.5B_v5 model from Hugging Face to generate embeddings for input prompts and LLM-generated outputs. Each text (prompt and output) was separately encoded, and the resulting embeddings were combined.
- **Neural Network Classifier**: The combined embeddings were then passed into a simple feedforward neural network to predict which LLM was used to generate the output.
- **Training**: The neural network was trained on these embeddings, with training accuracy and loss monitored to ensure convergence.

### 2. Fine-tuned BERT Model

- **Model Selection**: bert-base-uncased from the Hugging Face library was chosen for fine-tuning. This pre-trained model was selected due to its general-purpose nature and well-documented training stability.
- **Tokenizer**: The BERT tokenizer was used to prepare the input data for the model. Specifically, both the input prompt and LLM-generated output were tokenized separately.
- **Fine-tuning**: BERT was fine-tuned on the dataset to classify the LLM that generated each given output. Only selected layers of BERT were fine-tuned to reduce computational cost and prevent overfitting.

## Data Curation

For the data curation process, we focused on generating a dataset using several language models, all under 3 billion parameters. We utilized the Ollama library to manage these models and perform sentence completions on the HellaSwag dataset, which served as our input source. This code is designed to compare multiple Large Language Models (LLMs) by generating text completions and measuring the time it takes for each model to respond. The code utilizes the langchain and langchain_ollama libraries to interact with these LLMs, allowing users to input text prompts and evaluate the model's output. The models were selected based on their size to ensure efficiency and compatibility with local hardware resources, as all operations were run on a local macOS machine.

The models used for this task included:

- LLaMA 3.2 (1B): (llama3.2:1b)
- Gemma 2b: (gemma2:2b)
- Qwen 2.5 (3B): (qwen2.5:3b)
- Phi-3.5 (3B): (phi3.5)
- TinyLlama (1.1B): (tinyllama)
- nemotron-mini (1B): (nemotron-mini)

We curated 60,000 texts in total, with 10,000 texts generated by each model. The dataset included text completions from two sources: Wikipedia and the HellaSwag sentence completion dataset.

### Running the Data Generation Script
Run the ml.py file with the correct path to the dataset to generate the dataset.

### Dataset Details

We curated a dataset of 60,000 text completions, with 10,000 completions from each model. The data was generated using two main sources:

- Wikipedia: Used to provide a diverse set of inputs based on general knowledge and facts.
- HellaSwag Sentence Completion Dataset: Used to evaluate the models' ability to complete sentences in a challenging and contextually complex manner.

This curated dataset was then utilized in training and testing our models, providing valuable insights into the performance of various LLMs in sentence completion tasks.

## Training Details

- **Stella+NN Classifier**: The neural network model was trained using the combined embeddings from dunzhang/stella_en_1.5B_v5. The training loop included monitoring accuracy and loss per epoch.
- **Fine-tuned BERT**: The BERT model was fine-tuned for text classification with a focus on adjusting only a subset of its layers. The model training included monitoring both training loss and accuracy for each epoch.

## Results

- **Stella+NN Classifier**: Achieved an accuracy of 85% on the test set.
- **Fine-tuned BERT**: Achieved an accuracy of 89.92% on the test set.
- **Label Analysis**: Further analysis was conducted on the predictions to determine which labels were most frequently predicted by each model. Graphs were also created to visualize model performance and prediction distribution.

## Graphical Analysis

Graphs were generated to provide a visual understanding of:

- Loss and Accuracy per Epoch: Showing the training process for each model.
- Label Distribution: Highlighting the most frequent predictions for each model to identify any biases.

## Usage

To use either of the models, you can follow the steps in the provided code to:

1. Load the pre-trained Stella or BERT model.
2. Preprocess your dataset by encoding the input prompts and outputs.
3. Train the classifier or directly use the pre-trained/fine-tuned models for inference.

## Requirements

- Python 3.7+
- PyTorch
- Transformers
- SentenceTransformers
- scikit-learn
- pandas

## Running the Code

1. Clone the repository and install the dependencies.
2. Run midsem-project.ipyb file.
3. The dataset in a CSV file is created with columns: Input Prompt, LLM Output, and Used LLM. or You can use the .csv file train your models.
4. The training script is run to train the Roberta model and gives train and test accuracy for various experiments.

## Future Work

- Model Improvements: Experiment with more advanced architectures or ensemble methods to improve accuracy.
- Generalizability: Train the model on outputs from more diverse LLMs to improve generalizability.

## License

This project is open-source under the MIT License.
