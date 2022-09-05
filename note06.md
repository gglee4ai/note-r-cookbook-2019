note06
================

# 6 데이터 변환

``` r
library(tidyverse)
```

## 6.1 각 목록 요소에 함수 적용하기

``` r
lst <- list(
  a = c(1, 2, 3),
  b = c(4, 5, 6)
)
lst %>%
  map(mean)
```

    ## $a
    ## [1] 2
    ## 
    ## $b
    ## [1] 5

``` r
fun <- function(x) {
  if (x > 1) {
    1
  } else {
    "Less Than 1"
  }
}

fun(5)
```

    ## [1] 1

``` r
fun(0.5)
```

    ## [1] "Less Than 1"

``` r
lst <- list(.5, 1.5, .9, 2)
map(lst, fun)
```

    ## [[1]]
    ## [1] "Less Than 1"
    ## 
    ## [[2]]
    ## [1] 1
    ## 
    ## [[3]]
    ## [1] "Less Than 1"
    ## 
    ## [[4]]
    ## [1] 1

``` r
map_chr(lst, fun)
```

    ## [1] "Less Than 1" "1.000000"    "Less Than 1" "1.000000"

``` r
try(map_dbl(lst, fun))
```

    ## Error : Can't coerce element 1 from a character to a double

## 6.2 데이터 프레임의 모든 행에 함수 적용하기

``` r
fun <- function(a, b, c) {
  sum(seq(a, b, c))
}

df <- data.frame(
  mn = c(1, 2, 3),
  mx = c(8, 13, 18),
  rng = c(1, 2, 3)
)

df %>%
  rowwise() %>%
  mutate(output = fun(a = mn, b = mx, c = rng))
```

    ## # A tibble: 3 × 4
    ## # Rowwise: 
    ##      mn    mx   rng output
    ##   <dbl> <dbl> <dbl>  <dbl>
    ## 1     1     8     1     36
    ## 2     2    13     2     42
    ## 3     3    18     3     63

``` r
try(df %>%
  mutate(output = fun(a = mn, b = mx, c = rng)))
```

    ## Error in mutate(., output = fun(a = mn, b = mx, c = rng)) : 
    ##   Problem while computing `output = fun(a = mn, b = mx, c = rng)`.
    ## Caused by error in `seq.default()`:
    ## ! 'from' must be of length 1

## 6.3 행렬의 모든 행에 함수 적용하기

``` r
long <- matrix(1:15, 3, 5)
long
```

    ##      [,1] [,2] [,3] [,4] [,5]
    ## [1,]    1    4    7   10   13
    ## [2,]    2    5    8   11   14
    ## [3,]    3    6    9   12   15

``` r
apply(long, 1, mean)
```

    ## [1] 7 8 9

``` r
rownames(long) <- c("Moe", "Larry", "Curly")
apply(long, 1, mean)
```

    ##   Moe Larry Curly 
    ##     7     8     9

``` r
apply(long, 1, range)
```

    ##      Moe Larry Curly
    ## [1,]   1     2     3
    ## [2,]  13    14    15

## 6.4 모든 열에 함수 적용하기

``` r
mat <- matrix(c(1, 3, 2, 5, 4, 6), 2, 3)
colnames(mat) <- c("t1", "t2", "t3")
mat
```

    ##      t1 t2 t3
    ## [1,]  1  2  4
    ## [2,]  3  5  6

``` r
apply(mat, 2, mean)
```

    ##  t1  t2  t3 
    ## 2.0 3.5 5.0

## 6.5 병렬 벡터 또는 목록에 함수 적용하기

``` r
gcd <- function(a, b) {
  if (b == 0) {
    return(a)
  } else {
    return(gcd(b, a %% b))
  }
}
```

``` r
try(gcd(c(1, 2, 3), c(9, 6, 3)))
```

    ## Error in if (b == 0) { : the condition has length > 1

``` r
a <- c(1, 2, 3)
b <- c(9, 6, 3)
my_gcds <- map2(a, b, gcd)
my_gcds
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
unlist(my_gcds)
```

    ## [1] 1 2 3

``` r
map2_chr(a, b, gcd)
```

    ## [1] "1.000000" "2.000000" "3.000000"

``` r
map2_dbl(a, b, gcd)
```

    ## [1] 1 2 3

``` r
lst <- list(a, b)
pmap(lst, gcd)
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
pmap_dbl(lst, gcd)
```

    ## [1] 1 2 3

## 6.6 데이터 그룹에 함수 적용하기

``` r
df <- tibble(
  my_group = c("A", "B", "A", "B", "A", "B"),
  values = 1:6
)
df
```

    ## # A tibble: 6 × 2
    ##   my_group values
    ##   <chr>     <int>
    ## 1 A             1
    ## 2 B             2
    ## 3 A             3
    ## 4 B             4
    ## 5 A             5
    ## 6 B             6

``` r
df %>%
  group_by(my_group) %>%
  summarize(
    avg_values = mean(values),
    tot_values = sum(values),
    count_values = n()
  )
```

    ## # A tibble: 2 × 4
    ##   my_group avg_values tot_values count_values
    ##   <chr>         <dbl>      <int>        <int>
    ## 1 A                 3          9            3
    ## 2 B                 4         12            3

## 6.7 일부 조건을 기반으로 새 열 만들기

``` r
df <- data.frame(vals = 1:5)
df %>%
  mutate(new_vals = case_when(
    vals <= 2 ~ "2 or less",
    vals > 2 & vals <= 4 ~ "2 to 4",
    TRUE ~ "over 4"
  ))
```

    ##   vals  new_vals
    ## 1    1 2 or less
    ## 2    2 2 or less
    ## 3    3    2 to 4
    ## 4    4    2 to 4
    ## 5    5    over 4
