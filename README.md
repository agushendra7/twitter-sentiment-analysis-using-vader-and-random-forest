# Twitter Sentiment Analysis Using Random Forest Classifier

I conducted a comparison of word weighting using Count Vectorizer and TF-IDF, in classifying sentiment on tweets of motorcycle racing events at Mandalika Circuit. The dataset was taken from Twitter in the form of tweets from February 04, 2022, to March 27, 2022, with a total dataset of `23526`. Then the dataset is cleaned to get a clean dataset that will be used to the next stage, using text preprocessing techniques. The clean dataset obtained is `21687`. After that, sentiment labeling will be carried out, using `Vader Sentiment`. The last stage is data modeling. Data modeling is done using the `Random Forest Classifier` method to get the final result in the form of a classification model and the results of the comparison between Count Vectorizer and TF-IDF word weighting. 

## Requirements
There are some general library requirements for the project and some which are specific to individual methods. The general requirements are as follows.

- `NumPy` [https://numpy.org] - Fast and versatile, the NumPy vectorization, indexing, and broadcasting concepts are the de-facto standards of array computing today.
- `Pandas` [https://pandas.pydata.org] - Fast, powerful, flexible, and easy-to-use open-source data analysis and manipulation tool.
- `NLTK` [https://www.nltk.org] - Standard Python library with prebuilt functions and utilities for ease of use and implementation.
- `Scikit-learn` [https://scikit-learn.org] - Simple and efficient tools for predictive data analysis.

The library requirements specific to some methods are:
- `Seaborn` [https://seaborn.pydata.org] - It provides a high-level interface for drawing attractive statistical graphics.
- `Matplotlib` [https://matplotlib.org] - Comprehensive library for creating static, animated, and interactive visualizations.
- `Swifter` [https://pypi.org/project/swifter] - A package that efficiently applies any function to a pandas data frame or series in the fastest available manner.

## Usage

### Preprocessing
Text pre-processing is carried out to ensure good data quality before being used during data analysis, and is able to change the data to be more structured. The stages carried out in text pre-processing include Case Folding¸ Tokenizing, Normalization, Stemming, and Filtering.
1. Case Folding => Case folding is a process where the program will read the text per row in the `Text` column, if there are characters that are uppercase or capital letters, they will be converted to lowercase or lowercase letters.
2. Tokenizing => In the tokenizing process, the text is separated into pieces called tokens, which are then analyzed. `Words`, `numbers`, `symbols`, `punctuation marks`, and other important entities can be considered tokens. In NLP, tokens are defined as "words" although tokenizing can also be done in paragraphs or sentences. The tokenizing process also removes `symbols`, `numbers`, `spaces`, and `links`.
3. Normalization => The normalization process will change words that are not standard into standard words and also correct words that are typos, abbreviations, or "slang" by matching terms or words that come from the previous tokenizing process with the normalization dictionary. If the word is in the normalization dictionary, then the word will be changed to the correct word or the word that should be. In this process, I added a normalization dictionary in Excel (.xlsx), with the name `kata_baku.xlsx`. The normalization dictionary is obtained from the source https://github.com/teguhary/Automated-labelling-Inset-Lexicon/blob/master/Data/kamus_kata_alay.xlsx.
4. Stemming => Stemming is the process of returning the root word of a word that has successfully gone through the normalization process. At this stage, a word will be converted into a base word until the word that has a prefix and suffix will be removed according to the base word. At this stage, I also use the `swifter` library to speed up the stemming process on the dataframe by running tasks in parallel. The processing speed can be twice or even faster if using `swifter`.
5. Filtering => Filtering is the process of removing words that have no meaning such as conjunctions. At this stage, I used English stopwords obtained from the NLTK library for filtering the data frame. I added the stopword list in the form of .txt with the name `stopword inggris.txt`.
