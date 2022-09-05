note12
================

# 12 가지 유용한 트릭

## 12.1 데이터 엿보기

``` r
load(file = "./data/lab_df.rdata")
head(lab_df)
```

    ##             x lab          y
    ## 1  0.07613317  NJ  1.6212870
    ## 2  1.41494855  KY 10.3377301
    ## 3  2.51757643  KY 14.2844286
    ## 4 -0.30426377  KY  0.5992972
    ## 5  2.39156565  KY 13.0913340
    ## 6  2.06024789  NJ 16.3205385

``` r
tail(lab_df)
```

    ##              x lab          y
    ## 195  7.3532639  KY 38.8804138
    ## 196 -0.7417428  KY -0.2979567
    ## 197  2.1155183  NJ 11.6294607
    ## 198  1.6058650  KY  9.4077103
    ## 199 -0.5230353  KY -1.0887942
    ## 200  0.6751149  KY  5.8083875

``` r
View(lab_df)
```

## 12.2 할당 결과 인쇄

``` r
x <- 1 / pi
(x <- 1 / pi)
```

    ## [1] 0.3183099

``` r
load(file = "./data/daily.prod.rdata")
daily.prod
```

    ##     Widgets Gadgets Thingys
    ## Mon     179     167     182
    ## Tue     153     193     166
    ## Wed     183     190     170
    ## Thu     153     161     171
    ## Fri     154     181     186

``` r
colSums(daily.prod)
```

    ## Widgets Gadgets Thingys 
    ##     822     892     875

``` r
rowSums(daily.prod)
```

    ## Mon Tue Wed Thu Fri 
    ## 528 512 543 485 521

``` r
rbind(daily.prod, Totals = colSums(daily.prod))
```

    ##        Widgets Gadgets Thingys
    ## Mon        179     167     182
    ## Tue        153     193     166
    ## Wed        183     190     170
    ## Thu        153     161     171
    ## Fri        154     181     186
    ## Totals     822     892     875

## 12.3 행과 열 합산

``` r
load(file = './data/daily.prod.rdata')
daily.prod
```

    ##     Widgets Gadgets Thingys
    ## Mon     179     167     182
    ## Tue     153     193     166
    ## Wed     183     190     170
    ## Thu     153     161     171
    ## Fri     154     181     186

``` r
colSums(daily.prod)
```

    ## Widgets Gadgets Thingys 
    ##     822     892     875

``` r
rowSums(daily.prod)
```

    ## Mon Tue Wed Thu Fri 
    ## 528 512 543 485 521

``` r
rbind(daily.prod, Totals=colSums(daily.prod))
```

    ##        Widgets Gadgets Thingys
    ## Mon        179     167     182
    ## Tue        153     193     166
    ## Wed        183     190     170
    ## Thu        153     161     171
    ## Fri        154     181     186
    ## Totals     822     892     875

## 12.4 열에 데이터 인쇄하기

``` r
load(file = "./data/xy.rdata")
print(x)
```

    ##  [1] -0.6264538  0.1836433 -0.8356286  1.5952808  0.3295078 -0.8204684  0.4874291  0.7383247  0.5757814
    ## [10] -0.3053884

``` r
print(y)
```

    ##  [1]  1.51178117  0.38984324 -0.62124058 -2.21469989  1.12493092 -0.04493361 -0.01619026  0.94383621
    ##  [9]  0.82122120  0.59390132

``` r
cbind(x, y, Total = x + y)
```

    ##                x           y      Total
    ##  [1,] -0.6264538  1.51178117  0.8853274
    ##  [2,]  0.1836433  0.38984324  0.5734866
    ##  [3,] -0.8356286 -0.62124058 -1.4568692
    ##  [4,]  1.5952808 -2.21469989 -0.6194191
    ##  [5,]  0.3295078  1.12493092  1.4544387
    ##  [6,] -0.8204684 -0.04493361 -0.8654020
    ##  [7,]  0.4874291 -0.01619026  0.4712388
    ##  [8,]  0.7383247  0.94383621  1.6821609
    ##  [9,]  0.5757814  0.82122120  1.3970025
    ## [10,] -0.3053884  0.59390132  0.2885129

## 12.5 데이터 비닝

``` r
x <- rnorm(1000)
breaks <- c(-3, -2, -1, 0, 1, 2, 3)
f <- cut(x, breaks)
summary(f)
```

    ## (-3,-2] (-2,-1]  (-1,0]   (0,1]   (1,2]   (2,3]    NA's 
    ##      20     134     320     375     131      19       1

``` r
f <- cut(x, breaks, labels = c("Bottom", "Low", "Neg", "Pos", "High", "Top"))
summary(f)
```

    ## Bottom    Low    Neg    Pos   High    Top   NA's 
    ##     20    134    320    375    131     19      1

## 12.6 특정 값의 위치 찾기

``` r
vec <- c(100, 90, 80, 70, 60, 50, 40, 30, 20, 10)
match(80, vec)
```

    ## [1] 3

``` r
which.min(vec)
```

    ## [1] 10

``` r
which.max(vec)
```

    ## [1] 1

## 12.7 벡터의 모든 n번째 요소 선택하기

``` r
v <- rnorm(10)
n <- 2
v[seq_along(v) %% n == 0]
```

    ## [1]  1.7111994  1.3218111  0.1465995 -0.7848352 -1.2215102

``` r
v[c(FALSE, TRUE)]
```

    ## [1]  1.7111994  1.3218111  0.1465995 -0.7848352 -1.2215102

## 12.8 최소값 또는 최대값 찾기

``` r
pmin(1:5, 5:1)
```

    ## [1] 1 2 3 2 1

``` r
pmax(1:5, 5:1)
```

    ## [1] 5 4 3 4 5

``` r
v <- c(-3:3)
pmax(v, 0)
```

    ## [1] 0 0 0 0 1 2 3

``` r
df <- data.frame(
  a = c(1, 5, 8),
  b = c(2, 3, 7),
  c = c(0, 4, 9)
)
df
```

    ##   a b c
    ## 1 1 2 0
    ## 2 5 3 4
    ## 3 8 7 9

``` r
library(tidyverse)
df %>%
  mutate(max_val = pmax(a, b, c))
```

    ##   a b c max_val
    ## 1 1 2 0       2
    ## 2 5 3 4       5
    ## 3 8 7 9       9

## 12.9 여러 변수의 모든 조합 생성

``` r
sides <- c("Heads", "Tails")
faces <- c("1 pip", paste(2:6, "pips"))
sides
```

    ## [1] "Heads" "Tails"

``` r
faces
```

    ## [1] "1 pip"  "2 pips" "3 pips" "4 pips" "5 pips" "6 pips"

``` r
expand.grid(faces, sides)
```

    ##      Var1  Var2
    ## 1   1 pip Heads
    ## 2  2 pips Heads
    ## 3  3 pips Heads
    ## 4  4 pips Heads
    ## 5  5 pips Heads
    ## 6  6 pips Heads
    ## 7   1 pip Tails
    ## 8  2 pips Tails
    ## 9  3 pips Tails
    ## 10 4 pips Tails
    ## 11 5 pips Tails
    ## 12 6 pips Tails

``` r
expand.grid(faces, faces)
```

    ##      Var1   Var2
    ## 1   1 pip  1 pip
    ## 2  2 pips  1 pip
    ## 3  3 pips  1 pip
    ## 4  4 pips  1 pip
    ## 5  5 pips  1 pip
    ## 6  6 pips  1 pip
    ## 7   1 pip 2 pips
    ## 8  2 pips 2 pips
    ## 9  3 pips 2 pips
    ## 10 4 pips 2 pips
    ## 11 5 pips 2 pips
    ## 12 6 pips 2 pips
    ## 13  1 pip 3 pips
    ## 14 2 pips 3 pips
    ## 15 3 pips 3 pips
    ## 16 4 pips 3 pips
    ## 17 5 pips 3 pips
    ## 18 6 pips 3 pips
    ## 19  1 pip 4 pips
    ## 20 2 pips 4 pips
    ## 21 3 pips 4 pips
    ## 22 4 pips 4 pips
    ## 23 5 pips 4 pips
    ## 24 6 pips 4 pips
    ## 25  1 pip 5 pips
    ## 26 2 pips 5 pips
    ## 27 3 pips 5 pips
    ## 28 4 pips 5 pips
    ## 29 5 pips 5 pips
    ## 30 6 pips 5 pips
    ## 31  1 pip 6 pips
    ## 32 2 pips 6 pips
    ## 33 3 pips 6 pips
    ## 34 4 pips 6 pips
    ## 35 5 pips 6 pips
    ## 36 6 pips 6 pips

``` r
expand_grid(faces, faces)
```

    ## # A tibble: 36 × 2
    ##    faces...1 faces...2
    ##    <chr>     <chr>    
    ##  1 1 pip     1 pip    
    ##  2 1 pip     2 pips   
    ##  3 1 pip     3 pips   
    ##  4 1 pip     4 pips   
    ##  5 1 pip     5 pips   
    ##  6 1 pip     6 pips   
    ##  7 2 pips    1 pip    
    ##  8 2 pips    2 pips   
    ##  9 2 pips    3 pips   
    ## 10 2 pips    4 pips   
    ## # … with 26 more rows

``` r
?expand_grid
```

## 12.10 데이터 프레임 병합하기

``` r
load(file = "./data/daily.prod.rdata")
daily.prod
```

    ##     Widgets Gadgets Thingys
    ## Mon     179     167     182
    ## Tue     153     193     166
    ## Wed     183     190     170
    ## Thu     153     161     171
    ## Fri     154     181     186

``` r
mean(as.matrix(daily.prod))
```

    ## [1] 172.6

## 12.11 데이터 프레임 정렬하기

``` r
load(file = "./data/outcome.rdata")
df
```

    ##   month day outcome
    ## 1     7  11     Win
    ## 2     8  10    Lose
    ## 3     8  25     Tie
    ## 4     6  27     Tie
    ## 5     7  22     Win

``` r
library(dplyr)
arrange(df, month)
```

    ##   month day outcome
    ## 1     6  27     Tie
    ## 2     7  11     Win
    ## 3     7  22     Win
    ## 4     8  10    Lose
    ## 5     8  25     Tie

``` r
arrange(df, -month)
```

    ##   month day outcome
    ## 1     8  10    Lose
    ## 2     8  25     Tie
    ## 3     7  11     Win
    ## 4     7  22     Win
    ## 5     6  27     Tie

``` r
arrange(df, month, day)
```

    ##   month day outcome
    ## 1     6  27     Tie
    ## 2     7  11     Win
    ## 3     7  22     Win
    ## 4     8  10    Lose
    ## 5     8  25     Tie

## 12.12 변수에서 속성 제거

``` r
load(file = "./data/conf.rdata")
m <- lm(y ~ x1)
slope <- coef(m)[2]
slope
```

    ##        x1 
    ## -10.96094

``` r
str(slope)
```

    ##  Named num -11
    ##  - attr(*, "names")= chr "x1"

``` r
attributes(slope) <- NULL
slope
```

    ## [1] -10.96094

``` r
attr(slope, "names") <- NULL
```

## 12.13 객체의 구조 공개하기

``` r
load(file = "./data/conf.rdata")
m <- lm(y ~ x1)
print(m)
```

    ## 
    ## Call:
    ## lm(formula = y ~ x1)
    ## 
    ## Coefficients:
    ## (Intercept)           x1  
    ##       15.86       -10.96

``` r
class(m)
```

    ## [1] "lm"

``` r
mode(m)
```

    ## [1] "list"

``` r
names(m)
```

    ##  [1] "coefficients"  "residuals"     "effects"       "rank"          "fitted.values" "assign"       
    ##  [7] "qr"            "df.residual"   "xlevels"       "call"          "terms"         "model"

``` r
str(m)
```

    ## List of 12
    ##  $ coefficients : Named num [1:2] 15.9 -11
    ##   ..- attr(*, "names")= chr [1:2] "(Intercept)" "x1"
    ##  $ residuals    : Named num [1:30] 36.6 58.6 112.1 -35.2 -61.7 ...
    ##   ..- attr(*, "names")= chr [1:30] "1" "2" "3" "4" ...
    ##  $ effects      : Named num [1:30] -73.1 69.3 93.9 -31.1 -66.3 ...
    ##   ..- attr(*, "names")= chr [1:30] "(Intercept)" "x1" "" "" ...
    ##  $ rank         : int 2
    ##  $ fitted.values: Named num [1:30] 25.69 13.83 -1.55 28.25 16.74 ...
    ##   ..- attr(*, "names")= chr [1:30] "1" "2" "3" "4" ...
    ##  $ assign       : int [1:2] 0 1
    ##  $ qr           :List of 5
    ##   ..$ qr   : num [1:30, 1:2] -5.477 0.183 0.183 0.183 0.183 ...
    ##   .. ..- attr(*, "dimnames")=List of 2
    ##   .. .. ..$ : chr [1:30] "1" "2" "3" "4" ...
    ##   .. .. ..$ : chr [1:2] "(Intercept)" "x1"
    ##   .. ..- attr(*, "assign")= int [1:2] 0 1
    ##   ..$ qraux: num [1:2] 1.18 1.02
    ##   ..$ pivot: int [1:2] 1 2
    ##   ..$ tol  : num 1e-07
    ##   ..$ rank : int 2
    ##   ..- attr(*, "class")= chr "qr"
    ##  $ df.residual  : int 28
    ##  $ xlevels      : Named list()
    ##  $ call         : language lm(formula = y ~ x1)
    ##  $ terms        :Classes 'terms', 'formula'  language y ~ x1
    ##   .. ..- attr(*, "variables")= language list(y, x1)
    ##   .. ..- attr(*, "factors")= int [1:2, 1] 0 1
    ##   .. .. ..- attr(*, "dimnames")=List of 2
    ##   .. .. .. ..$ : chr [1:2] "y" "x1"
    ##   .. .. .. ..$ : chr "x1"
    ##   .. ..- attr(*, "term.labels")= chr "x1"
    ##   .. ..- attr(*, "order")= int 1
    ##   .. ..- attr(*, "intercept")= int 1
    ##   .. ..- attr(*, "response")= int 1
    ##   .. ..- attr(*, ".Environment")=<environment: R_GlobalEnv> 
    ##   .. ..- attr(*, "predvars")= language list(y, x1)
    ##   .. ..- attr(*, "dataClasses")= Named chr [1:2] "numeric" "numeric"
    ##   .. .. ..- attr(*, "names")= chr [1:2] "y" "x1"
    ##  $ model        :'data.frame':   30 obs. of  2 variables:
    ##   ..$ y : num [1:30] 62.25 72.45 110.59 -6.94 -44.99 ...
    ##   ..$ x1: num [1:30] -0.8969 0.1848 1.5878 -1.1304 -0.0803 ...
    ##   ..- attr(*, "terms")=Classes 'terms', 'formula'  language y ~ x1
    ##   .. .. ..- attr(*, "variables")= language list(y, x1)
    ##   .. .. ..- attr(*, "factors")= int [1:2, 1] 0 1
    ##   .. .. .. ..- attr(*, "dimnames")=List of 2
    ##   .. .. .. .. ..$ : chr [1:2] "y" "x1"
    ##   .. .. .. .. ..$ : chr "x1"
    ##   .. .. ..- attr(*, "term.labels")= chr "x1"
    ##   .. .. ..- attr(*, "order")= int 1
    ##   .. .. ..- attr(*, "intercept")= int 1
    ##   .. .. ..- attr(*, "response")= int 1
    ##   .. .. ..- attr(*, ".Environment")=<environment: R_GlobalEnv> 
    ##   .. .. ..- attr(*, "predvars")= language list(y, x1)
    ##   .. .. ..- attr(*, "dataClasses")= Named chr [1:2] "numeric" "numeric"
    ##   .. .. .. ..- attr(*, "names")= chr [1:2] "y" "x1"
    ##  - attr(*, "class")= chr "lm"

## 12.14 코드 타이밍

``` r
library(tictoc)
tic("making big numbers")
total_val <- sum(rnorm(1e7))
toc()
```

    ## making big numbers: 0.423 sec elapsed

``` r
tic("two sums")
sum(rnorm(10000000))
```

    ## [1] -1873.736

``` r
sum(rnorm(10000000))
```

    ## [1] 2792.78

``` r
toc_result <- toc()
```

    ## two sums: 0.56 sec elapsed

``` r
print(toc_result)
```

    ## $tic
    ## elapsed 
    ##  33.163 
    ## 
    ## $toc
    ## elapsed 
    ##  33.723 
    ## 
    ## $msg
    ## [1] "two sums"
    ## 
    ## $callback_msg
    ## [1] "two sums: 0.56 sec elapsed"

``` r
paste("the code ran in", round((toc_result$toc - toc_result$tic) / 60, 4), "minutes")
```

    ## [1] "the code ran in 0.0093 minutes"

``` r
start <- Sys.time()
sum(rnorm(10000000))
```

    ## [1] -1743.237

``` r
sum(rnorm(10000000))
```

    ## [1] 6796.581

``` r
Sys.time() - start
```

    ## Time difference of 0.5584109 secs

## 12.15 경고 및 오류 메시지 억제

``` r
library(tseries)
```

    ## Registered S3 method overwritten by 'quantmod':
    ##   method            from
    ##   as.zoo.data.frame zoo

    ## 
    ##     'tseries' version: 0.10-51
    ## 
    ##     'tseries' is a package for time series analysis and computational finance.
    ## 
    ##     See 'library(help="tseries")' for details.

``` r
load("data/adf.rdata")
results <- adf.test(x)
```

    ## Warning in adf.test(x): p-value smaller than printed p-value

``` r
results <- suppressWarnings(adf.test(x))
results
```

    ## 
    ##  Augmented Dickey-Fuller Test
    ## 
    ## data:  x
    ## Dickey-Fuller = -5.6009, Lag order = 1, p-value = 0.01
    ## alternative hypothesis: stationary

``` r
warnings()
```

## 12.16 목록에서 함수 인수 가져오기

``` r
vec <- c(1, 3, 5, 7, 9)
mean(vec)
```

    ## [1] 5

``` r
numbers <- list(1, 3, 5, 7, 9)
mean(unlist(numbers))
```

    ## [1] 5

``` r
my_lists <-
  list(
    col1 = list(7, 8),
    col2 = list(70, 80),
    col3 = list(700, 800)
  )
my_lists
```

    ## $col1
    ## $col1[[1]]
    ## [1] 7
    ## 
    ## $col1[[2]]
    ## [1] 8
    ## 
    ## 
    ## $col2
    ## $col2[[1]]
    ## [1] 70
    ## 
    ## $col2[[2]]
    ## [1] 80
    ## 
    ## 
    ## $col3
    ## $col3[[1]]
    ## [1] 700
    ## 
    ## $col3[[2]]
    ## [1] 800

``` r
cbind(my_lists)
```

    ##      my_lists
    ## col1 list,2  
    ## col2 list,2  
    ## col3 list,2

``` r
cbind(unlist(my_lists))
```

    ##       [,1]
    ## col11    7
    ## col12    8
    ## col21   70
    ## col22   80
    ## col31  700
    ## col32  800

``` r
do.call(cbind, my_lists)
```

    ##      col1 col2 col3
    ## [1,] 7    70   700 
    ## [2,] 8    80   800

## 12.17 자신만의 이진 연산자 정의하기

``` r
"%+-%" <- function(x, margin) {
  x + c(-1, +1) * margin
}
```

``` r
100 %+-% (1.96 * 15)
```

    ## [1]  70.6 129.4

``` r
"%+%" <- function(s1, s2) {
  paste(s1, s2, sep = "")
}
"Hello" %+% "World"
```

    ## [1] "HelloWorld"

``` r
"limit=" %+% round(qnorm(1 - 0.05 / 2), 2)
```

    ## [1] "limit=1.96"

``` r
100 %+-% 1.96 * 15
```

    ## [1] 1470.6 1529.4

## 12.18 시작 메시지 표시 안 함

``` r
# R --quiet
```

## 12.19 환경 변수 가져오기 및 설정

``` r
Sys.getenv()
```

    ## __CF_USER_TEXT_ENCODING          0x1F5:0x0:0x0
    ## __CFBundleIdentifier             org.rstudio.RStudio
    ## CLICOLOR_FORCE                   1
    ## COMMAND_MODE                     unix2003
    ## DISPLAY                          /private/tmp/com.apple.launchd.jyKl1ohu9c/org.xquartz:0
    ## EDITOR                           vi
    ## GIT_ASKPASS                      rpostback-askpass
    ## HOME                             /Users/gglee
    ## LANG                             en_US.UTF-8
    ## LC_CTYPE                         en_US.UTF-8
    ## LN_S                             ln -s
    ## LOGNAME                          gglee
    ## MAKE                             make
    ## MPLENGINE                        tkAgg
    ## PAGER                            /usr/bin/less
    ## PATH                             /opt/homebrew/bin:/opt/homebrew/sbin:/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin:/opt/X11/bin:/Users/gglee/Applications/quarto/bin:/Library/TeX/texbin:/usr/texbin:/Applications/RStudio.app/Contents/MacOS/quarto/bin:/Applications/RStudio.app/Contents/MacOS
    ## PYTHONIOENCODING                 utf-8
    ## R_BROWSER                        /usr/bin/open
    ## R_BZIPCMD                        /usr/bin/bzip2
    ## R_CLI_HAS_HYPERLINK_IDE_HELP     true
    ## R_CLI_HAS_HYPERLINK_IDE_RUN      true
    ## R_CLI_HAS_HYPERLINK_IDE_VIGNETTE
    ##                                  true
    ## R_DOC_DIR                        /Library/Frameworks/R.framework/Versions/4.2-arm64/Resources/doc
    ## R_GZIPCMD                        /usr/bin/gzip
    ## R_HOME                           /Library/Frameworks/R.framework/Versions/4.2-arm64/Resources
    ## R_INCLUDE_DIR                    /Library/Frameworks/R.framework/Versions/4.2-arm64/Resources/include
    ## R_LIBS_SITE                      /Library/Frameworks/R.framework/Versions/4.2-arm64/Resources/site-library
    ## R_LIBS_USER                      /Users/gglee/Library/R/arm64/4.2/library
    ## R_PAPERSIZE                      a4
    ## R_PDFVIEWER                      /usr/bin/open
    ## R_PLATFORM                       aarch64-apple-darwin20
    ## R_PRINTCMD                       lpr
    ## R_QPDF                           /Library/Frameworks/R.framework/Versions/4.2-arm64/Resources/bin/qpdf
    ## R_RD4PDF                         times,inconsolata,hyper
    ## R_SESSION_TMPDIR                 /var/folders/nl/mgrs1_xj5jggr_n38rmyxdyc0000gn/T//RtmpfLcVXk
    ## R_SHARE_DIR                      /Library/Frameworks/R.framework/Versions/4.2-arm64/Resources/share
    ## R_STRIP_SHARED_LIB               strip -x
    ## R_STRIP_STATIC_LIB               strip -S
    ## R_SYSTEM_ABI                     macos,gcc,gxx,gfortran,gfortran
    ## R_TEXI2DVICMD                    /opt/R/arm64/bin/texi2dvi
    ## R_UNZIPCMD                       /usr/bin/unzip
    ## R_ZIPCMD                         /usr/bin/zip
    ## RMARKDOWN_MATHJAX_PATH           /Applications/RStudio.app/Contents/Resources/resources/mathjax-27
    ## RS_PPM_FD_READ                   16
    ## RS_PPM_FD_WRITE                  24
    ## RS_RPOSTBACK_PATH                /Applications/RStudio.app/Contents/rpostback
    ## RS_SHARED_SECRET                 aafcd899-a6bb-4b0b-aa6d-129092fbffb8
    ## RSTUDIO                          1
    ## RSTUDIO_CLI_HYPERLINKS           true
    ## RSTUDIO_CONSOLE_COLOR            256
    ## RSTUDIO_CONSOLE_WIDTH            111
    ## RSTUDIO_FALLBACK_LIBRARY_PATH    /var/folders/nl/mgrs1_xj5jggr_n38rmyxdyc0000gn/T/rstudio-fallback-library-path-dmxXmL
    ## RSTUDIO_PANDOC                   /Applications/RStudio.app/Contents/MacOS/quarto/bin/tools
    ## RSTUDIO_PROGRAM_MODE             desktop
    ## RSTUDIO_SESSION_PID              1103
    ## RSTUDIO_SESSION_PORT             59195
    ## RSTUDIO_USER_IDENTITY            gglee
    ## RSTUDIO_WINUTILS                 bin/winutils
    ## SED                              /usr/bin/sed
    ## SHELL                            /bin/zsh
    ## SSH_ASKPASS                      rpostback-askpass
    ## SSH_AUTH_SOCK                    /private/tmp/com.apple.launchd.yHWXanx3fI/Listeners
    ## TAR                              /usr/bin/tar
    ## TERM                             xterm-256color
    ## TMPDIR                           /var/folders/nl/mgrs1_xj5jggr_n38rmyxdyc0000gn/T/
    ## TZDIR                            /var/db/timezone/zoneinfo
    ## USER                             gglee
    ## XPC_FLAGS                        0x0
    ## XPC_SERVICE_NAME                 application.org.rstudio.RStudio.4643821.4643841

## 12.20 코드 섹션 사용

``` r
# test ----
```

## 12.21 로컬에서 병렬로 R 실행하기

``` r
# devtools::install_github("DavisVaughan/furrr")
```

``` r
simulate_pi <- function(n_iterations) {
  rand_draws <- matrix(runif(2 * n_iterations, -1, 1), ncol = 2)
  num_in <- sum(sqrt(rand_draws[, 1]**2 + rand_draws[, 2]**2) <= 1)
  pi_hat <- (num_in / n_iterations) * 4
  return(pi_hat)
}
simulate_pi(1000000)
```

    ## [1] 3.143172

``` r
library(purrr) # for `map`
library(tictoc) # for timing our code

draw_list <- as.list(rep(5000000, 200))

tic("simulate pi - single process")
sims_list <- map(draw_list, simulate_pi)
toc()
```

    ## simulate pi - single process: 21.201 sec elapsed

``` r
#> simulate pi - single process: 131.861 sec elapsed

mean(unlist(sims_list))
```

    ## [1] 3.141563

``` r
library(furrr)
```

    ## Loading required package: future

    ## 
    ## Attaching package: 'future'

    ## The following object is masked from 'package:tseries':
    ## 
    ##     value

``` r
plan(multiprocess)
```

    ## Warning: Strategy 'multiprocess' is deprecated in future (>= 1.20.0) [2020-10-30]. Instead, explicitly
    ## specify either 'multisession' (recommended) or 'multicore'. In the current R session, 'multiprocess' equals
    ## 'multisession'.

    ## Warning in supportsMulticoreAndRStudio(...): [ONE-TIME WARNING] Forked processing ('multicore') is
    ## not supported when running R from RStudio because it is considered unstable. For more details, how
    ## to control forked processing or not, and how to silence this warning in future R sessions, see ?
    ## parallelly::supportsMulticore

``` r
tic("simulate pi - parallel")
sims_list <- future_map(draw_list, simulate_pi)
```

    ## Warning: UNRELIABLE VALUE: Future ('<none>') unexpectedly generated random numbers without specifying argument
    ## 'seed'. There is a risk that those random numbers are not statistically sound and the overall results might be
    ## invalid. To fix this, specify 'seed=TRUE'. This ensures that proper, parallel-safe random numbers are produced
    ## via the L'Ecuyer-CMRG method. To disable this check, use 'seed=NULL', or set option 'future.rng.onMisuse' to
    ## "ignore".

    ## Warning: UNRELIABLE VALUE: Future ('<none>') unexpectedly generated random numbers without specifying argument
    ## 'seed'. There is a risk that those random numbers are not statistically sound and the overall results might be
    ## invalid. To fix this, specify 'seed=TRUE'. This ensures that proper, parallel-safe random numbers are produced
    ## via the L'Ecuyer-CMRG method. To disable this check, use 'seed=NULL', or set option 'future.rng.onMisuse' to
    ## "ignore".

    ## Warning: UNRELIABLE VALUE: Future ('<none>') unexpectedly generated random numbers without specifying argument
    ## 'seed'. There is a risk that those random numbers are not statistically sound and the overall results might be
    ## invalid. To fix this, specify 'seed=TRUE'. This ensures that proper, parallel-safe random numbers are produced
    ## via the L'Ecuyer-CMRG method. To disable this check, use 'seed=NULL', or set option 'future.rng.onMisuse' to
    ## "ignore".

    ## Warning: UNRELIABLE VALUE: Future ('<none>') unexpectedly generated random numbers without specifying argument
    ## 'seed'. There is a risk that those random numbers are not statistically sound and the overall results might be
    ## invalid. To fix this, specify 'seed=TRUE'. This ensures that proper, parallel-safe random numbers are produced
    ## via the L'Ecuyer-CMRG method. To disable this check, use 'seed=NULL', or set option 'future.rng.onMisuse' to
    ## "ignore".

    ## Warning: UNRELIABLE VALUE: Future ('<none>') unexpectedly generated random numbers without specifying argument
    ## 'seed'. There is a risk that those random numbers are not statistically sound and the overall results might be
    ## invalid. To fix this, specify 'seed=TRUE'. This ensures that proper, parallel-safe random numbers are produced
    ## via the L'Ecuyer-CMRG method. To disable this check, use 'seed=NULL', or set option 'future.rng.onMisuse' to
    ## "ignore".

    ## Warning: UNRELIABLE VALUE: Future ('<none>') unexpectedly generated random numbers without specifying argument
    ## 'seed'. There is a risk that those random numbers are not statistically sound and the overall results might be
    ## invalid. To fix this, specify 'seed=TRUE'. This ensures that proper, parallel-safe random numbers are produced
    ## via the L'Ecuyer-CMRG method. To disable this check, use 'seed=NULL', or set option 'future.rng.onMisuse' to
    ## "ignore".

    ## Warning: UNRELIABLE VALUE: Future ('<none>') unexpectedly generated random numbers without specifying argument
    ## 'seed'. There is a risk that those random numbers are not statistically sound and the overall results might be
    ## invalid. To fix this, specify 'seed=TRUE'. This ensures that proper, parallel-safe random numbers are produced
    ## via the L'Ecuyer-CMRG method. To disable this check, use 'seed=NULL', or set option 'future.rng.onMisuse' to
    ## "ignore".

    ## Warning: UNRELIABLE VALUE: Future ('<none>') unexpectedly generated random numbers without specifying argument
    ## 'seed'. There is a risk that those random numbers are not statistically sound and the overall results might be
    ## invalid. To fix this, specify 'seed=TRUE'. This ensures that proper, parallel-safe random numbers are produced
    ## via the L'Ecuyer-CMRG method. To disable this check, use 'seed=NULL', or set option 'future.rng.onMisuse' to
    ## "ignore".

    ## Warning: UNRELIABLE VALUE: Future ('<none>') unexpectedly generated random numbers without specifying argument
    ## 'seed'. There is a risk that those random numbers are not statistically sound and the overall results might be
    ## invalid. To fix this, specify 'seed=TRUE'. This ensures that proper, parallel-safe random numbers are produced
    ## via the L'Ecuyer-CMRG method. To disable this check, use 'seed=NULL', or set option 'future.rng.onMisuse' to
    ## "ignore".

    ## Warning: UNRELIABLE VALUE: Future ('<none>') unexpectedly generated random numbers without specifying argument
    ## 'seed'. There is a risk that those random numbers are not statistically sound and the overall results might be
    ## invalid. To fix this, specify 'seed=TRUE'. This ensures that proper, parallel-safe random numbers are produced
    ## via the L'Ecuyer-CMRG method. To disable this check, use 'seed=NULL', or set option 'future.rng.onMisuse' to
    ## "ignore".

``` r
toc()
```

    ## simulate pi - parallel: 4.324 sec elapsed

``` r
mean(unlist(sims_list))
```

    ## [1] 3.141571

## 12.22 원격에서 병렬로 R 실행하기
