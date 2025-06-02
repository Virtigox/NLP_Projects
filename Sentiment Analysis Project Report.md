# 📝 Project Overview

This project applies **Natural Language Processing (NLP)** techniques to classify the sentiment of tweets as either **positive** or **negative**. Using the **Sentiment140** dataset, the tweets were cleaned, vectorized, and used to train a **Logistic Regression** classifier. The project includes:

- Preprocessing real-world tweet data  
- Feature extraction using TF-IDF and CountVectorizer  
- Model training and evaluation  
- Custom sentiment prediction on new text

---

# 🗺️ Project Roadmap

## 1. Data Loading
- Downloaded Sentiment140 dataset using `kagglehub`.
- Loaded the CSV using `pandas` with `latin-1` encoding.

## 2. Data Cleaning
- Assigned meaningful column names:  
  `["target", "ids", "date", "flag", "user", "text"]`
- Removed unnecessary columns: `ids`, `date`, `flag`, `user`
- Cleaned the `text` column by:
  - Removing Twitter handles (`@username`)
  - Removing hyperlinks (`http...`)

## 3. Feature Extraction

### 🔹 TF-IDF Vectorization
- Used `TfidfVectorizer` with `stop_words="english"` and `max_features=500`  
- Transformed tweet text into feature vectors

### 🔹 Count Vectorization (Alternative)
- Tested `CountVectorizer` with the same parameters for comparison

## 4. Dataset Preparation
- Extracted the `target` column as `y` (label)
- Split dataset into training and testing sets (80/20 split)  
- Used stratification to maintain class balance

## 5. Model Training
- Trained a **Logistic Regression** model on the TF-IDF-transformed dataset
- Compared training and testing accuracies

## 6. Performance Evaluation
- **Training Accuracy**: `71.89%`
- **Testing Accuracy**: `71.95%`
- **Accuracy Score**: `71.95%`

### 📉 Confusion Matrix (Normalized)
```Python
[[True Negative: 33.5% | False Positive: 16.5%]
[False Negative: 11.6% | True Positive: 38.4%]]
```

## 7. Sentiment Prediction
- Tested model on new custom tweet inputs
- Classified each as **positive** or **negative** sentiment

---

# ⚠️ Challenges
- **Feature Extraction Limits**: Only 500 features were extracted; increasing this could improve results
- **Ambiguity in Sentiment**: Some tweets are inherently difficult to classify
- **Model Bias**: Logistic Regression is limited; alternatives like SVM, Random Forest, or BERT may improve accuracy

---

# ✅ Key Learnings
- Logistic Regression with TF-IDF performs well for basic sentiment classification tasks
- Proper **preprocessing** is crucial for handling social media data
- **Feature size** and selection significantly affect performance
