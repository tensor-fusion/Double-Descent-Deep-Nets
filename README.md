# Double descent experiments

![](/output/polynomial_double_descent.gif)

In this repo I'm trying to reproduce some double descent results from several papers:
- **Double Descent Demystified: Identifying, Interpreting & Ablating the Sources of a Deep Learning Puzzle**: https://arxiv.org/abs/2303.14151
- **Deep Double Descent: Where Bigger Models and More Data Hurt**: https://arxiv.org/abs/1912.02292
- **High-dimensional analysis of double descent for linear regression with random projections**: https://arxiv.org/abs/2303.01372
- **More Data Can Hurt for Linear Regression: Sample-wise Double Descent**: https://arxiv.org/abs/1912.07242
- **A U-turn on Double Descent: Rethinking Parameter Counting in Statistical Learning**: https://arxiv.org/abs/2310.18988
- **Reconciling modern machine learning practice and the bias-variance trade-off**: https://arxiv.org/abs/1812.11118
- **Double Trouble in Double Descent : Bias and Variance(s) in the Lazy Regime**: https://arxiv.org/abs/2003.01054
- **The generalization error of random features regression: Precise asymptotics and double descent curve**: https://arxiv.org/abs/1908.05355
- **Triple descent and the two kinds of overfitting: Where & why do they appear?** : https://arxiv.org/abs/2006.03509`


Nothing particularly useful here (unless you're interested in double descent).


## Example
Reproducing polynomial regression results from the **Double Descent Demystified** paper:
![](/output/polynomial_double_descent.gif)


Underparameterized regime | Interpolation threshold | Overparameterized regime
:-------------------------:|:-------------------------:|:-------------------------:
![](/output/parameter_count=1/animation.gif)  |  ![](/output/parameter_count=10/animation.gif) |  ![](/output/parameter_count=200/animation.gif) 


# Background

Double descent describes the phenomenon where the error curve of a model as a function of model complexity or size doesn't follow the traditional bias-variance tradeoff U-shaped curve. Instead, after an initial descent (error reduction) and subsequent ascent (error increase due to overfitting), there is a second descent in error even as model complexity continues to grow beyond the interpolation threshold.

# Linear regression example

Given a model's complexity represented by the number of parameters $p$ and training samples $n$, the interpolation threshold is reached when $p$ equals $n$. Traditionally, if $p$ exceeds $n$, models are expected to generalize poorly on new data due to overfitting, but in double descent, as $p$ grows even larger, the generalization error decreases after surpassing the threshold.

Assume a scenario where you fit a polynomial regression model:

$$y_i=f\left(x_i\right)+\epsilon_i$$

where $f(x)$ is the true function, $x_i$ are the data points, $y_i$ are the observed values, and $\epsilon_i$ represents noise. 

As the degree of the polynomial (akin to model complexity) increases, the fit to the training data becomes perfect when the degree $d$ is at least $n-1$. If $d$ surpasses $n-1$, classical theory suggests a blowup in generalization error due to high variance. However, as observed in the double descent phenomena, if $d$ continues to increase significantly beyond $n$, test error decreases again.

