# Project Overview

This project applies **Natural Language Processing (NLP)** techniques to classify the sentiment of tweets as either **positive** or **negative**. Using the **Sentiment140** dataset, the tweets were cleaned, vectorized, and used to train a **Logistic Regression** classifier. The project includes:

- Preprocessing real-world tweet data  
- Feature extraction using TF-IDF and CountVectorizer  
- Model training and evaluation  
- Custom sentiment prediction on new text

---

# Project Roadmap

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

### TF-IDF Vectorization
- Used `TfidfVectorizer` with `stop_words="english"` and `max_features=500`  
- Transformed tweet text into feature vectors

### Count Vectorization (Alternative)
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

# Challenges
- **Feature Extraction Limits**: Only 500 features were extracted; increasing this could improve results
- **Ambiguity in Sentiment**: Some tweets are inherently difficult to classify
- **Model Bias**: Logistic Regression is limited; alternatives like SVM, Random Forest, or BERT may improve accuracy

---

# Key Learnings
- Logistic Regression with TF-IDF performs well for basic sentiment classification tasks
- Proper **preprocessing** is crucial for handling social media data
- **Feature size** and selection significantly affect performance

---

# Results & Observation

The project yielded the following key observations:

* **Feature Importance in Different Datasets:** The findings suggest a significant difference in the optimal number of features required for sentiment analysis based on the nature of the text data. While a relatively small number of features (e.g., 100) proved sufficient for achieving optimal accuracy with product-oriented Amazon reviews (as observed in prior work or comparisons), the analysis of 1.6 million diverse tweets necessitates a significantly larger number of features.
* **Tweet Data Variability:** The increased need for features in the tweet dataset is attributed to the broader range of vocabulary, linguistic styles, and topics present in social media text compared to the more constrained language of product reviews. A higher dimensionality of features allows the model to capture the nuances and complexities of tweet sentiment more effectively.
* **Accuracy vs. Computational Cost:** The project likely involved a trade-off analysis between the number of features extracted and the resulting model accuracy, considering the computational resources and time required for training and prediction on such a large dataset. The goal was to identify a feature count that provides a good balance between performance and efficiency.
* **Error Analysis:** The confusion matrix provided valuable insights into the types of errors the model makes, distinguishing between false positives (incorrectly classifying a negative tweet as positive) and false negatives (incorrectly classifying a positive tweet as negative). This information is crucial for further model refinement.
* **Qualitative Validation:** The testing with custom sentences offered a qualitative assessment of the model's ability to generalize and correctly predict the sentiment of new, unseen text examples.

## Conclusion

This project successfully implemented a sentiment analysis pipeline for a large Twitter dataset using machine learning techniques. The findings highlight the importance of considering the characteristics of the text data when determining the optimal number of features for model training. The diversity and complexity of tweet content necessitate a higher feature dimensionality compared to more domain-specific text. The evaluation metrics, including accuracy and the confusion matrix, provide a quantitative measure of the model's performance, while the validation with custom texts offers a qualitative understanding of its predictive capabilities. Further work could focus on exploring more advanced text preprocessing techniques, experimenting with different machine learning models, and optimizing the feature extraction process for improved accuracy and efficiency.
