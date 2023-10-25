# Variance matters
Simple notebook where are proposed three methodoloy to model vaiance of a regression model.
The interesting part is how Model 2 and Model 3 handle the constraint of having positive values when dealing with variance prediction

1. Constant variance
2. Varinace modeled by a spline model always positive by costruction
3. Variance modeled by a spline model positive thank to a penalization term in likelihood function


## Model 1
$$
\begin{align}
y & ∼N(μ(x),σ) \\
m(x)& = Spline(x) \cdot \beta + c \\
\beta & \sim \mathcal{N}(0, 1)^n \\
c & \sim \mathcal{N}(0, 1)\\
\sigma & \sim \mathcal{HN}(0, 1)\\
\end{align}
$$


## Model 2
$$
\begin{align}
y & ∼N(μ(x),σ(x)) \\
m(x) & = Spline(x) \cdot \beta_\mu + c_\mu \\
\sigma(x) & = Spline(x) \cdot \beta_\sigma + c_\sigma \\
\beta_\mu & \sim \mathcal{N}(0, 1)^n \\
c_\mu & \sim \mathcal{N}(0, 1) \\
\beta_\sigma & \sim \mathcal{HN}(0, 1)^n \\
c_\sigma & \sim \mathcal{HN}(0, 1)
\end{align}
$$


## Model 3
$$
\begin{align}
y & ∼N(μ(x),σ(x)) +\mathcal{P}(\sigma(x))\\
m(x) & = Spline(x) \cdot \beta_\mu + c_\mu \\
\sigma(x) & = Spline(x) \cdot \beta_\sigma + c_\sigma \\
\mathcal{P}(\sigma(x)) & = -P  \cdot \mathcal{1}(\sigma(x) < 0) \hspace{0.5cm} P \gg 1\\
\beta_\mu & \sim \mathcal{N}(0, 1)^n \\
c_\mu & \sim \mathcal{N}(0, 1) \\
\beta_\sigma & \sim \mathcal{HN}(0, 1)^n \\
c_\sigma & \sim \mathcal{HN}(0, 1)
\end{align}
$$
