---
title: "singletM_code"
author: "Erin M. Buchanan"
date: "3/17/2018"
output: 
  html_document:
        self_contained: no
---
 
The formula for d is: $$d = \frac{t}{\sqrt{N}}$$
 
The formula for t is: $$t = \frac{M_1 - M_2}{SE_{differences}}$$
 
The code to use MOTE in R is: 
 

 
<h2>d.dep.t.diff</h2>  <h3>Description</h3>  <p>This function displays d for repeated measures data and the non-central confidence interval using the  standard deviation of the differences as the denominator estimating from the t-statistic. </p>   <h3>Usage</h3>  <pre> d.dep.t.diff.t(t, n, a = 0.05) </pre>   <h3>Arguments</h3>  <table summary="R argblock"> <tr valign="top"><td><code>t</code></td> <td> <p>t-test value</p> </td></tr> <tr valign="top"><td><code>n</code></td> <td> <p>sample size</p> </td></tr> <tr valign="top"><td><code>a</code></td> <td> <p>significance level</p> </td></tr> </table>   <h3>Examples</h3>  <pre> d.dep.t.diff.t(t = 5, n = 100, a = .05) </pre>   </body></html> 