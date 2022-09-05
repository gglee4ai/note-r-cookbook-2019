note03
================

# 3 소프트웨어 탐색

## 3.1 작업 디렉토리 가져오기 및 설정

``` r
x <- getwd()
setwd(x)
getwd()
```

    ## [1] "/Users/gglee/github/note/note-r-cookbook-2019"

## 3.2 새 RStudio 프로젝트 생성

## 3.3 작업 공간 저장

``` r
# save.image()
```

## 3.4 명령 기록 보기

``` r
history()
```

## 3.5 이전 명령의 결과 저장

``` r
rnorm(10)
```

    ##  [1]  1.8228095 -0.2643788  2.0204190  0.0732640  2.1486045  0.4515201  0.6816636  0.1872521  0.8280608
    ## [10] -1.4915543

``` r
x <- .Last.value
x
```

    ##  [1] "note02.Rmd" "note03.Rmd" "note04.Rmd" "note05.Rmd" "note06.Rmd" "note07.Rmd" "note08.Rmd" "note09.Rmd"
    ##  [9] "note10.Rmd" "note11.Rmd" "note12.Rmd" "note13.Rmd" "note14.Rmd" "note15.Rmd" "note16.Rmd"

## 3.6 검색 경로를 통해 로드된 패키지 표시

``` r
search()
```

    ##  [1] ".GlobalEnv"        "package:forcats"   "package:stringr"   "package:dplyr"     "package:purrr"    
    ##  [6] "package:readr"     "package:tidyr"     "package:tibble"    "package:ggplot2"   "package:tidyverse"
    ## [11] "tools:rstudio"     "package:stats"     "package:graphics"  "package:grDevices" "package:utils"    
    ## [16] "package:datasets"  "package:methods"   "Autoloads"         "org:r-lib"         "package:base"

## 3.7 설치된 패키지 목록 보기

``` r
# library()
```

``` r
installed.packages()[1:5, c("Package", "Version")]
```

    ##           Package     Version 
    ## abind     "abind"     "1.4-5" 
    ## adagio    "adagio"    "0.8.4" 
    ## ADGofTest "ADGofTest" "0.3"   
    ## AER       "AER"       "1.2-10"
    ## agua      "agua"      "0.0.1"

## 3.8 패키지의 기능에 접근하기

``` r
library(MASS)
```

    ## 
    ## Attaching package: 'MASS'

    ## The following object is masked from 'package:dplyr':
    ## 
    ##     select

``` r
data(mpg, package = "ggplot2")
my_model <- lda(cty ~ displ + year, data = mpg)
```

``` r
detach(package:MASS)
```

## 3.9 내장 데이터셋에 접근하기

``` r
head(pressure)
```

    ##   temperature pressure
    ## 1           0   0.0002
    ## 2          20   0.0012
    ## 3          40   0.0060
    ## 4          60   0.0300
    ## 5          80   0.0900
    ## 6         100   0.2700

``` r
# help(pressure)
```

``` r
data()
```

``` r
data(package = .packages(all.available = TRUE))
```

``` r
data(Cars93, package = "MASS")
```

``` r
data(package = "MASS")
```

## 3.10 CRAN에서 패키지 설치하기

## 3.11 GitHub에서 패키지 설치하기

``` r
# devtools::install_github("thomasp85/tidygraph")
```

## 3.12 기본 CRAN 미러 설정 또는 변경

``` r
options("repos")[[1]][1]
```

    ##                          CRAN 
    ## "https://cloud.r-project.org"

## 3.13 스크립트 실행

``` r
source("hello.R")
```

    ## [1] "Hello, World!"

``` r
source("hello.R", echo = TRUE)
```

    ## 
    ## > print("Hello, World!")
    ## [1] "Hello, World!"

## 3.14 배치 스크립트 실행

``` r
# Rscript --slave arith.R 2 3.1415
# ./arith.R 2 3.1415
```

## 3.15 R 홈 디렉토리 찾기

``` r
Sys.getenv("R_HOME")
```

    ## [1] "/Library/Frameworks/R.framework/Versions/4.2-arm64/Resources"

## 3.16 R 시작 사용자 지정

## 3.17 클라우드에서 R 및 RStudio 사용
