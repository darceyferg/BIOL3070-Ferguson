Homework 10: Build 1 Figure
================
Darcey Ferguson
10/28/2025

- [**ABSTRACT**](#abstract)
- [**BACKGROUND**](#background)
- [**STUDY QUESTIONS and HYPOTHESIS**](#study-questions-and-hypothesis)
  - [**Questions**](#questions)
  - [**Hypothesis**](#hypothesis)
  - [**Prediction**](#prediction)
- [**METHODS**](#methods)
- [**GGplot**](#ggplot)
  - [**Interpretation of Bar Plot
    Visualization**](#interpretation-of-bar-plot-visualization)
- [**GGPlot**](#ggplot-1)
  - [**Interpretation of GLM**](#interpretation-of-glm)
- [**DISCUSSION**](#discussion)
- [**CONCLUSION**](#conclusion)
- [**REFERENCES**](#references)

``` r
heart <- read.csv(file = "heart_attack_dataset2.new.csv", header = TRUE)
```

# **ABSTRACT**

# **BACKGROUND**

# **STUDY QUESTIONS and HYPOTHESIS**

## **Questions**

## **Hypothesis**

## **Prediction**

# **METHODS**

# **GGplot**

``` r
library(ggplot2)

levels(heart$Outcome) <- c(0, 1)

heart$OutcomeNum <- ifelse(heart$Outcome == "Heart Attack", 1, 0)

ggplot(heart, aes(x=StressLevel, y= ST_Depression, size = OutcomeNum)) +
    geom_point(alpha=0.1) +
    scale_size(range = c(0, 1))
```

![](Heart-Attack-Dataset---Final-Project_files/figure-gfm/unnamed-chunk-2-1.png)<!-- -->

## **Interpretation of Bar Plot Visualization**

# **GGPlot**

``` r
library(ggplot2)
heart$OutcomeNum <- ifelse(heart$Outcome == "Heart Attack", 1, 0)

ggplot(heart, aes(x=StressLevel, y=ST_Depression, size = OutcomeNum)) + 
    geom_point(color="darkred") +
    ggtitle("Size")
```

![](Heart-Attack-Dataset---Final-Project_files/figure-gfm/unnamed-chunk-3-1.png)<!-- -->

## **Interpretation of GLM**

# **DISCUSSION**

# **CONCLUSION**

# **REFERENCES**
