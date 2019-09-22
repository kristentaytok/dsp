[Think Stats Chapter 3 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2004.html#toc31) (actual vs. biased)

>> resp = nsfg.ReadFemResp()
pmf = thinkstats2.Pmf(resp.numkdhh, label='actual number of children')
def BiasPmf(pmf, label):
    new_pmf = pmf.Copy(label=label)

    for x, p in pmf.Items():
        new_pmf.Mult(x, x)
        
    new_pmf.Normalize()
    return new_pmf
biased_pmf = BiasPmf(pmf, label='observed (biased)')
thinkplot.PrePlot(2)
thinkplot.Pmfs([pmf, biased_pmf])
thinkplot.Config(xlabel='Family household size', ylabel='PMF')
print('Actual mean', pmf.Mean())
print('Observed mean', biased_pmf.Mean())
Actual mean 1.024205155043831
Observed mean 2.403679100664282

#The "class size paradox" appears in this survey for number of children under 18 in the respondents' households. Because families with many children are more likely to appear in our sample, while familes with no children have no chance of being in the sample, the observed distribution is biased and skewed to look more "normal" than the actual distribution--which is calculated by dividing the probability of each family size by the number of respondents who observe that family size. The actual, unbiased result has a much lower mean than the observed "survey" data would show.  
