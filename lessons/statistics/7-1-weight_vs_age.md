[Think Stats Chapter 7 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2008.html#toc70) (weight vs. age)

>> import first

live, firsts, others = first.MakeFrames()
live = live.dropna(subset=['agepreg', 'totalwgt_lb'])

ages = live.agepreg
weights = live.totalwgt_lb
print('Corr', Corr(ages, weights))
print('SpearmanCorr', SpearmanCorr(ages, weights))

ages = live.agepreg
weights = live.totalwgt_lb
print('Corr', Corr(ages, weights))
print('SpearmanCorr', SpearmanCorr(ages, weights))

Corr 0.06883397035410907
SpearmanCorr 0.09461004109658226

#The scatterplot shows a weak relationship between mother's age and birth weight, as indicated by a large, dense, seemingly-flat line. The correlation values also indicate a low correlation: Pearson's ~ 0.07, Spearman's ~ 0.09. Because this value is close to zero, this is a weak non-linear relationship; differences can be attributed to the influence of outliers affecting Pearson's correlation coefficient, or Pearson's underestimating the strength of this non-linear relationship. This non-linear relationship can be more clearly seen on the percentile plot of weight vs. age because the lines are flat.     
