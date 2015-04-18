# Reproducible Research: Peer Assessment 1


## Loading and preprocessing the data

```r
  if (!file.exists("activity.csv")) {
    if (!file.exists("activity.zip")) {
      print("ERROR: Cannot open file. Please check that you're running in the repo directory")
    } else {
      unzip("activity.zip")
    }
  }
  activity_data_raw <- read.csv("activity.csv")
```



## What is mean total number of steps taken per day?
First, calculate the total number of steps taken each day.  

1. Load the dplyr library to make sure it's available

2. Use dplyr functions group_by & summarize to sum steps for each day 

```r
library(dplyr)
```

```
## 
## Attaching package: 'dplyr'
## 
## The following object is masked from 'package:stats':
## 
##     filter
## 
## The following objects are masked from 'package:base':
## 
##     intersect, setdiff, setequal, union
```

```r
byday <- group_by(activity_data_raw, date)
steps_byday <- summarize(byday, step_sum = sum(steps, na.rm=TRUE))
```

Make a histogram of the total number of steps taken each day

```r
hist(steps_byday$step_sum, main="Histogram of sum of steps by day", xlab="Sum of Daily Steps")
```

![](PA1_template_files/figure-html/unnamed-chunk-3-1.png) 

Calculate & report the mean number of steps per day

```r
mean(steps_byday$step_sum)
```

```
## [1] 9354.23
```
Calculate & report the median number of steps per day

```r
median(steps_byday$step_sum)
```

```
## [1] 10395
```

## What is the average daily activity pattern?



## Imputing missing values



## Are there differences in activity patterns between weekdays and weekends?
