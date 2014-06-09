Reproducible Research: Peer Assessment 1
========================================

## Loading and preprocessing the data
Loading the data from the activity.zip file:

```r
setwd("~/workspace/RepData_PeerAssessment1/")
activity_file <- unz("activity.zip", "activity.csv")
activity <- read.csv(activity_file)
```
Transforming the 'date' and 'interval' columns into a date and time POSIXlt format, named 'datetime':

```r
activity$hour <- as.character(activity$interval)
activity$hour <- sapply(activity$hour, function(x) {
    if (nchar(x) == 1) {
        paste0("000", x)
    } else if (nchar(x) == 2) {
        paste0("00", x)
    } else if (nchar(x) == 3) {
        paste0("0", x)
    } else {
        x
    }
})
activity$datetime <- paste(activity$date, activity$hour)
activity$datetime <- strptime(activity$datetime, "%Y-%m-%d %H%M", tz="UTC")
```
Extracting the datafarame that is needed for the analysis, named 'data':

```r
data <- activity[, c("steps", "datetime")]
```

## What is mean total number of steps taken per day?



## What is the average daily activity pattern?



## Imputing missing values



## Are there differences in activity patterns between weekdays and weekends?
