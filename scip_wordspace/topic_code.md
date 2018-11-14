---
title: "topic_code"
author: "Erin M. Buchanan"
date: "11/14/2018"
output: 
  html_document:
        self_contained: no
---

First, you would need to load the libraries for the Topic Modeling packages:


```r
library(tm)
library(topicmodels)
library(slam)
library(lsa)
```

Then, you could load a dataset you are interested in working with:


```r
importdf = read.csv('exam_answers.csv', header = F, stringsAsFactors = F)
```

From these documents, we will create a corpus (a set of text documents). Because our data is in one column in our dataset, we will use `VectorSource()` to create the corpus:


```r
import_corpus = Corpus(VectorSource(importdf$V1))
```

When you perform these analyses, you usually have to edit the text. Therefore, we are going to lower case the words, take out the punctuation, and remove English stop words (like *the, an, a*). This step will also transform the documents in a term (words) by document matrix. 


```r
import_mat = DocumentTermMatrix(import_corpus,
                                control = list(stemming = TRUE, #create root words
                                               stopwords = TRUE, #remove stop words
                                               minWordLength = 3, #cut out small words
                                               removeNumbers = TRUE, #take out the numbers
                                               removePunctuation = TRUE)) #take out punctuation 
```

Then you would want to weight that matrix to help control for the sparsity of the matrix. That means you are controlling for the fact that not all words are in each document, as well as the fact that some words are very frequent. Then you usualy ignore very frequent words and words with zero frequency. 


```r
#weight the space
import_weight = tapply(import_mat$v/row_sums(import_mat)[import_mat$i], import_mat$j, mean) *
  log2(nDocs(import_mat)/col_sums(import_mat > 0))

#ignore very frequent and 0 terms
import_mat = import_mat[ , import_weight >= .1]
import_mat = import_mat[ row_sums(import_mat) > 0, ]
```

First, you will pick a number of expected topics - which is the k option. The SEED should be a random number to start the analysis on. There are several model types:

    - LDA stands for Latent Dirichlet Allocation, which estimates topcis based on the idea that every document includes a mix of topics, and every topic includes a mix of words. The LDA Fit model includes this analysis with VEM (variational expectation-maximization) algorithm and estimating an alpha.
    - The LDA Fixed model using the VEM algorithm with a fixed alpha value. 
    - Last, the LDA Gibbs option uses a Gibbs (Bayesian) algorithm to fit the data. 
    - CTM stands for correlated topics models, which allows the correlation between topics, and this method uses a VEM algorithm.


```r
k = 5 #set the number of topics

SEED = 2010 #set a random number 

LDA_fit = LDA(import_mat, k = k, control = list(seed = SEED))

LDA_fixed = LDA(import_mat, k = k, control = list(estimate.alpha = FALSE, seed = SEED))

LDA_gibbs = LDA(import_mat, k = k, method = "Gibbs", 
                control = list(seed = SEED, burnin = 1000, thin = 100, iter = 1000))

CTM_fit = CTM(import_mat, k = k, 
              control = list(seed = SEED, 
                             var = list(tol = 10^-4), 
                             em = list(tol = 10^-3)))
```

You can then get the alpha values, and smaller alpha values indicate higher percentages of documents that were classified to one single topic. You can also get entropy values where higher values indicate that topics are evenly spread.


```r
LDA_fit@alpha

LDA_fixed@alpha

LDA_gibbs@alpha

sapply(list(LDA_fit, LDA_fixed, LDA_gibbs, CTM_fit), function (x) mean(apply(posterior(x)$topics, 1, function(z) - sum(z * log(z)))))
```

The topic matrix indicates the rank of the number of topics for each document. For instance, if you select to estimate 5 topics, you will see see which topic is covered most in each document, with less covered topics ranked lower. Therefore, a score set of 5, 3, 1, 2, 4 indicates that the 5th topic was covered most in that document, and the 4th topic was covered least.


```r
topics(LDA_fit, k)
topics(LDA_fixed, k)
topics(LDA_gibbs, k)
topics(CTM_fit, k)
```

Last,you can get the most frequent terms for each of the topics that were estimated.


```r
terms(LDA_fit,10)
terms(LDA_fixed, 10)
terms(LDA_gibbs,10)
terms(CTM_fit,10)
```







