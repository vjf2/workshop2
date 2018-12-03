---
title: "workshop"
author: "Vivienne Foroughirad"
date: "December 3, 2018"
output: 
  html_document:
    keep_md: TRUE
---



## Cape Hatteras BRS Analysis

Load in the libraries and library paths


```
## 
## Attaching package: 'dplyr'
```

```
## The following objects are masked from 'package:stats':
## 
##     filter, lag
```

```
## The following objects are masked from 'package:base':
## 
##     intersect, setdiff, setequal, union
```

```
## Loading required package: spam
```

```
## Loading required package: dotCall64
```

```
## Loading required package: grid
```

```
## Spam version 2.2-0 (2018-06-19) is loaded.
## Type 'help( Spam)' or 'demo( spam)' for a short introduction 
## and overview of this package.
## Help for individual functions is also obtained by adding the
## suffix '.spam' to the function name, e.g. 'help( chol.spam)'.
```

```
## 
## Attaching package: 'spam'
```

```
## The following objects are masked from 'package:base':
## 
##     backsolve, forwardsolve
```

```
## Loading required package: maps
```

```
## See www.image.ucar.edu/~nychka/Fields for
##  a vignette and other supplements.
```

```
## Loading required package: Matrix
```

```
## 
## Attaching package: 'Matrix'
```

```
## The following object is masked from 'package:spam':
## 
##     det
```

## Read in the data


```r
kahuna <- read_csv('C:/Users/froug/Desktop/myRepo/data/2018-11-26_2017-Cape-Hatteras-BRS-kahuna-CEE.csv')
```

```
## Parsed with column specification:
## cols(
##   date = col_character(),
##   time = col_time(format = ""),
##   longitude = col_double(),
##   latitude = col_double(),
##   ship = col_character(),
##   status = col_character()
## )
```

```r
kStart <- kahuna %>% 
  filter(status == 'start')

# Read in Gm182 Data: 100 estimated positions of Gm182, augmented with focal follow data
gm182UP <- read_csv('C:/Users/froug/Desktop/myRepo/data/2018-11-27_Gm182-UserPoints-Start-CEE-Locations-Kahuna.csv') %>% 
  mutate(status = 'userPoints')
```

```
## Parsed with column specification:
## cols(
##   trackNum = col_integer(),
##   time = col_datetime(format = ""),
##   dfOrig.x = col_double(),
##   dfOrig.y = col_double()
## )
```

```r
# Read in Gm182 Data: 100 estimated positions of Gm182
gm182 <- read_csv('C:/Users/froug/Desktop/myRepo/data/2018-11-27_Gm182-Start-CEE-Locations-Kahuna.csv') %>% 
  mutate(status = 'noUserPoints')
```

```
## Parsed with column specification:
## cols(
##   trackNum = col_integer(),
##   time = col_datetime(format = ""),
##   dfOrig.x = col_double(),
##   dfOrig.y = col_double()
## )
```

Note that the `echo = FALSE` parameter was added to the code chunk to prevent printing of the R code that generated the plot.
