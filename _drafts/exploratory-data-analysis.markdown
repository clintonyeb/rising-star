---
layout: post
title:  "Exploratory Data Analysis"
categories: data-science python machine-learning
tags: data-science python data science machine-learning
---

There are three most important steps in data science: Exploratory Data Analysis (EDA), Model Selection, and Hyperparameter Tuning. Mastering machine learning refers to mastering each of these steps. In this article, we are going to understand some of the popular ways of approaching EDA, and we will be able to build better intuition for it.

Exploratory Data Analysis is the process of exploring or analyzing data to gain insights and summarize their features. EDA is an open-ended and iterative process where we calculate statistics and make figures to find trends, anomalies, patterns, or relationships within data. The goal of EDA is to learn what our data can tell us. It generally starts with a high level overview, then narrow down in to specific areas as our understanding of the data grows.The findings may be interesting in their own right: they can inform us about our model choices, including which features of the data are most relevant.

EDA is the first step of data analysis that brings you closer to the data to gain an intuition about the data. It provides a somewhat abstract overview about the various features in the data including how they affect each other and how they contribute to our target variable. As part of EDA also is extracting additional features (feature engineering), and removing unnecessary ones (dimensionality reduction).

## Where do we begin

Lets say a client gave you a data and asked you to take a look and see if you can find some information from it. Well, where do you begin to look? And what follows from that? The first step is to load the data in to your working environment.

## Loading the Data

Lets start by loading the data. Python provides a set of utilities to accomplish this, and depending on the source of source of the data, your approach will be different.
The simplest one is when the data is given as CSV files. Then you could simply load them like this:

```python
import pandas as pd

train_data = pd.read_csv(os.path.join(DATA_PATH, 'train.csv'))
```
The Pandas library from Python provides a wealth of tools for loading data in this format based on your need.

Sometimes also, you may need to download the dataset yourself. Downloaded dataset may come compressed and will also require decompressing.

```python
from six.moves import urllib

def fetch_data(data_url, download_path):
    if not os.path.isdir(download_path):
        os.makedirs(download_path)
    urllib.request.urlretrieve(data_url, download_path)
```
The function above first checks if the download directory exists, and if not not, creates itt before it downloads the files. It then downloads the file at the data_url (example: https://raw.githubusercontent.com/ageron/handson-ml/master/datasets/housing/housing.tgz) and save it at the locally given download path (example: /home/username/data)

Once the data file is download, you may have to take extra steps to decompress it, the steps to decompress depends on the kind of the file, popular compress formats include zip, gz, and tgz.

Here are example of inflating tgz file.

```python
import tarfile

def decompress_tgz_file(file_path, location):
    tar_file = tarfile.open(file_path)
    tar_file.extractall(path=location)
    tar_file.close()
```
Another popular file format is gz:

```python
def decompress_gz_file(file_path, destination_file):
    with gzip.open(file_path, 'rb') as f_in:
        with open(destination_file, 'wb') as f_out:
            shutil.copyfileobj(f_in, f_out)
```

This opens the gz file (file_path) and outputs its content into the destination file (destination_file).

These are just examples, you may receive files in other formats, just look around and you will find a way to put the file in a format that you can work with.

Lets see the data files we have:

```python
import os

def print_files_directory(data_path='.'):
    os.listdir(path=data_path)
```
The function above will print all the files in a given directory.

Example, in my case:

```python
In [9]: os.listdir(path='/home/clint/Projects/ML/machine-learning-practice/data/
   ...: mnist/')
Out[9]: ['train.csv', 'test.csv']
```
In the above example, I am making use of the Ipython shell. In[?] means a command I run and Out[?] means the output of the command.

Once we know which files we were given, we can safely load them using our initial approach to loading data.

```python
import pandas as pd

train_data = pd.read_csv(os.path.join(DATA_PATH, 'train.csv'))
test_data = pd.read_csv(os.path.join(DATA_PATH, 'test.csv'))
```

Okay, so our data is loaded into our working environment, what next?

## A Peek into the Data

Once the data, is loaded, you will want to see what's in it right? This is called peeking (probably made this name up, but anyway it will do the job). Peeking into the data means looking at data items in each file, the size of the data in terms of rows and columns in them. Let see how this is usually done.

Lets see how many columns and rows we have:

```python
print("Size of training data is", train_data.shape)
print("Size of testing data is", test_data.shape)
```

This will give you the shape of the data in terms of its rows and columns. For example, (4000, 25). This means that the data file has 4000 rows and 25 columns.

## Bivariate Analysis

## Multivariate Analysis

## Missing Values

## Outliers
