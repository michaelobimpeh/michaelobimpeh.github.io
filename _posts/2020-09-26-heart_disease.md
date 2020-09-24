---
title: "Data Mining Projects"
date: 2020-09-25
tags: [data wrangling, data science, messy data]
header:
  image: "/images/perceptron/percept.jpg"
excerpt: "Data Wrangling, Data Science, Messy Data"
mathjax: "true"
---
## GitHub Documents

This is an R Markdown format used for publishing markdown documents to
GitHub. When you click the **Knit** button all R code chunks are run and
a markdown file (.md) suitable for publishing to GitHub is generated.

## Including Code

You can include R code in the document as follows:

``` r
library(tidyverse)
heart<-read_csv("C:\\Users\\aba\\Desktop\\Dataset\\heart.csv")
```

    ## Parsed with column specification:
    ## cols(
    ##   age = col_double(),
    ##   sex = col_double(),
    ##   cp = col_double(),
    ##   trestbps = col_double(),
    ##   chol = col_double(),
    ##   fbs = col_double(),
    ##   restecg = col_double(),
    ##   thalach = col_double(),
    ##   exang = col_double(),
    ##   oldpeak = col_double(),
    ##   slope = col_double(),
    ##   ca = col_double(),
    ##   thal = col_double(),
    ##   target = col_double()
    ## )

``` r
heart %>%
  mutate(target=as.factor(target))%>%
  ggplot(aes(age,fill=target)) + 
  geom_histogram(position="dodge",alpha=0.7 )
```

    ## `stat_bin()` using `bins = 30`. Pick better value with `binwidth`.

![](heart_disease_files/figure-gfm/unnamed-chunk-2-1.png)<!-- -->

\`\`\`

ggcorrplot(): Returns a ggplot2

cor\_pmat(): Returns a matrix containing the p-values of correlations

# Correlation matrix

``` r
corr <- round(cor(heart), 1)
corr
```

    ##           age  sex   cp trestbps chol  fbs restecg thalach exang oldpeak slope
    ## age       1.0 -0.1 -0.1      0.3  0.2  0.1    -0.1    -0.4   0.1     0.2  -0.2
    ## sex      -0.1  1.0  0.0     -0.1 -0.2  0.0    -0.1     0.0   0.1     0.1   0.0
    ## cp       -0.1  0.0  1.0      0.0 -0.1  0.1     0.0     0.3  -0.4    -0.1   0.1
    ## trestbps  0.3 -0.1  0.0      1.0  0.1  0.2    -0.1     0.0   0.1     0.2  -0.1
    ## chol      0.2 -0.2 -0.1      0.1  1.0  0.0    -0.2     0.0   0.1     0.1   0.0
    ## fbs       0.1  0.0  0.1      0.2  0.0  1.0    -0.1     0.0   0.0     0.0  -0.1
    ## restecg  -0.1 -0.1  0.0     -0.1 -0.2 -0.1     1.0     0.0  -0.1    -0.1   0.1
    ## thalach  -0.4  0.0  0.3      0.0  0.0  0.0     0.0     1.0  -0.4    -0.3   0.4
    ## exang     0.1  0.1 -0.4      0.1  0.1  0.0    -0.1    -0.4   1.0     0.3  -0.3
    ## oldpeak   0.2  0.1 -0.1      0.2  0.1  0.0    -0.1    -0.3   0.3     1.0  -0.6
    ## slope    -0.2  0.0  0.1     -0.1  0.0 -0.1     0.1     0.4  -0.3    -0.6   1.0
    ## ca        0.3  0.1 -0.2      0.1  0.1  0.1    -0.1    -0.2   0.1     0.2  -0.1
    ## thal      0.1  0.2 -0.2      0.1  0.1  0.0     0.0    -0.1   0.2     0.2  -0.1
    ## target   -0.2 -0.3  0.4     -0.1 -0.1  0.0     0.1     0.4  -0.4    -0.4   0.3
    ##            ca thal target
    ## age       0.3  0.1   -0.2
    ## sex       0.1  0.2   -0.3
    ## cp       -0.2 -0.2    0.4
    ## trestbps  0.1  0.1   -0.1
    ## chol      0.1  0.1   -0.1
    ## fbs       0.1  0.0    0.0
    ## restecg  -0.1  0.0    0.1
    ## thalach  -0.2 -0.1    0.4
    ## exang     0.1  0.2   -0.4
    ## oldpeak   0.2  0.2   -0.4
    ## slope    -0.1 -0.1    0.3
    ## ca        1.0  0.2   -0.4
    ## thal      0.2  1.0   -0.3
    ## target   -0.4 -0.3    1.0

# Compute a matrix of correlation p-values

``` r
p.mat <- cor_pmat(mtcars)
p.mat
```

    ##               mpg          cyl         disp           hp         drat
    ## mpg  0.000000e+00 6.112687e-10 9.380327e-10 1.787835e-07 1.776240e-05
    ## cyl  6.112687e-10 0.000000e+00 1.802838e-12 3.477861e-09 8.244636e-06
    ## disp 9.380327e-10 1.802838e-12 0.000000e+00 7.142679e-08 5.282022e-06
    ## hp   1.787835e-07 3.477861e-09 7.142679e-08 0.000000e+00 9.988772e-03
    ## drat 1.776240e-05 8.244636e-06 5.282022e-06 9.988772e-03 0.000000e+00
    ## wt   1.293959e-10 1.217567e-07 1.222320e-11 4.145827e-05 4.784260e-06
    ## qsec 1.708199e-02 3.660533e-04 1.314404e-02 5.766253e-06 6.195826e-01
    ## vs   3.415937e-05 1.843018e-08 5.235012e-06 2.940896e-06 1.167553e-02
    ## am   2.850207e-04 2.151207e-03 3.662114e-04 1.798309e-01 4.726790e-06
    ## gear 5.400948e-03 4.173297e-03 9.635921e-04 4.930119e-01 8.360110e-06
    ## carb 1.084446e-03 1.942340e-03 2.526789e-02 7.827810e-07 6.211834e-01
    ##                wt         qsec           vs           am         gear
    ## mpg  1.293959e-10 1.708199e-02 3.415937e-05 2.850207e-04 5.400948e-03
    ## cyl  1.217567e-07 3.660533e-04 1.843018e-08 2.151207e-03 4.173297e-03
    ## disp 1.222320e-11 1.314404e-02 5.235012e-06 3.662114e-04 9.635921e-04
    ## hp   4.145827e-05 5.766253e-06 2.940896e-06 1.798309e-01 4.930119e-01
    ## drat 4.784260e-06 6.195826e-01 1.167553e-02 4.726790e-06 8.360110e-06
    ## wt   0.000000e+00 3.388683e-01 9.798492e-04 1.125440e-05 4.586601e-04
    ## qsec 3.388683e-01 0.000000e+00 1.029669e-06 2.056621e-01 2.425344e-01
    ## vs   9.798492e-04 1.029669e-06 0.000000e+00 3.570439e-01 2.579439e-01
    ## am   1.125440e-05 2.056621e-01 3.570439e-01 0.000000e+00 5.834043e-08
    ## gear 4.586601e-04 2.425344e-01 2.579439e-01 5.834043e-08 0.000000e+00
    ## carb 1.463861e-02 4.536949e-05 6.670496e-04 7.544526e-01 1.290291e-01
    ##              carb
    ## mpg  1.084446e-03
    ## cyl  1.942340e-03
    ## disp 2.526789e-02
    ## hp   7.827810e-07
    ## drat 6.211834e-01
    ## wt   1.463861e-02
    ## qsec 4.536949e-05
    ## vs   6.670496e-04
    ## am   7.544526e-01
    ## gear 1.290291e-01
    ## carb 0.000000e+00

# correlation plot

``` r
ggcorrplot(corr, method = "circle")
```

![](heart_disease_files/figure-gfm/unnamed-chunk-5-1.png)<!-- -->

# Add correlation coefficients

# argument lab = TRUE

``` r
ggcorrplot(corr,
  hc.order = TRUE, type = "lower",
  lab = TRUE,
  ggtheme = ggplot2::theme_dark(),
)
```

![](heart_disease_files/figure-gfm/unnamed-chunk-6-1.png)<!-- -->

# correlation plot

``` r
heart %>%
  mutate(target=as.factor(target))%>%
ggplot(aes(age,thalach, colour = target)) +
geom_point()
```

![](heart_disease_files/figure-gfm/unnamed-chunk-7-1.png)<!-- -->

# Training model

``` r
library(tidymodels)
```

    ## -- Attaching packages ------------------------------------------- tidymodels 0.1.1 --

    ## v broom     0.7.0      v recipes   0.1.13
    ## v dials     0.0.8      v rsample   0.0.7 
    ## v infer     0.5.3      v tune      0.1.1 
    ## v modeldata 0.0.2      v workflows 0.1.3 
    ## v parsnip   0.1.3      v yardstick 0.0.7

    ## -- Conflicts ---------------------------------------------- tidymodels_conflicts() --
    ## x foreach::accumulate() masks purrr::accumulate()
    ## x scales::discard()     masks purrr::discard()
    ## x dplyr::filter()       masks stats::filter()
    ## x recipes::fixed()      masks stringr::fixed()
    ## x dplyr::lag()          masks stats::lag()
    ## x yardstick::spec()     masks readr::spec()
    ## x recipes::step()       masks stats::step()
    ## x foreach::when()       masks purrr::when()

``` r
heart_split<- heart %>%
  initial_split(strata = target)
heart_split
```

    ## <Analysis/Assess/Total>
    ## <228/75/303>

``` r
training(heart_split)
```

    ## # A tibble: 228 x 14
    ##      age   sex    cp trestbps  chol   fbs restecg thalach exang oldpeak slope
    ##    <dbl> <dbl> <dbl>    <dbl> <dbl> <dbl>   <dbl>   <dbl> <dbl>   <dbl> <dbl>
    ##  1    63     1     3      145   233     1       0     150     0     2.3     0
    ##  2    37     1     2      130   250     0       1     187     0     3.5     0
    ##  3    41     0     1      130   204     0       0     172     0     1.4     2
    ##  4    56     1     1      120   236     0       1     178     0     0.8     2
    ##  5    57     0     0      120   354     0       1     163     1     0.6     2
    ##  6    57     1     0      140   192     0       1     148     0     0.4     1
    ##  7    56     0     1      140   294     0       0     153     0     1.3     1
    ##  8    44     1     1      120   263     0       1     173     0     0       2
    ##  9    52     1     2      172   199     1       1     162     0     0.5     2
    ## 10    54     1     0      140   239     0       1     160     0     1.2     2
    ## # ... with 218 more rows, and 3 more variables: ca <dbl>, thal <dbl>,
    ## #   target <dbl>

The function createDataPartition can be used to create stratied random
splits of a data set. In this case, 75% of the data will be used for
model training and the remainder will be used for evaluating model
performance. The function creates the random splits within each class so
that the overall class distribution is preserved as well as possible.

``` r
# Data spliting
library("caret")
```

    ## Loading required package: lattice

    ## 
    ## Attaching package: 'caret'

    ## The following objects are masked from 'package:yardstick':
    ## 
    ##     precision, recall, sensitivity, specificity

    ## The following object is masked from 'package:purrr':
    ## 
    ##     lift

``` r
library("e1071")
```

    ## 
    ## Attaching package: 'e1071'

    ## The following object is masked from 'package:tune':
    ## 
    ##     tune

``` r
set.seed(1)
heartNew<- heart %>% 
  mutate(target=as.factor(target))

inTrain <- createDataPartition(heartNew$target, p = .75, list = FALSE)

training<- heartNew[inTrain,]
```

    ## Warning: The `i` argument of ``[`()` can't be a matrix as of tibble 3.0.0.
    ## Convert to a vector.
    ## This warning is displayed once every 8 hours.
    ## Call `lifecycle::last_warnings()` to see where this warning was generated.

``` r
testing <- heartNew[-inTrain,]
```

# model fitting

``` r
modelFit1<-train(target~.,data=training,method="glm")
modelFit1
```

    ## Generalized Linear Model 
    ## 
    ## 228 samples
    ##  13 predictor
    ##   2 classes: '0', '1' 
    ## 
    ## No pre-processing
    ## Resampling: Bootstrapped (25 reps) 
    ## Summary of sample sizes: 228, 228, 228, 228, 228, 228, ... 
    ## Resampling results:
    ## 
    ##   Accuracy   Kappa    
    ##   0.7922618  0.5814713

``` r
modelFit1$finalModel
```

    ## 
    ## Call:  NULL
    ## 
    ## Coefficients:
    ## (Intercept)          age          sex           cp     trestbps         chol  
    ##     2.01003      0.01493     -2.49042      0.95190     -0.01814     -0.00547  
    ##         fbs      restecg      thalach        exang      oldpeak        slope  
    ##     0.03865      0.38113      0.02574     -1.08496     -0.46410      0.72715  
    ##          ca         thal  
    ##    -0.89300     -0.79020  
    ## 
    ## Degrees of Freedom: 227 Total (i.e. Null);  214 Residual
    ## Null Deviance:       314.3 
    ## Residual Deviance: 151.7     AIC: 179.7

# predictions on test data

``` r
predictions<-predict(modelFit1,newdata = testing)
predictions
```

    ##  [1] 1 1 1 1 0 1 1 1 1 0 0 1 1 0 1 1 1 1 1 1 1 1 1 1 1 0 1 1 1 1 1 1 1 1 1 0 1 0
    ## [39] 1 0 0 0 0 0 1 0 0 0 0 1 0 0 0 0 1 0 0 0 0 0 0 1 0 0 0 1 1 0 0 0 0 0 0 0 1
    ## Levels: 0 1

# Confusing Matrix

``` r
confusionMatrix(predictions,testing$target)
```

    ## Confusion Matrix and Statistics
    ## 
    ##           Reference
    ## Prediction  0  1
    ##          0 27  9
    ##          1  7 32
    ##                                           
    ##                Accuracy : 0.7867          
    ##                  95% CI : (0.6768, 0.8729)
    ##     No Information Rate : 0.5467          
    ##     P-Value [Acc > NIR] : 1.324e-05       
    ##                                           
    ##                   Kappa : 0.5717          
    ##                                           
    ##  Mcnemar's Test P-Value : 0.8026          
    ##                                           
    ##             Sensitivity : 0.7941          
    ##             Specificity : 0.7805          
    ##          Pos Pred Value : 0.7500          
    ##          Neg Pred Value : 0.8205          
    ##              Prevalence : 0.4533          
    ##          Detection Rate : 0.3600          
    ##    Detection Prevalence : 0.4800          
    ##       Balanced Accuracy : 0.7873          
    ##                                           
    ##        'Positive' Class : 0               
    ## 

Note that the `echo = FALSE` parameter was added to the code chunk to
prevent printing of the R code that generated the plot.
