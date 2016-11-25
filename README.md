# Smartly.io | Junction Hackathlon 2016

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Tools of the trade](#tools-of-the-trade)
  - [Anaconda](#anaconda)
  - [Pandas](#pandas)
  - [scikit-learn](#scikit-learn)
  - [SentiWordNet](#sentiwordnet)
- [Data sets](#data-sets)
  - [Hatebase](#hatebase)
  - [Trump tweets](#trump-tweets)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## Tools of the trade

### Anaconda

If you plan to do data science with Python (which is a good idea), we recommend using Anaconda. Anaconda is a very handy data science platform for Python and will make you happier.

First install Anaconda from [here](https://www.continuum.io/downloads). After the installation is complete create a new environment called `junction` with some relevant packages (you can add more packages later):

```
conda create --name junction python=3.5 ipykernel pandas scikit-learn nltk
source activate junction
ipython kernel install --user --name junction
jupyter notebook
```

The last line will launch the Jupyter notebook server at localhost:8888 and should open it in your browser.

To start working create a new notebook by clicking the "New" button in top right corner, select "Python [junction]". Each notebook consists of multiple cells. The shortcut to execute the code in one cell is Shift-Enter. Notebook has two modes, Command Mode (indicated by blue frame; press Esc to enable) and Edit mode (green frame; press Enter to enable). To create a new cell below current one press "b" while in Command mode. You can see all keyboard shortcuts from "Help > Keyboard Shortcuts".


If you ever stop the server you can restart it with:
```
source activate junction
jupyter notebook
```

### Pandas

Pandas is a Python module for handling tabular data (rows and columns, think of Excel).

Here are some useful places to start:
- [10 minutes to pandas](http://pandas.pydata.org/pandas-docs/stable/10min.html)
- [Pandas cheat sheet](http://www.webpages.uidaho.edu/~stevel/504/Pandas%20DataFrame%20Notes.pdf)

### scikit-learn

Scikit-learn is a large machine learning library for Python. It contains most methods you can dream of and then some. If you want to do classification, clustering or regressions models, look no further.

More information from [Scikit-learn documentation](http://scikit-learn.org/stable/documentation.html).


### SentiWordNet

SentiWordNet is a word corpus with positive/negative sentiments. The easiest way to use SentiWordNet with Python is to download it with `nltk`, Natural Language Toolkit (and if you plan to do natural language processing, NTLK should prove useful in other ways too).

```
import nltk
# Download relevant corpora
nltk.download('wordnet')
nltk.download('sentiwordnet')

# Import SentiWordNet and check that it works.
from nltk.corpus import sentiwordnet as swn
print(swn.senti_synset('fast.a.01'))

# Example: print synonyms of 'slow' ordered by negativity.
slowSynsets = list(swn.senti_synsets('slow'))
slowSynsets = sorted(slowSynsets, key=lambda x: -x.neg_score())
for term in slowSynsets:
    print(term.neg_score(), term.synset.lemmas()[0].name(), '-', term.synset.definition())
```

Here are some examples on how to classify tweets with `nltk`:
- [NLTK How-to - Sentiment Analysis](http://www.nltk.org/howto/sentiment.html)
- [Twitter sentiment analysis using Python and NLTK](http://www.laurentluce.com/posts/twitter-sentiment-analysis-using-python-and-nltk/)

## Data sets

To get around API limitations and avoid excess load on external servers we have included few of the data sets in this repository.

### Hatebase
Hatebase.org has an API that can be used to download full data, but because of API limitations you can also find the full data set in directory `data/hatebase`.

### Trump tweets
All tweets from Donald Trump since 2008 can be found in directory `data/trump_tweets`. The data has been downloaded from [Trump Twitter Archive](http://trumptwitterarchive.com/).

