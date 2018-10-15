---
title: d-g corrected for Independent t
author: DOOM Lab
date: '2018-05-09'
slug: gindt
url: /tests/gindt.html
showDate: false
---

<script src="//yihui.name/js/math-code.js"></script>
<script async
src="//cdn.bootcss.com/mathjax/2.7.1/MathJax.js?config=TeX-MML-AM_CHTML">
</script>

# Description   

This function displays *d*-g corrected and the non-central confidence interval for independent t.

The formula for *d* is: $$d = \frac{M_1 - M_2}{SD_{pooled}}*(1-\frac{3}{4*(N_1+N_2)-9})$$
 
The formula for *t* is: $$t = \frac{M_1 - M_2}{SE_{pooled}}$$

# R Function

g.ind.t(m1, m2, sd1, sd2, n1, n2, a = 0.05)

# Arguments 

+ m1	= mean one  
+ m2	= mean two
+ sd1 = standard deviation group one
+ sd2	= standard deviation group two
+ n1 = sample size group one
+ n2 = sample size group two
+ a = significance level

# Example  

A forensic psychologist conducted a study to examine whether being hypnotized during recall affects how well a witness can remember facts about an event. Eight participants watched a short film of a mock robbery, after which each participant was questioned about what he or she had seen. The four participants in the experimental group were questioned while they were hypnotized and gave 14, 22, 18, and 17 accurate responses. The four participants in the control group gave 20, 25, 24, and 23 accurate responses. The data is included at [GitHub](https://github.com/doomlab/shiny-server/tree/master/MOTE/examples). Example output from JASP, SPSS, and SAS are shown below.

**JASP**
![Independent t JASP](https://raw.githubusercontent.com/doomlab/shiny-server/master/MOTE/examples/independent%20t%20JASP.png)

**SPSS**
![Independent t SPSS](https://raw.githubusercontent.com/doomlab/shiny-server/master/MOTE/examples/independent%20t%20SPSS.png)

**SAS**
![Independent t SAS](https://raw.githubusercontent.com/doomlab/shiny-server/master/MOTE/examples/independent%20t%20SAS.PNG)

+ m1 = -2.66
+ m2	= 4
+ sd1 = 4
+ sd2	= .05
+ n1 = 
+ n2 = 
+ a = 

**JASP**
![Independent t JASP](https://raw.githubusercontent.com/doomlab/shiny-server/master/MOTE/examples/independent%20t%20JASP.png)

**SPSS**
![Independent t SPSS](https://raw.githubusercontent.com/doomlab/shiny-server/master/MOTE/examples/independent%20t%20SPSS.png)

**SAS**
![Independent t SAS](https://raw.githubusercontent.com/doomlab/shiny-server/master/MOTE/examples/independent%20t%20SAS.PNG)

# Function in R: 

d.ind.t.t(t = -2.66, n1 = 4, n2 = 4, a = .05)

# MOTE

## Screenshot

![Independent t - Means Screenshot](../images/indtt.jpg)

## Effect Size:

*d* = -2.17, 95% CI [-3.57, -0.10]

## Interpretation: 

Your confidence interval does not include zero, and therefore, you might conclude that this effect size is different from zero.

## Summary Statistics: 

Not applicable. 

## Test Statistic: 

*t*(6) = -2.66, *p* = .038

## Interpretation: 

Your p-value is less than the alpha value, and therefore, this test would be considered statistically significant.

# Tutorial

<iframe width="560" height="315" src="https://www.youtube.com/embed/kH3UOoFh9Ng" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>