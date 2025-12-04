Final Project Heart Attack Predictions
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
- [**RESULTS**](#results)
  - [**Heart Attack vs Stress Level**](#heart-attack-vs-stress-level)
    - [**Interpretation of Stress Level vs Heart Attack
      Plot**](#interpretation-of-stress-level-vs-heart-attack-plot)
  - [**Gender vs Heart Attack Heat
    Plot**](#gender-vs-heart-attack-heat-plot)
    - [**Interpretation of Gender vs Heart Attack
      Plot**](#interpretation-of-gender-vs-heart-attack-plot)
  - [**Education Level vs Heart
    Attack**](#education-level-vs-heart-attack)
    - [**Interpretation of Education Level vs Heart
      Attack**](#interpretation-of-education-level-vs-heart-attack)
  - [**All Variable Combined Plot**](#all-variable-combined-plot)
    - [**Interpretation of Stress Level, Education Level, and Gender vs
      Heart
      Attack**](#interpretation-of-stress-level-education-level-and-gender-vs-heart-attack)
- [**DISCUSSION**](#discussion)
- [**CONCLUSION**](#conclusion)
- [**REFERENCES**](#references)

``` r
knitr::opts_chunk$set(fig.path = "images/")
```

``` r
heart_data <- read.csv(file = "heart_attack_dataset_age.csv", header = TRUE)
heart_data$EducationLevel <- factor(
  heart_data$EducationLevel,
  levels = c(
    "High School",
    "College",
    "Postgraduate"
  )
)
```

``` r
install.packages("dplyr", dependencies = TRUE)
```

    ## Installing package into '/cloud/lib/x86_64-pc-linux-gnu-library/4.5'
    ## (as 'lib' is unspecified)

``` r
library(dplyr)
```

    ## 
    ## Attaching package: 'dplyr'

    ## The following objects are masked from 'package:stats':
    ## 
    ##     filter, lag

    ## The following objects are masked from 'package:base':
    ## 
    ##     intersect, setdiff, setequal, union

``` r
install.packages("ggplot2", dependencies = TRUE)
```

    ## Installing package into '/cloud/lib/x86_64-pc-linux-gnu-library/4.5'
    ## (as 'lib' is unspecified)

``` r
library(ggplot2)
install.packages("viridis", dependencies = TRUE)
```

    ## Installing package into '/cloud/lib/x86_64-pc-linux-gnu-library/4.5'
    ## (as 'lib' is unspecified)

    ## also installing the dependency 'terra'

    ## Warning in download.file(urls, destfiles, "libcurl", mode = "wb", ...): cannot
    ## open URL
    ## 'http://rspm/default/__linux__/focal/latest/src/contrib/terra_1.8-80.tar.gz':
    ## HTTP status was '404 Not Found'

    ## Warning in download.file(urls, destfiles, "libcurl", mode = "wb", ...): some
    ## files were not downloaded

    ## Warning in download.packages(pkgs, destdir = tmpd, available = available, :
    ## download of package 'terra' failed

``` r
library(viridis)
```

    ## Loading required package: viridisLite

``` r
install.packages("ggridges", dependencies = TRUE)
```

    ## Installing package into '/cloud/lib/x86_64-pc-linux-gnu-library/4.5'
    ## (as 'lib' is unspecified)

``` r
library(ggridges)
```

# **ABSTRACT**

Heart attacks affect approximately 805,000 Americans annually, showing
the importance to understand factors that contribute to increased
cardiovascular risk. Previous research indicates that chronic stress can
heighten inflammation, promote arterial plaque buildup, and elevate
blood pressure through increased hormone release, ultimately leading to
more risk of cardiac events. Stress is particularly prevalent among
individuals pursuing higher education, as both undergraduate and
postgraduate students face academic, professional, and personal
pressures that may contribute to long-term stress. Additionally, gender
has been identified as a potential risk factor, with men experiencing
heart attacks at roughly twice the rate of women, suggesting a possibly
protective hormonal difference. Given these observations, this study
examines how stress levels, educational status, and gender may interact
to influence the likelihood of experiencing a heart attack. The results
conclude no correlation between these factors and the presence of an
individual having a heart attack. This continues our search to find a
potential risk factor for heart attacks.

# **BACKGROUND**

Every year about 805,000 Americans have a heart attack (Tsao et al.,
2023). A heart attack can pose pain from a mild discomfort to severe
crushing pain (Kulkarni, 2025). This health risk has become like a
ticking bomb being able to strike anyone. With this disease that has the
ability to strike a variety of different individuals, research has begun
to try and predict risk factors or conditions that can cause an
individual to be more susceptible to having a heart attack. Long-term or
chronic stress can lead to higher levels of inflammation in the body
which leads to more plaque buildup in the arteries (Katella, 2024).
Additionally, stress also causes hormones such as adrenaline (Katella,
2024). Adrenaline increases mental alertness and the heart beats faster
and raises blood pressure and eventually heart damage (Katella, 2024).
From this knowledge we can theorize that prolonged stress can lead to a
damaged heart.

With this in mind we turn to what might cause an individual to have
prolonged stress. Specifically, undergraduate students often experience
stress related to adapting to higher education and managing coursework
(Pérez-Jorge, 2025). Postgraduate students also exhibit stress about
advanced research, thesis completion, and balancing academic work and
professional responsibilities (Pérez-Jorge, 2025). When it comes to
pursuing higher education there are a lot of stressful responsibilities
for individuals. This could be a cause of having a risk of heart attacks
because of the impact of the stress on the body.

Another factor that might contribute to a higher risk of heart attacks
is gender. Researchers have found that men are twice as likely to have a
heart attack than women (Harvard Health Publishing, 2016). There is also
some suspicion that hormones in women before menopause cause more
defense for women against heart attacks (Harvard Health Publishing,
2016).

Knowing this information brings a lot of questions of how much factors
like stress, gender, or education could lead to an individual being more
likely to have a heart attack.

# **STUDY QUESTIONS and HYPOTHESIS**

## **Questions**

Does the gender, education level, and/or stress level an individual has
affect the probability of them getting a heart attack?

## **Hypothesis**

If an individual is male, has a higher level of education, and a higher
stress level then we will see statistical significance with correlation
to having a heart attack because of how these factors affect heart
conditions over time.

## **Prediction**

An individual is male, has a higher level of education, and a higher the
stress level they will be more likely to have a heart attack at some
point in their life

# **METHODS**

This is a Kaggle database listing lifestyle habits and traits of
American individuals and whether they had a heart attack. The following
variables were selected, and statistical analysis was conducted to
determine correlation between the variable and having a heart attack.
Stress level was measured through a self-report on a scale from 1-10,
with 1 indicating low stress and 10 indicating high stress used in a
logistic regression model. Education level was the highest attained by
the individual reported as; high school, college, or postgraduate. Then
a chi-square test was used to measure the correlation to heart attacks.
Gender was listed as male or female with a chi-square test. A combined
model including education, stress, and gender was a logistic regression
model to identify combined contribution to heart attack prediction.

# **RESULTS**

## **Heart Attack vs Stress Level**

``` r
ggplot(heart_data, aes(x = Outcome, y = StressLevel, fill = Outcome)) +
  geom_violin(trim = FALSE, alpha = 0.7) +
  geom_boxplot(width = 0.5, fill = "white", alpha = 0.5) +
  labs(
    title = "Stress Levels by Heart Attack Outcome",
    x = "Heart Attack Outcome",
    y = "Stress Level (1–9)"
  ) +
  theme_minimal(base_size = 14) +
  theme(
    plot.title = element_text(hjust = 0.5, face = "bold"),
    legend.position = "none"
  )
```

![](images/Heart%20Attack%20vs%20StressLevel%20Violin%20Plot-1.png)<!-- -->

### **Interpretation of Stress Level vs Heart Attack Plot**

Analysis showed no statistically significant association between stress
levels and heart attack occurrence (p = 0.297). This suggests that
variations in stress level are not strongly linked to the likelihood of
experiencing a heart attack. However, this analysis does not account for
the potential effects of chronic or long-term stress exposure.

## **Gender vs Heart Attack Heat Plot**

``` r
library(dplyr)
library(ggplot2)
library(viridis)  

# Summarize counts
gender_counts <- heart_data %>%
  group_by(Gender, Outcome) %>%
  summarise(count = n(), .groups = "drop")

#Heat map
ggplot(gender_counts, aes(x = Gender, y = Outcome, fill = count)) +
  geom_tile(color = "white", size = 0.8) +  # white borders between tiles
  geom_text(aes(label = count), color = "white", size = 6, fontface = "bold") +
  scale_fill_viridis(option = "C", direction = -1) +  # smooth and modern gradient
  labs(
    title = "Heart Attack Outcomes by Gender",
    x = "Gender",
    y = "Heart Attack Outcome",
    fill = "Count"
  ) +
  theme_minimal(base_size = 15) +
  theme(
    plot.title = element_text(hjust = 0.5, face = "bold", size = 20),
    axis.text = element_text(face = "bold", size = 14),
    axis.title = element_text(face = "bold", size = 16),
    legend.title = element_text(face = "bold", size = 14),
    legend.text = element_text(size = 12)
  )
```

    ## Warning: Using `size` aesthetic for lines was deprecated in ggplot2 3.4.0.
    ## ℹ Please use `linewidth` instead.
    ## This warning is displayed once every 8 hours.
    ## Call `lifecycle::last_lifecycle_warnings()` to see where this warning was
    ## generated.

![](images/Gender%20vs%20Heart%20Attack%20Heat%20Plot-1.png)<!-- -->

### **Interpretation of Gender vs Heart Attack Plot**

Analysis showed no statistically significant relationship between
education level and heart attack occurrence (p = 0.554). This indicates
that differences in education level are not very likely to cause a
change in how likely someone is to have a heart attack.

## **Education Level vs Heart Attack**

``` r
# Summarize counts
edu_counts <- heart_data %>%
  group_by(EducationLevel, Outcome) %>%
  summarise(count = n(), .groups = "drop")

# Ensure order of education levels
edu_counts$EducationLevel <- factor(
  edu_counts$EducationLevel,
  levels = c("High School", "College", "Postgraduate")
)

# Side-by-side bar plot
ggplot(edu_counts, aes(x = EducationLevel, y = count, fill = Outcome)) +
  geom_col(position = position_dodge(width = 0.8), width = 0.7) +
  scale_fill_manual(values = c(
    "No Heart Attack" = "lightblue3",
    "Heart Attack" = "indianred2"
  )) +
  labs(
    title = "Heart Attack Outcomes by Education Level",
    x = "Education Level",
    y = "Count of Individuals",
    fill = "Heart Attack Outcome"
  ) +
  theme_minimal(base_size = 14) +
  theme(plot.title = element_text(hjust = 0.5, face = "bold"))
```

![](images/Heart%20Attack%20Vs%20Education%20Level%20Side%20by%20Side%20Bar%20Plot-1.png)<!-- -->

### **Interpretation of Education Level vs Heart Attack**

Analysis showed no statistically significant association between gender
and heart attack occurrence (p = 0.672). This suggests that being male
or female does not meaningfully influence the likelihood of experiencing
a heart attack.

## **All Variable Combined Plot**

``` r
library(ggplot2)

ggplot(heart_data, aes(
  x = EducationLevel,
  y = StressLevel,
  color = Outcome,       
  alpha = Outcome,  
  shape = Gender
)) +
  geom_jitter(width = 0.5, size = 4) +
  scale_alpha_manual(values = c("No Heart Attack" = .9, "Heart Attack" = 1)) +
  scale_shape_manual(values = c("Female" = 1, "Male" = 16)) +  # hollow vs filled
  scale_color_manual(values = c("No Heart Attack" = "lightblue3", "Heart Attack" = "indianred2")) + 
  labs(
    title = "Stress Levels by Education, Gender, and Heart Attack Outcome",
    x = "Education Level",
    y = "Stress Level (1–9)",
    color = "Heart Attack Outcome",
    alpha = "Heart Attack Outcome",
    shape = "Gender"
  ) +
  theme_minimal(base_size = 7) +
  theme(
    plot.title = element_text(hjust = 0.5, face = "bold")
  )
```

![](images/Stress%20Levels,%20Education%20Level,%20Gender,%20Heart%20Attack-1.png)<!-- -->

### **Interpretation of Stress Level, Education Level, and Gender vs Heart Attack**

Analysis showed no statistically significant association between the
combined effects of stress levels, education levels, and gender, and
heart attack occurrence (p = 0.624). This indicates that, collectively,
these factors do not significantly influence heart attack risk.

# **DISCUSSION**

From the database we saw no statistical significance between the stress
level an individual gave themselves and whether or not that person had a
heart attack. This could be due to a number of different factors. Having
an individual give their own assessment of stress might not be accurate
to the stress they actually exhibit at the time. They could feel stress
very casually or very intensely from person to person. Also, the stress
level they gave does not reflect whether or not they have prolonged
stress. They could be having a bad day that caused them to give a higher
stress level on the day they were asked, but overall they do not have
prolonged stress.

When we looked at how education level could be tied to heart attacks, we
found no statistically significant relationship between the two. A
possible explanation of this is that education level and prolonged
stress might not be as correlated as we thought. There are so many
nuances that more education can lead to a more secure job while they
might experience more stress due to the long education journey. Also,
education is not directly tied to how stressful someone might be. A
person could be completely stress free in a job and life situation
without having education as much as someone that might have a lot of
education.

After evaluating correlation between gender and heart attacks we found
no statistically significance between the two. While we found out that
women are more able to prevent heart attacks theorized to be menopausal
hormones, women are more likely to die from a heart attack than men
(Harvard Health Publishing, 2016) (Huebschmann and Regensteiner, 2024).
This really just brings to attention that there are more factors at play
when it comes to heart attacks than gender, education, and short term
stress.

# **CONCLUSION**

In conclusion, this study found no statistically significant data
showing that heart attacks can be predicted by the lifestyle of being
male, having a higher education, a higher stress level. That there must
be other factors contributing to individuals having heart attacks.
Future steps would be to look at more factors that are leading to more
heart attacks like genetic history, personal fitness, or heart
conditions. It would also be good to find a way to test for prolonged
stress through checking inflammation in the body. This way we could rule
out or rule in stress as a factor for heart damage. Overall we want to
highlight how we need to have more research on why heart attacks happen
to certain individuals.

# **REFERENCES**

Harvard Health Publishing. “Throughout Life, Heart Attacks Are Twice as
Common in Men than Women - Harvard Health.” Harvard Health, Harvard
Health, 8 Nov. 2016,
www.health.harvard.edu/heart-health/throughout-life-heart-attacks-are-twice-as-common-in-men-than-women.

Huebschmann, Amy, and Judith Regensteiner. “Women Are at a Higher Risk
of Dying from Heart Disease − in Part Because Doctors Don’t Take Major
Sex and Gender Differences into Account.” The Conversation, 22
Oct. 2024,
theconversation.com/women-are-at-a-higher-risk-of-dying-from-heart-disease-in-part-because-doctors-dont-take-major-sex-and-gender-differences-into-account-233861.

Katella, Kathy. “Yes, Stress Can Hurt Your Heart: 3 Things to Know.”
Yale Medicine, 12 Feb. 2024,
www.yalemedicine.org/news/stress-affects-your-heart.

Kulkarni, Anandita. “What Does a Heart Attack Feel Like? 8 Warning Signs
You Shouldn’t Ignore.” @Bswhealth, 2025,
www.bswhealth.com/blog/what-does-a-heart-attack-feel-like-8-warning-signs.

OpenAI. “ChatGPT.” Chatgpt.com, OpenAI, 12 Sept. 2025, chatgpt.com.

Panday, Ankush. “Heart Attack Prediction in United States.” Kaggle.com,
2025,
www.kaggle.com/datasets/ankushpanday2/heart-attack-prediction-in-united-states/data.
Accessed 6 Nov. 2025.

Pérez-Jorge, David, et al. “Examining the Effects of Academic Stress on
Student Well-Being in Higher Education.” Humanities and Social Sciences
Communications, vol. 12, no. 1, 28 Mar. 2025, pp. 1–13,
www.nature.com/articles/s41599-025-04698-y,
<https://doi.org/10.1057/s41599-025-04698-y>.

Tsao, Connie W., et al. “Heart Disease and Stroke Statistics—2023
Update: A Report from the American Heart Association.” Circulation,
vol. 147, no. 8, 25 Jan. 2023,
www.ahajournals.org/doi/10.1161/CIR.0000000000001123,
<https://doi.org/10.1161/cir.0000000000001123>.
