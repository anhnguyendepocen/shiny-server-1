---
title: Dependent *t* Averages - Means
author: DOOM Lab
date: '2018-05-09'
slug: deptavgM
url: /tests/deptavgM.html
showDate: false
---

<script src="//yihui.name/js/math-code.js"></script>
<script async
src="//cdn.bootcss.com/mathjax/2.7.1/MathJax.js?config=TeX-MML-AM_CHTML">
</script>

# Description   

This function displays *d* for repeated measures data and the non-central confidence interval using the average standard deviation of each level as the denominator.

The formula for d is: $$d = \frac{M_1 - M_2}{\frac{SD_1 + SD_2}{2}}$$

# R Function

d.dep.t.avg(m1, m2, sd1, sd2, n, a = 0.05) 

# Arguments 


+ m1 = mean from first level
+ m2 = mean from second level
+ sd1 = standard deviation from first level
+ sd2	= standard deviation from second level
+ n = sample size
+ a	= significance level

# Example  

In a study to test the effects of science fiction movies on people's belief in the supernatural, seven people completed a measure of belief in the supernatural before and after watching a popular science fiction movie. Participants' scores are shown with high scores indicating high levels of belief. The data is included at [GitHub](https://github.com/doomlab/shiny-server/tree/master/MOTE/examples). Example output from JASP, SPSS, and SAS are shown below.

**JASP**
![Dependent t JASP](https://raw.githubusercontent.com/doomlab/shiny-server/master/MOTE/examples/dependent%20t%20JASP.png)

**SPSS**
![Dependent t SPSS](https://raw.githubusercontent.com/doomlab/shiny-server/master/MOTE/examples/dependent%20t%20SPSS.png)

**SAS**
![Dependent t SAS](https://raw.githubusercontent.com/doomlab/shiny-server/master/MOTE/examples/dependent%20t%20SAS.PNG)

+ m1 = 5.571
+ m2 = 4.429
+ sd1 = 1.988
+ sd2	= 2.878
+ n = 14
+ a	= .05

# Function in R: 

d.dep.t.avg(m1 = 5.571, m2 = 4.429, sd1 = 1.988, sd2 = 2.878, n = 14, a = .05)

# MOTE

## Screenshot

![Z-Test Means Screenshot](../images/z-test-means-screen.png)

## Effect Size:

*d* = 0.47, 95% CI [-0.09, 1.01]

## Interpretation: 

Your confidence interval does include zero, and therefore, you might conclude that this effect size is similar to zero.

## Summary Statistics: 

Group 1 Summary Statistics: *M* = 5.57, *SD* = 1.99, *SE* = 0.53, 95% CI [4.42, 6.72]

Group 2 Summary Statistics: *M* = 4.43, *SD* = 2.88, *SE* = 0.77, 95% CI [2.77, 6.09]
## Test Statistic: 

Not applicable.

## Interpretation: 

Not applicable.

# Tutorial

<iframe width="560" height="315" src="https://www.youtube.com/embed/eq9X4ynxq2A" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>