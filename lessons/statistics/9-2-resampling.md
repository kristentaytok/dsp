[Think Stats Chapter 9 Exercise 2](http://greenteapress.com/thinkstats2/html/thinkstats2010.html#toc90) (resampling)

>> class DiffMeansResample(DiffMeansPermute):
    """Tests a difference in means using resampling."""
    
    def RunModel(self):
        """Run the model of the null hypothesis.

        returns: simulated data
        """
        group1 = np.random.choice(self.pool, self.n, replace=True)
        group2 = np.random.choice(self.pool, self.m, replace=True)
        return group1, group2
        
    def RunResampleTest(firsts, others):
    """Tests differences in means by resampling.

    firsts: DataFrame
    others: DataFrame
    """
    data = firsts.prglngth.values, others.prglngth.values
    ht = DiffMeansResample(data)
    p_value = ht.PValue(iters=10000)
    print('\ndiff means resample preglength')
    print('p-value =', p_value)
    print('actual =', ht.actual)
    print('ts max =', ht.MaxTestStat())

    data = (firsts.totalwgt_lb.dropna().values,
            others.totalwgt_lb.dropna().values)
    ht = DiffMeansPermute(data)
    p_value = ht.PValue(iters=10000)
    print('\ndiff means resample birthweight')
    print('p-value =', p_value)
    print('actual =', ht.actual)
    print('ts max =', ht.MaxTestStat())

RunResampleTest(firsts, others)

diff means resample preglength
p-value = 0.1674
actual = 0.07803726677754952
ts max = 0.21393028325881147

diff means resample birthweight
p-value = 0.0003
actual = 0.12476118453549034
ts max = 0.1335955672457132

#The difference in means of birth weight using a simulation of the null hypothesis by permutation (i.e., using the observed values as an estimate of the entire population, and randomly assign the members of the population to the two groups) had a difference of 0.12 lbs with a p-value < 0.001, which was statistically significant. The difference in means of birth weight calculated by resampling (i.e., using a sample to estimate the distribution for a population, then draw a random sample from that estimated distribution with the same length, with replacement) was similar: difference of ~ 0.12 with p-value = 0.0003. In both cases, the results were similar and p-values were statistically significant. The difference in means of pregnancy length calculated by resampling was 0.078 and the p-value using this model was 0.1674--which is not statistically significant. For these particular case uses, the two models yielded similar results and p-values. 
