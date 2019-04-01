# Naive Bayes Classifier

This project was to code a Naive Bayes classifier from scratch. The algorithm and implementation style was of individual design. It was designed as a binary text classifier, with the possibility of it being performing multinominal classification. To evaluate this classifier, it was trained on game reviews in German with for sentiment analysis. The classifier evaluates whether the review was positive or negative. The 15 most highest weighted terms for each respective class were also generated beneath the classification and evaluation.
<br/>
<br/>

## Prerequisites
All libraries should come standard
{CSV, regex, random, collection, math}

<br/>
<br/>

```python
## dependecies
import csv
import re
import random
from collections import defaultdict
import math

```


## Cleaning the data
<br/>
<br/>
The data came for this project had four collumns: {game title, rating, author, review}.
The only relevent data for are the 2nd and third columns. For additional refinement, all non alphanumeric characters were removed from the data. The data was also normalized by making all tokens lowercase.

<br/>
<br/>

```python
## Cleaning Extracting the Dataset
data_set=[]
for num, dat in enumerate(data):
    dat[3] = re.sub(r'[^\w\säöüß]', ' ', dat[3].lower())
    data_set.append([num, dat[1],[token for token in dat[3].lower().split()]])

```

<br/>
<br/>

## Running the Code
<br/>
<br/>
This can be run directly in the notebook.
However you may require jupyter-notebook as well.


```bash
sudo apt-get install jupyter-notebook
```
<br/>
<br/>

## Initiation

For the initiation of the classifier, there are no hyperparamenters.  
In additon, several dictionaries are created for use during training.

```python
clf = Naive_Bayes()
```

### Train_test_Split Method
The train_test_split method takes three arguements. It accepts the data to be trained, the percentage of the split (percent 0 to 1) with a default of 0.85, and a random state for result replication. The method returns four separate arrays: training data, training labels, test data, and test labels.

```python
x_train, x_test, y_train, y_test = clf.train_test_split(data_set,0.90, random_state=42)
```

<br/>
<br/>

### Training Method

The training method takes two arguments, the data and the labels for the data. Within this method it calls an internal IDF method that stores IDF scores for each term in the lexicon. For each respective class, the term frequency calculated and conditional probablities are generated for each token. Return value is None.

<br/>
<br/>

### Prediction Method

The predict method takes in data without labels and calculates the probablity of each tweet with respect to each sentiment value. Tokens that do not appear in a given class are given probablities based on Laplace smoothing. The method then returns an argmax evalution for each respective review.


<br/>
<br/>

### Evaluation Method

The evaluation method generates confusion matrix values for each respective class and erforms Precision, Recall and F-1 measure on each respective class. In addition, it calculates the Macro and Micro scores for Percison, Recall and F-1 measure.

```python
output:
Class: gut 
 TP: 91681 FP: 19647 FN: 37 
 Precision: 0.8235214860592124 Recall: 0.9995965895462178 
 F1-score: 0.9030564502625021
Class: schlecht 
 TP: 78 FP: 37 FN: 19647 
 Precision: 0.6782608695652174 Recall: 0.003954372623574145 
 F1-score: 0.007862903225806453
Macro Precision: 0.7508911778122149 	Macro Recall: 0.501775481084896 	Macro F1 measure: 0.6015627211166565
Micro Precision: 0.8233715890634674 	Micro Recall: 0.8233715890634674 	Micro F1 measure: 0.8233715890634674

```
<br/><br/>

#### Notes on Evaluation

The given data was about 85% positive and only about 15% negative reviews. This particular dataset made the results of this classifier quite biased. In general, it predicted nearly 100% of the reviews to be possitive. 

<br/>
<br/>

## Expansion

Potential expansions for this classifier would include refining it for multinomial classification. In addition, vectorizing with tf-idf scores was an alternative to using conditional probabilities. Also, in the training data, if examples remained as plentiful but were more balanced, future evaluations may be more accurate and relyable. 
One more possible expansion would be an additional method to show which terms had the highest weights for each respective class.

<br/>
<br/>

## The Data

The data for this project was collected and distributed via the University of Stuttgart.
<br/>
<br/>
<br/>
<br/>

## Authors


* **King De Lany** - *Initial work* - [DelanyK](https://github.com/DelanyK)



## Acknowledgments

*This project was from the Information Retrieval and Text mining course and the University of Stuttgart. 
