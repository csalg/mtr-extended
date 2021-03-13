I introduced the Memory-Tracing Regression procedure in my paper presented at CSCWD 2021. For my masters thesis, I use this work and then address some of its shortcomings with some new ideas. This repository contains this extended work. When I am finished, it will be possible to reproduce all the figures in the thesis by running the notebook.

## Contributions
1. *Online re-weighing* In general, users will have very different memory strengths for different languages, so in fact the weights should be calculated for each user/language pair. There is another problem: the skill level of users will evolve in the language with time, so weights will also be expected to change. These two problems are related: there is a need to evolve the weights as the users progress in their language learning journey. This can be done very easily by using online regression techniques like stochastic gradient descent. To evaluate, we can train the model on some users and evaluate on others or something like that. The goal is to show adaptability and generalization ability.

2. *Weighted loss*. In the paper, I just used linear regression to fit the weights, but an interesting idea to explore is the use of weighted losses, since I am already using weighted residuals for evaluation. This might backfire, though, e.g. suddenly the model learns to be very pessimistic or optimistic. 

3. *Aggregation by proximity* The least important shortcoming of the paper is the aggregation procedure. The aggregation itself is fine, but it currently aggregates all events within a certain time window. It would be better to aggregate events that happen no more than T time apart.

## Figures
*Online re-weighing*
- The effectiveness of this is actually difficult to test.
- To show that this thing works well, we would need to show that it either converges or improve to the same error rate as an offline procedure. It would be computationally very expensive, but it is also the sort of thing that we can do with a small dataset.
- Suppose we find out the weights from a small sample size of the points (e.g. 1%). Then, for each new datapoint we recalculate the error rate after refitting everything and after using online stochastic descent. This would be a graph. It would show that as an online procedure it doesn't work too badly.
- We can do the same using individual models (as opposed to population models). I would imagine that in this case there is a chance that SGD outperforms offline fitting, because the weights themselves are actually changing.
- The next step would be to vary the step size. Which step size reduces the average error rate the most? 
- Then there could be some figures which show how the different variations perform.
- What are the variants? It depends on the variables: whole population vs individual, offline vs online, unweighted vs weighted loss.
So there are many possible figures for this:
- Results of fitting the different variables (8 possibilities).

*Weighted loss*
- Some plots of curves fit using weighted and unweighted loss.

*Aggregation by proximity*
- A histogram of the score distribution for both variants.
- A plot of the number of events per score and the number of scores.
- Plots with examples of the two clustering strategies for intuition.


