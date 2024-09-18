data import
================

``` r
litters_df=read_csv('data_import_examples/FAS_litters.csv')
```

    ## Rows: 49 Columns: 8
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr (4): Group, Litter Number, GD0 weight, GD18 weight
    ## dbl (4): GD of Birth, Pups born alive, Pups dead @ birth, Pups survive
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
names(litters_df)
```

    ## [1] "Group"             "Litter Number"     "GD0 weight"       
    ## [4] "GD18 weight"       "GD of Birth"       "Pups born alive"  
    ## [7] "Pups dead @ birth" "Pups survive"

``` r
litters_df = janitor::clean_names(litters_df)
names(litters_df)
```

    ## [1] "group"           "litter_number"   "gd0_weight"      "gd18_weight"    
    ## [5] "gd_of_birth"     "pups_born_alive" "pups_dead_birth" "pups_survive"

## Look at the dataset

``` r
litters_df
```

    ## # A tibble: 49 × 8
    ##    group litter_number   gd0_weight gd18_weight gd_of_birth pups_born_alive
    ##    <chr> <chr>           <chr>      <chr>             <dbl>           <dbl>
    ##  1 Con7  #85             19.7       34.7                 20               3
    ##  2 Con7  #1/2/95/2       27         42                   19               8
    ##  3 Con7  #5/5/3/83/3-3   26         41.4                 19               6
    ##  4 Con7  #5/4/2/95/2     28.5       44.1                 19               5
    ##  5 Con7  #4/2/95/3-3     <NA>       <NA>                 20               6
    ##  6 Con7  #2/2/95/3-2     <NA>       <NA>                 20               6
    ##  7 Con7  #1/5/3/83/3-3/2 <NA>       <NA>                 20               9
    ##  8 Con8  #3/83/3-3       <NA>       <NA>                 20               9
    ##  9 Con8  #2/95/3         <NA>       <NA>                 20               8
    ## 10 Con8  #3/5/2/2/95     28.5       <NA>                 20               8
    ## # ℹ 39 more rows
    ## # ℹ 2 more variables: pups_dead_birth <dbl>, pups_survive <dbl>

``` r
head(litters_df)
```

    ## # A tibble: 6 × 8
    ##   group litter_number gd0_weight gd18_weight gd_of_birth pups_born_alive
    ##   <chr> <chr>         <chr>      <chr>             <dbl>           <dbl>
    ## 1 Con7  #85           19.7       34.7                 20               3
    ## 2 Con7  #1/2/95/2     27         42                   19               8
    ## 3 Con7  #5/5/3/83/3-3 26         41.4                 19               6
    ## 4 Con7  #5/4/2/95/2   28.5       44.1                 19               5
    ## 5 Con7  #4/2/95/3-3   <NA>       <NA>                 20               6
    ## 6 Con7  #2/2/95/3-2   <NA>       <NA>                 20               6
    ## # ℹ 2 more variables: pups_dead_birth <dbl>, pups_survive <dbl>

``` r
tail(litters_df, 10)
```

    ## # A tibble: 10 × 8
    ##    group litter_number gd0_weight gd18_weight gd_of_birth pups_born_alive
    ##    <chr> <chr>         <chr>      <chr>             <dbl>           <dbl>
    ##  1 Mod8  #7/110/3-2    27.5       46                   19               8
    ##  2 Mod8  #2/95/2       28.5       44.5                 20               9
    ##  3 Mod8  #82/4         33.4       52.7                 20               8
    ##  4 Low8  #53           21.8       37.2                 20               8
    ##  5 Low8  #79           25.4       43.8                 19               8
    ##  6 Low8  #100          20         39.2                 20               8
    ##  7 Low8  #4/84         21.8       35.2                 20               4
    ##  8 Low8  #108          25.6       47.5                 20               8
    ##  9 Low8  #99           23.5       39                   20               6
    ## 10 Low8  #110          25.5       42.7                 20               7
    ## # ℹ 2 more variables: pups_dead_birth <dbl>, pups_survive <dbl>

``` r
view(litters_df)
skimr::skim(litters_df)
```

|                                                  |            |
|:-------------------------------------------------|:-----------|
| Name                                             | litters_df |
| Number of rows                                   | 49         |
| Number of columns                                | 8          |
| \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_   |            |
| Column type frequency:                           |            |
| character                                        | 4          |
| numeric                                          | 4          |
| \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ |            |
| Group variables                                  | None       |

Data summary

**Variable type: character**

| skim_variable | n_missing | complete_rate | min | max | empty | n_unique | whitespace |
|:--------------|----------:|--------------:|----:|----:|------:|---------:|-----------:|
| group         |         0 |          1.00 |   4 |   4 |     0 |        6 |          0 |
| litter_number |         0 |          1.00 |   3 |  15 |     0 |       49 |          0 |
| gd0_weight    |        13 |          0.73 |   1 |   4 |     0 |       26 |          0 |
| gd18_weight   |        15 |          0.69 |   1 |   4 |     0 |       31 |          0 |

**Variable type: numeric**

| skim_variable   | n_missing | complete_rate |  mean |   sd |  p0 | p25 | p50 | p75 | p100 | hist  |
|:----------------|----------:|--------------:|------:|-----:|----:|----:|----:|----:|-----:|:------|
| gd_of_birth     |         0 |             1 | 19.65 | 0.48 |  19 |  19 |  20 |  20 |   20 | ▅▁▁▁▇ |
| pups_born_alive |         0 |             1 |  7.35 | 1.76 |   3 |   6 |   8 |   8 |   11 | ▁▃▂▇▁ |
| pups_dead_birth |         0 |             1 |  0.33 | 0.75 |   0 |   0 |   0 |   0 |    4 | ▇▂▁▁▁ |
| pups_survive    |         0 |             1 |  6.41 | 2.05 |   1 |   5 |   7 |   8 |    9 | ▁▃▂▇▇ |

``` r
litters_df = 
    read_csv(file = "data_import_examples/FAS_litters.csv",
    skip = 10, col_names = FALSE)
```

    ## Rows: 40 Columns: 8
    ## ── Column specification ────────────────────────────────────────────────────────
    ## Delimiter: ","
    ## chr (4): X1, X2, X3, X4
    ## dbl (4): X5, X6, X7, X8
    ## 
    ## ℹ Use `spec()` to retrieve the full column specification for this data.
    ## ℹ Specify the column types or set `show_col_types = FALSE` to quiet this message.

``` r
litters_df
```

    ## # A tibble: 40 × 8
    ##    X1    X2              X3    X4       X5    X6    X7    X8
    ##    <chr> <chr>           <chr> <chr> <dbl> <dbl> <dbl> <dbl>
    ##  1 Con8  #3/5/2/2/95     28.5  <NA>     20     8     0     8
    ##  2 Con8  #5/4/3/83/3     28    <NA>     19     9     0     8
    ##  3 Con8  #1/6/2/2/95-2   <NA>  <NA>     20     7     0     6
    ##  4 Con8  #3/5/3/83/3-3-2 <NA>  <NA>     20     8     0     8
    ##  5 Con8  #2/2/95/2       <NA>  <NA>     19     5     0     4
    ##  6 Con8  #3/6/2/2/95-3   <NA>  <NA>     20     7     0     7
    ##  7 Mod7  #59             17    33.4     19     8     0     5
    ##  8 Mod7  #103            21.4  42.1     19     9     1     9
    ##  9 Mod7  #1/82/3-2       <NA>  <NA>     19     6     0     6
    ## 10 Mod7  #3/83/3-2       <NA>  <NA>     19     8     0     8
    ## # ℹ 30 more rows

``` r
litters_df = 
    read.csv(file = "./data_import_examples/FAS_litters.csv",
    na = c(".", "NA", ""))
litters_df
```

    ##    Group   Litter.Number GD0.weight GD18.weight GD.of.Birth Pups.born.alive
    ## 1   Con7             #85       19.7        34.7          20               3
    ## 2   Con7       #1/2/95/2       27.0        42.0          19               8
    ## 3   Con7   #5/5/3/83/3-3       26.0        41.4          19               6
    ## 4   Con7     #5/4/2/95/2       28.5        44.1          19               5
    ## 5   Con7     #4/2/95/3-3         NA          NA          20               6
    ## 6   Con7     #2/2/95/3-2         NA          NA          20               6
    ## 7   Con7 #1/5/3/83/3-3/2         NA          NA          20               9
    ## 8   Con8       #3/83/3-3         NA          NA          20               9
    ## 9   Con8         #2/95/3         NA          NA          20               8
    ## 10  Con8     #3/5/2/2/95       28.5          NA          20               8
    ## 11  Con8     #5/4/3/83/3       28.0          NA          19               9
    ## 12  Con8   #1/6/2/2/95-2         NA          NA          20               7
    ## 13  Con8 #3/5/3/83/3-3-2         NA          NA          20               8
    ## 14  Con8       #2/2/95/2         NA          NA          19               5
    ## 15  Con8   #3/6/2/2/95-3         NA          NA          20               7
    ## 16  Mod7             #59       17.0        33.4          19               8
    ## 17  Mod7            #103       21.4        42.1          19               9
    ## 18  Mod7       #1/82/3-2         NA          NA          19               6
    ## 19  Mod7       #3/83/3-2         NA          NA          19               8
    ## 20  Mod7       #2/95/2-2         NA          NA          20               7
    ## 21  Mod7       #3/82/3-2       28.0        45.9          20               5
    ## 22  Mod7       #4/2/95/2       23.5          NA          19               9
    ## 23  Mod7     #5/3/83/5-2       22.6        37.0          19               5
    ## 24  Mod7      #8/110/3-2         NA          NA          20               9
    ## 25  Mod7            #106       21.7        37.8          20               5
    ## 26  Mod7           #94/2       24.4        42.9          19               7
    ## 27  Mod7             #62       19.5        35.9          19               7
    ## 28  Low7           #84/2       24.3        40.8          20               8
    ## 29  Low7            #107       22.6        42.4          20               9
    ## 30  Low7           #85/2       22.2        38.5          20               8
    ## 31  Low7             #98       23.8        43.8          20               9
    ## 32  Low7            #102       22.6        43.3          20              11
    ## 33  Low7            #101       23.8        42.7          20               9
    ## 34  Low7            #111       25.5        44.6          20               3
    ## 35  Low7            #112       23.9        40.5          19               6
    ## 36  Mod8             #97       24.5        42.8          20               8
    ## 37  Mod8           #5/93         NA        41.1          20              11
    ## 38  Mod8         #5/93/2         NA          NA          19               8
    ## 39  Mod8       #7/82-3-2       26.9        43.2          20               7
    ## 40  Mod8      #7/110/3-2       27.5        46.0          19               8
    ## 41  Mod8         #2/95/2       28.5        44.5          20               9
    ## 42  Mod8           #82/4       33.4        52.7          20               8
    ## 43  Low8             #53       21.8        37.2          20               8
    ## 44  Low8             #79       25.4        43.8          19               8
    ## 45  Low8            #100       20.0        39.2          20               8
    ## 46  Low8           #4/84       21.8        35.2          20               4
    ## 47  Low8            #108       25.6        47.5          20               8
    ## 48  Low8             #99       23.5        39.0          20               6
    ## 49  Low8            #110       25.5        42.7          20               7
    ##    Pups.dead...birth Pups.survive
    ## 1                  4            3
    ## 2                  0            7
    ## 3                  0            5
    ## 4                  1            4
    ## 5                  0            6
    ## 6                  0            4
    ## 7                  0            9
    ## 8                  1            8
    ## 9                  0            8
    ## 10                 0            8
    ## 11                 0            8
    ## 12                 0            6
    ## 13                 0            8
    ## 14                 0            4
    ## 15                 0            7
    ## 16                 0            5
    ## 17                 1            9
    ## 18                 0            6
    ## 19                 0            8
    ## 20                 0            7
    ## 21                 0            5
    ## 22                 0            7
    ## 23                 0            5
    ## 24                 0            9
    ## 25                 0            2
    ## 26                 1            3
    ## 27                 2            4
    ## 28                 0            8
    ## 29                 0            8
    ## 30                 0            6
    ## 31                 0            9
    ## 32                 0            7
    ## 33                 0            9
    ## 34                 2            3
    ## 35                 1            1
    ## 36                 1            8
    ## 37                 0            9
    ## 38                 0            8
    ## 39                 0            7
    ## 40                 1            8
    ## 41                 0            9
    ## 42                 0            6
    ## 43                 1            7
    ## 44                 0            7
    ## 45                 0            7
    ## 46                 0            4
    ## 47                 0            7
    ## 48                 0            5
    ## 49                 0            6

``` r
litters_df = 
    read_csv(file = "./data_import_examples/FAS_litters.csv",
        na = c(".", "NA", ""),
    col_types = cols(
      Group = col_character(),
      `Litter Number` = col_character(),
      `GD0 weight` = col_double(),
      `GD18 weight` = col_double(),
      `GD of Birth` = col_integer(),
      `Pups born alive` = col_integer(),
      `Pups dead @ birth` = col_integer(),
      `Pups survive` = col_integer()
    )
  )
litters_df
```

    ## # A tibble: 49 × 8
    ##    Group `Litter Number` `GD0 weight` `GD18 weight` `GD of Birth`
    ##    <chr> <chr>                  <dbl>         <dbl>         <int>
    ##  1 Con7  #85                     19.7          34.7            20
    ##  2 Con7  #1/2/95/2               27            42              19
    ##  3 Con7  #5/5/3/83/3-3           26            41.4            19
    ##  4 Con7  #5/4/2/95/2             28.5          44.1            19
    ##  5 Con7  #4/2/95/3-3             NA            NA              20
    ##  6 Con7  #2/2/95/3-2             NA            NA              20
    ##  7 Con7  #1/5/3/83/3-3/2         NA            NA              20
    ##  8 Con8  #3/83/3-3               NA            NA              20
    ##  9 Con8  #2/95/3                 NA            NA              20
    ## 10 Con8  #3/5/2/2/95             28.5          NA              20
    ## # ℹ 39 more rows
    ## # ℹ 3 more variables: `Pups born alive` <int>, `Pups dead @ birth` <int>,
    ## #   `Pups survive` <int>

``` r
litters_df = 
    read_csv(file = 'data_import_examples/FAS_litters.csv',
        na = c(".", "NA", ""),
    col_types = cols(
      Group = col_factor()
    )
)
```

``` r
pups_df = 
    read_csv("./data_import_examples/FAS_pups.csv",
        na = c(".", "NA"), col_types = "fddddd")
pups_df
```

    ## # A tibble: 313 × 6
    ##    `Litter Number`   Sex `PD ears` `PD eyes` `PD pivot` `PD walk`
    ##    <fct>           <dbl>     <dbl>     <dbl>      <dbl>     <dbl>
    ##  1 #85                 1         4        13          7        11
    ##  2 #85                 1         4        13          7        12
    ##  3 #1/2/95/2           1         5        13          7         9
    ##  4 #1/2/95/2           1         5        13          8        10
    ##  5 #5/5/3/83/3-3       1         5        13          8        10
    ##  6 #5/5/3/83/3-3       1         5        14          6         9
    ##  7 #5/4/2/95/2         1        NA        14          5         9
    ##  8 #4/2/95/3-3         1         4        13          6         8
    ##  9 #4/2/95/3-3         1         4        13          7         9
    ## 10 #2/2/95/3-2         1         4        NA          8        10
    ## # ℹ 303 more rows

``` r
skimr::skim(pups_df)
```

|                                                  |         |
|:-------------------------------------------------|:--------|
| Name                                             | pups_df |
| Number of rows                                   | 313     |
| Number of columns                                | 6       |
| \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_   |         |
| Column type frequency:                           |         |
| factor                                           | 1       |
| numeric                                          | 5       |
| \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ |         |
| Group variables                                  | None    |

Data summary

**Variable type: factor**

| skim_variable | n_missing | complete_rate | ordered | n_unique | top_counts                         |
|:--------------|----------:|--------------:|:--------|---------:|:-----------------------------------|
| Litter Number |         0 |             1 | FALSE   |       49 | \#1/: 9, \#98: 9, \#10: 9, \#10: 9 |

**Variable type: numeric**

| skim_variable | n_missing | complete_rate |  mean |   sd |  p0 | p25 | p50 | p75 | p100 | hist  |
|:--------------|----------:|--------------:|------:|-----:|----:|----:|----:|----:|-----:|:------|
| Sex           |         0 |          1.00 |  1.50 | 0.50 |   1 |   1 |   2 |   2 |    2 | ▇▁▁▁▇ |
| PD ears       |        18 |          0.94 |  3.68 | 0.59 |   2 |   3 |   4 |   4 |    5 | ▁▅▁▇▁ |
| PD eyes       |        13 |          0.96 | 12.99 | 0.62 |  12 |  13 |  13 |  13 |   15 | ▂▇▁▂▁ |
| PD pivot      |        13 |          0.96 |  7.09 | 1.51 |   4 |   6 |   7 |   8 |   12 | ▂▇▂▂▁ |
| PD walk       |         0 |          1.00 |  9.50 | 1.34 |   7 |   9 |   9 |  10 |   14 | ▆▇▇▂▁ |

``` r
library(readxl)
mlb11_df = read_excel("data_import_examples/mlb11.xlsx", n_max = 20)
head(mlb11_df, 5)
```

    ## # A tibble: 5 × 12
    ##   team         runs at_bats  hits homeruns bat_avg strikeouts stolen_bases  wins
    ##   <chr>       <dbl>   <dbl> <dbl>    <dbl>   <dbl>      <dbl>        <dbl> <dbl>
    ## 1 Texas Rang…   855    5659  1599      210   0.283        930          143    96
    ## 2 Boston Red…   875    5710  1600      203   0.28        1108          102    90
    ## 3 Detroit Ti…   787    5563  1540      169   0.277       1143           49    95
    ## 4 Kansas Cit…   730    5672  1560      129   0.275       1006          153    71
    ## 5 St. Louis …   762    5532  1513      162   0.273        978           57    90
    ## # ℹ 3 more variables: new_onbase <dbl>, new_slug <dbl>, new_obs <dbl>

``` r
library(haven)
pulse_df = read_sas("./data_import_examples/public_pulse_data.sas7bdat")
head(pulse_df, 5)
```

    ## # A tibble: 5 × 7
    ##      ID   age Sex   BDIScore_BL BDIScore_01m BDIScore_06m BDIScore_12m
    ##   <dbl> <dbl> <chr>       <dbl>        <dbl>        <dbl>        <dbl>
    ## 1 10003  48.0 male            7            1            2            0
    ## 2 10015  72.5 male            6           NA           NA           NA
    ## 3 10022  58.5 male           14            3            8           NA
    ## 4 10026  72.7 male           20            6           18           16
    ## 5 10035  60.4 male            4            0            1            2

This document will show how to import data.
