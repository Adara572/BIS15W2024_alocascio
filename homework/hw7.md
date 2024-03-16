---
title: "Homework 7"
author: "Adara"
date: "2024-02-12"
output:
  html_document: 
    theme: spacelab
    keep_md: yes
---



## Instructions
Answer the following questions and complete the exercises in RMarkdown. Please embed all of your code and push your final work to your repository. Your final lab report should be organized, clean, and run free from errors. Remember, you must remove the `#` for the included code chunks to run. Be sure to add your name to the author header above.  

Make sure to use the formatting conventions of RMarkdown to make your report neat and clean!  

## Load the libraries

```r
library(tidyverse)
library(janitor)
library(skimr)
library(naniar)
```

## Data
**1. For this homework, we will use two different data sets. Please load `amniota` and `amphibio`.**  

`amniota` data:  
Myhrvold N, Baldridge E, Chan B, Sivam D, Freeman DL, Ernest SKM (2015). “An amniote life-history
database to perform comparative analyses with birds, mammals, and reptiles.” _Ecology_, *96*, 3109.
doi: 10.1890/15-0846.1 (URL: https://doi.org/10.1890/15-0846.1).



```r
#amniota<-read_csv("data/amniota.csv") %>% clean_names()
```

`amphibio` data:  
Oliveira BF, São-Pedro VA, Santos-Barrera G, Penone C, Costa GC (2017). “AmphiBIO, a global database
for amphibian ecological traits.” _Scientific Data_, *4*, 170123. doi: 10.1038/sdata.2017.123 (URL:
https://doi.org/10.1038/sdata.2017.123).

```r
#amphibio <- read_csv("data/amphibio.csv") %>% clean_names() #its saying it can't open the connection
```

## Questions  
**2. Do some exploratory analysis of the `amniota` data set. Use the function(s) of your choice. Try to get an idea of how NA's are represented in the data.**  

```r
#glimpse(amniota)
```

**3. Do some exploratory analysis of the `amphibio` data set. Use the function(s) of your choice. Try to get an idea of how NA's are represented in the data.**  

```r
#glimpse(amphibio)
```

**4. How many total NA's are in each data set? Do these values make sense? Are NA's represented by values?**   

```r
#amniota %>% 
  #map_df(~ sum(is.na(.)))
```


```r
#amphibio %>% 
  #map_df(~ sum(is.na(.)))
```

**5. Make any necessary replacements in the data such that all NA's appear as "NA".**   

```r
#amniota %>% 
  #replace_with_na_all(condition = ~.x== -999)
```

```r
#amphibio %>% 
  #replace_with_na_all(condition = ~.x== -999)
```

**6. Use the package `naniar` to produce a summary, including percentages, of missing data in each column for the `amniota` data.**  

```r
#miss_var_summary(amniota)
```



**7. Use the package `naniar` to produce a summary, including percentages, of missing data in each column for the `amphibio` data.**

```r
#miss_var_summary(amphibio)
```

**8. For the `amniota` data, calculate the number of NAs in the `egg_mass_g` column sorted by taxonomic class; i.e. how many NA's are present in the `egg_mass_g` column in birds, mammals, and reptiles? Does this results make sense biologically? How do these results affect your interpretation of NA's?**  

```r
#amniota %>% 
  #group_by(class) %>% 
  #select(class, egg_mass_g) %>% 
  #miss_var_summary(order=T)
```

**9. The `amphibio` data have variables that classify species as fossorial (burrowing), terrestrial, aquatic, or arboreal.Calculate the number of NA's in each of these variables. Do you think that the authors intend us to think that there are NA's in these columns or could they represent something else? Explain.**

```r
#amphibio %>% 
  #select(Arb, Fos, Aqu, Ter) %>% 
  #miss_var_summary(order=T)
```

**10. Now that we know how NA's are represented in the `amniota` data, how would you load the data such that the values which represent NA's are automatically converted?**

```r
#read.csv("data/amniota.csv", na= c("NA", "-999", "-999.00")) %>% clean_names() # Its saying it can't open the connection
#i put hash tags in front of everything because it refused to knit because it didn't recognize the data as an object. I'm thinking its because I had to import the data and not load it. 
```

## Push your final code to GitHub!
Please be sure that you check the `keep md` file in the knit preferences.  
