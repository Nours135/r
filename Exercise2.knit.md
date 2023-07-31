---
output:
  pdf_document: default
  html_document: default
---
\usepackage{ctex}
---
title: "Exercise2"
output:
  pdf_document: default
  html_document:
    df_print: paged
date: "2023-07-22"
---



## R Markdown

This is an R Markdown document. Markdown is a simple formatting syntax for authoring HTML, PDF, and MS Word documents. For more details on using R Markdown see <http://rmarkdown.rstudio.com>.

When you click the **Knit** button a document will be generated that includes both content as well as the output of any embedded R code chunks within the document. You can embed an R code chunk like this:


```r
#Q1
data(rivers)
#T1
print(rivers)
```

```
##   [1]  735  320  325  392  524  450 1459  135  465  600  330  336  280  315  870
##  [16]  906  202  329  290 1000  600  505 1450  840 1243  890  350  407  286  280
##  [31]  525  720  390  250  327  230  265  850  210  630  260  230  360  730  600
##  [46]  306  390  420  291  710  340  217  281  352  259  250  470  680  570  350
##  [61]  300  560  900  625  332 2348 1171 3710 2315 2533  780  280  410  460  260
##  [76]  255  431  350  760  618  338  981 1306  500  696  605  250  411 1054  735
##  [91]  233  435  490  310  460  383  375 1270  545  445 1885  380  300  380  377
## [106]  425  276  210  800  420  350  360  538 1100 1205  314  237  610  360  540
## [121] 1038  424  310  300  444  301  268  620  215  652  900  525  246  360  529
## [136]  500  720  270  430  671 1770
```

```r
#T2 method1
length(rivers)
```

```
## [1] 141
```

```r
mean(rivers)
```

```
## [1] 591.1844
```

```r
median(rivers)
```

```
## [1] 425
```

```r
sd(rivers)
```

```
## [1] 493.8708
```

```r
var(rivers)
```

```
## [1] 243908.4
```

```r
min(rivers)
```

```
## [1] 135
```

```r
max(rivers)
```

```
## [1] 3710
```

```r
#T2 method2
library(Hmisc)
```

```
## 
## 载入程辑包：'Hmisc'
```

```
## The following objects are masked from 'package:base':
## 
##     format.pval, units
```

```r
describe(rivers)
```

```
## rivers 
##        n  missing distinct     Info     Mean      Gmd      .05      .10 
##      141        0      114        1    591.2    428.5      230      255 
##      .25      .50      .75      .90      .95 
##      310      425      680     1054     1450 
## 
## lowest :  135  202  210  215  217, highest: 1885 2315 2348 2533 3710
```

```r
#T3
rivers.Des.1 <- c(length(rivers),mean(rivers),median(rivers),sd(rivers),var(rivers),min(rivers),max(rivers));rivers.Des.1
```

```
## [1]    141.0000    591.1844    425.0000    493.8708 243908.4086    135.0000
## [7]   3710.0000
```

```r
#T4
river.Des.2 <- as.data.frame(describe(rivers)$counts)
river.Des.2$FeatureName <- row.names(river.Des.2)
river.Des.2 <- river.Des.2[,c(2,1)] #颠倒了下两个列的顺序
colnames(river.Des.2) = c('FeatureName', 'Values')

#Q2
rm(list = ls()) #清空所有变量
data(women)
#T1
print(dim(women))
```

```
## [1] 15  2
```

```r
#T2
women[c(1:6),] #前六个
```

```
##   height weight
## 1     58    115
## 2     59    117
## 3     60    120
## 4     61    123
## 5     62    126
## 6     63    129
```

```r
women[c((dim(women)[1] - 6):dim(women)[1]),]
```

```
##    height weight
## 9      66    139
## 10     67    142
## 11     68    146
## 12     69    150
## 13     70    154
## 14     71    159
## 15     72    164
```

```r
#T3
mean(women$height)
```

```
## [1] 65
```

```r
var(women$height)
```

```
## [1] 20
```

```r
#T4
women.Height60 <- women[which(women$height > 60),] #加不加which看起来没区别
#T5
women.List = as.list(women)
#T6
women.matrix = as.matrix(women)
print(women.matrix)
```

```
##       height weight
##  [1,]     58    115
##  [2,]     59    117
##  [3,]     60    120
##  [4,]     61    123
##  [5,]     62    126
##  [6,]     63    129
##  [7,]     64    132
##  [8,]     65    135
##  [9,]     66    139
## [10,]     67    142
## [11,]     68    146
## [12,]     69    150
## [13,]     70    154
## [14,]     71    159
## [15,]     72    164
```

```r
print(t(women.matrix))
```

```
##        [,1] [,2] [,3] [,4] [,5] [,6] [,7] [,8] [,9] [,10] [,11] [,12] [,13]
## height   58   59   60   61   62   63   64   65   66    67    68    69    70
## weight  115  117  120  123  126  129  132  135  139   142   146   150   154
##        [,14] [,15]
## height    71    72
## weight   159   164
```

```r
#T7
cor(women)
```

```
##           height    weight
## height 1.0000000 0.9954948
## weight 0.9954948 1.0000000
```

```r
#T8
```


Note that the `echo = FALSE` parameter was added to the code chunk to prevent printing of the R code that generated the plot.
