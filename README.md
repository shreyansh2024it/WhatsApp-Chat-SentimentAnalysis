
# WhatsApp Chat Sentiment Analysis

Uncover the Emotions Behind Your Chats: Dive into the Heart of Conversations with WhatsApp Chat Sentiment Analysis. Gain insights, discover trends, and decode the sentiment of your messages, all in one powerful tool.



## Export WhatsApp Chat 
1.Open Chat Click Option (Three dot)  
2.Tap on more  
3.Click Export chat  
4.Without Media  
5.Now use *.txt file


## Getting Started
Getting started with your WhatsApp chat sentiment analysis project involves setting up the environment, installing dependencies, and running the tool. Here's a step-by-step guide for users to get started.
## Prerequisites 

Before you begin, ensure you have the following prerequisites installed on your system:

Python 3.7+: The project is written in Python, so you'll need Python installed. You can download it from python.org.
## Installation

Clone The Repository

```bash
  git clone https://github.com/shreyansh2024it/WhatsApp-Chat-Sentiment_Analysis/blob/82cf5a914a80107dc71ab382f99b9cfe97e44134/Sentiment_Analysis.ipynb
```
Navigate to the project directory
```bash
  cd WhatsApp-Chat-Sentiment_Analysis
```




    
## Deployment

Importing the required libraries

```python
import re
import pandas as pd
import numpy as np
import emoji
from collections import Counter
import matplotlib.pyplot as plt
from PIL import Image
from wordcloud import WordCloud, STOPWORDS, ImageColorGenerator
```
Definition of Functions
```python
# Extract the Date time
def date_time(s):
    pattern='^([0-9]+)(\/)([0-9]+)(\/)([0-9]+), ([0-9]+):([0-9]+)[ ]?(AM|PM|am|pm)? -'
    result=re.match(pattern, s)
    if result:
        return True
    return False 

# Extract contacts
def find_contact(s):
    s=s.split(":")
    if len(s)==2:
        return True
    else:
        return False
    
# Extract Message
def getMassage(line):
    splitline=line.split(' - ')
    datetime= splitline[0];
    date, time= datetime.split(', ')
    message=" ".join(splitline[1:])
    
    if find_contact(message):
        splitmessage=message.split(": ")
        author=splitmessage[0]
        message=splitmessage[1]
    else:
        author=None
    return date, time, author, message
```
Analyse the sentiments
```python
df=pd.DataFrame(data, columns=["Date", "Time", "contact", "Message"])
df['Date']=pd.to_datetime(df['Date'])

data=df.dropna()
from nltk.sentiment.vader import SentimentIntensityAnalyzer
sentiments=SentimentIntensityAnalyzer()
data["positive"]=[sentiments.polarity_scores(i)["pos"] for i in data["Message"]]
data["negative"]=[sentiments.polarity_scores(i)["neg"] for i in data["Message"]]
data["neutral"]=[sentiments.polarity_scores(i)["neu"] for i in data["Message"]]

data.head()

x=sum(data["positive"])
y=sum(data["negative"])
z=sum(data["neutral"])

def score(a,b,c):
    if (a>b) and (a>c):
        print("Positive ")
    if (b>a) and (b>c):
        print("Negative")
    if (c>a) and (c>b):
        print("Neutal")

score(x,y,z)

```





## 🔗 Links

[![linkedin](https://img.shields.io/badge/linkedin-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/shreyansh-tripathi-264157206/)


