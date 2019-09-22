[Think Stats Chapter 4 Exercise 2](http://greenteapress.com/thinkstats2/html/thinkstats2005.html#toc41) (a random distribution)

>> random_numbers = np.random.random(1000)
pmf = thinkstats2.Pmf(random_numbers)
thinkplot.Pmf(pmf, linewidth=0.1)
thinkplot.Config(xlabel='Random variate', ylabel='PMF')
#There are too many values in the PMF, making the probability associated with each value smaller and the effect of random noise larger. Additionally, because the probability of each value in this generated random sample is uniform, all of the 1000 values have the same probability--which is why the PMF appears to be a straight line across the value 0.001.
cdf = thinkstats2.Cdf(random_numbers)
thinkplot.Cdf(cdf)
thinkplot.Config(xlabel='Random variate', ylabel='CDF')
#Conversely, it is much easier to confirm that the distribution is uniform using the CDF with so many sample values because the approximately straight line shows that about 10% of the sample is below the 10th percentile, etc. If there were more common values in any percentile rank, the CDF shape would be a steep vertical line, while fewer values would be represented by a flat horizontal section of the CDF curve.
