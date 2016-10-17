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
