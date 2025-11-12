# Report

*Please be concise, but include essential elements such as analyses, figures, and explanations that support your answers to the questions.*

## Part I

**Question 1** (1 pt)

Which expression did you reach for the truncation error of the Crank-Nicolson scheme?

Copy here your answer of Task 1.1. Including the mathematical formulations is sufficient, but you may want to add comments on what was done for clarity. 

% solution_start

First, we replace the numerical solution $y^n$ by the exact one, that is, $y(t_n)$. Hence, we consider the following equation for
the error analysis

$$
  \frac{y(t_{n+1})-y(t_n)}{\Delta t} = \frac 12 \lambda \left ( y(t_n) + y(t_{n+1}) \right ) + \tau_{\Delta t}
$$

with $\tau_{\Delta t}$ the truncation error.

Next, we expand the function $y(t_{n+1})$ using Taylor series till order 3, as follows

$$
  y(t_{n+1}) = y(t_n) + \Delta t\,y_t(t_n) + \frac 12 \Delta t^2\,y_{tt}(t_n) + \frac 16 \Delta t^3\,y_{ttt}(t_n)
$$

with $y_t$, $y_{tt}$ and $y_{ttt}$ the first, second and third derivatives of $y$ to $t$, respectively.
Note that we have truncated the Taylor series after third order since we expect second order accuracy approximation for the first
derivative (2+1=3).

By substitution we obtain the following expression of the truncation error

$$
\begin{align*}
  \tau_{\Delta t} &= \frac{y(t_{n+1})-y(t_n)}{\Delta t} - \frac 12 \lambda \left ( y(t_n) + y(t_{n+1}) \right ) \\
                  \\
                  &= y_t + \frac 12 \Delta t\,y_{tt} + \frac 16 \Delta t^2\,y_{ttt} -
                  \lambda \left ( y + \frac12 \Delta t\,y_t + \frac 14 \Delta t^2\,y_{tt} + \frac{1}{12} \Delta t^3\,y_{ttt} \right )
                  + \mathcal{O}(\Delta t^4) \\
                  \\
                  &= \left ( {\color{red} y_t - \lambda y} \right ) + \frac 12 \Delta t \left ( {\color{green} y_{tt} - \lambda y_t} \right ) +
                     \Delta t^2 \left ( \frac 16 y_{ttt} - \frac 14 \lambda y_{tt} \right ) + \mathcal{O}(\Delta t^3) \\
                  \\
                  &= \Delta t^2 \left ( \frac 16 y_{ttt} - \frac 14 \lambda y_{tt} \right ) + \mathcal{O}(\Delta t^3) \\
                  \\
                  &= \mathcal{O}(\Delta t^2)
\end{align*}
$$

Note that we have used the following expressions here:

$$
  {\color{red} y_t = \lambda \, y} \quad \Rightarrow \quad {\color{green} y_{tt} = \lambda \, y_t}
$$

so that the first two colored terms can be cancelled.

% solution_end

**Question 2** (0.5 pt)

Given the test equation

$$
  \frac{dy}{dt} = \lambda y
$$

Why does $\lambda$ have to be negative?
Include in your answer what happens to the solution when  $\lambda > 0$ and  $\lambda < 0$.

Write your answer here.

% solution_start

The solution of the test equation is given by

$$
  y(t) = y_0\,e^{\lambda t}
$$

where $y_0$ is the integration constant that can be determined by an initial condition.

Clearly, when $\lambda > 0$ the solution is continuously increasing in such a way that $y(t) \rightarrow \infty$, if $t \rightarrow \infty$.
This implies that the test equation with $\lambda > 0$ is an ill-posed problem. (Its solution is not bounded.)

On the other hand, if $\lambda < 0$, then $y(t) \rightarrow 0$ for $t \rightarrow \infty$, so that the solution remains stable.
Therefore, we required for the above test equation that $\lambda < 0$.

% solution_end

**Question 3** (1 pt)

Provide a brief explanation with two figures from Tasks 1.3 and 1.4 on how you arrived at the final time steps of both Crank-Nicolson and forward Euler schemes in such a way that they are sufficiently accurate.
Base your explanation on the concept of *order of accuracy*. Include any relevant quantitative values and graphs.

% solution_start

The solution to the advection-diffusion equation obtained with the Crank-Nicolson (trapezoidal rule) is depicted in the following
[graph](https://files.mude.citg.tudelft.nl/GA21_task13.png).

The final time step with which the solution has converged was $\Delta t = 500$ s, corresponding to Courant number $\sigma = 2.5$.

With respect to the forward Euler scheme, its solution is plotted
[here](https://files.mude.citg.tudelft.nl/GA21_task14.png).

The final solution was obtained with $\Delta t = 20$ s (the corresponding Courant number is 0.1). Even with that small time step / Courant number the solution is still not *converged* (see the difference in color near the maximum of the profile). This implies that the order of accuracy of the forward Euler scheme is lower than that of the trapezoidal rule. Indeed, the latter scheme is second order in time while the former is first order accurate.

% solution_end

## Part II

The following five questions are related to Task 2.1 of the notebook.
You may copy your answers from this task directly.

% solution_start

See also the following figure of [Task 2.1](https://files.mude.citg.tudelft.nl/GA21_task21.png).

% solution_end

**Question 4** (0.5 pt)

Which of the schemes has the most numerical diffusion?

% solution_start

The BTCS scheme. (This is due to the backward Euler scheme.)

% solution_end

**Question 5** (0.5 pt)

For what value of $\theta$ is the numerical diffusion the largest?

% solution_start

$\theta = 1$. (One can proof that this value corresponding to backward Euler produces the most diffusion.)

% solution_end

**Question 6** (0.5 pt)

For what value of $\theta$ is there no numerical diffusion?

% solution_start

$\theta = \frac12$. (This is general the case.)

% solution_end

**Question 7** (0.5 pt)

Which of the two contributions to numerical diffusion has the largest impact?
- the first order upwind scheme or
- the $\theta$-method

% solution_start

The $\theta$-method. (This is general the case.)

% solution_end

**Question 8** (0.5 pt)

Which of the schemes gives a non-negative solution?

% solution_start

The FTBS scheme. (Note: other schemes produce negative values in the front of the box-profile!)

% solution_end

## Part III

**Question 9** (1 pt)

Provide here a figure of the results according to Task 3.1.
In your answer, comment on the cases without and with diffusion include the corresponding values of $K$.
What is the mesh P&eacute;clet number?

% solution_start

The figure for Task 3.1 is plotted [here](https://files.mude.citg.tudelft.nl/GA21_task31.png).

The case without diffusion ($K=0$) represents a propagated substance along the river as shown by the green curve.
Its shape is fixed throughout the propagation. However, the Crank-Nicolson scheme is not able to conserve this block-shaped profile.
The associated numerical solution contains wiggles as the scheme does not have numerical diffusion.

The case with diffusion ($K = 55$ m<sup>2</sup>/s) represents a propagated substance while it spreads in the river as time proceeds.
So its shape becomes more smooth during its journey through the river and also takes the shape of a Gaussian bell curve.

The Crank-Nicolson scheme seems to be able to reproduce this curve (see blue curve) because the mesh P&eacute;clet number = $0.35 \times 100 / 55$ = 0.64 is less than 2.
Also note that this scheme has no numerical diffusion so the smoothing is caused solely by physical diffusion.

% solution_end

**Question 10** (1 pt)

Provide here two figures from Tasks 3.2 and 3.3, respectively.

% solution_start

The FTCS solution of Task 3.2 is plotted
[here](https://files.mude.citg.tudelft.nl/GA21_task32.png) which is unstable.

The FTCS solution of Task 3.3 is plotted
[here](https://files.mude.citg.tudelft.nl/GA21_task33.png) which is stable.

% solution_end

Derive the stability limit for the FTCS scheme. Show your derivation!

% solution_start

See the MUDE book. The stability condition is given by

$$
  \frac{K\Delta t}{\Delta x^2} \leq \frac12
$$

% solution_end

Provide here your explanation and conclusions based on your findings.
Include any calculations you made to reach your conclusions, and any recommendations for modifying any parameters, if at all. 

% solution_start

With $K = 55$ m<sup>2</sup>/s, $\Delta x = 100$ m and $\Delta t = 0.75\Delta x/v = 0.75 \times 100 / 0.35 = 214.3$ s, we obtain

$$
  \frac{55 \times 214.3}{100^2} = 1.179 > 0.5
$$

This explains the plot of Task 3.2. We should therefore decrease the time step such that the solution becomes stable. It is given by

$$
  \Delta t = \frac{\Delta x^2}{2K} = \frac{100^2}{2 \times 55} = 90.9 \text{s}
$$

and the corresponding solution is plotted above.

% solution_end

**Question 11** (1 pt)

Provide here two figures from Tasks 3.4 and 3.5, respectively.

% solution_start

The FTBS solution of Task 3.4 is plotted
[here](https://files.mude.citg.tudelft.nl/GA21_task34.png) which is unstable.

The FTBS solution of Task 3.5 is plotted
[here](https://files.mude.citg.tudelft.nl/GA21_task35.png) which is stable.

% solution_end

Derive the stability limit for the FTBS scheme. Show your derivation!

% solution_start

The difference with the FTCS scheme here is the addition of the numerical diffusion which is given by

$$
  K_a = \frac 12 v \Delta x
$$

Hence, we should consider the *total* diffusion coefficient of $K + K_a$ instead of just the physical diffusion coefficient $K$.
For instance, the stability condition is like the previous one except that we now have the following condition for FTBS

$$
  \frac{(K+K_a)\Delta t}{\Delta x^2} \leq \frac12
$$

% solution_end

Provide here your explanation and conclusions based on your findings.
Include any calculations you made to reach your conclusions, and any recommendations for modifying any parameters, if at all. 

% solution_start

First, we calculate the amount of numerical diffusion which reads

$$
 K_a = \frac12 v \Delta x = \frac{0.35 \times 100}{2} = 17.5 \text{m}^2/\text{s}
$$

Furthermore, $K = 55$ m<sup>2</sup>/s, so that the total amount of diffusion is 72.5 m<sup>2</sup>/s.
The maximum time step for a stable solution is then

$$
  \Delta t = \frac{\Delta x^2}{2(K+K_a)} = \frac{100^2}{2 \times 72.5} = 69 \text{s}
$$

So, the solution obtained with $\Delta t = 90.9$ s is thus unstable but the solution with a time step of smaller than 69 s is stable.

% solution_end

**Question 12** (1 pt)

Provide a figure that shows three stable numerical solutions of the advection-diffusion equation with $v= 0.35$ m/s and $K = 55$ m<sup>2</sup>/s, namely,
- the one obtained from Crank-Nicolson with central differences (Task 3.1),
- the one obtained from stable FTCS scheme (Task 3.3), and
- the one obtained from stable FTBS scheme (Task 3.5).

% solution_start

The three stable solutions of Tasks 3.1, 3.3 and 3.5 are plotted
[here](https://files.mude.citg.tudelft.nl/GA21_task36.png).

% solution_end

Answer the following questions.

1. Which of the schemes is the most accurate one? Why?
2. Which of the numerical solutions has the largest maximum? Why? You may include numerical values to help illustrate your answer.

% solution_start

The answers are:
1. The Crank-Nicolson scheme because it is second order accurate both in time and space and does not contain numerical diffusion.
2. The FTCS scheme because the forward Euler scheme produces *negative* amount of diffusion which implies a larger maximum.
   
% solution_end

**End of file.**
