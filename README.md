# Getting started

## Tools

### Anaconda

If you plan to do data science with Python (which is a good idea), we recommend using Anaconda. Anaconda is a popular data science platform for Python and will make you happier.

To install Anaconda follow the instruction [here](https://www.continuum.io/downloads). After the installation is complete create a new environment called `junction` with some relevant packages (you can add more packages later):

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


### scikit-learn

Scikit-learn is a large machine learning library for Python. It contains most methods you can dream of and then some. If you want to do classification, clustering or regressions models, look no further.

More information from [Scikit-learn documentation](http://scikit-learn.org/stable/documentation.html).


### SentiWordNet

SentiWordNet is a word corpus with positive/negative sentiments. The easiest way to use SentiWordNet with Python is to download it with `nltk`, Natural Language Toolkit (if you plan on doing natural language processing, NTLK should prove useful in other ways too).

```
import nltk
# Download relevant corpora
nltk.download('wordnet')
nltk.download('sentiwordnet')

# Import SentiWordNet and check that it works.
from nltk.corpus import sentiwordnet as swn
print(swn.senti_synset('fast.a.01'))

# Example: print all synonyms of 'slow' ordered by negativity.
slowSynsets = list(swn.senti_synsets('slow'))
slowSynsetsWithScore = [(synset.neg_score(), synset) for synset in slowSynsets]
slowSynsetsWithScore = sorted(slowSynsetsWithScore, key=operator.itemgetter(0), reverse=True)
for negScore, term in slowSynsetsWithScore:
    print(negScore, term.synset.lemmas()[0].name(), '-', term.synset.definition())
```

Here are some examples on how to classify tweets with `nltk`:
[NLTK How-to - Sentiment Analysis](http://www.nltk.org/howto/sentiment.html)
[Twitter sentiment analysis using Python and NLTK](http://www.laurentluce.com/posts/twitter-sentiment-analysis-using-python-and-nltk/)

## Data

To get around API limitations and avoid excess load on external servers we have included few of the data sets in this repository.

### Hatebase
Hatebase.org has an API that can be used to download full data, but because of API limitations you can also find the full data set in directory `data/hatebase`.

### Trump tweets
All tweets from Donald Trump since 2008 can be found in directory `data/trump_tweets`. The data has been downloaded from [Trump Twitter Archive](http://trumptwitterarchive.com/).

