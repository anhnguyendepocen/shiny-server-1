---
title: d-g Corrected for Independent t
author: DOOM Lab
date: '2018-05-09'
slug: indtg
url: /tests/indtg.html
showDate: false
---

<script src="//yihui.name/js/math-code.js"></script>
<script type = "text/x-mathjax-config">
MathJax.Hub.Config({
tex2jax: {
inlineMath: [['$', '$']],
}
})
</script>
<script async
src="//cdn.bootcss.com/mathjax/2.7.1/MathJax.js?config=TeX-MML-AM_CHTML">
</script>

# Description   

This function displays $d\_{g}$ corrected and the non-central confidence interval for independent t.

The formula for $d\_{g}$ is: $$d\_{g} = \frac{M_1 - M_2}{SD_{pooled}}*(1-\frac{3}{4*(N_1+N_2)-9})$$

The formula for *t* is: $$t = \frac{M\_{1} - M\_{2}}{SE\_{pooled}}$$

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

A forensic psychologist conducted a study to examine whether being hypnotized during recall affects how well a witness can remember facts about an event. Eight participants watched a short film of a mock robbery, after which each participant was questioned about what he or she had seen. The four participants in the experimental group were questioned while they were hypnotized and gave 14, 22, 18, and 17 accurate responses. The four participants in the control group gave 20, 25, 24, and 23 accurate responses. The data are available on [GitHub](https://github.com/doomlab/shiny-server/tree/master/MOTE/examples). Example output from JASP, SPSS, and SAS are shown below.

**JASP**
![Independent t JASP](https://raw.githubusercontent.com/doomlab/shiny-server/master/MOTE/examples/independent%20t%20JASP.png)

**SPSS**
![Independent t SPSS](https://raw.githubusercontent.com/doomlab/shiny-server/master/MOTE/examples/independent%20t%20SPSS.png)

**SAS**
![Independent t SAS](https://raw.githubusercontent.com/doomlab/shiny-server/master/MOTE/examples/independent%20t%20SAS.PNG)

# Function in R: 

g.ind.t(m1 = 17.75, m2 = 23, sd1 = 3.304, sd2 = 3.304, n1 = 4, n2 = 4, a = 0.05)

# MOTE

## Screenshot

![Independent t - Means Screenshot](../images/indtg.jpg)

## Effect Size:

$d\_{g}$ = -1.64, 95% CI [-3.10, -0.09]

## Interpretation: 

Your confidence interval does not include zero, and therefore, you might conclude that this effect size is different from zero.

## Summary Statistics: 

*M* = 17.75, *SD* = 3.30, *SE* = 1.65, 95% CI [12.49, 23.01]

*M* = 23.00, *SD* = 2.16, *SE* = 1.08, 95% CI [19.56, 26.44]

## Test Statistic: 

*t*(6) = -2.66, *p* = .038

## Interpretation: 

Your p-value is less than the alpha value, and therefore, this test would be considered statistically significant.

# Tutorial

<iframe width="560" height="315" src="https://www.youtube.com/embed/kH3UOoFh9Ng" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>
