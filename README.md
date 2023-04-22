# Project "Dependence of Schizophrenia on different world development and healthcare systems indicators"

Authors:
1. [Sergey Orlov](https://www.linkedin.com/in/orlovtsu/)
2. [Shrivarshini Balaji](https://www.linkedin.com/in/shrivarshini-balaji-999551188/)
3. [Niloofar Mirzadzare](https://www.linkedin.com/in/niloofar-mirzadzare-280211271/)

## Introduction

Mental health constitutes our emotions and feelings and it can affect our behavior, thoughts, and coping abilities [1]. The rate of mental health disorders is on a rise worldwide, due to modern society's chronic stress, demographic factors, substance abuse, and unhealthy lifestyles [2].
Nowadays, with less stigma, there is more recognition of the importance of mental health and how it can impact individuals in society. Schizophrenia is one type of mental health disorder that affects about 24 million individuals around the world. It is a chronic and severe mental illness that influences an individual's ability to think, feel, and behave clearly [3]. The symptoms of schizophrenia can be either positive or negative. Positive symptoms basically add, such as hallucinations, delusions, and distorted thinking or speech. Negative symptoms on the other hand can contribute to reduction. Negative symptoms can include, no emotion or motivation and social withdrawal [4]. The severity and type of symptoms can vary from person to person and can change over time. 

Schizophrenia is a complex mental illness and its causes can be mainly due to chemical and neurotransmitter imbalances in the brain [5]. While there is no cure for Schizophrenia, researchers are trying to enhance their understanding of the underlying mechanisms and factors leading to the illness, and thus develop more effective and safer treatment options [4]. Several factors can trigger schizophrenia and impact its severity, including genetic predisposition, environmental factors, and substance use (i.e. cannabis). Stress and trauma can also exacerbate symptoms of schizophrenia and contribute to its severity [6].

![Distribution of schozophrenia worldwide](/images/Schizophrenia.png)
Fig 1. Distribution of schozophrenia worldwide.

The distribution of schizophrenia is relatively uniform worldwide, with a prevalence of 1 in 300 (0.32%) in different regions [3]. However, significant disparities exist in access to mental health services and treatment for people with schizophrenia, especially in low- and middle-income and
developing countries. Addressing these inequalities and ensuring that people with schizophrenia receive appropriate care and support is critical to improving outcomes and reducing the global burden of mental illness.

In this project, our main goal was to perform a multiple regression analysis to further enhance our understanding of the impact of different socioeconomic factors on the prevalence of schizophrenia around the world.

## Dataset:

We collected our datasets in CSV format from the World Health Organization (WHO), which offers open-source data [7]. There were a total of 8 CSV files obtained from the WHO website:
1. MentalHealthDisorders.csv
2. WDIData_T.csv
3. Beds_in_mental_health_hospitals_per_100thousands.csv
4. Beds_for_mh_in_general_hospital_per100thousand_2019.csv
5. Psychologists_in_mental_health_per_100thousands.csv
6. Psychiatrists_in_mental_health.csv
7. Social_workers_in_mental_health_per_100thousands.csv
8. 2.12_Health_systems.csv

To measure the impact of Schizophrenia within each society, the parameter of disability-adjusted life year (DALY) per 100,000 people is utilized. The DALY parameter is employed to gauge the total burden of depression. To compare countries using this parameter, the dataset "DALY” estimates WHO Member States by country. This dataset is sourced from the official World Health Organization website (http://who.int) and may be utilized for research purposes, with proper citation [7]. The dataset includes DALY parameters for each country in the WHO for every monitored disorder, segregated by gender and age, spanning the years from 2000 to 2019.
For our project, we will utilize the data for Schizophrenia disorder from this dataset to find the indicators based on the DALY parameter.

The dataset about expenditures for the healthcare system worldwide is taken from The World Bank website [8]. This dataset contains health expenditures in percentage to Gross Domestic Product (GDP), expenditures in U.S. dollars, and expenditures in U.S. dollars per capita for 2019 by countries. This data is used in combination with the dataset "Government expenditures on mental health as a percentage of total government expenditures on health (%)" from the World Health Organization website [9]. By combining these data, we can analyze spending on mental health worldwide by country and the efficiency of spending on diagnostics and treatment in each healthcare system.

<i>R code:</i>
```{r}
# Loading libraries
library(ggplot2)
library(olsrr)
library(dplyr)
library(lmtest)
library(mctest)
library(GGally)
library(MASS)
library(stats)

# Loading datasets
mhd <- read.csv('MentalHealthDisorders.csv')
wdi <- read.csv('WDIData_T.csv')
beds_mhh_p100t <- read.csv('beds_in_mental_health_hospitals_per_100thousands.csv')
beds_mhg_p100t <- read.csv('beds_for_mh_in_general_hospital_per100thousand_2019.csv')
psycho_p100t <- read.csv('psychologists_in_mental_health_per_100thousands.csv')
psychi_p100t <- read.csv('psychiatrists_in_mental_health.csv')
sw_p100t <- read.csv('social_workers_in_mental_health_per_100thousands.csv')
```
