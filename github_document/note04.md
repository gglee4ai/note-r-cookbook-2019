note04
================

# 4 입력 및 출력

## 4.1 키보드에서 데이터 입력

``` r
scores <- c(61, 66, 90, 88, 100)
points <- data.frame(
  label = c("Low", "Mid", "High"),
  lbound = c(0, 0.67, 1.64),
  ubound = c(0.67, 1.64, 2.33)
)
```

## 4.2 더 적은 자릿수(또는 더 많은 자릿수) 인쇄

``` r
print(pi, digits = 4)
```

    ## [1] 3.142

``` r
print(100 * pi, digits = 4)
```

    ## [1] 314.2

``` r
cat(pi, "\n")
```

    ## 3.141593

``` r
cat(format(pi, digits = 4), "\n")
```

    ## 3.142

``` r
print(pnorm(-3:3), digits = 2)
```

    ## [1] 0.0013 0.0228 0.1587 0.5000 0.8413 0.9772 0.9987

``` r
format(pnorm(-3:3), digits = 2)
```

    ## [1] "0.0013" "0.0228" "0.1587" "0.5000" "0.8413" "0.9772" "0.9987"

``` r
q <- seq(from = 0, to = 3, by = 0.5)
tbl <- data.frame(Quant = q, Lower = pnorm(-q), Upper = pnorm(q))
tbl
```

    ##   Quant       Lower     Upper
    ## 1   0.0 0.500000000 0.5000000
    ## 2   0.5 0.308537539 0.6914625
    ## 3   1.0 0.158655254 0.8413447
    ## 4   1.5 0.066807201 0.9331928
    ## 5   2.0 0.022750132 0.9772499
    ## 6   2.5 0.006209665 0.9937903
    ## 7   3.0 0.001349898 0.9986501

``` r
print(tbl, digits = 2)
```

    ##   Quant  Lower Upper
    ## 1   0.0 0.5000  0.50
    ## 2   0.5 0.3085  0.69
    ## 3   1.0 0.1587  0.84
    ## 4   1.5 0.0668  0.93
    ## 5   2.0 0.0228  0.98
    ## 6   2.5 0.0062  0.99
    ## 7   3.0 0.0013  1.00

## 4.3 출력을 파일로 리디렉션

``` r
answer <- 100
cat("The answer is", answer, "\n", file = "write-file.txt")
```

``` r
cat(answer, file = "write-file.txt", append = TRUE)
```

``` r
con <- file("write-file.txt", "w")
cat("This is Spartan!", file = con)
close(con)
```

``` r
file.remove("write-file.txt")
```

    ## [1] TRUE

## 4.4 파일 나열

``` r
list.files()
```

    ##  [1] "arith.R"                    "data"                       "g1.png"                    
    ##  [4] "github_document"            "hello.R"                    "note-r-cookbook-2019.Rproj"
    ##  [7] "note02_files"               "note02.html"                "note02.md"                 
    ## [10] "note02.nb.html"             "note02.Rmd"                 "note03.html"               
    ## [13] "note03.md"                  "note03.Rmd"                 "note04.Rmd"                
    ## [16] "note05.Rmd"                 "note06.Rmd"                 "note07.Rmd"                
    ## [19] "note08.Rmd"                 "note09.Rmd"                 "note10.Rmd"                
    ## [22] "note11.Rmd"                 "note12.Rmd"                 "note13.Rmd"                
    ## [25] "note14.Rmd"                 "note15.Rmd"                 "note16.Rmd"                
    ## [28] "README.md"

``` r
list.files(path = getwd(), pattern = "[.]Rmd")
```

    ##  [1] "note02.Rmd" "note03.Rmd" "note04.Rmd" "note05.Rmd" "note06.Rmd" "note07.Rmd" "note08.Rmd" "note09.Rmd"
    ##  [9] "note10.Rmd" "note11.Rmd" "note12.Rmd" "note13.Rmd" "note14.Rmd" "note15.Rmd" "note16.Rmd"

``` r
list.files(path = getwd(), pattern = "\\.R$")
```

    ## [1] "arith.R" "hello.R"

``` r
list.files(recursive = TRUE)
```

    ##   [1] "arith.R"                                                       
    ##   [2] "data/ac.rdata"                                                 
    ##   [3] "data/adf.rdata"                                                
    ##   [4] "data/anova.rdata"                                              
    ##   [5] "data/anova2.rdata"                                             
    ##   [6] "data/bad.rdata"                                                
    ##   [7] "data/batches.rdata"                                            
    ##   [8] "data/bnd_cmty.Rdata"                                           
    ##   [9] "data/compositePerf-2010.csv"                                   
    ##  [10] "data/conf.rdata"                                               
    ##  [11] "data/daily.prod.rdata"                                         
    ##  [12] "data/data1.csv"                                                
    ##  [13] "data/data2.csv"                                                
    ##  [14] "data/datafile_missing.tsv"                                     
    ##  [15] "data/datafile.csv"                                             
    ##  [16] "data/datafile.fwf"                                             
    ##  [17] "data/datafile.qsv"                                             
    ##  [18] "data/datafile.ssv"                                             
    ##  [19] "data/datafile.tsv"                                             
    ##  [20] "data/datafile1.ssv"                                            
    ##  [21] "data/df_decay.rdata"                                           
    ##  [22] "data/df_squared.rdata"                                         
    ##  [23] "data/diffs.rdata"                                              
    ##  [24] "data/example1_headless.csv"                                    
    ##  [25] "data/example1.csv"                                             
    ##  [26] "data/excel_table_data.xlsx"                                    
    ##  [27] "data/get_USDA_NASS_data.R"                                     
    ##  [28] "data/ibm.rdata"                                                
    ##  [29] "data/iris_excel.xlsx"                                          
    ##  [30] "data/lab_df.rdata"                                             
    ##  [31] "data/movies.sas7bdat"                                          
    ##  [32] "data/nacho_data.csv"                                           
    ##  [33] "data/NearestPoint.R"                                           
    ##  [34] "data/not_a_csv.txt"                                            
    ##  [35] "data/opt.rdata"                                                
    ##  [36] "data/outcome.rdata"                                            
    ##  [37] "data/pca.rdata"                                                
    ##  [38] "data/pred.rdata"                                               
    ##  [39] "data/pred2.rdata"                                              
    ##  [40] "data/sat.rdata"                                                
    ##  [41] "data/singles.txt"                                              
    ##  [42] "data/state_corn_yield.rds"                                     
    ##  [43] "data/student_data.rdata"                                       
    ##  [44] "data/suburbs.txt"                                              
    ##  [45] "data/tab1.csv"                                                 
    ##  [46] "data/tls.rdata"                                                
    ##  [47] "data/triples.txt"                                              
    ##  [48] "data/ts_acf.rdata"                                             
    ##  [49] "data/workers.rdata"                                            
    ##  [50] "data/world_series.csv"                                         
    ##  [51] "data/xy.rdata"                                                 
    ##  [52] "data/yield.Rdata"                                              
    ##  [53] "data/z.RData"                                                  
    ##  [54] "g1.png"                                                        
    ##  [55] "github_document/note02_files/figure-gfm/unnamed-chunk-62-1.png"
    ##  [56] "github_document/note02_files/figure-gfm/unnamed-chunk-63-1.png"
    ##  [57] "github_document/note02_files/figure-gfm/unnamed-chunk-64-1.png"
    ##  [58] "github_document/note02_files/figure-gfm/unnamed-chunk-71-1.png"
    ##  [59] "github_document/note02.md"                                     
    ##  [60] "github_document/note03.md"                                     
    ##  [61] "github_document/note04.md"                                     
    ##  [62] "github_document/note05.md"                                     
    ##  [63] "github_document/note06.md"                                     
    ##  [64] "github_document/note07.md"                                     
    ##  [65] "github_document/note08_files/figure-gfm/unnamed-chunk-29-1.png"
    ##  [66] "github_document/note08_files/figure-gfm/unnamed-chunk-30-1.png"
    ##  [67] "github_document/note08_files/figure-gfm/unnamed-chunk-31-1.png"
    ##  [68] "github_document/note08_files/figure-gfm/unnamed-chunk-32-1.png"
    ##  [69] "github_document/note08.md"                                     
    ##  [70] "github_document/note09_files/figure-gfm/unnamed-chunk-26-1.png"
    ##  [71] "github_document/note09_files/figure-gfm/unnamed-chunk-28-1.png"
    ##  [72] "github_document/note09_files/figure-gfm/unnamed-chunk-39-1.png"
    ##  [73] "github_document/note09.md"                                     
    ##  [74] "github_document/note10_files/figure-gfm/unnamed-chunk-10-1.png"
    ##  [75] "github_document/note10_files/figure-gfm/unnamed-chunk-11-1.png"
    ##  [76] "github_document/note10_files/figure-gfm/unnamed-chunk-11-2.png"
    ##  [77] "github_document/note10_files/figure-gfm/unnamed-chunk-11-3.png"
    ##  [78] "github_document/note10_files/figure-gfm/unnamed-chunk-11-4.png"
    ##  [79] "github_document/note10_files/figure-gfm/unnamed-chunk-12-1.png"
    ##  [80] "github_document/note10_files/figure-gfm/unnamed-chunk-13-1.png"
    ##  [81] "github_document/note10_files/figure-gfm/unnamed-chunk-14-1.png"
    ##  [82] "github_document/note10_files/figure-gfm/unnamed-chunk-15-1.png"
    ##  [83] "github_document/note10_files/figure-gfm/unnamed-chunk-16-1.png"
    ##  [84] "github_document/note10_files/figure-gfm/unnamed-chunk-17-1.png"
    ##  [85] "github_document/note10_files/figure-gfm/unnamed-chunk-18-1.png"
    ##  [86] "github_document/note10_files/figure-gfm/unnamed-chunk-19-1.png"
    ##  [87] "github_document/note10_files/figure-gfm/unnamed-chunk-2-1.png" 
    ##  [88] "github_document/note10_files/figure-gfm/unnamed-chunk-20-1.png"
    ##  [89] "github_document/note10_files/figure-gfm/unnamed-chunk-21-1.png"
    ##  [90] "github_document/note10_files/figure-gfm/unnamed-chunk-22-1.png"
    ##  [91] "github_document/note10_files/figure-gfm/unnamed-chunk-23-1.png"
    ##  [92] "github_document/note10_files/figure-gfm/unnamed-chunk-24-1.png"
    ##  [93] "github_document/note10_files/figure-gfm/unnamed-chunk-25-1.png"
    ##  [94] "github_document/note10_files/figure-gfm/unnamed-chunk-26-1.png"
    ##  [95] "github_document/note10_files/figure-gfm/unnamed-chunk-27-1.png"
    ##  [96] "github_document/note10_files/figure-gfm/unnamed-chunk-28-1.png"
    ##  [97] "github_document/note10_files/figure-gfm/unnamed-chunk-29-1.png"
    ##  [98] "github_document/note10_files/figure-gfm/unnamed-chunk-3-1.png" 
    ##  [99] "github_document/note10_files/figure-gfm/unnamed-chunk-30-1.png"
    ## [100] "github_document/note10_files/figure-gfm/unnamed-chunk-31-1.png"
    ## [101] "github_document/note10_files/figure-gfm/unnamed-chunk-32-1.png"
    ## [102] "github_document/note10_files/figure-gfm/unnamed-chunk-35-1.png"
    ## [103] "github_document/note10_files/figure-gfm/unnamed-chunk-36-1.png"
    ## [104] "github_document/note10_files/figure-gfm/unnamed-chunk-38-1.png"
    ## [105] "github_document/note10_files/figure-gfm/unnamed-chunk-39-1.png"
    ## [106] "github_document/note10_files/figure-gfm/unnamed-chunk-4-1.png" 
    ## [107] "github_document/note10_files/figure-gfm/unnamed-chunk-40-1.png"
    ## [108] "github_document/note10_files/figure-gfm/unnamed-chunk-41-1.png"
    ## [109] "github_document/note10_files/figure-gfm/unnamed-chunk-42-1.png"
    ## [110] "github_document/note10_files/figure-gfm/unnamed-chunk-43-1.png"
    ## [111] "github_document/note10_files/figure-gfm/unnamed-chunk-44-1.png"
    ## [112] "github_document/note10_files/figure-gfm/unnamed-chunk-45-1.png"
    ## [113] "github_document/note10_files/figure-gfm/unnamed-chunk-46-1.png"
    ## [114] "github_document/note10_files/figure-gfm/unnamed-chunk-47-1.png"
    ## [115] "github_document/note10_files/figure-gfm/unnamed-chunk-48-1.png"
    ## [116] "github_document/note10_files/figure-gfm/unnamed-chunk-49-1.png"
    ## [117] "github_document/note10_files/figure-gfm/unnamed-chunk-5-1.png" 
    ## [118] "github_document/note10_files/figure-gfm/unnamed-chunk-50-1.png"
    ## [119] "github_document/note10_files/figure-gfm/unnamed-chunk-53-1.png"
    ## [120] "github_document/note10_files/figure-gfm/unnamed-chunk-55-1.png"
    ## [121] "github_document/note10_files/figure-gfm/unnamed-chunk-56-1.png"
    ## [122] "github_document/note10_files/figure-gfm/unnamed-chunk-57-1.png"
    ## [123] "github_document/note10_files/figure-gfm/unnamed-chunk-58-1.png"
    ## [124] "github_document/note10_files/figure-gfm/unnamed-chunk-59-1.png"
    ## [125] "github_document/note10_files/figure-gfm/unnamed-chunk-6-1.png" 
    ## [126] "github_document/note10_files/figure-gfm/unnamed-chunk-60-1.png"
    ## [127] "github_document/note10_files/figure-gfm/unnamed-chunk-61-1.png"
    ## [128] "github_document/note10_files/figure-gfm/unnamed-chunk-62-1.png"
    ## [129] "github_document/note10_files/figure-gfm/unnamed-chunk-7-1.png" 
    ## [130] "github_document/note10_files/figure-gfm/unnamed-chunk-8-1.png" 
    ## [131] "github_document/note10_files/figure-gfm/unnamed-chunk-9-1.png" 
    ## [132] "github_document/note10.md"                                     
    ## [133] "github_document/note11_files/figure-gfm/unnamed-chunk-33-1.png"
    ## [134] "github_document/note11_files/figure-gfm/unnamed-chunk-33-2.png"
    ## [135] "github_document/note11_files/figure-gfm/unnamed-chunk-37-1.png"
    ## [136] "github_document/note11_files/figure-gfm/unnamed-chunk-39-1.png"
    ## [137] "github_document/note11_files/figure-gfm/unnamed-chunk-40-1.png"
    ## [138] "github_document/note11_files/figure-gfm/unnamed-chunk-40-2.png"
    ## [139] "github_document/note11_files/figure-gfm/unnamed-chunk-40-3.png"
    ## [140] "github_document/note11_files/figure-gfm/unnamed-chunk-40-4.png"
    ## [141] "github_document/note11_files/figure-gfm/unnamed-chunk-41-1.png"
    ## [142] "github_document/note11_files/figure-gfm/unnamed-chunk-42-1.png"
    ## [143] "github_document/note11_files/figure-gfm/unnamed-chunk-46-1.png"
    ## [144] "github_document/note11_files/figure-gfm/unnamed-chunk-49-1.png"
    ## [145] "github_document/note11_files/figure-gfm/unnamed-chunk-50-1.png"
    ## [146] "github_document/note11_files/figure-gfm/unnamed-chunk-50-2.png"
    ## [147] "github_document/note11_files/figure-gfm/unnamed-chunk-50-3.png"
    ## [148] "github_document/note11_files/figure-gfm/unnamed-chunk-50-4.png"
    ## [149] "github_document/note11_files/figure-gfm/unnamed-chunk-52-1.png"
    ## [150] "github_document/note11_files/figure-gfm/unnamed-chunk-53-1.png"
    ## [151] "github_document/note11_files/figure-gfm/unnamed-chunk-58-1.png"
    ## [152] "github_document/note11_files/figure-gfm/unnamed-chunk-60-1.png"
    ## [153] "github_document/note11_files/figure-gfm/unnamed-chunk-66-1.png"
    ## [154] "github_document/note11_files/figure-gfm/unnamed-chunk-71-1.png"
    ## [155] "github_document/note11_files/figure-gfm/unnamed-chunk-74-1.png"
    ## [156] "github_document/note11_files/figure-gfm/unnamed-chunk-76-1.png"
    ## [157] "github_document/note11.md"                                     
    ## [158] "github_document/note12.md"                                     
    ## [159] "github_document/note13_files/figure-gfm/unnamed-chunk-1-1.png" 
    ## [160] "github_document/note13_files/figure-gfm/unnamed-chunk-12-1.png"
    ## [161] "github_document/note13_files/figure-gfm/unnamed-chunk-15-1.png"
    ## [162] "github_document/note13_files/figure-gfm/unnamed-chunk-18-1.png"
    ## [163] "github_document/note13_files/figure-gfm/unnamed-chunk-22-1.png"
    ## [164] "github_document/note13_files/figure-gfm/unnamed-chunk-28-1.png"
    ## [165] "github_document/note13_files/figure-gfm/unnamed-chunk-9-1.png" 
    ## [166] "github_document/note13.md"                                     
    ## [167] "github_document/note14_files/figure-gfm/unnamed-chunk-48-1.png"
    ## [168] "github_document/note14_files/figure-gfm/unnamed-chunk-51-1.png"
    ## [169] "github_document/note14_files/figure-gfm/unnamed-chunk-53-1.png"
    ## [170] "github_document/note14_files/figure-gfm/unnamed-chunk-54-1.png"
    ## [171] "github_document/note14_files/figure-gfm/unnamed-chunk-58-1.png"
    ## [172] "github_document/note14_files/figure-gfm/unnamed-chunk-59-1.png"
    ## [173] "github_document/note14_files/figure-gfm/unnamed-chunk-60-1.png"
    ## [174] "github_document/note14_files/figure-gfm/unnamed-chunk-62-1.png"
    ## [175] "github_document/note14_files/figure-gfm/unnamed-chunk-63-1.png"
    ## [176] "github_document/note14_files/figure-gfm/unnamed-chunk-64-1.png"
    ## [177] "github_document/note14_files/figure-gfm/unnamed-chunk-66-1.png"
    ## [178] "github_document/note14_files/figure-gfm/unnamed-chunk-72-1.png"
    ## [179] "github_document/note14_files/figure-gfm/unnamed-chunk-73-1.png"
    ## [180] "github_document/note14_files/figure-gfm/unnamed-chunk-74-1.png"
    ## [181] "github_document/note14_files/figure-gfm/unnamed-chunk-77-1.png"
    ## [182] "github_document/note14_files/figure-gfm/unnamed-chunk-78-1.png"
    ## [183] "github_document/note14_files/figure-gfm/unnamed-chunk-79-1.png"
    ## [184] "github_document/note14_files/figure-gfm/unnamed-chunk-80-1.png"
    ## [185] "github_document/note14_files/figure-gfm/unnamed-chunk-84-1.png"
    ## [186] "github_document/note14_files/figure-gfm/unnamed-chunk-85-1.png"
    ## [187] "github_document/note14_files/figure-gfm/unnamed-chunk-9-1.png" 
    ## [188] "github_document/note14.md"                                     
    ## [189] "github_document/note15.md"                                     
    ## [190] "github_document/note16_files/figure-gfm/unnamed-chunk-10-1.png"
    ## [191] "github_document/note16_files/figure-gfm/unnamed-chunk-11-1.png"
    ## [192] "github_document/note16_files/figure-gfm/unnamed-chunk-12-1.png"
    ## [193] "github_document/note16_files/figure-gfm/unnamed-chunk-14-1.png"
    ## [194] "github_document/note16_files/figure-gfm/unnamed-chunk-15-1.png"
    ## [195] "github_document/note16_files/figure-gfm/unnamed-chunk-5-1.png" 
    ## [196] "github_document/note16_files/figure-gfm/unnamed-chunk-6-1.png" 
    ## [197] "github_document/note16_files/figure-gfm/unnamed-chunk-7-1.png" 
    ## [198] "hello.R"                                                       
    ## [199] "note-r-cookbook-2019.Rproj"                                    
    ## [200] "note02_files/figure-gfm/unnamed-chunk-62-1.png"                
    ## [201] "note02_files/figure-gfm/unnamed-chunk-63-1.png"                
    ## [202] "note02_files/figure-gfm/unnamed-chunk-64-1.png"                
    ## [203] "note02_files/figure-gfm/unnamed-chunk-71-1.png"                
    ## [204] "note02.html"                                                   
    ## [205] "note02.md"                                                     
    ## [206] "note02.nb.html"                                                
    ## [207] "note02.Rmd"                                                    
    ## [208] "note03.html"                                                   
    ## [209] "note03.md"                                                     
    ## [210] "note03.Rmd"                                                    
    ## [211] "note04.Rmd"                                                    
    ## [212] "note05.Rmd"                                                    
    ## [213] "note06.Rmd"                                                    
    ## [214] "note07.Rmd"                                                    
    ## [215] "note08.Rmd"                                                    
    ## [216] "note09.Rmd"                                                    
    ## [217] "note10.Rmd"                                                    
    ## [218] "note11.Rmd"                                                    
    ## [219] "note12.Rmd"                                                    
    ## [220] "note13.Rmd"                                                    
    ## [221] "note14.Rmd"                                                    
    ## [222] "note15.Rmd"                                                    
    ## [223] "note16.Rmd"                                                    
    ## [224] "README.md"

``` r
list.files(all.files = TRUE)
```

    ##  [1] "."                          ".."                         ".DS_Store"                 
    ##  [4] ".git"                       ".gitignore"                 ".Rhistory"                 
    ##  [7] ".Rproj.user"                "arith.R"                    "data"                      
    ## [10] "g1.png"                     "github_document"            "hello.R"                   
    ## [13] "note-r-cookbook-2019.Rproj" "note02_files"               "note02.html"               
    ## [16] "note02.md"                  "note02.nb.html"             "note02.Rmd"                
    ## [19] "note03.html"                "note03.md"                  "note03.Rmd"                
    ## [22] "note04.Rmd"                 "note05.Rmd"                 "note06.Rmd"                
    ## [25] "note07.Rmd"                 "note08.Rmd"                 "note09.Rmd"                
    ## [28] "note10.Rmd"                 "note11.Rmd"                 "note12.Rmd"                
    ## [31] "note13.Rmd"                 "note14.Rmd"                 "note15.Rmd"                
    ## [34] "note16.Rmd"                 "README.md"

## 4.5 Windows에서 “파일을 열 수 없음” 처리

## 4.6 고정 너비 레코드 읽기

``` r
# library(tidyverse)
# records <- read_fwf("myfile.txt",
#                     fwf_cols(col1 = 10,
#                              col2 = 7))
# records
```

``` r
# file <- "./data/datafile.fwf"
# t1 <- read_fwf(file, fwf_empty(file, col_names = c("last", "first", "birth", "death")))
```

``` r
# t2 <- read_fwf(file, fwf_widths(c(10, 10, 5, 4),
#                                 c("last", "first", "birth", "death")))
```

``` r
# t3 <-
#   read_fwf("./data/datafile.fwf",
#            fwf_cols(
#              last = 10,
#              first = 10,
#              birth = 5,
#              death = 5
#            ))
```

``` r
# t4 <- read_fwf(file, fwf_cols(
#   last = c(1, 10),
#   first = c(11, 20),
#   birth = c(21, 25),
#   death = c(26, 30)
# ))
```

``` r
# t5 <- read_fwf(file, fwf_positions(
#   c(1, 11, 21, 26),
#   c(10, 20, 25, 30),
#   c("first", "last", "birth", "death")
# ))
```

## 4.7 테이블 형식 데이터 파일 읽기

``` r
library(readr)
datafile <- tempfile()
cat(c(
  "last first birth death\n",
  "Fisher R.A. 1890 1962\n",
  "Pearson Karl 1857 1936\n",
  "Cox Gertrude 1900 1978\n",
  "Yates Frank 1902 1994\n",
  "Smith Kirstine 1878 1939\n"
), file = datafile)
tab1 <- read_table(datafile)
```

    ## 
    ## ── Column specification ───────────────────────────────────────────────────────────────────────────────────────
    ## cols(
    ##   last = col_character(),
    ##   first = col_character(),
    ##   birth = col_double(),
    ##   death = col_double()
    ## )

``` r
tab1
```

    ## # A tibble: 5 × 4
    ##   last    first    birth death
    ##   <chr>   <chr>    <dbl> <dbl>
    ## 1 Fisher  R.A.      1890  1962
    ## 2 Pearson Karl      1857  1936
    ## 3 Cox     Gertrude  1900  1978
    ## 4 Yates   Frank     1902  1994
    ## 5 Smith   Kirstine  1878  1939

``` r
read_table(
  datafile,
  col_types = c(
    col_character(),
    col_character(),
    col_integer(),
    col_integer()
  ),
  comment = "#"
)
```

    ## # A tibble: 5 × 4
    ##   last    first    birth death
    ##   <chr>   <chr>    <dbl> <dbl>
    ## 1 Fisher  R.A.      1890  1962
    ## 2 Pearson Karl      1857  1936
    ## 3 Cox     Gertrude  1900  1978
    ## 4 Yates   Frank     1902  1994
    ## 5 Smith   Kirstine  1878  1939

``` r
unlink(datafile)
```

``` r
# t <- read_table("./data/datafile_missing.tsv", na = ".")
# t <- read_table("./data/datafile.ssv", comment = '#')
```

## 4.8 CSV 파일에서 읽기

``` r
datafile <- tempfile(fileext = ".csv")
cat(c(
  "label,lbound,ubound\n",
  "low,0,0.674\n",
  "mid,0.674,1.64\n",
  "high,1.64,2.33\n"
),
sep = "", file = datafile
)

tbl <- read_csv(datafile)
```

    ## Rows: 3 Columns: 3
    ## ── Column specification ───────────────────────────────────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr (1): label
    ## dbl (2): lbound, ubound
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
# tbl <- read_csv(datafile, col_names = FALSE)

tbl
```

    ## # A tibble: 3 × 3
    ##   label lbound ubound
    ##   <chr>  <dbl>  <dbl>
    ## 1 low    0      0.674
    ## 2 mid    0.674  1.64 
    ## 3 high   1.64   2.33

``` r
unlink(datafile)
```

## 4.9 CSV 파일에 쓰기

``` r
write_csv(tbl, "tab1.csv")
file.remove("tab1.csv")
```

    ## [1] TRUE

## 4.10 웹에서 표 또는 CSV 데이터 읽기

``` r
berkley <- read_csv("http://bit.ly/barkley18", comment = "#")
```

    ## Rows: 26 Columns: 3
    ## ── Column specification ───────────────────────────────────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr  (2): Name, Location
    ## time (1): Time
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
berkley
```

    ## # A tibble: 26 × 3
    ##    Name                Location Time    
    ##    <chr>               <chr>    <time>  
    ##  1 Gary Robbins        CAN      08:38:08
    ##  2 Allie Beaven        SCO      08:38:09
    ##  3 Guillaume Calmettes CA       08:38:10
    ##  4 Jamil Coury         AZ       08:58:55
    ##  5 Benoit Laval        FRA      09:07:15
    ##  6 Valery Caussarieu   FRA      09:07:20
    ##  7 Jodi Isenor         CAN      09:23:31
    ##  8 Johan Steene        SWE      09:56:54
    ##  9 Scott Martin        OR       09:56:55
    ## 10 Josep Barbarillo    ESP      10:53:15
    ## # … with 16 more rows
    ## # ℹ Use `print(n = ...)` to see more rows

## 4.11 엑셀에서 데이터 읽기

``` r
library(openxlsx)
# df1 <- read.xlsx(xlsxFile = "file.xlsx",
#                  sheet = 'sheet_name')
```

``` r
# library(openxlsx)
# wb <- loadWorkbook("data/excel_table_data.xlsx")
# tables <- getTables(wb, 'input_data')
# table_range_str <- names(tables[tables == 'example_table'])
# table_range_refs <- strsplit(table_range_str, ':')[[1]]
#
# # use a regex to extract out the row numbers
# table_range_row_num <- gsub("[^0-9.]", "", table_range_refs)
#
# # extract out the column numbers
# table_range_col_num <- convertFromExcelRef(table_range_refs)
```

## 4.12 엑셀에 데이터 프레임 쓰기

``` r
# library(openxlsx)
# write.xlsx(df,
#            sheetName = "some_sheet",
#            file = "out_file.xlsx")
```

``` r
# library(openxlsx)
#
# wb <- loadWorkbook("data/excel_table_data.xlsx")
# tables <- getTables(wb, 'input_data')
# table_range_str <- names(tables[tables == 'example_table'])
# table_range_refs <- strsplit(table_range_str, ':')[[1]]
#
# # use a regex to extract out the starting row number
# table_row_num <- gsub("[^0-9.]", "", table_range_refs)[[1]]
#
# # extract out the starting column number
# table_col_num <- convertFromExcelRef(table_range_refs)[[1]]
```

``` r
# removeTable(wb = wb,
#             sheet = 'input_data',
#             table = 'example_table')
```

``` r
# writeDataTable(
#   wb = wb,
#   sheet = 'input_data',
#   x = iris,
#   startCol = table_col_num,
#   startRow = table_row_num,
#   tableStyle = "TableStyleLight9",
#   tableName = 'example_table'
# )
```

``` r
# writeData(
#   wb = wb,
#   sheet = 'input_data',
#   x = paste('example_table data refreshed on:', Sys.time()),
#   startCol = 2,
#   startRow = 5
# )
#
# ## then save the workbook
# saveWorkbook(wb = wb,
#              file = "data/excel_table_data.xlsx",
#              overwrite = TRUE)
```

## 4.13 SAS 파일에서 데이터 읽기

``` r
# library(haven)
#
# sas_movie_data <- read_sas("data/movies.sas7bdat")
```

``` r
# sapply(sas_movie_data, attributes)
```

## 4.14 HTML 테이블에서 데이터 읽기

``` r
# library(rvest)
# library(tidyverse)
#
# all_tables <-
#   read_html("URL") %>%
#   html_table(fill = TRUE, header = TRUE)
```

``` r
library(rvest)
```

    ## 
    ## Attaching package: 'rvest'

    ## The following object is masked from 'package:readr':
    ## 
    ##     guess_encoding

``` r
all_tables <-
  read_html("https://en.wikipedia.org/wiki/Aviation_accidents_and_incidents") %>%
  html_table(fill = TRUE, header = TRUE)
all_tables
```

    ## [[1]]
    ## # A tibble: 0 × 2
    ## # … with 2 variables:  <lgl>,
    ## #   This article needs additional citations for verification. Please help improve this article by adding citations to reliable sources. Unsourced material may be challenged and removed.Find sources: "Aviation accidents and incidents" – news · newspapers · books · scholar · JSTOR  (August 2014) (Learn how and when to remove this template message) <lgl>
    ## # ℹ Use `colnames()` to see all variable names
    ## 
    ## [[2]]
    ## # A tibble: 52 × 3
    ##     Year `Deaths[58]` `Number of incidents[59]`
    ##    <int> <chr>                            <int>
    ##  1  1970 2,226                              298
    ##  2  1971 2,228                              271
    ##  3  1972 3,346                              344
    ##  4  1973 2,814                              333
    ##  5  1974 2,621                              270
    ##  6  1975 1,856                              316
    ##  7  1976 2,419                              277
    ##  8  1977 2,449                              340
    ##  9  1978 2,042                              356
    ## 10  1979 2,511                              328
    ## # … with 42 more rows
    ## # ℹ Use `print(n = ...)` to see more rows
    ## 
    ## [[3]]
    ## # A tibble: 0 × 2
    ## # … with 2 variables: Air accident fatalities recorded by ACRO 1918–2018 <lgl>,
    ## #   Air accident incidents recorded by ACRO 1918–2019 <lgl>
    ## # ℹ Use `colnames()` to see all variable names
    ## 
    ## [[4]]
    ## # A tibble: 9 × 6
    ##   .mw-parser-output .navbar{display:inline;font-size:88%;font-weight:normal}.…¹ .mw-p…² ``    ``    ``    ``   
    ##   <chr>                                                                         <chr>   <chr> <chr> <chr> <chr>
    ## 1 By type                                                                       "All\n… <NA>   <NA> <NA>   <NA>
    ## 2 Commercial                                                                    "by ai… <NA>   <NA> <NA>   <NA>
    ## 3 Military                                                                      "By ye… By y… "Pre… By c… "Vie…
    ## 4 By year                                                                       "Pre-1… <NA>   <NA> <NA>   <NA>
    ## 5 By conflict                                                                   "Vietn… <NA>   <NA> <NA>   <NA>
    ## 6 Other                                                                         "by ai… <NA>   <NA> <NA>   <NA>
    ## 7 Deaths                                                                        "by ai… <NA>   <NA> <NA>   <NA>
    ## 8 Related topics                                                                "Accid… <NA>   <NA> <NA>   <NA>
    ## 9 Italics indicates that the list is a category page.                           "Itali… <NA>   <NA> <NA>   <NA>
    ## # … with abbreviated variable names
    ## #   ¹​`.mw-parser-output .navbar{display:inline;font-size:88%;font-weight:normal}.mw-parser-output .navbar-collapse{float:left;text-align:left}.mw-parser-output .navbar-boxtext{word-spacing:0}.mw-parser-output .navbar ul{display:inline-block;white-space:nowrap;line-height:inherit}.mw-parser-output .navbar-brackets::before{margin-right:-0.125em;content:"[ "}.mw-parser-output .navbar-brackets::after{margin-left:-0.125em;content:" ]"}.mw-parser-output .navbar li{word-spacing:-0.125em}.mw-parser-output .navbar a>span,.mw-parser-output .navbar a>abbr{text-decoration:inherit}.mw-parser-output .navbar-mini abbr{font-variant:small-caps;border-bottom:none;text-decoration:none;cursor:inherit}.mw-parser-output .navbar-ct-full{font-size:114%;margin:0 7em}.mw-parser-output .navbar-ct-mini{font-size:114%;margin:0 4em}vteLists of aviation accidents and incidents`,
    ## #   ²​`.mw-parser-output .navbar{display:inline;font-size:88%;font-weight:normal}.mw-parser-output .navbar-collapse{float:left;text-align:left}.mw-parser-output .navbar-boxtext{word-spacing:0}.mw-parser-output .navbar ul{display:inline-block;white-space:nowrap;line-height:inherit}.mw-parser-output .navbar-brackets::before{margin-right:-0.125em;content:"[ "}.mw-parser-output .navbar-brackets::after{margin-left:-0.125em;content:" ]"}.mw-parser-output .navbar li{word-spacing:-0.125em}.mw-parser-output .navbar a>span,.mw-parser-output .navbar a>abbr{text-decoration:inherit}.mw-parser-output .navbar-mini abbr{font-variant:small-caps;border-bottom:none;text-decoration:none;cursor:inherit}.mw-parser-output .navbar-ct-full{font-size:114%;margin:0 7em}.mw-parser-output .navbar-ct-mini{font-size:114%;margin:0 4em}vteLists of aviation accidents and incidents`
    ## 
    ## [[5]]
    ## # A tibble: 1 × 2
    ##   `By year`   Pre-1925\n1925–1934\n1935–1939\n1940–1942\n1943–1944\n1945–1949\n1950–1954\n1955-1959\n1960–196…¹
    ##   <chr>       <chr>                                                                                            
    ## 1 By conflict "Vietnam War\nUSAF\nSoviet Afghan War\nFalklands War\nArgentine\nBritish\nU.S war in Afghanistan…
    ## # … with abbreviated variable name
    ## #   ¹​`Pre-1925\n1925–1934\n1935–1939\n1940–1942\n1943–1944\n1945–1949\n1950–1954\n1955-1959\n1960–1969\n1970–1974\n1975–1979\n1980–1989\n1990–1999\n2000–2009\n2010–2019\n2020–present`
    ## 
    ## [[6]]
    ## # A tibble: 18 × 6
    ##    `vteAviation accident and incident investigation agencies`                   vteAv…¹ ``    ``    ``    ``   
    ##    <chr>                                                                        <chr>   <chr> <chr> <chr> <chr>
    ##  1 "Africa\n DACM\n CCAA\n ANACM\n ANAC\n BPEA\n MCA\n ECAA\n BEIAA\n GCAA\n K… "Afric… Afri… Afri… "DAC… "DAC…
    ##  2 "Africa"                                                                     "Afric… <NA>  <NA>   <NA>  <NA>
    ##  3 "DACM\n CCAA\n ANACM\n ANAC\n BPEA\n MCA\n ECAA\n BEIAA\n GCAA\n KCAA\n LYC… "DACM\… <NA>  <NA>   <NA>  <NA>
    ##  4 "Asia\n IAC\n IAC\n CAAB\n CAAC\n AAIA\n AAIB\n NTSC\n CAO\n CAA\n JTSB\n I… "Asia\… Asia  Asia  "IAC… "IAC…
    ##  5 "Asia"                                                                       "Asia"  <NA>  <NA>   <NA>  <NA>
    ##  6 "IAC\n IAC\n CAAB\n CAAC\n AAIA\n AAIB\n NTSC\n CAO\n CAA\n JTSB\n IAC\n AR… "IAC\n… <NA>  <NA>   <NA>  <NA>
    ##  7 "Europe\n IAC\n IAC\n SIA\n IAC\n AAIU\n AAIIB\n AAII\n AIB\n ESIB\n SIA\n … "Europ… Euro… Euro… "IAC… "IAC…
    ##  8 "Europe"                                                                     "Europ… <NA>  <NA>   <NA>  <NA>
    ##  9 "IAC\n IAC\n SIA\n IAC\n AAIU\n AAIIB\n AAII\n AIB\n ESIB\n SIA\n BEA\n BFU… "IAC\n… <NA>  <NA>   <NA>  <NA>
    ## 10 "North America\n AAIB\n ECCAA\n BCAD\n AAIB\n AAIB\n TSB\n AAIB\n DGAC\n IA… "North… Nort… Nort… "AAI… "AAI…
    ## 11 "North America"                                                              "North… <NA>  <NA>   <NA>  <NA>
    ## 12 "AAIB\n ECCAA\n BCAD\n AAIB\n AAIB\n TSB\n AAIB\n DGAC\n IACC\n ECCAA\n CIA… "AAIB\… <NA>  <NA>   <NA>  <NA>
    ## 13 "Oceania\n NTSB\n ATSB\n DTC&I\n BEA\n CAAF\n NTSB\n BEA\n TAIC\n NTSB\n AI… "Ocean… Ocea… Ocea… "NTS… "NTS…
    ## 14 "Oceania"                                                                    "Ocean… <NA>  <NA>   <NA>  <NA>
    ## 15 "NTSB\n ATSB\n DTC&I\n BEA\n CAAF\n NTSB\n BEA\n TAIC\n NTSB\n AIC"          "NTSB\… <NA>  <NA>   <NA>  <NA>
    ## 16 "South America\n JIAAC\n DGAC\n CENIPA\n DGAC\n UAEAC\n DGAC\n AAIB\n BEA\n… "South… Sout… Sout… "JIA… "JIA…
    ## 17 "South America"                                                              "South… <NA>  <NA>   <NA>  <NA>
    ## 18 "JIAAC\n DGAC\n CENIPA\n DGAC\n UAEAC\n DGAC\n AAIB\n BEA\n GCAA\n DINAC\n … "JIAAC… <NA>  <NA>   <NA>  <NA>
    ## # … with abbreviated variable name ¹​`vteAviation accident and incident investigation agencies`
    ## 
    ## [[7]]
    ## # A tibble: 1 × 2
    ##   Africa                                                                                                 Africa
    ##   <chr>                                                                                                  <chr> 
    ## 1 "DACM\n CCAA\n ANACM\n ANAC\n BPEA\n MCA\n ECAA\n BEIAA\n GCAA\n KCAA\n LYCAA\n BEA\n ANAC\n BEA\n DA… "DACM…
    ## 
    ## [[8]]
    ## # A tibble: 1 × 2
    ##   Asia                                                                                                    Asia 
    ##   <chr>                                                                                                   <chr>
    ## 1 "IAC\n IAC\n CAAB\n CAAC\n AAIA\n AAIB\n NTSC\n CAO\n CAA\n JTSB\n IAC\n ARAIB\n LCAA\n AACM\n MOT\n A… "IAC…
    ## 
    ## [[9]]
    ## # A tibble: 1 × 2
    ##   Europe                                                                                                 Europe
    ##   <chr>                                                                                                  <chr> 
    ## 1 "IAC\n IAC\n SIA\n IAC\n AAIU\n AAIIB\n AAII\n AIB\n ESIB\n SIA\n BEA\n BFU\n AAIB\n AAIASB\n TSB\n A… "IAC\…
    ## 
    ## [[10]]
    ## # A tibble: 1 × 2
    ##   `North America`                                                                                       North…¹
    ##   <chr>                                                                                                 <chr>  
    ## 1 "AAIB\n ECCAA\n BCAD\n AAIB\n AAIB\n TSB\n AAIB\n DGAC\n IACC\n ECCAA\n CIAA\n AAC\n ECCAA\n BEA\n D… "AAIB\…
    ## # … with abbreviated variable name ¹​`North America`
    ## 
    ## [[11]]
    ## # A tibble: 1 × 2
    ##   Oceania                                                             Oceania                                  
    ##   <chr>                                                               <chr>                                    
    ## 1 "NTSB\n ATSB\n DTC&I\n BEA\n CAAF\n NTSB\n BEA\n TAIC\n NTSB\n AIC" "NTSB\n ATSB\n DTC&I\n BEA\n CAAF\n NTSB…
    ## 
    ## [[12]]
    ## # A tibble: 1 × 2
    ##   `South America`                                                                                    South Am…¹
    ##   <chr>                                                                                              <chr>     
    ## 1 "JIAAC\n DGAC\n CENIPA\n DGAC\n UAEAC\n DGAC\n AAIB\n BEA\n GCAA\n DINAC\n CIAA\n OIPAIA\n DGPIAA" "JIAAC\n …
    ## # … with abbreviated variable name ¹​`South America`

``` r
out_table <-
  all_tables %>%
  magrittr::extract2(2)

head(out_table)
```

    ## # A tibble: 6 × 3
    ##    Year `Deaths[58]` `Number of incidents[59]`
    ##   <int> <chr>                            <int>
    ## 1  1970 2,226                              298
    ## 2  1971 2,228                              271
    ## 3  1972 3,346                              344
    ## 4  1973 2,814                              333
    ## 5  1974 2,621                              270
    ## 6  1975 1,856                              316

``` r
url <- "http://en.wikipedia.org/wiki/World_population"
tbls <- read_html(url) %>%
  html_table(fill = TRUE, header = TRUE)
tbls
```

    ## [[1]]
    ## # A tibble: 12 × 5
    ##    `#`                                                                            Most …¹ `2000` `2015` 2030[…²
    ##    <chr>                                                                          <chr>   <chr>  <chr>  <chr>  
    ##  1 "1"                                                                            "China… "1,27… "1,37… "1,416"
    ##  2 "2"                                                                            "India" "1,05… "1,31… "1,528"
    ##  3 "3"                                                                            "Unite… "283"  "322"  "356"  
    ##  4 "4"                                                                            "Indon… "212"  "258"  "295"  
    ##  5 "5"                                                                            "Pakis… "136"  "208"  "245"  
    ##  6 "6"                                                                            "Brazi… "176"  "206"  "228"  
    ##  7 "7"                                                                            "Niger… "123"  "182"  "263"  
    ##  8 "8"                                                                            "Bangl… "131"  "161"  "186"  
    ##  9 "9"                                                                            "Russi… "146"  "146"  "149"  
    ## 10 "10"                                                                           "Mexic… "103"  "127"  "148"  
    ## 11 ""                                                                             "World… "6,12… "7,34… "8,501"
    ## 12 "Notes:\n.mw-parser-output .reflist{font-size:90%;margin-bottom:0.5em;list-st… "Notes… "Note… "Note… "Notes…
    ## # … with abbreviated variable names ¹​`Most populous countries`, ²​`2030[A]`
    ## 
    ## [[2]]
    ## # A tibble: 7 × 5
    ##   Region                   `Density(inhabitants/km2)` `Population(millions)` `Most populous country`    Most …¹
    ##   <chr>                    <chr>                      <chr>                  <chr>                      <chr>  
    ## 1 Asia                     104.1                      4,641                  1,411,778,000 –  China[no… 13,515…
    ## 2 Africa                   44.4                       1,340                  0,211,401,000 –  Nigeria   09,500…
    ## 3 Europe                   73.4                       747                    0,146,171,000 –  Russia, … 13,200…
    ## 4 Latin America            24.1                       653                    0,214,103,000 –  Brazil    12,252…
    ## 5 Northern America[note 2] 14.9                       368                    0,332,909,000 –  United S… 08,804…
    ## 6 Oceania                  5                          42                     0,025,917,000 –  Australia 05,367…
    ## 7 Antarctica               ~0                         0.004[16]              N/A[note 3]                00,001…
    ## # … with abbreviated variable name ¹​`Most populous city (metropolitan area)`
    ## 
    ## [[3]]
    ## # A tibble: 3 × 11
    ##   World population milestones…¹ World…² World…³ World…⁴ World…⁵ World…⁶ World…⁷ World…⁸ World…⁹ World…˟ World…˟
    ##   <chr>                         <chr>     <int>   <int>   <int>   <int>   <int>   <int>   <int>   <int>   <int>
    ## 1 Population                    1             2       3       4       5       6       7       8       9      10
    ## 2 Year                          1804       1927    1960    1974    1987    1999    2011    2023    2037    2057
    ## 3 Years elapsed                 —           123      33      14      13      12      12      12      14      20
    ## # … with abbreviated variable names ¹​`World population milestones in billions [3](Worldometers estimates)`,
    ## #   ²​`World population milestones in billions [3](Worldometers estimates)`,
    ## #   ³​`World population milestones in billions [3](Worldometers estimates)`,
    ## #   ⁴​`World population milestones in billions [3](Worldometers estimates)`,
    ## #   ⁵​`World population milestones in billions [3](Worldometers estimates)`,
    ## #   ⁶​`World population milestones in billions [3](Worldometers estimates)`,
    ## #   ⁷​`World population milestones in billions [3](Worldometers estimates)`, …
    ## 
    ## [[4]]
    ## # A tibble: 0 × 2
    ## # … with 2 variables:
    ## #   .mw-parser-output .legend{page-break-inside:avoid;break-inside:avoid-column}.mw-parser-output .legend-color{display:inline-block;min-width:1.25em;height:1.25em;line-height:1.25;margin:1px 0;text-align:center;border:1px solid black;background-color:transparent;color:black}.mw-parser-output .legend-text{}  >80   77.5–80   75–77.5   72.5–75   70–72.5 <lgl>,
    ## #   67.5–70   65–67.5   60–65   55–60   50–55 <lgl>
    ## # ℹ Use `colnames()` to see all variable names
    ## 
    ## [[5]]
    ## # A tibble: 10 × 6
    ##     Rank `Country / Dependency` Population    `Percentage of the world` Date        Source (official or from …¹
    ##    <int> <chr>                  <chr>         <chr>                     <chr>       <chr>                      
    ##  1     1 China                  1,412,600,000 17.7%                     31 Dec 2021 National annual estimate[9…
    ##  2     2 India                  1,373,761,000 17.2%                     1 Mar 2022  Annual national estimate[9…
    ##  3     3 United States          333,058,724   4.18%                     4 Sep 2022  National population clock[…
    ##  4     4 Indonesia              272,248,500   3.41%                     1 Jul 2021  National annual estimate[9…
    ##  5     5 Pakistan               229,488,994   2.88%                     1 Jul 2022  UN projection[97]          
    ##  6     6 Nigeria                216,746,934   2.72%                     1 Jul 2022  UN projection[97]          
    ##  7     7 Brazil                 215,097,409   2.70%                     4 Sep 2022  National population clock[…
    ##  8     8 Bangladesh             168,220,000   2.11%                     1 Jul 2020  Annual Population Estimate…
    ##  9     9 Russia                 147,190,000   1.85%                     1 Oct 2021  2021 preliminary census re…
    ## 10    10 Mexico                 128,271,248   1.61%                     31 Mar 2022 National quarterly estimat…
    ## # … with abbreviated variable name ¹​`Source (official or from the United Nations)`
    ## 
    ## [[6]]
    ## # A tibble: 10 × 5
    ##     Rank Country     Population  `Area(km2)` `Density(pop/km2)`
    ##    <int> <chr>       <chr>       <chr>       <chr>             
    ##  1     1 Singapore   5,704,000   710         8,033             
    ##  2     2 Bangladesh  173,350,000 143,998     1,204             
    ##  3     3 Palestine   5,266,785   6,020       847               
    ##  4     4 Lebanon     6,856,000   10,452      656               
    ##  5     5 Taiwan      23,604,000  36,193      652               
    ##  6     6 South Korea 51,781,000  99,538      520               
    ##  7     7 Rwanda      12,374,000  26,338      470               
    ##  8     8 Haiti       11,578,000  27,065      428               
    ##  9     9 Netherlands 17,740,000  41,526      427               
    ## 10    10 Israel      9,570,000   22,072      434               
    ## 
    ## [[7]]
    ## # A tibble: 10 × 6
    ##     Rank Country        Population    `Area(km2)` `Density(pop/km2)` `Population trend`
    ##    <int> <chr>          <chr>         <chr>       <chr>              <chr>             
    ##  1     1 India          1,381,950,000 3,287,240   420                Growing           
    ##  2     2 Pakistan       229,850,000   803,940     286                Rapidly growing   
    ##  3     3 Bangladesh     173,350,000   143,998     1,204              Rapidly growing   
    ##  4     4 Japan          126,010,000   377,873     333                Declining[102]    
    ##  5     5 Philippines    112,380,000   300,000     375                Growing           
    ##  6     6 Vietnam        96,209,000    331,689     290                Growing           
    ##  7     7 United Kingdom 66,436,000    243,610     273                Growing           
    ##  8     8 South Korea    51,781,000    99,538      520                Steady            
    ##  9     9 Taiwan         23,604,000    36,193      652                Steady            
    ## 10    10 Sri Lanka      21,803,000    65,610      332                Growing           
    ## 
    ## [[8]]
    ## # A tibble: 71 × 7
    ##    Year  Population    `Yearly growth` `Yearly growth` `Density(pop/km2)` `Urban population` `Urban population`
    ##    <chr> <chr>         <chr>           <chr>           <chr>              <chr>              <chr>             
    ##  1 Year  Population    %               Number          Density(pop/km2)   Number             %                 
    ##  2 1951  2,584,034,261 1.88%           47,603,112      17                 775,067,697        30%               
    ##  3 1952  2,630,861,562 1.81%           46,827,301      18                 799,282,533        30%               
    ##  4 1953  2,677,608,960 1.78%           46,747,398      18                 824,289,989        31%               
    ##  5 1954  2,724,846,741 1.76%           47,237,781      18                 850,179,106        31%               
    ##  6 1955  2,773,019,936 1.77%           48,173,195      19                 877,008,842        32%               
    ##  7 1956  2,822,443,282 1.78%           49,423,346      19                 904,685,164        32%               
    ##  8 1957  2,873,306,090 1.80%           50,862,808      19                 933,113,168        32%               
    ##  9 1958  2,925,686,705 1.82%           52,380,615      20                 962,537,113        33%               
    ## 10 1959  2,979,576,185 1.84%           53,889,480      20                 992,820,546        33%               
    ## # … with 61 more rows
    ## # ℹ Use `print(n = ...)` to see more rows
    ## 
    ## [[9]]
    ## # A tibble: 7 × 15
    ##   Region      `1500` `1600` `1700` `1750` `1800` `1850` `1900` `1950` `1999` `2008` `2010` `2012` `2050` `2150`
    ##   <chr>        <int>  <int>  <int>  <int>  <int> <chr>  <chr>  <chr>  <chr>  <chr>  <chr>  <chr>  <chr>  <chr> 
    ## 1 World          585    660    710    791    978 1,262  1,650  2,521  6,008  6,707  6,896  7,052  9,725  9,746 
    ## 2 Africa          86    114    106    106    107 111    133    221    783    973    1,022  1,052  2,478  2,308 
    ## 3 Asia           282    350    411    502    635 809    947    1,402  3,700  4,054  4,164  4,250  5,267  5,561 
    ## 4 Europe         168    170    178    190    203 276    408    547    675    732    738    740    734    517   
    ## 5 Latin Amer…     40     20     10     16     24 38     74     167    508    577    590    603    784    912   
    ## 6 Northern A…      6      3      2      2      7 26     82     172    312    337    345    351    433    398   
    ## 7 Oceania          3      3      3      2      2 2      6      13     30     34     37     38     57     51    
    ## 
    ## [[10]]
    ## # A tibble: 6 × 15
    ##   Region      `1500` `1600` `1700` `1750` `1800` `1850` `1900` `1950` `1999` `2008` `2010` `2012` `2050` `2150`
    ##   <chr>        <dbl>  <dbl>  <dbl>  <dbl>  <dbl>  <dbl>  <dbl>  <dbl>  <dbl>  <dbl>  <dbl>  <dbl>  <dbl>  <dbl>
    ## 1 Africa        14.7   17.3   14.9   13.4   10.9    8.8    8.1    8.8   13     14.5   14.8   15.2   25.5   23.7
    ## 2 Asia          48.2   53     57.9   63.5   64.9   64.1   57.4   55.6   61.6   60.4   60.4   60.3   54.2   57.1
    ## 3 Europe        28.7   25.8   25.1   20.6   20.8   21.9   24.7   21.7   11.2   10.9   10.7   10.5    7.6    5.3
    ## 4 Latin Amer…    6.8    3      1.4    2      2.5    3      4.5    6.6    8.5    8.6    8.6    8.6    8.1    9.4
    ## 5 Northern A…    1      0.5    0.3    0.3    0.7    2.1    5      6.8    5.2    5      5      5      4.5    4.1
    ## 6 Oceania        0.5    0.5    0.4    0.3    0.2    0.2    0.4    0.5    0.5    0.5    0.5    0.5    0.6    0.5
    ## 
    ## [[11]]
    ## # A tibble: 33 × 9
    ##    Year      World   Africa Asia  Europe `Latin America& Carib.[Note 1]` `North America[Note 1]` Oceania Notes 
    ##    <chr>     <chr>   <chr>  <chr>  <int>                           <int>                   <int>   <dbl> <chr> 
    ##  1 70,000 BC < 0.015 ""     ""        NA                               0                       0      NA "[119…
    ##  2 10,000 BC 4       ""     ""        NA                              NA                      NA      NA "[120…
    ##  3 8000 BC   5       ""     ""        NA                              NA                      NA      NA ""    
    ##  4 6500 BC   5       ""     ""        NA                              NA                      NA      NA ""    
    ##  5 5000 BC   5       ""     ""        NA                              NA                      NA      NA ""    
    ##  6 4000 BC   7       ""     ""        NA                              NA                      NA      NA ""    
    ##  7 3000 BC   14      ""     ""        NA                              NA                      NA      NA ""    
    ##  8 2000 BC   27      ""     ""        NA                              NA                      NA      NA ""    
    ##  9 1000 BC   50      "7"    "33"       9                              NA                      NA      NA "[cit…
    ## 10 500 BC    100     "14"   "66"      16                              NA                      NA      NA ""    
    ## # … with 23 more rows
    ## # ℹ Use `print(n = ...)` to see more rows
    ## 
    ## [[12]]
    ## # A tibble: 0 × 2
    ## # … with 2 variables:  <lgl>,
    ## #   This section needs additional citations for verification. Please help improve this article by adding citations to reliable sources. Unsourced material may be challenged and removed.  (April 2020) (Learn how and when to remove this template message) <lgl>
    ## # ℹ Use `colnames()` to see all variable names
    ## 
    ## [[13]]
    ## # A tibble: 10 × 5
    ##     Year `UN est.(millions)` Difference `USCB est.(millions)` Difference
    ##    <int> <chr>               <chr>      <chr>                 <chr>     
    ##  1  2005 6,542               –          6,473                 –         
    ##  2  2010 6,957               415        6,866                 393       
    ##  3  2015 7,380               423        7,256                 390       
    ##  4  2020 7,795               415        7,643                 380       
    ##  5  2025 8,184               390        8,007                 363       
    ##  6  2030 8,549               364        8,341                 334       
    ##  7  2035 8,888               339        8,646                 306       
    ##  8  2040 9,199               311        8,926                 280       
    ##  9  2045 9,482               283        9,180                 254       
    ## 10  2050 9,735               253        9,408                 228       
    ## 
    ## [[14]]
    ## # A tibble: 21 × 8
    ##     Year World Asia          Africa        Europe      `Latin America/Caribbean` `Northern America` Oceania  
    ##    <int> <chr> <chr>         <chr>         <chr>       <chr>                     <chr>              <chr>    
    ##  1  2000 6,144 3,741 (60.9%) 811 (13.2%)   726 (11.8%) 522 (8.5%)                312 (5.1%)         31 (0.5%)
    ##  2  2005 6,542 3,978 (60.8%) 916 (14.0%)   729 (11.2%) 558 (8.5%)                327 (5.0%)         34 (0.5%)
    ##  3  2010 6,957 4,210 (60.5%) 1,039 (14.9%) 736 (10.6%) 591 (8.5%)                343 (4.9%)         37 (0.5%)
    ##  4  2015 7,380 4,434 (60.1%) 1,182 (16.0%) 743 (10.1%) 624 (8.5%)                357 (4.8%)         40 (0.5%)
    ##  5  2020 7,795 4,641 (59.5%) 1,341 (17.2%) 748 (9.6%)  654 (8.4%)                369 (4.7%)         43 (0.6%)
    ##  6  2025 8,184 4,823 (58.9%) 1,509 (18.4%) 746 (9.1%)  682 (8.3%)                380 (4.6%)         45 (0.6%)
    ##  7  2030 8,549 4,974 (58.2%) 1,688 (19.8%) 741 (8.7%)  706 (8.3%)                391 (4.6%)         48 (0.6%)
    ##  8  2035 8,888 5,096 (57.3%) 1,878 (21.1%) 735 (8.3%)  726 (8.2%)                401 (4.5%)         50 (0.6%)
    ##  9  2040 9,199 5,189 (56.4%) 2,077 (22.6%) 728 (7.9%)  742 (8.1%)                410 (4.5%)         53 (0.6%)
    ## 10  2045 9,482 5,253 (55.4%) 2,282 (24.1%) 720 (7.6%)  754 (8.0%)                418 (4.4%)         55 (0.6%)
    ## # … with 11 more rows
    ## # ℹ Use `print(n = ...)` to see more rows
    ## 
    ## [[15]]
    ## # A tibble: 2 × 11
    ##   `Population(in billions)` `0.5` `0.5`   `1`   `1`   `2`   `2`   `4`   `4`   `8`   `8`
    ##   <chr>                     <int> <int> <int> <int> <int> <int> <int> <int> <int> <int>
    ## 1 Year                       1500  1500  1804  1804  1927  1927  1974  1974  2024  2024
    ## 2 Years elapsed                NA   304   304   123   123    47    47    50    50    NA
    ## 
    ## [[16]]
    ## # A tibble: 2 × 11
    ##   `Population(in billions)` `0.375` `0.375` `0.75` `0.75` `1.5` `1.5`   `3`   `3`   `6`   `6`
    ##   <chr>                       <int>   <int>  <int>  <int> <int> <int> <int> <int> <int> <int>
    ## 1 Year                         1171    1171   1715   1715  1881  1881  1960  1960  1999  1999
    ## 2 Years elapsed                  NA     544    544    166   166    79    79    39    39    NA
    ## 
    ## [[17]]
    ## # A tibble: 10 × 2
    ##    .mw-parser-output .navbar{display:inline;font-size:88%;font-weight:normal}.mw-parser-output .navba…¹ .mw-p…²
    ##    <chr>                                                                                                <chr>  
    ##  1 "Major topics"                                                                                       "Demog…
    ##  2 "Biological andrelated topics"                                                                       "Popul…
    ##  3 "Populationecology"                                                                                  "Earth…
    ##  4 "Society and population"                                                                             "Bioca…
    ##  5 "Literature"                                                                                         "A Mod…
    ##  6 "Publications"                                                                                       "Popul…
    ##  7 "Lists"                                                                                              "Popul…
    ##  8 "Events andorganizations"                                                                            "7 Bil…
    ##  9 "Related topics"                                                                                     "Deep …
    ## 10 "Commons\nHuman overpopulation"                                                                      "Commo…
    ## # … with abbreviated variable names
    ## #   ¹​`.mw-parser-output .navbar{display:inline;font-size:88%;font-weight:normal}.mw-parser-output .navbar-collapse{float:left;text-align:left}.mw-parser-output .navbar-boxtext{word-spacing:0}.mw-parser-output .navbar ul{display:inline-block;white-space:nowrap;line-height:inherit}.mw-parser-output .navbar-brackets::before{margin-right:-0.125em;content:"[ "}.mw-parser-output .navbar-brackets::after{margin-left:-0.125em;content:" ]"}.mw-parser-output .navbar li{word-spacing:-0.125em}.mw-parser-output .navbar a>span,.mw-parser-output .navbar a>abbr{text-decoration:inherit}.mw-parser-output .navbar-mini abbr{font-variant:small-caps;border-bottom:none;text-decoration:none;cursor:inherit}.mw-parser-output .navbar-ct-full{font-size:114%;margin:0 7em}.mw-parser-output .navbar-ct-mini{font-size:114%;margin:0 4em}vteGlobal human population`,
    ## #   ²​`.mw-parser-output .navbar{display:inline;font-size:88%;font-weight:normal}.mw-parser-output .navbar-collapse{float:left;text-align:left}.mw-parser-output .navbar-boxtext{word-spacing:0}.mw-parser-output .navbar ul{display:inline-block;white-space:nowrap;line-height:inherit}.mw-parser-output .navbar-brackets::before{margin-right:-0.125em;content:"[ "}.mw-parser-output .navbar-brackets::after{margin-left:-0.125em;content:" ]"}.mw-parser-output .navbar li{word-spacing:-0.125em}.mw-parser-output .navbar a>span,.mw-parser-output .navbar a>abbr{text-decoration:inherit}.mw-parser-output .navbar-mini abbr{font-variant:small-caps;border-bottom:none;text-decoration:none;cursor:inherit}.mw-parser-output .navbar-ct-full{font-size:114%;margin:0 7em}.mw-parser-output .navbar-ct-mini{font-size:114%;margin:0 4em}vteGlobal human population`
    ## 
    ## [[18]]
    ## # A tibble: 35 × 70
    ##    Articles…¹ Artic…² ``    ``    ``    ``    ``    ``    ``    ``    ``    ``    ``    ``    ``    ``    ``   
    ##    <chr>      <chr>   <chr> <chr> <chr> <chr> <chr> <chr> <chr> <chr> <chr> <chr> <chr> <chr> <chr> <chr> <chr>
    ##  1 "vteHuman… "vteHu… vteH… vteH… Gene… "Ant… Caus… "Agr… Effe… "Bio… Miti… "Alt… "Com… "Com… vteL… vteL… Glob…
    ##  2 "vteHuman… "vteHu… <NA>  <NA>  <NA>   <NA> <NA>   <NA> <NA>   <NA> <NA>   <NA>  <NA>  <NA> <NA>  <NA>  <NA> 
    ##  3 "General"  "Anthr… <NA>  <NA>  <NA>   <NA> <NA>   <NA> <NA>   <NA> <NA>   <NA>  <NA>  <NA> <NA>  <NA>  <NA> 
    ##  4 "Causes"   "Agric… <NA>  <NA>  <NA>   <NA> <NA>   <NA> <NA>   <NA> <NA>   <NA>  <NA>  <NA> <NA>  <NA>  <NA> 
    ##  5 "Effects"  "Biodi… <NA>  <NA>  <NA>   <NA> <NA>   <NA> <NA>   <NA> <NA>   <NA>  <NA>  <NA> <NA>  <NA>  <NA> 
    ##  6 "Mitigati… "Alter… <NA>  <NA>  <NA>   <NA> <NA>   <NA> <NA>   <NA> <NA>   <NA>  <NA>  <NA> <NA>  <NA>  <NA> 
    ##  7 "Commons\… "Commo… <NA>  <NA>  <NA>   <NA> <NA>   <NA> <NA>   <NA> <NA>   <NA>  <NA>  <NA> <NA>  <NA>  <NA> 
    ##  8 "vteLists… "vteLi… <NA>  <NA>  <NA>   <NA> <NA>   <NA> <NA>   <NA> <NA>   <NA>  <NA>  <NA> <NA>  <NA>  <NA> 
    ##  9 "Global"   "Curre… <NA>  <NA>  <NA>   <NA> <NA>   <NA> <NA>   <NA> <NA>   <NA>  <NA>  <NA> <NA>  <NA>  <NA> 
    ## 10 "Continen… "Afric… <NA>  <NA>  <NA>   <NA> <NA>   <NA> <NA>   <NA> <NA>   <NA>  <NA>  <NA> <NA>  <NA>  <NA> 
    ## # … with 25 more rows, 53 more variables: `` <chr>, `` <chr>, `` <chr>, `` <chr>, `` <chr>, `` <chr>,
    ## #   `` <chr>, `` <chr>, `` <chr>, `` <chr>, `` <chr>, `` <chr>, `` <chr>, `` <chr>, `` <chr>, `` <chr>,
    ## #   `` <chr>, `` <chr>, `` <chr>, `` <chr>, `` <chr>, `` <chr>, `` <chr>, `` <chr>, `` <chr>, `` <chr>,
    ## #   `` <chr>, `` <chr>, `` <chr>, `` <chr>, `` <chr>, `` <chr>, `` <chr>, `` <chr>, `` <chr>, `` <chr>,
    ## #   `` <chr>, `` <chr>, `` <chr>, `` <chr>, `` <chr>, `` <chr>, `` <chr>, `` <chr>, `` <chr>, `` <chr>,
    ## #   `` <chr>, `` <chr>, `` <chr>, `` <chr>, `` <chr>, `` <chr>, `` <chr>, and abbreviated variable names
    ## #   ¹​`Articles related to the world's population`, ²​`Articles related to the world's population`
    ## # ℹ Use `print(n = ...)` to see more rows, and `colnames()` to see all variable names
    ## 
    ## [[19]]
    ## # A tibble: 5 × 2
    ##   `vteHuman impact on the environment`                     `vteHuman impact on the environment`                
    ##   <chr>                                                    <chr>                                               
    ## 1 "General"                                                "Anthropocene\nEnvironmental issues\nlist of issues…
    ## 2 "Causes"                                                 "Agriculture\ncannabis cultivation\nirrigation\nmea…
    ## 3 "Effects"                                                "Biodiversity threats\nbiodiversity loss\ndecline i…
    ## 4 "Mitigation"                                             "Alternative fuel vehicle propulsion\nBirth control…
    ## 5 "Commons\n Category\nby country\nassessment\nmitigation" "Commons\n Category\nby country\nassessment\nmitiga…
    ## 
    ## [[20]]
    ## # A tibble: 12 × 2
    ##    `vteLists of countries by population statistics`   `vteLists of countries by population statistics`         
    ##    <chr>                                              <chr>                                                    
    ##  1 "Global"                                           "Current population\nDemographics of the world"          
    ##  2 "Continents/subregions"                            "Africa\nAntarctica\nAsia\nEurope\nNorth America\nCaribb…
    ##  3 "Intercontinental"                                 "Americas\nArab world\nCommonwealth of Nations\nEurasia\…
    ##  4 "Cities/urban areas"                               "World cities\nNational capitals\nMegacities\nMegalopoli…
    ##  5 "Past and future"                                  "Past and future population\nWorld population estimates\…
    ##  6 "Population density"                               "Current density\nPast and future population density\nCu…
    ##  7 "Growth indicators"                                "Population growth rate\nNatural increase\nNet reproduct…
    ##  8 "Other demographics"                               "Age at childbearing\nAge at first marriage\nAge structu…
    ##  9 "Health"                                           "Antidepressant consumption\nAntiviral medications for p…
    ## 10 "Education and innovation"                         "Bloomberg Innovation Index\nEducation Index\nInternatio…
    ## 11 "Economic"                                         "Access to financial services\nDevelopment aid given\nOf…
    ## 12 "List of international rankings\nLists by country" "List of international rankings\nLists by country"       
    ## 
    ## [[21]]
    ## # A tibble: 1 × 2
    ##   `vteHierarchy of life`                                                                                vteHi…¹
    ##   <chr>                                                                                                 <chr>  
    ## 1 Biosphere > Biome > Ecosystem > Biocenosis > Population > Organism > Organ system > Organ > Tissue >… Biosph…
    ## # … with abbreviated variable name ¹​`vteHierarchy of life`
    ## 
    ## [[22]]
    ## # A tibble: 12 × 10
    ##    vteGlobalization             vteGlobalization                ``    ``    ``    ``    ``    ``    ``    ``   
    ##    <chr>                        <chr>                           <chr> <chr> <chr> <chr> <chr> <chr> <chr> <chr>
    ##  1 "Journals\nOutline\nStudies" "Journals\nOutline\nStudies"    <NA>   <NA> <NA>   <NA> <NA>   <NA> <NA>   <NA>
    ##  2 "Aspects"                    "Alter-globalization\nAnti-glo… <NA>   <NA> <NA>   <NA> <NA>   <NA> <NA>   <NA>
    ##  3 "Issues"                     "Global\nClimate change\nClima… Glob… "Cli… Other "Bra… <NA>   <NA> <NA>   <NA>
    ##  4 "Global"                     "Climate change\nClimate justi… <NA>   <NA> <NA>   <NA> <NA>   <NA> <NA>   <NA>
    ##  5 "Other"                      "Brain drain\nreverse\nCare dr… <NA>   <NA> <NA>   <NA> <NA>   <NA> <NA>   <NA>
    ##  6 "Theories"                   "Capital accumulation\nDepende… <NA>   <NA> <NA>   <NA> <NA>   <NA> <NA>   <NA>
    ##  7 "Notablescholars"            "Economics\nDavid Autor\nRicha… Econ… "Dav… Poli… "Sam… Poli… "Arj… Non–… "Noa…
    ##  8 "Economics"                  "David Autor\nRichard Baldwin\… <NA>   <NA> <NA>   <NA> <NA>   <NA> <NA>   <NA>
    ##  9 "Political economy"          "Samir Amin\nGiovanni Arrighi\… <NA>   <NA> <NA>   <NA> <NA>   <NA> <NA>   <NA>
    ## 10 "Politics /  sociology"      "Arjun Appadurai\nDaniele Arch… <NA>   <NA> <NA>   <NA> <NA>   <NA> <NA>   <NA>
    ## 11 "Non–academic"               "Noam Chomsky\nThomas Friedman… <NA>   <NA> <NA>   <NA> <NA>   <NA> <NA>   <NA>
    ## 12 "Category\n Business portal" "Category\n Business portal"    <NA>   <NA> <NA>   <NA> <NA>   <NA> <NA>   <NA>
    ## 
    ## [[23]]
    ## # A tibble: 1 × 2
    ##   Global Climate change\nClimate justice\nDisease\nCOVID-19 pandemic\nDigital divide\nLabor arbitrage\nPopula…¹
    ##   <chr>  <chr>                                                                                                 
    ## 1 Other  "Brain drain\nreverse\nCare drain\nDevelopment aid\nEconomic inequality\nEndangered languages\nFair t…
    ## # … with abbreviated variable name
    ## #   ¹​`Climate change\nClimate justice\nDisease\nCOVID-19 pandemic\nDigital divide\nLabor arbitrage\nPopulation\nTax havens\nOffshore financial centres\nTax inversions\nWater crisis`
    ## 
    ## [[24]]
    ## # A tibble: 3 × 2
    ##   Economics             David Autor\nRichard Baldwin\nRavi Batra\nJagdish Bhagwati\nRobert Brenner\nJayati Gh…¹
    ##   <chr>                 <chr>                                                                                  
    ## 1 Political economy     "Samir Amin\nGiovanni Arrighi\nRobert W. Cox\nAndre Gunder Frank\nStephen Gill\nPeter …
    ## 2 Politics /  sociology "Arjun Appadurai\nDaniele Archibugi\nK. Anthony Appiah\nUlrich Beck\nWalden Bello\nJea…
    ## 3 Non–academic          "Noam Chomsky\nThomas Friedman\nNaomi Klein\nJohn R. Saul\nVandana Shiva"              
    ## # … with abbreviated variable name
    ## #   ¹​`David Autor\nRichard Baldwin\nRavi Batra\nJagdish Bhagwati\nRobert Brenner\nJayati Ghosh\nMichael Hudson\nBranko Milanović\nKevin O'Rourke\nThomas Piketty\nDani Rodrik\nJeffrey Sachs\nAmartya Sen\nJoseph Stiglitz`
    ## 
    ## [[25]]
    ## # A tibble: 0 × 2
    ## # … with 2 variables: Authority control: National libraries <lgl>, Germany <lgl>
    ## # ℹ Use `colnames()` to see all variable names

``` r
library(magrittr)
```

    ## 
    ## Attaching package: 'magrittr'

    ## The following object is masked from 'package:purrr':
    ## 
    ##     set_names

    ## The following object is masked from 'package:tidyr':
    ## 
    ##     extract

``` r
tbl <- tbls %>%
  extract2(6)

head(tbl, 2)
```

    ## # A tibble: 2 × 5
    ##    Rank Country    Population  `Area(km2)` `Density(pop/km2)`
    ##   <int> <chr>      <chr>       <chr>       <chr>             
    ## 1     1 Singapore  5,704,000   710         8,033             
    ## 2     2 Bangladesh 173,350,000 143,998     1,204

``` r
tbl[, c(2, 3)]
```

    ## # A tibble: 10 × 2
    ##    Country     Population 
    ##    <chr>       <chr>      
    ##  1 Singapore   5,704,000  
    ##  2 Bangladesh  173,350,000
    ##  3 Palestine   5,266,785  
    ##  4 Lebanon     6,856,000  
    ##  5 Taiwan      23,604,000 
    ##  6 South Korea 51,781,000 
    ##  7 Rwanda      12,374,000 
    ##  8 Haiti       11,578,000 
    ##  9 Netherlands 17,740,000 
    ## 10 Israel      9,570,000

## 4.15 복잡한 구조의 파일 읽기

``` r
# lines <- readLines("input.txt")
# lines <- readLines("input.txt", n = 10)       # Read 10 lines and stop
```

``` r
# singles <- scan("./data/singles.txt", what = numeric(0))
```

``` r
# triples <-
#   scan("./data/triples.txt",
#        what = list(character(0), numeric(0), numeric(0)))
# triples
```

``` r
# triples <- scan("./data/triples.txt",
#                 what = list(
#                   date = character(0),
#                   high = numeric(0),
#                   low = numeric(0)
#                 ))
# triples
```

``` r
# df_triples <- data.frame(triples)
# df_triples
```

## 4.16 MySQL 데이터베이스에서 읽기

``` r
# library(RMySQL)
#
# con <- dbConnect(
#     drv = RMySQL::MySQL(),
#     dbname = "your_db_name",
#     host = "your.host.com",
#     username = "userid",
#     password = "pwd"
#   )
```

``` r
# con <- dbConnect(
#   drv = RMySQL::MySQL(),
#   dbname = "your_db_name")
```

``` r
# sql <- "SELECT * from SurveyResults WHERE City = 'Chicago'"
# rows <- dbGetQuery(con, sql)
```

``` r
# dbDisconnect(con)
```

## 4.17 dbplyr로 데이터베이스 접근하기

``` r
# con <- DBI::dbConnect(RSQLite::SQLite(), ":memory:")
# sleep_db <- copy_to(con, msleep, "sleep")
```

``` r
# little_sleep <- sleep_table %>%
#   select(name, genus, order, sleep_total) %>%
#   filter(sleep_total < 3)
# show_query(little_sleep)
```

``` r
# local_little_sleep <- collect(little_sleep)
# local_little_sleep
```

## 4.18 객체 저장 및 이동

``` r
# save(tbl, t, file = "myData.RData")
# load("myData.RData")
```

``` r
# dput(tbl, file = "myData.txt")
# dump("tbl", file = "myData.txt")    # Note quotes around variable name
```
