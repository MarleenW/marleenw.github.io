---
title       : Sat-scores and faculty members
subtitle    : A Shiny app
author      : Marleen Westerik
job         : QNH consulting (the Netherlands)
framework   : io2012     # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
# logo        : QNH%20blue.jpg
url         : 
    assets    : ../assets
    img       : ../assets/img
    
---

<style> 
.title-slide {
  background-color: #FFFFFF; /* #EDE0CF; ; #CA9F9D*/
}

</style>

## Data

The Shiny app 'Universities' uses the University dataset from [UCI](https://archive.ics.uci.edu/ml/datasets/University). This set provides data from a large number of US universities. The app plots the average sat-score of admitted students against the fraction of people at the university who are faculty-members. The universities are clustered into three groups and the source of the data is recorded.



```r
model <- kmeans(dataForClustering, centers = 3)
```




```r
uniQC <- cbind(dataForClustering, cluster = as.factor(model$cluster), src = src)
head(uniQC)
```

```
##   faculty  sat cluster  src
## 1    0.17 54.0       2 file
## 3    0.07 16.0       1 file
## 4    0.10 42.0       2 file
## 5    0.06 21.0       3 file
## 6    0.05 23.5       3 file
## 8    0.05 23.0       3 file
```

--- .class #id 

## App

The app displays the data and allows the user to add new datapoints.

<img src="assets/img/app.png", alt="app", style="max-width: 80% ;">

---

## New Data

New data can be added by giving values in the textboxes and hitting the add-button. More data can be added by repeating the process.

<img src="assets/img/appnew.png", alt="appnew", style="max-width: 80% ;">


---

## Interpretation

The plot shows very little correlation between the percentage faculty members and the average sat-scores of admitted students. The correlation is equal to


```r
cor(uniQC$faculty, uniQC$sat)
```

```
## [1] 0.2163181
```

which is indeed very little. This suggests that universities who invest in their education by hiring many faculty members do not necesserily have a strong selection on their applicants.

The clustering on the data is mainly for show and does not serve any genuine purpose.
