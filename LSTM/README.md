# LSTM-Based Emotion Detection and Sentiment Classification

## 📌 Project Overview

This project uses a **Long Short-Term Memory (LSTM)** neural network to identify the emotion expressed in a given text.

The model is trained using the **dair-ai/emotion** dataset and classifies text into different emotion categories. After detecting the emotion, the system also maps the emotion to a broader sentiment category such as **Positive, Negative, or Neutral/Complex**.

## 🎯 Objectives

* Detect emotions from text using Deep Learning.
* Apply Natural Language Processing (NLP) techniques for text preprocessing.
* Convert text into numerical sequences using tokenization.
* Use an LSTM model for text classification.
* Predict the emotion and confidence score for new text.
* Categorize the predicted emotion into a sentiment group.

## 🗂️ Dataset

The project uses the **dair-ai/emotion** dataset available through the Hugging Face `datasets` library.

The dataset contains text samples associated with emotion labels.

The project uses the following emotion categories:

1. Sadness
2. Happiness
3. Love
4. Anger
5. Fear
6. Surprise
7. Shame
8. Guilt
9. Disgust
10. Confusion
11. Boredom
12. Relief
13. Sarcasm

## 🛠️ Technologies Used

* Python
* TensorFlow
* Keras
* NumPy
* Hugging Face Datasets
* LSTM
* Natural Language Processing (NLP)
* Deep Learning

## 🧠 Model Architecture

The LSTM model consists of the following layers:

```text
Input Text
    ↓
Tokenization
    ↓
Padding
    ↓
Embedding Layer
    ↓
LSTM Layer
    ↓
Dropout Layer
    ↓
Dense + Softmax
    ↓
Predicted Emotion
    ↓
Sentiment Classification
```

### Model Parameters

| Parameter               |                           Value |
| ----------------------- | ------------------------------: |
| Vocabulary Size         |                          12,000 |
| Embedding Dimension     |                             100 |
| LSTM Hidden Units       |                             128 |
| Maximum Sequence Length |                              60 |
| Dropout                 |                             0.3 |
| Batch Size              |                              64 |
| Epochs                  |                               5 |
| Output Classes          |                              13 |
| Optimizer               |                            Adam |
| Loss Function           | Sparse Categorical Crossentropy |

## 🔄 Project Workflow

### 1. Load Dataset

The `dair-ai/emotion` dataset is loaded using:

```python
from datasets import load_dataset

dataset = load_dataset("dair-ai/emotion")
```

### 2. Label Mapping

Emotion labels are converted into numerical IDs so that they can be used by the neural network.

```text
sadness   → 0
happiness → 1
love      → 2
anger     → 3
fear      → 4
...
sarcasm   → 12
```

### 3. Text Tokenization

The Keras `Tokenizer` converts text into numerical sequences.

An out-of-vocabulary token `<OOV>` is used for words that are not present in the vocabulary.

### 4. Sequence Padding

All text sequences are converted to a fixed length of **60 tokens**.

Sequences are padded and truncated using post-padding/truncation.

### 5. LSTM Model

The model contains:

* Input layer
* Embedding layer
* LSTM layer
* Dropout layer
* Dense output layer with Softmax activation

### 6. Model Training

The model is trained using:

* **Adam optimizer**
* **Sparse categorical crossentropy**
* **Accuracy** as the evaluation metric
* **5 epochs**
* **Batch size of 64**

### 7. Emotion Prediction

For new text, the system:

1. Tokenizes the input.
2. Pads the sequence.
3. Passes it through the trained LSTM model.
4. Finds the class with the highest probability.
5. Converts the class ID into an emotion.
6. Calculates the confidence score.

### 8. Sentiment Classification

The detected emotion is mapped into a broader sentiment category.

**Positive emotions:**

* Happiness
* Love
* Relief

**Negative emotions:**

* Sadness
* Anger
* Fear
* Shame
* Guilt
* Disgust
* Boredom

**Neutral/Complex:**

* Surprise
* Confusion
* Sarcasm

## 💻 Example

### Input

```text
I am extremely angry right now.
```

### Output

```text
MODEL PREDICTION

Input Text: I am extremely angry right now.
Predicted Emotion: anger
Sentiment: Negative
Confidence: <model-generated percentage>
```

The confidence value depends on the trained model's prediction.

## 📁 Project Structure

```text
LSTM-Emotion-Detection/
│
├── Lstm.ipynb
└── README.md
```

## 🚀 How to Run

### 1. Install Required Libraries

```bash
pip install numpy tensorflow datasets
```

### 2. Open the Notebook

Open:

```text
Lstm.ipynb
```

using Jupyter Notebook, JupyterLab, or VS Code.

### 3. Run the Cells

Run the notebook cells in order:

```text
Import Libraries
      ↓
Set Parameters
      ↓
Load Dataset
      ↓
Prepare Labels
      ↓
Tokenization
      ↓
Padding
      ↓
Build LSTM Model
      ↓
Compile Model
      ↓
Train Model
      ↓
Predict Emotion
      ↓
Predict Sentiment
```

## 🔮 Future Enhancements

The project can be extended by:

* Adding a web-based user interface.
* Adding real-time text emotion detection.
* Displaying prediction probabilities for all emotions.
* Saving and loading the trained model.
* Adding more text datasets.
* Improving the model using Bidirectional LSTM or other advanced architectures.
* Supporting emotion detection from social media or chat messages.

## ✅ Conclusion

This project demonstrates how **LSTM-based Deep Learning** can be applied to Natural Language Processing for emotion detection. The system processes text, predicts one of the defined emotion categories, and converts the detected emotion into a broader sentiment classification.

It provides a simple foundation for developing applications such as **emotion-aware chat systems, feedback analysis, text analytics, and sentiment-based applications**.
