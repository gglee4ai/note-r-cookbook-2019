note05
================

# 5 데이터 구조

``` r
v <- c(10, 20, 30)
names(v) <- c("Moe", "Larry", "Curly")
v
```

    ##   Moe Larry Curly 
    ##    10    20    30

``` r
v[["Larry"]]
```

    ## [1] 20

``` r
mode(factor(c("NY", "CA", "IL")))
```

    ## [1] "numeric"

``` r
mode(3.1415)
```

    ## [1] "numeric"

``` r
mode(c(2.7182, 3.1415))
```

    ## [1] "numeric"

``` r
mode("Moe")
```

    ## [1] "character"

``` r
mode(list("Moe", "Larry", "Curly"))
```

    ## [1] "list"

``` r
d <- as.Date("2010-03-15")
mode(d)
```

    ## [1] "numeric"

``` r
length(d)
```

    ## [1] 1

``` r
class(d)
```

    ## [1] "Date"

``` r
pi
```

    ## [1] 3.141593

``` r
length(pi)
```

    ## [1] 1

``` r
pi[1]
```

    ## [1] 3.141593

``` r
pi[2]
```

    ## [1] NA

``` r
A <- 1:6
dim(A)
```

    ## NULL

``` r
A
```

    ## [1] 1 2 3 4 5 6

``` r
dim(A) <- c(2, 3)
print(A)
```

    ##      [,1] [,2] [,3]
    ## [1,]    1    3    5
    ## [2,]    2    4    6

``` r
B <- list(1, 2, 3, 4, 5, 6)
dim(B)
```

    ## NULL

``` r
dim(B) <- c(2, 3)
B
```

    ##      [,1] [,2] [,3]
    ## [1,] 1    3    5   
    ## [2,] 2    4    6

``` r
D <- 1:12
dim(D) <- c(2, 3, 2)
D
```

    ## , , 1
    ## 
    ##      [,1] [,2] [,3]
    ## [1,]    1    3    5
    ## [2,]    2    4    6
    ## 
    ## , , 2
    ## 
    ##      [,1] [,2] [,3]
    ## [1,]    7    9   11
    ## [2,]    8   10   12

``` r
C <- list(1, 2, 3, "X", "Y", "Z")
dim(C) <- c(2, 3)
C
```

    ##      [,1] [,2] [,3]
    ## [1,] 1    3    "Y" 
    ## [2,] 2    "X"  "Z"

## 5.1 벡터에 데이터 추가하기

``` r
v <- c(1, 2, 3)
newItems <- c(6, 7, 8)
c(v, newItems)
```

    ## [1] 1 2 3 6 7 8

``` r
v[length(v) + 1] <- 42
v
```

    ## [1]  1  2  3 42

``` r
v <- c(1, 2, 3)
v <- c(v, 4)
v
```

    ## [1] 1 2 3 4

``` r
w <- c(5, 6, 7, 8)
v <- c(v, w)
v
```

    ## [1] 1 2 3 4 5 6 7 8

``` r
v <- c(1, 2, 3)
v[10] <- 10
v
```

    ##  [1]  1  2  3 NA NA NA NA NA NA 10

## 5.2 벡터에 데이터 삽입하기

``` r
append(1:10, 99, after = 5)
```

    ##  [1]  1  2  3  4  5 99  6  7  8  9 10

``` r
append(1:10, 99, after = 0)
```

    ##  [1] 99  1  2  3  4  5  6  7  8  9 10

## 5.3 재활용 규칙의 이해

``` r
cbind(1:6, 1:3)
```

    ##      [,1] [,2]
    ## [1,]    1    1
    ## [2,]    2    2
    ## [3,]    3    3
    ## [4,]    4    1
    ## [5,]    5    2
    ## [6,]    6    3

``` r
cbind(1:6, 1:5)
```

    ## Warning in cbind(1:6, 1:5): number of rows of result is not a multiple of vector length (arg 2)

    ##      [,1] [,2]
    ## [1,]    1    1
    ## [2,]    2    2
    ## [3,]    3    3
    ## [4,]    4    4
    ## [5,]    5    5
    ## [6,]    6    1

``` r
(1:6) + 10
```

    ## [1] 11 12 13 14 15 16

## 5.4 요인 생성(범주형 변수)

``` r
f <- factor(v)
f
```

    ##  [1] 1    2    3    <NA> <NA> <NA> <NA> <NA> <NA> 10  
    ## Levels: 1 2 3 10

``` r
f <- factor(c("Win", "Win", "Lose", "Tie", "Win", "Lose"))
f
```

    ## [1] Win  Win  Lose Tie  Win  Lose
    ## Levels: Lose Tie Win

``` r
wday <- c(
  "Wed", "Thu", "Mon", "Wed", "Thu",
  "Thu", "Thu", "Tue", "Thu", "Tue"
)
f <- factor(wday)
f
```

    ##  [1] Wed Thu Mon Wed Thu Thu Thu Tue Thu Tue
    ## Levels: Mon Thu Tue Wed

``` r
f <- factor(wday, levels = c("Mon", "Tue", "Wed", "Thu", "Fri"))
f
```

    ##  [1] Wed Thu Mon Wed Thu Thu Thu Tue Thu Tue
    ## Levels: Mon Tue Wed Thu Fri

## 5.5 여러 벡터를 하나의 벡터와 인자로 결합하기

``` r
freshmen <- c(1, 2, 1, 1, 5)
sophomores <- c(3, 2, 3, 3, 5)
juniors <- c(5, 3, 4, 3, 3)
comb <- stack(list(fresh = freshmen, soph = sophomores, jrs = juniors))
comb
```

    ##    values   ind
    ## 1       1 fresh
    ## 2       2 fresh
    ## 3       1 fresh
    ## 4       1 fresh
    ## 5       5 fresh
    ## 6       3  soph
    ## 7       2  soph
    ## 8       3  soph
    ## 9       3  soph
    ## 10      5  soph
    ## 11      5   jrs
    ## 12      3   jrs
    ## 13      4   jrs
    ## 14      3   jrs
    ## 15      3   jrs

``` r
aov(values ~ ind, data = comb)
```

    ## Call:
    ##    aov(formula = values ~ ind, data = comb)
    ## 
    ## Terms:
    ##                       ind Residuals
    ## Sum of Squares   6.933333 20.000000
    ## Deg. of Freedom         2        12
    ## 
    ## Residual standard error: 1.290994
    ## Estimated effects may be unbalanced

## 5.6 목록 만들기

``` r
lst <- list(0.5, 0.841, 0.977)
lst
```

    ## [[1]]
    ## [1] 0.5
    ## 
    ## [[2]]
    ## [1] 0.841
    ## 
    ## [[3]]
    ## [1] 0.977

``` r
lst <- list(3.14, "Moe", c(1, 1, 2, 3), mean)
lst
```

    ## [[1]]
    ## [1] 3.14
    ## 
    ## [[2]]
    ## [1] "Moe"
    ## 
    ## [[3]]
    ## [1] 1 1 2 3
    ## 
    ## [[4]]
    ## function (x, ...) 
    ## UseMethod("mean")
    ## <bytecode: 0x1206e7640>
    ## <environment: namespace:base>

``` r
lst <- list()
lst[[1]] <- 3.14
lst[[2]] <- "Moe"
lst[[3]] <- c(1, 1, 2, 3)
lst[[4]] <- mean
lst
```

    ## [[1]]
    ## [1] 3.14
    ## 
    ## [[2]]
    ## [1] "Moe"
    ## 
    ## [[3]]
    ## [1] 1 1 2 3
    ## 
    ## [[4]]
    ## function (x, ...) 
    ## UseMethod("mean")
    ## <bytecode: 0x1206e7640>
    ## <environment: namespace:base>

``` r
lst <- list(mid = 0.5, right = 0.841, far.right = 0.977)
lst
```

    ## $mid
    ## [1] 0.5
    ## 
    ## $right
    ## [1] 0.841
    ## 
    ## $far.right
    ## [1] 0.977

## 5.7 위치별 목록 요소 선택

``` r
years <- list(1960, 1964, 1976, 1994)
years
```

    ## [[1]]
    ## [1] 1960
    ## 
    ## [[2]]
    ## [1] 1964
    ## 
    ## [[3]]
    ## [1] 1976
    ## 
    ## [[4]]
    ## [1] 1994

``` r
years[[1]]
```

    ## [1] 1960

``` r
years[c(1, 2)]
```

    ## [[1]]
    ## [1] 1960
    ## 
    ## [[2]]
    ## [1] 1964

``` r
class(years[[1]])
```

    ## [1] "numeric"

``` r
class(years[1])
```

    ## [1] "list"

``` r
cat(years[[1]], "\n")
```

    ## 1960

``` r
try(cat(years[1], "\n"))
```

    ## Error in cat(years[1], "\n") : 
    ##   argument 1 (type 'list') cannot be handled by 'cat'

## 5.8 이름으로 목록 요소 선택하기

``` r
years <- list(
  Kennedy = 1960, Johnson = 1964,
  Carter = 1976, Clinton = 1994
)
years[["Kennedy"]]
```

    ## [1] 1960

``` r
years$Kennedy
```

    ## [1] 1960

``` r
years[c("Kennedy", "Johnson")]
```

    ## $Kennedy
    ## [1] 1960
    ## 
    ## $Johnson
    ## [1] 1964

``` r
years["Carter"]
```

    ## $Carter
    ## [1] 1976

## 5.9 이름/값 연관 목록 작성

``` r
lst <- list(mid = 0.5, right = 0.841, far.right = 0.977)
lst
```

    ## $mid
    ## [1] 0.5
    ## 
    ## $right
    ## [1] 0.841
    ## 
    ## $far.right
    ## [1] 0.977

``` r
values <- c(1, 2, 3)
names <- c("a", "b", "c")
lst <- list()
lst[names] <- values
lst
```

    ## $a
    ## [1] 1
    ## 
    ## $b
    ## [1] 2
    ## 
    ## $c
    ## [1] 3

``` r
lst <- list(
  far.left = 0.023,
  left = 0.159,
  mid = 0.500,
  right = 0.841,
  far.right = 0.977
)
lst
```

    ## $far.left
    ## [1] 0.023
    ## 
    ## $left
    ## [1] 0.159
    ## 
    ## $mid
    ## [1] 0.5
    ## 
    ## $right
    ## [1] 0.841
    ## 
    ## $far.right
    ## [1] 0.977

``` r
lst <- list()
lst$far.left <- 0.023
lst$left <- 0.159
lst$mid <- 0.500
lst$right <- 0.841
lst$far.right <- 0.977
```

``` r
values <- -2:2
names <- c("far.left", "left", "mid", "right", "far.right")
lst <- list()
lst[names] <- values
lst
```

    ## $far.left
    ## [1] -2
    ## 
    ## $left
    ## [1] -1
    ## 
    ## $mid
    ## [1] 0
    ## 
    ## $right
    ## [1] 1
    ## 
    ## $far.right
    ## [1] 2

``` r
cat("The left limit is", lst[["left"]], "\n")
```

    ## The left limit is -1

``` r
cat("The right limit is", lst[["right"]], "\n")
```

    ## The right limit is 1

``` r
for (nm in names(lst)) cat("The", nm, "limit is", lst[[nm]], "\n")
```

    ## The far.left limit is -2 
    ## The left limit is -1 
    ## The mid limit is 0 
    ## The right limit is 1 
    ## The far.right limit is 2

## 5.10 목록에서 요소 제거하기

``` r
years <- list(
  Kennedy = 1960, Johnson = 1964,
  Carter = 1976, Clinton = 1994
)
years
```

    ## $Kennedy
    ## [1] 1960
    ## 
    ## $Johnson
    ## [1] 1964
    ## 
    ## $Carter
    ## [1] 1976
    ## 
    ## $Clinton
    ## [1] 1994

``` r
years[["Johnson"]] <- NULL # Remove the element labeled "Johnson"
years
```

    ## $Kennedy
    ## [1] 1960
    ## 
    ## $Carter
    ## [1] 1976
    ## 
    ## $Clinton
    ## [1] 1994

``` r
years[c("Carter", "Clinton")] <- NULL # Remove two elements
years
```

    ## $Kennedy
    ## [1] 1960

## 5.11 목록을 벡터로 병합하기

``` r
iq.scores <- list(100, 120, 103, 80, 99)
mean(unlist(iq.scores))
```

    ## [1] 100.4

``` r
# cat(iq.scores, "\n")
cat("IQ Scores:", unlist(iq.scores), "\n")
```

    ## IQ Scores: 100 120 103 80 99

## 5.12 목록에서 NULL 요소 제거

``` r
library(purrr) # or library(tidyverse)

lst <- list("Moe", NULL, "Curly")
lst
```

    ## [[1]]
    ## [1] "Moe"
    ## 
    ## [[2]]
    ## NULL
    ## 
    ## [[3]]
    ## [1] "Curly"

``` r
compact(lst) # Remove NULL element
```

    ## [[1]]
    ## [1] "Moe"
    ## 
    ## [[2]]
    ## [1] "Curly"

## 5.13 조건을 사용하여 목록 요소 제거하기

``` r
lst <- list(NA, 0, NA, 1, 2)
lst |> discard(is.na)
```

    ## [[1]]
    ## [1] 0
    ## 
    ## [[2]]
    ## [1] 1
    ## 
    ## [[3]]
    ## [1] 2

``` r
lst <- list(3, "dog", 2, "cat", 1)

lst %>%
  discard(is.character)
```

    ## [[1]]
    ## [1] 3
    ## 
    ## [[2]]
    ## [1] 2
    ## 
    ## [[3]]
    ## [1] 1

``` r
is_na_or_null <- function(x) {
  is.na(x) || is.null(x)
}

lst <- list(1, NA, 2, NULL, 3)

lst %>%
  discard(is_na_or_null)
```

    ## [[1]]
    ## [1] 1
    ## 
    ## [[2]]
    ## [1] 2
    ## 
    ## [[3]]
    ## [1] 3

``` r
x <- rnorm(10)
y1 <- 10 * x + rnorm(10)
y2 <- rnorm(10)
y3 <- rnorm(10)
mods <- list(
  lm(x ~ y1),
  lm(x ~ y2),
  lm(x ~ y3)
)

filter_r2 <- function(model) {
  summary(model)$r.squared < 0.7
}

mods %>%
  discard(filter_r2)
```

    ## [[1]]
    ## 
    ## Call:
    ## lm(formula = x ~ y1)
    ## 
    ## Coefficients:
    ## (Intercept)           y1  
    ##    -0.02272      0.09824

## 5.14 행렬 초기화

``` r
vec <- 1:6
matrix(vec, 2, 3)
```

    ##      [,1] [,2] [,3]
    ## [1,]    1    3    5
    ## [2,]    2    4    6

``` r
matrix(0, 2, 3) # Create an all-zeros matrix
```

    ##      [,1] [,2] [,3]
    ## [1,]    0    0    0
    ## [2,]    0    0    0

``` r
matrix(NA, 2, 3)
```

    ##      [,1] [,2] [,3]
    ## [1,]   NA   NA   NA
    ## [2,]   NA   NA   NA

``` r
mat <- matrix(c(1.1, 1.2, 1.3, 2.1, 2.2, 2.3), 2, 3)
mat
```

    ##      [,1] [,2] [,3]
    ## [1,]  1.1  1.3  2.2
    ## [2,]  1.2  2.1  2.3

``` r
theData <- c(
  1.1, 1.2, 1.3,
  2.1, 2.2, 2.3
)
mat <- matrix(theData, 2, 3, byrow = TRUE)
mat
```

    ##      [,1] [,2] [,3]
    ## [1,]  1.1  1.2  1.3
    ## [2,]  2.1  2.2  2.3

``` r
mat <- matrix(c(
  1.1, 1.2, 1.3,
  2.1, 2.2, 2.3
),
2, 3,
byrow = TRUE
)
mat
```

    ##      [,1] [,2] [,3]
    ## [1,]  1.1  1.2  1.3
    ## [2,]  2.1  2.2  2.3

``` r
v <- c(1.1, 1.2, 1.3, 2.1, 2.2, 2.3)
dim(v) <- c(2, 3)
v
```

    ##      [,1] [,2] [,3]
    ## [1,]  1.1  1.3  2.2
    ## [2,]  1.2  2.1  2.3

## 5.15 행렬 연산 수행

``` r
x <- matrix(1:4, 2, 2)
t(x)
```

    ##      [,1] [,2]
    ## [1,]    1    2
    ## [2,]    3    4

``` r
solve(x)
```

    ##      [,1] [,2]
    ## [1,]   -2  1.5
    ## [2,]    1 -0.5

``` r
x %*% x
```

    ##      [,1] [,2]
    ## [1,]    7   15
    ## [2,]   10   22

``` r
diag(4)
```

    ##      [,1] [,2] [,3] [,4]
    ## [1,]    1    0    0    0
    ## [2,]    0    1    0    0
    ## [3,]    0    0    1    0
    ## [4,]    0    0    0    1

## 5.16 행렬의 행과 열에 설명적인 이름 지정

``` r
corr_mat <- matrix(c(
  1.000, 0.556, 0.390,
  0.556, 1.000, 0.444,
  0.390, 0.444, 1.000
),
nrow = 3, byrow = TRUE
)
colnames(corr_mat) <- c("AAPL", "MSFT", "GOOG")
rownames(corr_mat) <- c("AAPL", "MSFT", "GOOG")
corr_mat
```

    ##       AAPL  MSFT  GOOG
    ## AAPL 1.000 0.556 0.390
    ## MSFT 0.556 1.000 0.444
    ## GOOG 0.390 0.444 1.000

``` r
corr_mat["MSFT", "GOOG"]
```

    ## [1] 0.444

## 5.17 행렬에서 하나의 행이나 열 선택하기

``` r
corr_mat[1, ]
```

    ##  AAPL  MSFT  GOOG 
    ## 1.000 0.556 0.390

``` r
corr_mat[, 3]
```

    ##  AAPL  MSFT  GOOG 
    ## 0.390 0.444 1.000

``` r
mat[1, , drop = FALSE]
```

    ##      [,1] [,2] [,3]
    ## [1,]  1.1  1.2  1.3

``` r
mat[, 3, drop = FALSE]
```

    ##      [,1]
    ## [1,]  1.3
    ## [2,]  2.3

## 5.18 열 데이터에서 데이터 프레임 초기화

``` r
pred1 <- 1:5
pred2 <- c(1.75, 4.01, 2.64, 6.03, 2.78)
pred3 <- c("AM", "PM", "AM", "PM", "PM")
resp <- c(13.2, 12.9, 13.9, 14.9, 16.4)
```

``` r
data.frame(pred1, pred2, pred3, resp)
```

    ##   pred1 pred2 pred3 resp
    ## 1     1  1.75    AM 13.2
    ## 2     2  4.01    PM 12.9
    ## 3     3  2.64    AM 13.9
    ## 4     4  6.03    PM 14.9
    ## 5     5  2.78    PM 16.4

``` r
data.frame(p1 = pred1, p2 = pred2, p3 = pred3, r = resp)
```

    ##   p1   p2 p3    r
    ## 1  1 1.75 AM 13.2
    ## 2  2 4.01 PM 12.9
    ## 3  3 2.64 AM 13.9
    ## 4  4 6.03 PM 14.9
    ## 5  5 2.78 PM 16.4

``` r
tibble::tibble(p1 = pred1, p2 = pred2, p3 = pred3, r = resp)
```

    ## # A tibble: 5 × 4
    ##      p1    p2 p3        r
    ##   <int> <dbl> <chr> <dbl>
    ## 1     1  1.75 AM     13.2
    ## 2     2  4.01 PM     12.9
    ## 3     3  2.64 AM     13.9
    ## 4     4  6.03 PM     14.9
    ## 5     5  2.78 PM     16.4

``` r
list.of.vectors <- list(p1 = pred1, p2 = pred2, p3 = pred3, r = resp)
as.data.frame(list.of.vectors)
```

    ##   p1   p2 p3    r
    ## 1  1 1.75 AM 13.2
    ## 2  2 4.01 PM 12.9
    ## 3  3 2.64 AM 13.9
    ## 4  4 6.03 PM 14.9
    ## 5  5 2.78 PM 16.4

``` r
tibble::as_tibble(list.of.vectors)
```

    ## # A tibble: 5 × 4
    ##      p1    p2 p3        r
    ##   <int> <dbl> <chr> <dbl>
    ## 1     1  1.75 AM     13.2
    ## 2     2  4.01 PM     12.9
    ## 3     3  2.64 AM     13.9
    ## 4     4  6.03 PM     14.9
    ## 5     5  2.78 PM     16.4

## 5.19 행 데이터에서 데이터 프레임 초기화

``` r
r1 <- data.frame(a = 1, b = 2, c = "X")
r2 <- data.frame(a = 3, b = 4, c = "Y")
r3 <- data.frame(a = 5, b = 6, c = "Z")
rbind(r1, r2, r3)
```

    ##   a b c
    ## 1 1 2 X
    ## 2 3 4 Y
    ## 3 5 6 Z

``` r
list.of.rows <- list(r1, r2, r3)
dplyr::bind_rows(list.of.rows)
```

    ##   a b c
    ## 1 1 2 X
    ## 2 3 4 Y
    ## 3 5 6 Z

``` r
l1 <- list(a = 1, b = 2, c = "X")
l2 <- list(a = 3, b = 4, c = "Y")
l3 <- list(a = 5, b = 6, c = "Z")
list.of.lists <- list(l1, l2, l3)
list.of.lists
```

    ## [[1]]
    ## [[1]]$a
    ## [1] 1
    ## 
    ## [[1]]$b
    ## [1] 2
    ## 
    ## [[1]]$c
    ## [1] "X"
    ## 
    ## 
    ## [[2]]
    ## [[2]]$a
    ## [1] 3
    ## 
    ## [[2]]$b
    ## [1] 4
    ## 
    ## [[2]]$c
    ## [1] "Y"
    ## 
    ## 
    ## [[3]]
    ## [[3]]$a
    ## [1] 5
    ## 
    ## [[3]]$b
    ## [1] 6
    ## 
    ## [[3]]$c
    ## [1] "Z"

``` r
dplyr::bind_rows(list.of.lists)
```

    ## # A tibble: 3 × 3
    ##       a     b c    
    ##   <dbl> <dbl> <chr>
    ## 1     1     2 X    
    ## 2     3     4 Y    
    ## 3     5     6 Z

``` r
data.frame(a = 1, b = 2, c = "a", stringsAsFactors = FALSE)
```

    ##   a b c
    ## 1 1 2 a

``` r
data.frame(a = 1, b = 2, c = "a")
```

    ##   a b c
    ## 1 1 2 a

``` r
l1 <- list(a = 1, b = 2, c = "X")
l2 <- list(a = 3, b = 4, c = "Y")
l3 <- list(a = 5, b = 6, c = "Z")
obs <- list(l1, l2, l3)
df <- do.call(rbind, Map(as.data.frame, obs))
df
```

    ##   a b c
    ## 1 1 2 X
    ## 2 3 4 Y
    ## 3 5 6 Z

``` r
do.call(rbind, Map(as.data.frame, obs))
```

    ##   a b c
    ## 1 1 2 X
    ## 2 3 4 Y
    ## 3 5 6 Z

``` r
i <- sapply(df, is.factor)
df[i] <- lapply(df[i], as.character)
df
```

    ##   a b c
    ## 1 1 2 X
    ## 2 3 4 Y
    ## 3 5 6 Z

## 5.20 데이터 프레임에 행 추가

``` r
cars
```

    ##    speed dist
    ## 1      4    2
    ## 2      4   10
    ## 3      7    4
    ## 4      7   22
    ## 5      8   16
    ## 6      9   10
    ## 7     10   18
    ## 8     10   26
    ## 9     10   34
    ## 10    11   17
    ## 11    11   28
    ## 12    12   14
    ## 13    12   20
    ## 14    12   24
    ## 15    12   28
    ## 16    13   26
    ## 17    13   34
    ## 18    13   34
    ## 19    13   46
    ## 20    14   26
    ## 21    14   36
    ## 22    14   60
    ## 23    14   80
    ## 24    15   20
    ## 25    15   26
    ## 26    15   54
    ## 27    16   32
    ## 28    16   40
    ## 29    17   32
    ## 30    17   40
    ## 31    17   50
    ## 32    18   42
    ## 33    18   56
    ## 34    18   76
    ## 35    18   84
    ## 36    19   36
    ## 37    19   46
    ## 38    19   68
    ## 39    20   32
    ## 40    20   48
    ## 41    20   52
    ## 42    20   56
    ## 43    20   64
    ## 44    22   66
    ## 45    23   54
    ## 46    24   70
    ## 47    24   92
    ## 48    24   93
    ## 49    24  120
    ## 50    25   85

``` r
new_row <- data.frame(speed = 20, dist = 20)
rbind(cars, new_row)
```

    ##    speed dist
    ## 1      4    2
    ## 2      4   10
    ## 3      7    4
    ## 4      7   22
    ## 5      8   16
    ## 6      9   10
    ## 7     10   18
    ## 8     10   26
    ## 9     10   34
    ## 10    11   17
    ## 11    11   28
    ## 12    12   14
    ## 13    12   20
    ## 14    12   24
    ## 15    12   28
    ## 16    13   26
    ## 17    13   34
    ## 18    13   34
    ## 19    13   46
    ## 20    14   26
    ## 21    14   36
    ## 22    14   60
    ## 23    14   80
    ## 24    15   20
    ## 25    15   26
    ## 26    15   54
    ## 27    16   32
    ## 28    16   40
    ## 29    17   32
    ## 30    17   40
    ## 31    17   50
    ## 32    18   42
    ## 33    18   56
    ## 34    18   76
    ## 35    18   84
    ## 36    19   36
    ## 37    19   46
    ## 38    19   68
    ## 39    20   32
    ## 40    20   48
    ## 41    20   52
    ## 42    20   56
    ## 43    20   64
    ## 44    22   66
    ## 45    23   54
    ## 46    24   70
    ## 47    24   92
    ## 48    24   93
    ## 49    24  120
    ## 50    25   85
    ## 51    20   20

``` r
rbind(
  cars,
  data.frame(speed = 22, dist = 22)
)
```

    ##    speed dist
    ## 1      4    2
    ## 2      4   10
    ## 3      7    4
    ## 4      7   22
    ## 5      8   16
    ## 6      9   10
    ## 7     10   18
    ## 8     10   26
    ## 9     10   34
    ## 10    11   17
    ## 11    11   28
    ## 12    12   14
    ## 13    12   20
    ## 14    12   24
    ## 15    12   28
    ## 16    13   26
    ## 17    13   34
    ## 18    13   34
    ## 19    13   46
    ## 20    14   26
    ## 21    14   36
    ## 22    14   60
    ## 23    14   80
    ## 24    15   20
    ## 25    15   26
    ## 26    15   54
    ## 27    16   32
    ## 28    16   40
    ## 29    17   32
    ## 30    17   40
    ## 31    17   50
    ## 32    18   42
    ## 33    18   56
    ## 34    18   76
    ## 35    18   84
    ## 36    19   36
    ## 37    19   46
    ## 38    19   68
    ## 39    20   32
    ## 40    20   48
    ## 41    20   52
    ## 42    20   56
    ## 43    20   64
    ## 44    22   66
    ## 45    23   54
    ## 46    24   70
    ## 47    24   92
    ## 48    24   93
    ## 49    24  120
    ## 50    25   85
    ## 51    22   22

## 5.21 위치별 데이터 프레임 열 선택

``` r
library(dplyr)
mtcars %>%
  select(1)
```

    ##                      mpg
    ## Mazda RX4           21.0
    ## Mazda RX4 Wag       21.0
    ## Datsun 710          22.8
    ## Hornet 4 Drive      21.4
    ## Hornet Sportabout   18.7
    ## Valiant             18.1
    ## Duster 360          14.3
    ## Merc 240D           24.4
    ## Merc 230            22.8
    ## Merc 280            19.2
    ## Merc 280C           17.8
    ## Merc 450SE          16.4
    ## Merc 450SL          17.3
    ## Merc 450SLC         15.2
    ## Cadillac Fleetwood  10.4
    ## Lincoln Continental 10.4
    ## Chrysler Imperial   14.7
    ## Fiat 128            32.4
    ## Honda Civic         30.4
    ## Toyota Corolla      33.9
    ## Toyota Corona       21.5
    ## Dodge Challenger    15.5
    ## AMC Javelin         15.2
    ## Camaro Z28          13.3
    ## Pontiac Firebird    19.2
    ## Fiat X1-9           27.3
    ## Porsche 914-2       26.0
    ## Lotus Europa        30.4
    ## Ford Pantera L      15.8
    ## Ferrari Dino        19.7
    ## Maserati Bora       15.0
    ## Volvo 142E          21.4

``` r
mtcars %>%
  select(1, 3, 4)
```

    ##                      mpg  disp  hp
    ## Mazda RX4           21.0 160.0 110
    ## Mazda RX4 Wag       21.0 160.0 110
    ## Datsun 710          22.8 108.0  93
    ## Hornet 4 Drive      21.4 258.0 110
    ## Hornet Sportabout   18.7 360.0 175
    ## Valiant             18.1 225.0 105
    ## Duster 360          14.3 360.0 245
    ## Merc 240D           24.4 146.7  62
    ## Merc 230            22.8 140.8  95
    ## Merc 280            19.2 167.6 123
    ## Merc 280C           17.8 167.6 123
    ## Merc 450SE          16.4 275.8 180
    ## Merc 450SL          17.3 275.8 180
    ## Merc 450SLC         15.2 275.8 180
    ## Cadillac Fleetwood  10.4 472.0 205
    ## Lincoln Continental 10.4 460.0 215
    ## Chrysler Imperial   14.7 440.0 230
    ## Fiat 128            32.4  78.7  66
    ## Honda Civic         30.4  75.7  52
    ## Toyota Corolla      33.9  71.1  65
    ## Toyota Corona       21.5 120.1  97
    ## Dodge Challenger    15.5 318.0 150
    ## AMC Javelin         15.2 304.0 150
    ## Camaro Z28          13.3 350.0 245
    ## Pontiac Firebird    19.2 400.0 175
    ## Fiat X1-9           27.3  79.0  66
    ## Porsche 914-2       26.0 120.3  91
    ## Lotus Europa        30.4  95.1 113
    ## Ford Pantera L      15.8 351.0 264
    ## Ferrari Dino        19.7 145.0 175
    ## Maserati Bora       15.0 301.0 335
    ## Volvo 142E          21.4 121.0 109

``` r
mtcars %>%
  select(2:4)
```

    ##                     cyl  disp  hp
    ## Mazda RX4             6 160.0 110
    ## Mazda RX4 Wag         6 160.0 110
    ## Datsun 710            4 108.0  93
    ## Hornet 4 Drive        6 258.0 110
    ## Hornet Sportabout     8 360.0 175
    ## Valiant               6 225.0 105
    ## Duster 360            8 360.0 245
    ## Merc 240D             4 146.7  62
    ## Merc 230              4 140.8  95
    ## Merc 280              6 167.6 123
    ## Merc 280C             6 167.6 123
    ## Merc 450SE            8 275.8 180
    ## Merc 450SL            8 275.8 180
    ## Merc 450SLC           8 275.8 180
    ## Cadillac Fleetwood    8 472.0 205
    ## Lincoln Continental   8 460.0 215
    ## Chrysler Imperial     8 440.0 230
    ## Fiat 128              4  78.7  66
    ## Honda Civic           4  75.7  52
    ## Toyota Corolla        4  71.1  65
    ## Toyota Corona         4 120.1  97
    ## Dodge Challenger      8 318.0 150
    ## AMC Javelin           8 304.0 150
    ## Camaro Z28            8 350.0 245
    ## Pontiac Firebird      8 400.0 175
    ## Fiat X1-9             4  79.0  66
    ## Porsche 914-2         4 120.3  91
    ## Lotus Europa          4  95.1 113
    ## Ford Pantera L        8 351.0 264
    ## Ferrari Dino          6 145.0 175
    ## Maserati Bora         8 301.0 335
    ## Volvo 142E            4 121.0 109

``` r
mtcars[1]
```

    ##                      mpg
    ## Mazda RX4           21.0
    ## Mazda RX4 Wag       21.0
    ## Datsun 710          22.8
    ## Hornet 4 Drive      21.4
    ## Hornet Sportabout   18.7
    ## Valiant             18.1
    ## Duster 360          14.3
    ## Merc 240D           24.4
    ## Merc 230            22.8
    ## Merc 280            19.2
    ## Merc 280C           17.8
    ## Merc 450SE          16.4
    ## Merc 450SL          17.3
    ## Merc 450SLC         15.2
    ## Cadillac Fleetwood  10.4
    ## Lincoln Continental 10.4
    ## Chrysler Imperial   14.7
    ## Fiat 128            32.4
    ## Honda Civic         30.4
    ## Toyota Corolla      33.9
    ## Toyota Corona       21.5
    ## Dodge Challenger    15.5
    ## AMC Javelin         15.2
    ## Camaro Z28          13.3
    ## Pontiac Firebird    19.2
    ## Fiat X1-9           27.3
    ## Porsche 914-2       26.0
    ## Lotus Europa        30.4
    ## Ford Pantera L      15.8
    ## Ferrari Dino        19.7
    ## Maserati Bora       15.0
    ## Volvo 142E          21.4

``` r
mtcars[c(1, 3)]
```

    ##                      mpg  disp
    ## Mazda RX4           21.0 160.0
    ## Mazda RX4 Wag       21.0 160.0
    ## Datsun 710          22.8 108.0
    ## Hornet 4 Drive      21.4 258.0
    ## Hornet Sportabout   18.7 360.0
    ## Valiant             18.1 225.0
    ## Duster 360          14.3 360.0
    ## Merc 240D           24.4 146.7
    ## Merc 230            22.8 140.8
    ## Merc 280            19.2 167.6
    ## Merc 280C           17.8 167.6
    ## Merc 450SE          16.4 275.8
    ## Merc 450SL          17.3 275.8
    ## Merc 450SLC         15.2 275.8
    ## Cadillac Fleetwood  10.4 472.0
    ## Lincoln Continental 10.4 460.0
    ## Chrysler Imperial   14.7 440.0
    ## Fiat 128            32.4  78.7
    ## Honda Civic         30.4  75.7
    ## Toyota Corolla      33.9  71.1
    ## Toyota Corona       21.5 120.1
    ## Dodge Challenger    15.5 318.0
    ## AMC Javelin         15.2 304.0
    ## Camaro Z28          13.3 350.0
    ## Pontiac Firebird    19.2 400.0
    ## Fiat X1-9           27.3  79.0
    ## Porsche 914-2       26.0 120.3
    ## Lotus Europa        30.4  95.1
    ## Ford Pantera L      15.8 351.0
    ## Ferrari Dino        19.7 145.0
    ## Maserati Bora       15.0 301.0
    ## Volvo 142E          21.4 121.0

``` r
mtcars[, 1]
```

    ##  [1] 21.0 21.0 22.8 21.4 18.7 18.1 14.3 24.4 22.8 19.2 17.8 16.4 17.3 15.2 10.4 10.4 14.7 32.4 30.4 33.9 21.5
    ## [22] 15.5 15.2 13.3 19.2 27.3 26.0 30.4 15.8 19.7 15.0 21.4

``` r
mtcars[, c(1, 3)]
```

    ##                      mpg  disp
    ## Mazda RX4           21.0 160.0
    ## Mazda RX4 Wag       21.0 160.0
    ## Datsun 710          22.8 108.0
    ## Hornet 4 Drive      21.4 258.0
    ## Hornet Sportabout   18.7 360.0
    ## Valiant             18.1 225.0
    ## Duster 360          14.3 360.0
    ## Merc 240D           24.4 146.7
    ## Merc 230            22.8 140.8
    ## Merc 280            19.2 167.6
    ## Merc 280C           17.8 167.6
    ## Merc 450SE          16.4 275.8
    ## Merc 450SL          17.3 275.8
    ## Merc 450SLC         15.2 275.8
    ## Cadillac Fleetwood  10.4 472.0
    ## Lincoln Continental 10.4 460.0
    ## Chrysler Imperial   14.7 440.0
    ## Fiat 128            32.4  78.7
    ## Honda Civic         30.4  75.7
    ## Toyota Corolla      33.9  71.1
    ## Toyota Corona       21.5 120.1
    ## Dodge Challenger    15.5 318.0
    ## AMC Javelin         15.2 304.0
    ## Camaro Z28          13.3 350.0
    ## Pontiac Firebird    19.2 400.0
    ## Fiat X1-9           27.3  79.0
    ## Porsche 914-2       26.0 120.3
    ## Lotus Europa        30.4  95.1
    ## Ford Pantera L      15.8 351.0
    ## Ferrari Dino        19.7 145.0
    ## Maserati Bora       15.0 301.0
    ## Volvo 142E          21.4 121.0

## 5.22 이름으로 데이터 프레임 열 선택하기

## 5.23 데이터 프레임 열의 이름 변경

``` r
df <- data.frame(V1 = 1:3, V2 = 4:6, V3 = 7:9)
df %>%
  rename(tom = V1, dick = V2)
```

    ##   tom dick V3
    ## 1   1    4  7
    ## 2   2    5  8
    ## 3   3    6  9

``` r
colnames(df) <- c("tom", "dick", "V2")
```

``` r
df <- data.frame(V1 = 1:3, V2 = 4:6, V3 = 7:9)
df %>% select(tom = V1, V2)
```

    ##   tom V2
    ## 1   1  4
    ## 2   2  5
    ## 3   3  6

## 5.24 데이터 프레임에서 NA 제거하기

``` r
df <- data.frame(
  x = c(1, NA, 3, 4, 5),
  y = c(1, 2, NA, 4, 5)
)
na.omit(df)
```

    ##   x y
    ## 1 1 1
    ## 4 4 4
    ## 5 5 5

## 5.25 이름으로 열 제외하기

``` r
mtcars %>%
  select(-(mpg:hp))
```

    ##                     drat    wt  qsec vs am gear carb
    ## Mazda RX4           3.90 2.620 16.46  0  1    4    4
    ## Mazda RX4 Wag       3.90 2.875 17.02  0  1    4    4
    ## Datsun 710          3.85 2.320 18.61  1  1    4    1
    ## Hornet 4 Drive      3.08 3.215 19.44  1  0    3    1
    ## Hornet Sportabout   3.15 3.440 17.02  0  0    3    2
    ## Valiant             2.76 3.460 20.22  1  0    3    1
    ## Duster 360          3.21 3.570 15.84  0  0    3    4
    ## Merc 240D           3.69 3.190 20.00  1  0    4    2
    ## Merc 230            3.92 3.150 22.90  1  0    4    2
    ## Merc 280            3.92 3.440 18.30  1  0    4    4
    ## Merc 280C           3.92 3.440 18.90  1  0    4    4
    ## Merc 450SE          3.07 4.070 17.40  0  0    3    3
    ## Merc 450SL          3.07 3.730 17.60  0  0    3    3
    ## Merc 450SLC         3.07 3.780 18.00  0  0    3    3
    ## Cadillac Fleetwood  2.93 5.250 17.98  0  0    3    4
    ## Lincoln Continental 3.00 5.424 17.82  0  0    3    4
    ## Chrysler Imperial   3.23 5.345 17.42  0  0    3    4
    ## Fiat 128            4.08 2.200 19.47  1  1    4    1
    ## Honda Civic         4.93 1.615 18.52  1  1    4    2
    ## Toyota Corolla      4.22 1.835 19.90  1  1    4    1
    ## Toyota Corona       3.70 2.465 20.01  1  0    3    1
    ## Dodge Challenger    2.76 3.520 16.87  0  0    3    2
    ## AMC Javelin         3.15 3.435 17.30  0  0    3    2
    ## Camaro Z28          3.73 3.840 15.41  0  0    3    4
    ## Pontiac Firebird    3.08 3.845 17.05  0  0    3    2
    ## Fiat X1-9           4.08 1.935 18.90  1  1    4    1
    ## Porsche 914-2       4.43 2.140 16.70  0  1    5    2
    ## Lotus Europa        3.77 1.513 16.90  1  1    5    2
    ## Ford Pantera L      4.22 3.170 14.50  0  1    5    4
    ## Ferrari Dino        3.62 2.770 15.50  0  1    5    6
    ## Maserati Bora       3.54 3.570 14.60  0  1    5    8
    ## Volvo 142E          4.11 2.780 18.60  1  1    4    2

## 5.26 두 데이터 프레임 결합

``` r
df1 <- data.frame(a = c(1, 2))
df2 <- data.frame(b = c(7, 8))

cbind(df1, df2)
```

    ##   a b
    ## 1 1 7
    ## 2 2 8

``` r
df1 <- data.frame(x = c("a", "a"), y = c(5, 6))
df2 <- data.frame(x = c("b", "b"), y = c(9, 10))
rbind(df1, df2)
```

    ##   x  y
    ## 1 a  5
    ## 2 a  6
    ## 3 b  9
    ## 4 b 10

## 5.27 공통 열로 데이터 프레임 병합하기

``` r
born <- tibble(
  name = c("Moe", "Larry", "Curly", "Harry"),
  year.born = c(1887, 1902, 1903, 1964),
  place.born = c("Bensonhurst", "Philadelphia", "Brooklyn", "Moscow")
)

died <- tibble(
  name = c("Curly", "Moe", "Larry"),
  year.died = c(1952, 1975, 1975)
)
```

``` r
inner_join(born, died, by = "name")
```

    ## # A tibble: 3 × 4
    ##   name  year.born place.born   year.died
    ##   <chr>     <dbl> <chr>            <dbl>
    ## 1 Moe        1887 Bensonhurst       1975
    ## 2 Larry      1902 Philadelphia      1975
    ## 3 Curly      1903 Brooklyn          1952

``` r
full_join(born, died, by = "name")
```

    ## # A tibble: 4 × 4
    ##   name  year.born place.born   year.died
    ##   <chr>     <dbl> <chr>            <dbl>
    ## 1 Moe        1887 Bensonhurst       1975
    ## 2 Larry      1902 Philadelphia      1975
    ## 3 Curly      1903 Brooklyn          1952
    ## 4 Harry      1964 Moscow              NA

``` r
full_join(born, died)
```

    ## Joining, by = "name"

    ## # A tibble: 4 × 4
    ##   name  year.born place.born   year.died
    ##   <chr>     <dbl> <chr>            <dbl>
    ## 1 Moe        1887 Bensonhurst       1975
    ## 2 Larry      1902 Philadelphia      1975
    ## 3 Curly      1903 Brooklyn          1952
    ## 4 Harry      1964 Moscow              NA

``` r
df1 <- data.frame(key1 = 1:3, value = 2)
df2 <- data.frame(key2 = 1:3, value = 3)
```

``` r
inner_join(df1, df2, by = c("key1" = "key2"))
```

    ##   key1 value.x value.y
    ## 1    1       2       3
    ## 2    2       2       3
    ## 3    3       2       3

## 5.28 하나의 원자 값을 다른 원자 값으로 변환

``` r
as.numeric(" 3.14 ")
```

    ## [1] 3.14

``` r
as.integer(3.14)
```

    ## [1] 3

``` r
as.numeric("foo")
```

    ## Warning: NAs introduced by coercion

    ## [1] NA

``` r
as.character(101)
```

    ## [1] "101"

``` r
as.numeric(c("1", "2.718", "7.389", "20.086"))
```

    ## [1]  1.000  2.718  7.389 20.086

``` r
as.numeric(c("1", "2.718", "7.389", "20.086", "etc."))
```

    ## Warning: NAs introduced by coercion

    ## [1]  1.000  2.718  7.389 20.086     NA

``` r
as.character(101:105)
```

    ## [1] "101" "102" "103" "104" "105"

``` r
as.numeric(FALSE)
```

    ## [1] 0

``` r
as.numeric(TRUE)
```

    ## [1] 1

``` r
logvec <- c(TRUE, FALSE, TRUE, TRUE, TRUE, FALSE)
sum(logvec)
```

    ## [1] 4

``` r
length(logvec) - sum(logvec)
```

    ## [1] 2

## 5.29 하나의 구조화된 데이터 유형을 다른 유형으로 변환
