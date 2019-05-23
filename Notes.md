# Translating Portfolio Management into Policy Management

### Price Relative Vector
Rather than looking at available prices, we want Pareto to look at the economic and criminal history as it's context, it's environment. Pareto will then map this context to the best policy levels for a given point in time. 

#### Representing the environment
Take state-level averages. Incorporate existing crime and economic levels, perhaps scaling economic levels gini coefficients, feed them into the model. Keep a state-level binary indicator, along with a year. 
- For every year, we'll loop through every state at least once. While training, we'll let Pareto take as many steps as necessary to learn the maximum reward per year. We'll penalize time spent, but highly reward effective decisions. 
- For each state, we'll pick the single state that is the most valid from a causal estimation point of view. 
- We want one model that learns from every state + policy combination. We will then use this model to generate new state-level decisions. 

#### Determining causal validity
1. Similarity between treatment and control groups at the covariate level. We need the two groups to be statistically similar.
2. Lack of intervening event. We need there to not be a totally different event that contributes to the difference in outcomes, such as differences in weather or availability of transportation that would otherwise contribute to the difference in outcomes, in this case crime. 
3. Evenness of trends prior-to the time of evaluation. It's helpful to see that both groups have similar growth trends in the outcome prior to the time of evaluation. 
4. Lack of fundamental difference in the assignment mechanism. If either group has been created through an underlying assignment mechanism, such as fundamental differences in preferences regarding the outcome. 

#### Limitations in this aproach
1. Accounting for cross-state influences, eg, interstate gun trafficking and exchange. We may be able to overcome this through grouping state-wise analysis into higher level abstractions, such as multi-state conglomerates with similar policy levels. 
2. Considering intervening events. While items 1, 3, and 4 in determining causal validity can be handled through digital and automatic means, considering the intervening event is freqently a matter of local knowledge and economic review. Ideally, we would like to leverage Amazon SageMaker Ground Truth labelling services. 
3. Accounting for differences in state treatment by the federal level. These would be a special type of intervening event that may contribute to differences in economic and crime levels. They would be especially relevant in public policy scenarios, where the inter-dependence of state and federal policy decisions also themselves lead to differences in both outcomes and covariates. 

All three of these potential avenues are worth exploration, but outside the scope of this inital attempt. 





