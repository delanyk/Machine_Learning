# Naive Bayes Classifier

This project was to code a Naive Bayes classifier from scratch. The algorithm and implemenation style was of individual design. It was designed as only as a binary text classifier.  To evaluate this classifier, it was trained on game reviews in German with for sentimate analysis. The classifier evaluates whether the review was positive or negative.
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

### Initiation

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



<br/>
<br/>

### Prediction Method




<br/>
<br/>

### Evaluation Method



<br/>
<br/>

### Micro/Macro F-scores




<br/>
<br/>

## Expansion
<br/>
<br/>

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
