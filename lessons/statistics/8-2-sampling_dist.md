[Think Stats Chapter 8 Exercise 2](http://greenteapress.com/thinkstats2/html/thinkstats2009.html#toc77) (scoring)

>> REPLACE THIS TEXT WITH YOUR RESPONSE


Suppose you draw a sample with size n=10 from an exponential distribution with λ=2. Simulate this experiment 1000 times and plot the sampling distribution of the estimate L. Compute the standard error of the estimate and the 90% confidence interval.

Repeat the experiment with a few different values of n and make a plot of standard error versus n.

Solution:

standard error of lamda estimated from 1000 n=10 samples was 0.83

the confidence interval is 1.25 to 3.67, 90 percent of estimates of lambda made from sampling this way would fall within this range


I'm not sure how to put a plot in a markdown file 


Code:

```{python}

l=2
n=10
l_estimates=[]
for i in range(1000):
    sample = np.random.exponential(scale=1/l, size=n)
    l_estimate=1/np.mean(sample)
    l_estimates.append(l_estimate)
    
standard_error = np.sqrt(np.mean([(estimate-l)**2 for estimate in l_estimates]))

cdf = thinkstats2.Cdf(l_estimates)

cdf.Percentile(5)

cdf.Percentile(95)
```

    




