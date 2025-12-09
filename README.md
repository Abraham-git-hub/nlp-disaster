# Natural Language Processing with Disaster Tweets

Binary text classification using deep learning (RNN/LSTM/GRU) to identify real disaster tweets from metaphorical language.

[![Kaggle](https://img.shields.io/badge/Kaggle-Competition-20BEFF)](https://www.kaggle.com/c/nlp-getting-started)
[![Python](https://img.shields.io/badge/Python-3.8+-blue)](https://www.python.org/)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-orange)](https://www.tensorflow.org/)

## 📋 Project Overview

This project implements multiple Recurrent Neural Network (RNN) architectures to classify tweets as either referring to real disasters or using disaster-related terms metaphorically. This is a solution for the Kaggle competition: [Natural Language Processing with Disaster Tweets](https://www.kaggle.com/c/nlp-getting-started).

### Problem Statement
Social media platforms like Twitter are important communication channels during emergencies. However, not all tweets containing disaster-related keywords actually refer to real disasters. This project aims to build a machine learning model that can automatically distinguish between real disaster tweets and non-disaster tweets.

**Examples:**
- "Earthquake hits California, magnitude 6.5" → **Real Disaster** ✓
- "The concert was an absolute disaster!" → **Not a Disaster** ✗

## 🎯 Project Objectives

- Perform comprehensive Exploratory Data Analysis (EDA) on tweet data
- Implement text preprocessing and cleaning techniques
- Build and compare multiple RNN architectures (LSTM, GRU, Bidirectional)
- Train models with proper hyperparameter tuning
- Evaluate and analyze model performance
- Generate predictions for Kaggle submission

## 📊 Dataset

- **Training Set:** 7,613 tweets with binary labels
- **Test Set:** 3,263 tweets
- **Features:**
  - `text`: The tweet content (primary feature)
  - `keyword`: Disaster-related keyword (optional)
  - `location`: Tweet location (optional)
  - `target`: Binary label (1 = disaster, 0 = not disaster)

## 🏗️ Model Architectures

This project implements and compares four different RNN architectures:

1. **Simple LSTM**
   - Single LSTM layer
   - Fast training, good baseline
   
2. **GRU (Gated Recurrent Unit)**
   - Alternative to LSTM with fewer parameters
   - Faster training, similar performance
   
3. **Bidirectional LSTM**
   - Processes text in both directions
   - Better context understanding
   
4. **Deep Bidirectional LSTM**
   - Stacked LSTM layers
   - Captures hierarchical features

## 🔧 Technologies & Libraries

- **Python 3.8+**
- **Deep Learning:** TensorFlow 2.x, Keras
- **Data Processing:** Pandas, NumPy
- **Visualization:** Matplotlib, Seaborn
- **NLP:** NLTK, Keras Preprocessing
- **ML Tools:** Scikit-learn

## 📁 Project Structure

```
├── Disaster_Tweets_NLP_Classification.ipynb  # Main analysis notebook
├── train.csv                                  # Training data
├── test.csv                                   # Test data
├── sample_submission.csv                      # Submission format
├── submission.csv                             # Generated predictions
├── requirements.txt                           # Python dependencies
├── README.md                                  # This file
└── models/                                    # Saved model weights
    ├── lstm_best.keras
    ├── gru_best.keras
    ├── bilstm_best.keras
    └── deep_bilstm_best.keras
```

## 🚀 Getting Started

### Prerequisites

```bash
Python 3.8 or higher
pip (Python package manager)
```

### Installation

1. **Clone or download the repository**

2. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

3. **Download the data:**
   - Option 1: Download from [Kaggle Competition Page](https://www.kaggle.com/c/nlp-getting-started/data)
   - Option 2: Use Kaggle API:
     ```bash
     kaggle competitions download -c nlp-getting-started
     unzip nlp-getting-started.zip
     ```

### Running the Project

**Option 1: Run Jupyter Notebook Locally**
```bash
jupyter notebook Disaster_Tweets_NLP_Classification.ipynb
```

**Option 2: Run on Kaggle (Recommended)**
- Upload the notebook to Kaggle
- Enable GPU accelerator
- Run all cells

**Option 3: Run on Google Colab**
- Upload notebook to Colab
- Upload CSV files or mount Google Drive
- Run all cells

## 📈 Results

### Model Performance

| Model | Val Accuracy | Precision | Recall | F1 Score |
|-------|--------------|-----------|--------|----------|
| Simple LSTM | ~0.80 | ~0.78 | ~0.82 | ~0.80 |
| GRU | ~0.81 | ~0.79 | ~0.83 | ~0.81 |
| Bidirectional LSTM | ~0.82 | ~0.80 | ~0.84 | ~0.82 |
| Deep Bidirectional LSTM | ~0.81 | ~0.79 | ~0.83 | ~0.81 |

*Note: Actual results may vary based on training runs*

### Key Findings

- **Best Model:** Bidirectional LSTM achieved the highest F1 score
- **Training Time:** GRU was fastest, Deep BiLSTM was slowest
- **Overfitting:** Dropout and early stopping effectively prevented overfitting
- **Context Matters:** Bidirectional processing significantly improved performance

## 🧪 Methodology

### 1. Data Preprocessing
- Text cleaning (URLs, mentions, special characters removal)
- Tokenization with vocabulary size of 10,000
- Sequence padding to fixed length (100 tokens)
- Train-validation split (80-20)

### 2. Model Training
- **Optimizer:** Adam
- **Loss Function:** Binary Crossentropy
- **Metrics:** Accuracy, Precision, Recall, F1 Score
- **Callbacks:** Early Stopping, Learning Rate Reduction, Model Checkpoint
- **Epochs:** Up to 15 (with early stopping)
- **Batch Size:** 32

### 3. Evaluation
- Validation accuracy and loss tracking
- Confusion matrix analysis
- Classification report (precision, recall, F1)
- Comparison across all models

## 📝 Key Learnings

### What Worked Well
✅ Bidirectional processing captured context effectively  
✅ Proper dropout prevented overfitting  
✅ Learning rate scheduling improved convergence  
✅ Text cleaning significantly improved performance  

### What Could Be Improved
🔄 Pre-trained embeddings (GloVe, Word2Vec)  
🔄 Transformer models (BERT, RoBERTa)  
🔄 Ensemble methods  
🔄 Data augmentation techniques  

## 🔮 Future Work

1. **Advanced Architectures:**
   - Implement BERT/transformer models
   - Try CNN-LSTM hybrid architectures
   - Experiment with attention mechanisms

2. **Feature Engineering:**
   - Use pre-trained word embeddings
   - Include sentiment analysis features
   - Leverage keyword and location data

3. **Model Optimization:**
   - Hyperparameter tuning with Optuna/Keras Tuner
   - Ensemble multiple models
   - Cross-validation for robust evaluation

4. **Data Augmentation:**
   - Back translation
   - Synonym replacement
   - Contextual word embeddings

## 📚 References

1. Hochreiter & Schmidhuber (1997) - Long Short-Term Memory
2. Cho et al. (2014) - Learning Phrase Representations using RNN Encoder-Decoder
3. TensorFlow/Keras Documentation
4. Kaggle NLP Getting Started Competition

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

## 🙏 Acknowledgments

- Kaggle for hosting the competition and providing the dataset
- TensorFlow and Keras teams for excellent deep learning frameworks
- Course instructors and peers for guidance and feedback

---

**⭐ If you found this project helpful, please give it a star!**

---

*This project was completed as part of a machine learning course assignment.*
