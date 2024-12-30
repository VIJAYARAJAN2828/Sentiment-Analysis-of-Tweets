# Sentiment Analysis of Tweets

This project performs sentiment analysis on the **Sentiment140 Dataset**, which contains 1,000,000 tweets annotated with sentiment polarity. The goal is to classify tweets as positive or negative based on their text content.

---

## Dataset Description

- **Dataset Source**: [Sentiment140 Dataset](https://www.kaggle.com/datasets/kazanova/sentiment140)
- **Annotations**:
  - `0`: Negative sentiment
  - `4`: Positive sentiment
  - `2`: Neutral sentiment (rarely present)
- **Fields**:
  - `target`: Sentiment polarity of the tweet (`0` or `4`).
  - `ids`: Unique identifier for the tweet.
  - `date`: Timestamp when the tweet was posted.
  - `flag`: Query used to retrieve the tweet, or `NO_QUERY` if none.
  - `user`: Username of the person who tweeted.
  - `text`: The actual tweet content.

---

## Project Workflow

### Preprocessing

1. **Column Renaming**  
   Renamed dataset columns to: `['target', 'Id', 'date', 'flag', 'user', 'text']`.

2. **Target Transformation**  
   Replaced target values as follows:
   - `0` → `0` (Negative sentiment)
   - `4` → `1` (Positive sentiment)

3. **Text Cleaning and Preprocessing**  
   The following steps were applied:
   - Removed non-alphabetic characters.
   - Converted text to lowercase.
   - Removed stop words using NLTK's stop words list.
   - Applied lemmatization using NLTK's `WordNetLemmatizer`.

4. ** Vectorization **

### Purpose
The text data, after preprocessing, is not directly usable for machine learning models. To convert this text data into numerical format, **TF-IDF Vectorization** was used. TF-IDF captures the importance of words in the dataset while reducing the impact of commonly occurring words.

### Method
- Transformed the cleaned text into feature vectors using **Scikit-learn's TF-IDF Vectorizer**.
- Ensured the vectorizer handles high-dimensional text data efficiently.

---

5. ** Model Development **

### Model Building
The primary model used for sentiment classification is **Logistic Regression**. It was chosen for its simplicity, interpretability, and efficiency for binary classification tasks.

### Steps
1. Trained the model on the TF-IDF-transformed features from the dataset.
2. Evaluated the model on test data to ensure its accuracy in classifying sentiment.

---

6. ** Model Saving **

To allow reuse of the trained model without retraining it each time, the model was saved using **Joblib**. This ensures faster deployment and efficient storage of the trained model.

## **✨ Real-Time Prediction ✨**

The model is integrated with a tool to predict the sentiment of real-time tweets fetched from the **X API**. Users can input any tweet or real-time tweet data, and the model will classify it as either **positive** or **negative**.

### 🚀 **Try It Out**  
👉 [**Click here to try the real-time prediction tool**](#https://x.com/sudi0ne/status/1716739204011405583) <!-- Replace # with the actual link -->

