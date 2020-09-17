[Think Stats Chapter 2 Exercise 4](http://greenteapress.com/thinkstats2/html/thinkstats2003.html#toc24) (Cohen's d)

Using the variable totalwgt_lb, investigate whether first babies are lighter or heavier than others. Compute Cohen’s d to quantify the difference between the groups. How does it compare to the difference in pregnancy length?

The Cohen's d for weight between the first born group and the other births group was -0.0887. This is a measure of effect size, and it says that the mean birth weight in the other births group was 0.0887 units of pooled standard deviation lower than the mean birth weight in the first borns group. This is not a significant difference.

The Cohen's d for pregnancy length between the first born group and the other births group was 0.0289. This is also not a very big difference and not significant.

                                   
Code:                              
```{python}                               

import os

os.chdir('/Users/beth/Documents/Metis/ThinkStats/ThinkStats2/code')

import thinkstats2

import math

import nsfg

preg = nsfg.ReadFemPreg()
live = preg[preg.outcome == 1 ]


preg = nsfg.ReadFemPreg()
live = preg[preg.outcome == 1 ]

firsts = live[live.birthord == 1]
others = live[live.birthord != 1]


first_weight=firsts.totalwgt_lb
other_weight=others.totalwgt_lb

first_length=firsts.prglngth
other_length=others.prglngth


def CohenEffectSize(group1, group2):
    diff = group1.mean() - group2.mean()

    var1 = group1.var()
    var2 = group2.var()
    n1, n2 = len(group1), len(group2)

    pooled_var = (n1 * var1 + n2 * var2) / (n1 + n2)
    d = diff / math.sqrt(pooled_var)
    return d


CohenEffectSize(first_weight, other_weight)

CohenEffectSize(first_length, other_length)

```
                                   
                                   

