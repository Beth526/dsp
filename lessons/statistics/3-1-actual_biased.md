[Think Stats Chapter 3 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2004.html#toc31) (actual vs. biased)


Something like the class size paradox appears if you survey children and ask how many children are in their family. Families with many children are more likely to appear in your sample, and families with no children have no chance to be in the sample.
Use the NSFG respondent variable NUMKDHH to construct the actual distribution for the number of children under 18 in the household.

Now compute the biased distribution we would see if we surveyed the children and asked them how many children under 18 (including themselves) are in their household.

Plot the actual and biased distributions, and compute their means. As a starting place, you can use chap03ex.ipynb. 

Answer: The mean of the unbiased PMF is 1.02 and the mean of the biased PMF is 2.40. This is more than twice as large because of the bias.




Code:
```{python}

resp = nsfg.ReadFemResp()

pmf = thinkstats2.Pmf(resp.numkdhh)


thinkplot.Pmf(pmf, label="unbiased")
thinkplot.Config(xlabel='Number of children', ylabel='PMF')

def BiasPmf(pmf, label):
    new_pmf = pmf.Copy(label=label)

    for x, p in pmf.Items():
        new_pmf.Mult(x, x)
        
    new_pmf.Normalize()
    return new_pmf
    
biased = BiasPmf(pmf, label='biased')


thinkplot.PrePlot(2)
thinkplot.Pmfs([pmf, biased])
thinkplot.Config(xlabel='Number of children', ylabel='PMF')

pmf.Mean()

biased.Mean()
```
    
 


