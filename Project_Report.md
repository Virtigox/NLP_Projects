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
------------

- [ ] Build NLP model for Classification.
- [ ] Training model
- [ ] Measuring and Improving the accuracy
