# Statistical Hypothesis Tests for Business Decision Making

*Author:* **Afridi Jubair** [zubyr09](https://github.com/zubyr09)
*Repository:* [Statistical-Hypothesis-Tests-for-Business-Decision-Making](https://github.com/zubyr09/Statistical-Hypothesis-Tests-for-Business-Decision-Making)

## Overview

This repository contains a collection of Jupyter notebooks demonstrating various statistical hypothesis tests applied to common business scenarios. The primary goal is to showcase how these tests can be leveraged to make data-driven decisions. Each notebook includes:
- A clear definition of the business problem.
- Formulation of null (H₀) and alternative (H₁) hypotheses.
- Necessary assumption checks for each test (e.g., normality, homogeneity of variances).
- Python implementation of the statistical tests using libraries like scipy.stats and statsmodels.
- Detailed interpretation of the test outputs (p-values, test statistics) and their business implications.

The significance level (alpha, α) used for all tests is *0.05*.

## Table of Contents

1.  [A/B Testing: Website Layout Engagement](#ab-testing-website-layout-engagement)
    * [Notebook Link](#notebook-link-ab-testing)
    * [Test Used](#test-used-ab-testing)
    * [Theory: Independent Samples t-test & Mann-Whitney U Test](#theory-independent-samples-t-test--mann-whitney-u-test)
    * [Scenario & Goal](#scenario--goal-ab-testing)
    * [Hypotheses](#hypotheses-ab-testing)
    * [Assumption Checks & Test Selection](#assumption-checks--test-selection-ab-testing)
    * [Key Findings & Interpretation](#key-findings--interpretation-ab-testing)
2.  [Chi-Square Test: Customer Region vs. Support Channel Preference](#chi-square-test-customer-region-vs-support-channel-preference)
    * [Notebook Link](#notebook-link-chi-square-independence)
    * [Test Used](#test-used-chi-square-independence)
    * [Theory: Chi-Square Test of Independence](#theory-chi-square-test-of-independence)
    * [Scenario & Goal](#scenario--goal-chi-square-independence)
    * [Hypotheses](#hypotheses-chi-square-independence)
    * [Assumption Check](#assumption-check-chi-square-independence)
    * [Key Findings & Interpretation](#key-findings--interpretation-chi-square-independence)
3.  [Comprehensive Hypothesis Tests in Python](#comprehensive-hypothesis-tests-in-python)
    * [Notebook Link](#notebook-link-comprehensive-tests)
    * [3.1 One-Sample t-test: Fast-Food Delivery Times](#one-sample-t-test-fast-food-delivery-times)
        * [Theory](#theory-one-sample-t-test)
        * [Scenario & Goal](#scenario--goal-one-sample-t-test)
        * [Hypotheses](#hypotheses-one-sample-t-test)
        * [Assumption Check](#assumption-check-one-sample-t-test)
        * [Key Findings & Interpretation](#key-findings--interpretation-one-sample-t-test)
    * [3.2 Independent Samples t-test / Mann-Whitney U: Customer Spending](#independent-samples-t-test--mann-whitney-u-customer-spending)
        * [Scenario & Goal](#scenario--goal-independent-samples-spending)
        * [Hypotheses](#hypotheses-independent-samples-spending)
        * [Assumption Checks & Test Selection](#assumption-checks--test-selection-independent-samples-spending)
        * [Key Findings & Interpretation](#key-findings--interpretation-independent-samples-spending)
    * [3.3 Paired Samples t-test / Wilcoxon Signed-Rank: Sales Performance](#paired-samples-t-test--wilcoxon-signed-rank-sales-performance)
        * [Theory](#theory-paired-samples-t-test--wilcoxon-signed-rank-test)
        * [Scenario & Goal](#scenario--goal-paired-samples-sales)
        * [Hypotheses](#hypotheses-paired-samples-sales)
        * [Assumption Check](#assumption-check-paired-samples-sales)
        * [Key Findings & Interpretation](#key-findings--interpretation-paired-samples-sales)
    * [3.4 ANOVA / Kruskal-Wallis: Campaign CLV](#anova--kruskal-wallis-campaign-clv)
        * [Theory: ANOVA & Kruskal-Wallis Test](#theory-anova--kruskal-wallis-test)
        * [Scenario & Goal](#scenario--goal-anova-clv)
        * [Hypotheses](#hypotheses-anova-clv)
        * [Assumption Checks & Test Selection](#assumption-checks--test-selection-anova-clv)
        * [Key Findings & Interpretation](#key-findings--interpretation-anova-clv)
    * [3.5 Chi-Square Goodness-of-Fit Test: Website Traffic](#chi-square-goodness-of-fit-test-website-traffic)
        * [Theory: Chi-Square Goodness-of-Fit Test](#theory-chi-square-goodness-of-fit-test)
        * [Scenario & Goal](#scenario--goal-chi-square-gof)
        * [Hypotheses](#hypotheses-chi-square-gof)
        * [Assumption Check](#assumption-check-chi-square-gof)
        * [Key Findings & Interpretation](#key-findings--interpretation-chi-square-gof)
4.  [Setup & How to Run](#setup--how-to-run)

---

## 1. A/B Testing: Website Layout Engagement
<a id="ab-testing-website-layout-engagement"></a>

### Notebook Link
<a id="notebook-link-ab-testing" href="https://github.com/zubyr09/Statistical-Hypothesis-Tests-for-Business-Decision-Making/blob/main/Analyzing_Website_Layout_Engagement_via_AB_Test.ipynb" target="_blank">Analyzing_Website_Layout_Engagement_via_AB_Test.ipynb</a>


### Test Used
<a id="test-used-ab-testing"></a>
Independent Samples t-test (or Welch's t-test if variances are unequal) / Mann-Whitney U test (if normality assumption is violated).

### Theory: Independent Samples t-test & Mann-Whitney U Test
<a id="theory-independent-samples-t-test--mann-whitney-u-test"></a>
The *Independent Samples t-test* is used to determine if there is a statistically significant difference between the means of two independent groups.
Assumptions:
    1.  Independence of observations.
    2.  Normality of data in each group.
    3.  Homogeneity of variances (variances are equal between groups). If this assumption is violated, Welch's t-test is used.

The *Mann-Whitney U Test* (also known as the Wilcoxon rank-sum test) is a non-parametric alternative to the independent samples t-test. It is used when the assumption of normality is not met. It tests whether the distributions of two independent samples are equal.

### Scenario & Goal
<a id="scenario--goal-ab-testing"></a>
*Scenario:* Interactive Cares, a Bangladeshi Skill Development Platform, wants to test if a newly designed user dashboard (Version B) leads to higher average user engagement time (measured in minutes per session) compared to the current dashboard (Version A).
*Goal:* Determine if the difference in average engagement time is statistically significant.
*Metric:* Average Session Duration (in minutes).

### Hypotheses
<a id="hypotheses-ab-testing"></a>
* *Null Hypothesis (H₀):* There is no difference in the mean engagement time between Version A and Version B.
    * Mathematically: μ<sub>A</sub> = μ<sub>B</sub>
* *Alternative Hypothesis (H₁):* There is a difference in the mean engagement time between Version A and Version B.
    * Mathematically (Two-tailed): μ<sub>A</sub> ≠ μ<sub>B</sub>

### Assumption Checks & Test Selection
<a id="assumption-checks--test-selection-ab-testing"></a>
* *Normality Check (Shapiro-Wilk Test):*
    * Group A (Old Layout): Statistic = 0.9966, p-value = 0.6551
    * Group B (New Layout): Statistic = 0.9954, p-value = 0.4236
    * Interpretation: Both groups appear normally distributed (p > 0.05 for both).
* *Homogeneity of Variances Check (Levene's Test):*
    * Statistic = 2.5046, p-value = 0.1141
    * Interpretation: Variances are assumed equal (p > 0.05).
* *Test Selected:* Standard Independent Samples t-test (since normality and homogeneity of variances assumptions are met).

### Key Findings & Interpretation
<a id="key-findings--interpretation-ab-testing"></a>
* *T-statistic:* -5.9724
* *P-value (two-tailed):* 0.0000
* *Mean Engagement Time (Group A - Old):* 15.04 minutes
* *Mean Engagement Time (Group B - New):* 16.53 minutes
* *Conclusion:* Reject the Null Hypothesis (H₀) as p-value (0.0000) < α (0.05).
* *Interpretation:* There is a statistically significant difference in the mean engagement time between the old layout (Group A) and the new layout (Group B). Specifically, the new layout (Group B) shows a significantly higher average engagement time.
* *Cohen's d (effect size):* 0.3783 (small to medium effect)
* *Achieved Power:* 0.9998 (adequate power)

---

## 2. Chi-Square Test: Customer Region vs. Support Channel Preference
<a id="chi-square-test-customer-region-vs-support-channel-preference"></a>

### Notebook Link
<a id="notebook-link-chi-square-independence"></a>
[Chi_Square_Test - Region_vs_Support_Channel_Preference.ipynb](https://github.com/zubyr09/Statistical-Hypothesis-Tests-for-Business-Decision-Making/blob/main/Chi_Square_Test%20-%20Region_vs_Support_Channel_Preference.ipynb)

### Test Used
<a id="test-used-chi-square-independence"></a>
Chi-Square Test of Independence.

### Theory: Chi-Square Test of Independence
<a id="theory-chi-square-test-of-independence"></a>
The *Chi-Square Test of Independence* is used to determine if there is a statistically significant association (dependence) between two categorical variables. It compares the observed frequencies in a contingency table to the frequencies that would be expected if the variables were independent.
Assumptions:
    1.  Two categorical variables.
    2.  Independence of observations.
    3.  Expected cell frequencies: Most (≥80%) expected cell frequencies should be 5 or greater, and none should be less than 1.

### Scenario & Goal
<a id="scenario--goal-chi-square-independence"></a>
*Scenario:* A Bangladeshi company offers customer support through multiple channels: Phone, Email, Chat, and FAQ/Self-Service. They want to understand if customers in different geographical regions of the country (Dhaka, Rajshahi, Chittagong, Sylhet, Khulna, Mymensingh, Barisal, Rangpur) have different preferences for these support channels.
*Goal:* Determine if there is a statistically significant association between customer region and their preferred support channel.

### Hypotheses
<a id="hypotheses-chi-square-independence"></a>
* *Null Hypothesis (H₀):* Customer region and preferred support channel are independent.
* *Alternative Hypothesis (H₁):* Customer region and preferred support channel are dependent.

### Assumption Check
<a id="assumption-check-chi-square-independence"></a>
* *Expected Frequencies:* The minimum expected frequency was 22.53.
* Interpretation: Assumption met (all expected frequencies are ≥ 5).

### Key Findings & Interpretation
<a id="key-findings--interpretation-chi-square-independence"></a>
* *Chi-Square Statistic:* 21.0047
* *P-value:* 0.3802
* *Degrees of Freedom:* 21
* *Conclusion:* Fail to Reject the Null Hypothesis (H₀) as p-value (0.3802) > α (0.05).
* *Interpretation:* There is not enough evidence to conclude a statistically significant association between customer region (division) and preferred support channel at the 5% significance level. Based on this data, we cannot say that support channel preferences differ significantly across regions.

---

## 3. Comprehensive Hypothesis Tests in Python
<a id="comprehensive-hypothesis-tests-in-python"></a>

### Notebook Link
<a id="notebook-link-comprehensive-tests"></a>
[Comprehensive_Hypothesis_Tests_in_Python.ipynb](https://github.com/zubyr09/Statistical-Hypothesis-Tests-for-Business-Decision-Making/blob/main/Comprehensive_Hypothesis_Tests_in_Python.ipynb)

This notebook covers a variety of parametric and non-parametric tests.

### 3.1 One-Sample t-test: Fast-Food Delivery Times
<a id="one-sample-t-test-fast-food-delivery-times"></a>

#### Theory
<a id="theory-one-sample-t-test"></a>
The *One-Sample t-test* is used to determine whether the mean of a single sample is statistically different from a known or hypothesized population mean.
Assumptions:
    1.  The data are continuous.
    2.  The data are a random sample from the population.
    3.  The data are approximately normally distributed.
    4.  The variance of the population is unknown.

#### Scenario & Goal
<a id="scenario--goal-one-sample-t-test"></a>
*Scenario:* A fast-food chain claims that the average delivery time for their orders is 30 minutes or less. Data were collected from a sample of 50 recent deliveries.
*Goal:* Determine if the sample data provides enough evidence to refute the chain's claim.
*Metric:* Delivery Time (in minutes).

#### Hypotheses
<a id="hypotheses-one-sample-t-test"></a>
* *Null Hypothesis (H₀):* The true average delivery time is 30 minutes (μ = 30).
* *Alternative Hypothesis (H₁):* The true average delivery time is greater than 30 minutes (μ > 30).

#### Assumption Check
<a id="assumption-check-one-sample-t-test"></a>
* *Normality (Shapiro-Wilk Test):* Statistic = 0.9713, p-value = 0.2615.
* Interpretation: Data appears normally distributed (p > 0.05). Assumption met.

#### Key Findings & Interpretation
<a id="key-findings--interpretation-one-sample-t-test"></a>
* *Sample Mean:* 34.14 minutes
* *T-statistic:* 3.5313
* *P-value (one-tailed):* 0.0005
* *Conclusion:* Reject the Null Hypothesis (H₀) as p-value (0.0005) < α (0.05).
* *Interpretation:* There is statistically significant evidence to suggest that the average delivery time is greater than 30 minutes. The sample mean (34.14 mins) is significantly higher than the claimed 30 minutes.

### 3.2 Independent Samples t-test / Mann-Whitney U: Customer Spending
<a id="independent-samples-t-test--mann-whitney-u-customer-spending"></a>
(Theory covered in [Section 1.3](#theory-independent-samples-t-test--mann-whitney-u-test))

#### Scenario & Goal
<a id="scenario--goal-independent-samples-spending"></a>
*Scenario:* A retail company wants to compare the average spending per visit of customers who use their loyalty card versus those who don't.
*Goal:* Determine if there's a significant difference in average spending between loyalty card users and non-users.
*Metric:* Spending per Visit ($).

#### Hypotheses
<a id="hypotheses-independent-samples-spending"></a>
* *Null Hypothesis (H₀):* The mean spending per visit is the same for loyalty card users and non-users (μ<sub>loyalty</sub> = μ<sub>non_loyalty</sub>).
* *Alternative Hypothesis (H₁):* The mean spending per visit is different between the two groups (μ<sub>loyalty</sub> ≠ μ<sub>non_loyalty</sub>).

#### Assumption Checks & Test Selection
<a id="assumption-checks--test-selection-independent-samples-spending"></a>
* *Normality (Shapiro-Wilk Test):*
    * Loyalty Group: Statistic = 0.9895, p-value = 0.6254
    * Non-Loyalty Group: Statistic = 0.9830, p-value = 0.1349
    * Interpretation: Both groups appear normally distributed (p > 0.05 for both).
* *Homogeneity of Variances (Levene's Test):*
    * Statistic = 2.4570, p-value = 0.1185
    * Interpretation: Variances are assumed equal (p > 0.05).
* *Test Selected:* Standard Independent Samples t-test.

#### Key Findings & Interpretation
<a id="key-findings--interpretation-independent-samples-spending"></a>
* *Mean Spending (Loyalty):* $86.37
* *Mean Spending (Non-Loyalty):* $78.11
* *T-statistic:* 2.3714
* *P-value (two-tailed):* 0.0186
* *Conclusion:* Reject the Null Hypothesis (H₀) as p-value (0.0186) < α (0.05).
* *Interpretation:* There is a statistically significant difference in average spending per visit between loyalty card users and non-users. Loyalty card users tend to spend significantly more per visit.

### 3.3 Paired Samples t-test / Wilcoxon Signed-Rank: Sales Performance
<a id="paired-samples-t-test--wilcoxon-signed-rank-sales-performance"></a>

#### Theory: Paired Samples t-test & Wilcoxon Signed-Rank Test
<a id="theory-paired-samples-t-test--wilcoxon-signed-rank-test"></a>
The *Paired Samples t-test* (also known as the dependent samples t-test) is used to compare the means of two related groups (e.g., the same subjects before and after a treatment). It tests if the mean difference between paired observations is significantly different from zero.
Assumptions:
    1.  The differences between pairs are continuous.
    2.  The differences are a random sample.
    3.  The differences are approximately normally distributed.

The *Wilcoxon Signed-Rank Test* is a non-parametric alternative to the paired samples t-test. It is used when the assumption of normality of differences is not met. It tests whether the median of the differences is zero.

#### Scenario & Goal
<a id="scenario--goal-paired-samples-sales"></a>
*Scenario:* A company implements a new training program for its sales team. They measure the sales performance (number of deals closed) for a sample of salespeople before and after the training.
*Goal:* Determine if the training program significantly improved sales performance.
*Metric:* Number of Deals Closed (per month).

#### Hypotheses
<a id="hypotheses-paired-samples-sales"></a>
* *Null Hypothesis (H₀):* There is no difference in the mean number of deals closed before and after the training (μ<sub>diff</sub> = 0).
* *Alternative Hypothesis (H₁):* The mean number of deals closed is higher after the training (μ<sub>diff</sub> > 0).

#### Assumption Check
<a id="assumption-check-paired-samples-sales"></a>
* *Normality of Differences (Shapiro-Wilk Test):* Statistic = 0.9711, p-value = 0.3848.
* Interpretation: Differences appear normally distributed (p > 0.05). Assumption met.
* *Test Selected:* Paired Samples t-test.

#### Key Findings & Interpretation
<a id="key-findings--interpretation-paired-samples-sales"></a>
* *Mean Deals (Before):* 14.78
* *Mean Deals (After):* 17.80
* *Mean Difference (After - Before):* 3.03
* *T-statistic:* 4.8082
* *P-value (one-tailed):* 0.0000
* *Conclusion:* Reject the Null Hypothesis (H₀) as p-value (0.0000) < α (0.05).
* *Interpretation:* There is statistically significant evidence that the sales training program improved performance. The average number of deals closed after training is significantly higher than before.

### 3.4 ANOVA / Kruskal-Wallis: Campaign CLV
<a id="anova--kruskal-wallis-campaign-clv"></a>

#### Theory: ANOVA & Kruskal-Wallis Test
<a id="theory-anova--kruskal-wallis-test"></a>
*One-Way Analysis of Variance (ANOVA)* is used to determine whether there are any statistically significant differences between the means of three or more independent groups.
Assumptions:
    1.  Independence of observations.
    2.  Normality of data in each group.
    3.  Homogeneity of variances (variances are equal across groups).

The *Kruskal-Wallis Test* is a non-parametric alternative to one-way ANOVA. It is used when the assumptions of ANOVA (especially normality or homogeneity of variances if group sizes are unequal) are not met. It tests whether the median ranks of the groups are different.

#### Scenario & Goal
<a id="scenario--goal-anova-clv"></a>
*Scenario:* A marketing team tested three different advertising campaigns (Campaign A, Campaign B, Campaign C) on different, comparable customer segments. They measured the resulting 'Customer Lifetime Value' (CLV).
*Goal:* Determine if there is a significant difference in the mean CLV generated by the three campaigns.
*Metric:* Customer Lifetime Value (CLV) ($).

#### Hypotheses
<a id="hypotheses-anova-clv"></a>
* *Null Hypothesis (H₀):* The mean CLV is the same for all three campaigns (μ<sub>A</sub> = μ<sub>B</sub> = μ<sub>C</sub>).
* *Alternative Hypothesis (H₁):* At least one campaign has a different mean CLV than the others.

#### Assumption Checks & Test Selection
<a id="assumption-checks--test-selection-anova-clv"></a>
* *Normality (Shapiro-Wilk Test):*
    * Campaign A: Statistic = 0.9838, p-value = 0.4940
    * Campaign B: Statistic = 0.9884, p-value = 0.7249
    * Campaign C: Statistic = 0.9838, p-value = 0.4916
    * Interpretation: All groups appear normally distributed (p > 0.05 for all).
* *Homogeneity of Variances (Levene's Test):*
    * Statistic = 0.2081, p-value = 0.8123
    * Interpretation: Variances are assumed equal (p > 0.05).
* *Test Selected:* One-Way ANOVA.

#### Key Findings & Interpretation
<a id="key-findings--interpretation-anova-clv"></a>
* *Mean CLV (Campaign A):* $501.93
* *Mean CLV (Campaign B):* $561.39
* *Mean CLV (Campaign C):* $503.57
* *F-statistic:* 4.2155
* *P-value:* 0.0159
* *Conclusion:* Reject the Null Hypothesis (H₀) as p-value (0.0159) < α (0.05).
* *Interpretation:* There is a statistically significant difference in the mean CLV among the three campaigns. Further post-hoc tests (e.g., Tukey's HSD) would be needed to determine which specific campaigns differ from each other. (The notebook output indicates Campaign B has a higher mean.)

### 3.5 Chi-Square Goodness-of-Fit Test: Website Traffic
<a id="chi-square-goodness-of-fit-test-website-traffic"></a>

#### Theory: Chi-Square Goodness-of-Fit Test
<a id="theory-chi-square-goodness-of-fit-test"></a>
The *Chi-Square Goodness-of-Fit Test* is used to determine if an observed frequency distribution for a single categorical variable significantly differs from a hypothesized or expected frequency distribution.
Assumptions:
    1.  One categorical variable.
    2.  Independence of observations.
    3.  Expected frequencies in each category should be reasonably large (typically ≥ 5).

#### Scenario & Goal
<a id="scenario--goal-chi-square-gof"></a>
*Scenario:* A website manager believes that traffic is evenly distributed across four main sections of the site: Home, Products, Blog, and Contact Us (i.e., 25% to each).
*Goal:* Determine if the observed distribution of page views significantly differs from the expected uniform distribution.
*Metric:* Page Views per Section.

#### Hypotheses
<a id="hypotheses-chi-square-gof"></a>
* *Null Hypothesis (H₀):* The observed distribution of page views matches the expected uniform distribution.
* *Alternative Hypothesis (H₁):* The observed distribution of page views does not match the expected uniform distribution.

#### Assumption Check
<a id="assumption-check-chi-square-gof"></a>
* *Observed Views:* Home: 1250, Products: 1100, Blog: 950, Contact Us: 700 (Total: 4000)
* *Expected Views (uniform):* 1000 for each section.
* *Minimum Expected Frequency:* 1000.00.
* Interpretation: Assumption met (all expected frequencies are ≥ 5).

#### Key Findings & Interpretation
<a id="key-findings--interpretation-chi-square-gof"></a>
* *Chi-Square Statistic:* 121.0000
* *P-value:* 0.0000
* *Conclusion:* Reject the Null Hypothesis (H₀) as p-value (0.0000) < α (0.05).
* *Interpretation:* There is a statistically significant difference between the observed distribution of website traffic and the expected uniform distribution. The traffic is not evenly distributed across the four sections as hypothesized.

---

## 4. Setup & How to Run
<a id="setup--how-to-run"></a>

To run these Jupyter notebooks, you will need Python installed along with the following libraries:
* pandas
* numpy
* scipy
* statsmodels
* matplotlib
* seaborn

You can typically install these using pip:
```bash
pip install pandas numpy scipy statsmodels matplotlib seaborn jupyter
