# Project Roadmap

- [X] **Data Scrapping**
    - Scrapping text dataset from public websites where scrapping is legal.
    - Citing the website.
    - Convert into .txt format.
- [X] **Data Cleaning**
    - This step not actively involved since the scrapped text are ready to be processed.
- [X] **Data processing**
    - Turn the words of indviduals articles, or news into tokens
    - Make a bag-of-words, or a dictionary that describe the frequency of each words
    - Convert the key values of dictionary into integer id - words_id
    - Calculate the TFIDF(Term Frequency Inverse Document Frequency) of each words.
- [X] **Topic Identification**
    - Extract the most significant keywords from each articles
    - Idenfity which keywords describe which article.
    - This approach could be improved by more data cleaning, and emphasizing only the document materials of the webpage or articles.
    - There is not much of a challenges, but trying to be more modular such as splitting into smaller functions and compatible with other functions is ambigious.

- [X] **Data preparation for Classification**
    - Get the .csv dataset
    - load the data with pandas to create a table/dataframe.
    - Access the "label" columns and use its values as `y`.
    - Set the two groups of training sets and test sets: `x` and `y`.
    - Create two different vectorizers: `CountVectorizer` and `TfidfVectrizer`, to produce transformed, and fitted test, and training data.

- [X] **Training and Testing the model**
    - Build a classification model from `MultinomialNB` of `naive_bayes`.
    - Fit the training dataset, and predict the result with test dataset.

- [X] Measuring and Improving the accuracy
    - Check the acuuracies of two different models: one with dataset from `CountVectorizer`, and other from `TfidfVectorizer`
    - By testing different alpha values while training models, we will know which alpha value resulted higher accuracy.
    - This model could be imporoved by using more datasets, and better classification model.
    - CounterVectorizer's train and test dataset gives more accurate prediction compares to TfidfVectorizer.
- [X] **Challenges**
    - `.get_feature_names()` of both vectorizers is no longer callable; therefore I replaced with `.get_feature_names_out()`
    - `.coef_[0]` for nb_classifier also no longer usuable; therefore I replaced with `.feature_log_prob_[0]`
