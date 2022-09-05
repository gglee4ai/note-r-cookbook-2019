note07
================

# 7 문자열과 날짜

## 7.1 문자열 길이 구하기

``` r
nchar("Moe")
```

    ## [1] 3

``` r
nchar("Curly")
```

    ## [1] 5

``` r
s <- c("Moe", "Larry", "Curly")
nchar(s)
```

    ## [1] 3 5 5

``` r
length("Moe")
```

    ## [1] 1

``` r
length(c("Moe", "Larry", "Curly"))
```

    ## [1] 3

## 7.2 문자열 연결

``` r
paste("Everybody", "loves", "stats.")
```

    ## [1] "Everybody loves stats."

``` r
paste("Everybody", "loves", "stats.", sep = "-")
```

    ## [1] "Everybody-loves-stats."

``` r
paste("Everybody", "loves", "stats.", sep = "")
```

    ## [1] "Everybodylovesstats."

``` r
paste0("Everybody", "loves", "stats.")
```

    ## [1] "Everybodylovesstats."

``` r
paste("The square root of twice pi is approximately", sqrt(2 * pi))
```

    ## [1] "The square root of twice pi is approximately 2.506628274631"

``` r
stooges <- c("Moe", "Larry", "Curly")
paste(stooges, "loves", "stats.")
```

    ## [1] "Moe loves stats."   "Larry loves stats." "Curly loves stats."

``` r
paste(stooges, "loves", "stats", collapse = ", and ")
```

    ## [1] "Moe loves stats, and Larry loves stats, and Curly loves stats"

## 7.3 부분 문자열 추출

``` r
substr("Statistics", 1, 4)
```

    ## [1] "Stat"

``` r
substr("Statistics", 7, 10)
```

    ## [1] "tics"

``` r
ss <- c("Moe", "Larry", "Curly")
substr(ss, 1, 3)
```

    ## [1] "Moe" "Lar" "Cur"

``` r
cities <- c("New York, NY", "Los Angeles, CA", "Peoria, IL")
substr(cities, nchar(cities) - 1, nchar(cities))
```

    ## [1] "NY" "CA" "IL"

## 7.4 구분 기호에 따라 문자열 분할하기

``` r
path <- "/home/mike/data/trials.csv"
strsplit(path, "/")
```

    ## [[1]]
    ## [1] ""           "home"       "mike"       "data"       "trials.csv"

``` r
strsplit(path, "/")[[1]]
```

    ## [1] ""           "home"       "mike"       "data"       "trials.csv"

``` r
paths <- c(
  "/home/mike/data/trials.csv",
  "/home/mike/data/errors.csv",
  "/home/mike/corr/reject.doc"
)
strsplit(paths, "/")
```

    ## [[1]]
    ## [1] ""           "home"       "mike"       "data"       "trials.csv"
    ## 
    ## [[2]]
    ## [1] ""           "home"       "mike"       "data"       "errors.csv"
    ## 
    ## [[3]]
    ## [1] ""           "home"       "mike"       "corr"       "reject.doc"

## 7.5 부분 문자열 바꾸기

``` r
str <- "Curly is the smart one. Curly is funny, too."
sub("Curly", "Moe", str)
```

    ## [1] "Moe is the smart one. Curly is funny, too."

``` r
gsub("Curly", "Moe", str)
```

    ## [1] "Moe is the smart one. Moe is funny, too."

## 7.6 문자열의 모든 쌍별 조합 생성하기

``` r
locations <- c("NY", "LA", "CHI", "HOU")
treatments <- c("T1", "T2", "T3")
outer(locations, treatments, paste, sep = "-")
```

    ##      [,1]     [,2]     [,3]    
    ## [1,] "NY-T1"  "NY-T2"  "NY-T3" 
    ## [2,] "LA-T1"  "LA-T2"  "LA-T3" 
    ## [3,] "CHI-T1" "CHI-T2" "CHI-T3"
    ## [4,] "HOU-T1" "HOU-T2" "HOU-T3"

``` r
outer(treatments, treatments, paste, sep = "-")
```

    ##      [,1]    [,2]    [,3]   
    ## [1,] "T1-T1" "T1-T2" "T1-T3"
    ## [2,] "T2-T1" "T2-T2" "T2-T3"
    ## [3,] "T3-T1" "T3-T2" "T3-T3"

``` r
expand.grid(treatments, treatments)
```

    ##   Var1 Var2
    ## 1   T1   T1
    ## 2   T2   T1
    ## 3   T3   T1
    ## 4   T1   T2
    ## 5   T2   T2
    ## 6   T3   T2
    ## 7   T1   T3
    ## 8   T2   T3
    ## 9   T3   T3

``` r
m <- outer(treatments, treatments, paste, sep = "-")
m[!lower.tri(m)]
```

    ## [1] "T1-T1" "T1-T2" "T2-T2" "T1-T3" "T2-T3" "T3-T3"

## 7.7 현재 날짜 얻기

``` r
Sys.Date()
```

    ## [1] "2022-09-05"

``` r
class(Sys.Date())
```

    ## [1] "Date"

## 7.8 문자열을 날짜로 변환하기

``` r
as.Date("2018-12-31")
```

    ## [1] "2018-12-31"

``` r
as.Date("12/31/2018", format = "%m/%d/%Y")
```

    ## [1] "2018-12-31"

## 7.9 날짜를 문자열로 변환

``` r
format(Sys.Date())
```

    ## [1] "2022-09-05"

``` r
as.character(Sys.Date())
```

    ## [1] "2022-09-05"

``` r
format(Sys.Date(), format = "%m/%d/%Y")
```

    ## [1] "09/05/2022"

## 7.10 년, 월, 일을 날짜로 변환

``` r
year <- 2018
month <- 12
day <- 31
as.Date(ISOdate(year, month, day))
```

    ## [1] "2018-12-31"

``` r
ISOdate(2020, 2, 29)
```

    ## [1] "2020-02-29 12:00:00 GMT"

``` r
as.Date(ISOdate(2020, 2, 29))
```

    ## [1] "2020-02-29"

``` r
years <- c(2010, 2011, 2012, 2014)
months <- c(1, 1, 1, 1, 1)
days <- c(15, 21, 20, 18, 17)
ISOdate(years, months, days)
```

    ## [1] "2010-01-15 12:00:00 GMT" "2011-01-21 12:00:00 GMT" "2012-01-20 12:00:00 GMT" "2014-01-18 12:00:00 GMT"
    ## [5] "2010-01-17 12:00:00 GMT"

``` r
as.Date(ISOdate(years, months, days))
```

    ## [1] "2010-01-15" "2011-01-21" "2012-01-20" "2014-01-18" "2010-01-17"

``` r
as.Date(ISOdate(years, 1, days))
```

    ## [1] "2010-01-15" "2011-01-21" "2012-01-20" "2014-01-18" "2010-01-17"

## 7.11 율리우스력 날짜 구하기

``` r
d <- as.Date("2019-03-15")
as.integer(d)
```

    ## [1] 17970

``` r
jd <- julian(d)
jd
```

    ## [1] 17970
    ## attr(,"origin")
    ## [1] "1970-01-01"

``` r
as.integer(as.Date("1970-01-01"))
```

    ## [1] 0

``` r
as.integer(as.Date("1970-01-02"))
```

    ## [1] 1

``` r
as.integer(as.Date("1970-01-03"))
```

    ## [1] 2

## 7.12 날짜 부분 추출하기

``` r
d <- as.Date("2019-03-15")
p <- as.POSIXlt(d)
p$mday
```

    ## [1] 15

``` r
p$mon
```

    ## [1] 2

``` r
p$year + 1900
```

    ## [1] 2019

``` r
d <- as.Date("2020-04-02")
as.POSIXlt(d)$wday
```

    ## [1] 4

``` r
as.POSIXlt(d)$yday
```

    ## [1] 92

``` r
as.POSIXlt(d)$year # Oops!
```

    ## [1] 120

``` r
as.POSIXlt(d)$year + 1900
```

    ## [1] 2020

## 7.13 날짜 시퀀스 생성

``` r
s <- as.Date("2019-01-01")
e <- as.Date("2019-02-01")
seq(from = s, to = e, by = 1)
```

    ##  [1] "2019-01-01" "2019-01-02" "2019-01-03" "2019-01-04" "2019-01-05" "2019-01-06" "2019-01-07" "2019-01-08"
    ##  [9] "2019-01-09" "2019-01-10" "2019-01-11" "2019-01-12" "2019-01-13" "2019-01-14" "2019-01-15" "2019-01-16"
    ## [17] "2019-01-17" "2019-01-18" "2019-01-19" "2019-01-20" "2019-01-21" "2019-01-22" "2019-01-23" "2019-01-24"
    ## [25] "2019-01-25" "2019-01-26" "2019-01-27" "2019-01-28" "2019-01-29" "2019-01-30" "2019-01-31" "2019-02-01"

``` r
seq(from = s, by = 1, length.out = 7)
```

    ## [1] "2019-01-01" "2019-01-02" "2019-01-03" "2019-01-04" "2019-01-05" "2019-01-06" "2019-01-07"

``` r
seq(from = s, by = "month", length.out = 12)
```

    ##  [1] "2019-01-01" "2019-02-01" "2019-03-01" "2019-04-01" "2019-05-01" "2019-06-01" "2019-07-01" "2019-08-01"
    ##  [9] "2019-09-01" "2019-10-01" "2019-11-01" "2019-12-01"

``` r
seq(from = s, by = "3 months", length.out = 4)
```

    ## [1] "2019-01-01" "2019-04-01" "2019-07-01" "2019-10-01"

``` r
seq(from = s, by = "year", length.out = 10)
```

    ##  [1] "2019-01-01" "2020-01-01" "2021-01-01" "2022-01-01" "2023-01-01" "2024-01-01" "2025-01-01" "2026-01-01"
    ##  [9] "2027-01-01" "2028-01-01"

``` r
seq(as.Date("2019-01-29"), by = "month", len = 3)
```

    ## [1] "2019-01-29" "2019-03-01" "2019-03-29"
