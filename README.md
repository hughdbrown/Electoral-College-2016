# Overview
American presidential elections are decided by electoral votes, not
by popular vote. Each electoral district is treated as an independent race
and the winner is the candidate who wins the most electoral votes.

The [website FiveThirtyEight](http://projects.fivethirtyeight.com/2016-election-forecast/)
tracks polls and estimates outcomes by electoral district. It then
appears to run Monte Carlo simulations to estimate the distribution of outcomes in
Electoral College votes, from which it projects a likelihood that each
candidate will win. Those probabilities should be the percentage of
times each candidate won in the simulated elections.

This project repeats the Monte Carlo simulation, given some assumptions
about the data in the FiveThirtyEight HTML file. FiveThirtyEight shows
bars for the range that 80% of election outcomes are expected to come under.
I use this to back out the mean and standard deviation of each
district’s outcome distribution, and using this description of the
distribution, I perform a Monte Carlo simulation.

At least, that is the plan. The simulation produces an improbably
high expectation of victory for Hillary Clinton that does not
match FiveThirtyEight’s simulation results.

# Method
1. Getting the standard deviation and the mean
    Given the left side of the bar and the width, and knowing that 
    the bar represents 80% of the outcomes, I set the mean to the midpoint
    of the bar and set the standard deviation to the width of the bar
    divided by the symmetric Z-score that captures 80% of outcomes (i.e.
    2 * 1.2816).
2. Getting the probability of victory
    Given the mean, standard deviation, and the estiomated position
    of the 50% mark, I back out the Z-score that the candidate’s
    opponent’s popular vote must be below for the candidate to win.
    Given this Z-score, I can back out the probability of victory
    for the candidate.
3. Simulating the districts
    Given the probability of winning for the candidate in each district,
    I sample from a linear distribution from 0 to 1. In the cases that
    a random linear variable exceeds the candidate’s probability of winning,
    the candidate loses that district. If the random linear variable is 
    below, then the candidate wins that district.
4. The distribution of outcomes
    Having run the simulation millions of times, we obtain a distribution
    of electoral college results that we can plot. The count of outcomes
    are normalized against the number of simulations to produce 
    projected Electoral College votes on the x-axis and the probability
    of that outcome on the y-axis.
