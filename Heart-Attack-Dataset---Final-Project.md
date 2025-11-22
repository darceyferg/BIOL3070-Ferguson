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
  - [**Heart Attack vs Stress Level**](#heart-attack-vs-stress-level)
  - [**Interpretation of Stress Level vs Heart Attack
    Plot**](#interpretation-of-stress-level-vs-heart-attack-plot)
  - [**Gender vs Heart Attack Heat
    Plot**](#gender-vs-heart-attack-heat-plot)
  - [**Education Level vs Heart
    Attack**](#education-level-vs-heart-attack)
  - [**All Variable Combined Plot**](#all-variable-combined-plot)
  - [**Stress Level, Education Level, and Gender vs Heart
    Attack**](#stress-level-education-level-and-gender-vs-heart-attack)
- [**DISCUSSION**](#discussion)
- [**CONCLUSION**](#conclusion)
- [**REFERENCES**](#references)

``` r
heart_data <- read.csv(file = "heart_attack_dataset_age.csv", header = TRUE)
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

    ## Warning in install.packages("viridis", dependencies = TRUE): installation of
    ## package 'terra' had non-zero exit status

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
protective hormonal differences. Given these observations, this study
examines how stress levels, educational status, and gender may interact
to influence the likelihood of experiencing a heart attack. The results
conclude no correlation between these factors and the presence of an
individual having a heart attack. This continues our search to find a
potential risk factor for heart attacks.

# **BACKGROUND**

Every year about 805,000 Americans have a heart attack. (Tsao et al.,
2023) A heart attack can pose pain from a mild discomfort to severe
crushing pain. (Kulkarni, 2025) This health risk has become like a
ticking bomb being able to strike anyone. With this disease that has the
ability to strike a variety of different individuals, research has begun
to try and predict risk factors or conditions that can cause an
individual to be more susceptible to having a heart attack. Long-term or
chronic stress can lead to higher levels of inflammation in the body
which leads to more plague buildup in the arteries. (Katella, 2024)
Additionally, stress also causes hormones such as adrenaline. (Katella,
2024) Adrenaline increases mental alertness and the heart beats faster
and raises blood pressure. (Katella, 2024) Prolonged stress leads to
heart damage.

With this in mind we turn to what might cause an individual to have
prolonged stress. Specifically, undergraduate students often experience
stress related to adapting to higher education and managing coursework.
(Pérez-Jorge, 2025) Postgraduate students also exhibit stress about
advanced research, thesis completion, and balancing academic work and
professional responsibilities. (Pérez-Jorge, 2025) When it comes to
pursuing higher education there are a lot of stressful responsibilities
for individuals. This could be a cause of having a risk of heart attacks
because of the impact of the stress on the body.

Another factor that might contribute to a higher risk of heart attacks
is gender. Researchers have found that men are twice as likely to have a
heart attack than women. (Harvard Health Publishing, 2016) There is also
some suspicion that hormones in women before menopause cause more
defense for women against heart attacks. (Harvard Health Publishing,
2016)

Knowing this information brings a lot of question of how much factors
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

The database chosen for this study was the Kaggle database, and the
heart attack prediction set was the one chosen for this study. It was
chosen because it had enough entries for our purposes and many variables
to test. Once the variables were chosen, an excel spreadsheet was
created to hold all the data. Multiple linear regression models were
made testing variables against the outcomes of heart attack. After all
the variables were tested individually, they were then all tested at the
same time vs heart attack outcome to test for a correlation between all
of them.

### **Heart Attack vs Stress Level**

``` r
ggplot(heart_data, aes(x = Outcome, y = StressLevel, fill = Outcome)) +
  geom_violin(trim = FALSE, alpha = 0.7) +
  geom_boxplot(width = 0.1, fill = "white", alpha = 0.5) +
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

<img src="Heart-Attack-Dataset---Final-Project_files/figure-gfm/Heart Attack vs StressLevel Violin Plot-1.png" style="display: block; margin: auto auto auto 0;" />

### **Interpretation of Stress Level vs Heart Attack Plot**

Analysis showed no statistically significant association between stress
levels and heart attack occurrence (p = 0.297). This suggests that
variations in stress level are not strongly linked to the likelihood of
experiencing a heart attack. However, this analysis does not account for
the potential effects of chronic or long-term stress exposure.

### **Gender vs Heart Attack Heat Plot**

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

<img src="Heart-Attack-Dataset---Final-Project_files/figure-gfm/Gender vs Heart Attack Heat Plot-1.png" style="display: block; margin: auto auto auto 0;" />
\### **Interpretation of Gender vs Heart Attack Plot**

Analysis showed no statistically significant relationship between
education level and heart attack occurrence (p = 0.554). This indicates
that differences in education level are not very likely to cause a
change in how likely someone is to have a heart attack.

### **Education Level vs Heart Attack**

``` r
library(dplyr)
library(ggplot2)

# Summarize counts
edu_counts <- heart_data %>%
  group_by(EducationLevel, Outcome) %>%
  summarise(count = n(), .groups = "drop")

# Fancy lollipop chart
ggplot(edu_counts, aes(x = EducationLevel, y = count, color = Outcome)) +
  geom_segment(aes(x = EducationLevel, xend = EducationLevel, y = 0, yend = count), linewidth = 1.2) +
  geom_point(size = 6) +
  scale_color_manual(values = c("No Heart Attack" = "skyblue", "Heart Attack" = "tomato")) +
  labs(
    title = "Heart Attack Outcomes by Education Level",
    x = "Education Level",
    y = "Count of Individuals",
    color = "Heart Attack Outcome"
  ) +
  theme_minimal(base_size = 14) +
  theme(plot.title = element_text(hjust = 0.5, face = "bold"))
```

<img src="Heart-Attack-Dataset---Final-Project_files/figure-gfm/Heart Attack Vs Education Level lollipop Plot-1.png" style="display: block; margin: auto auto auto 0;" />
\### **Interpretation of Education Level vs Heart Attack**

Analysis showed no statistically significant association between gender
and heart attack occurrence (p = 0.672). This suggests that being male
or female does not meaningfully influence the likelihood of experiencing
a heart attack.

### **All Variable Combined Plot**

``` r
library(ggplot2)

ggplot(heart_data, aes(
  x = EducationLevel,
  y = StressLevel,
  color = Outcome,       
  alpha = Outcome,  
  shape = Gender
)) +
  geom_jitter(width = 0.3, size = 4) +
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

<img src="Heart-Attack-Dataset---Final-Project_files/figure-gfm/Stress Levels, Education Level, Gender, Heart Attack-1.png" style="display: block; margin: auto auto auto 0;" />

### **Stress Level, Education Level, and Gender vs Heart Attack**

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
stress might not be as correlated as we thought. Even if school work
leads to stress over a long period of time, having more education can
lead to a more secure job environment and lower stress.

…

# **CONCLUSION**

In conclusion, we found no statistically significant data showing that
heart attacks can be predicted by the lifestyle of being male, having a
higher education, a higher stress level. …

# **REFERENCES**

Harvard Health Publishing. “Throughout Life, Heart Attacks Are Twice as
Common in Men than Women - Harvard Health.” Harvard Health, Harvard
Health, 8 Nov. 2016,
www.health.harvard.edu/heart-health/throughout-life-heart-attacks-are-twice-as-common-in-men-than-women.

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
