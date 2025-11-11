# Report

*Please be concise, but include essential elements such as analyses, figures, and explanations that support your answers to the questions.*

## Part I

**Question 1**

Which expression did you reach for the truncation error of the Crank-Nicolson scheme?

Copy here your answer of Task 1.1.

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
\begin{align}
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
\end{align}
$$

Note that we have used the following expressions here:

$$
  {\color{red} y_t = \lambda \, y} \quad \Rightarrow \quad {\color{green} y_{tt} = \lambda \, y_t}
$$

so that the first two colored terms can be cancelled.
% solution_end

**Question 2**

Given the test equation

$$
  \frac{dy}{dt} = \lambda y
$$

Why does $\lambda$ have to be negative?

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

**Question 3**

Provide a brief explanation with two figures from Tasks 1.3 and 1.4 on how you arrived at the final time steps of both Crank-Nicolson and forward Euler schemes in such a way that they are sufficiently accurate.
Base your explanation on the concept of *order of accuracy*.

## Part II

The following five questions are related to Task 2.1 of the notebook.
You may copy your answers from this task directly.

**Question 4**

Which of the schemes has the most numerical diffusion?

% solution_start
The BTCS scheme.
% solution_end

**Question 5**

For what value of $\theta$ is the numerical diffusion the largest?

% solution_start
$\theta = 1$.
% solution_end

**Question 6**

For what value of $\theta$ is there no numerical diffusion?

% solution_start
$\theta = \frac12$.
% solution_end

**Question 7**

Which of the two contributions to numerical diffusion has the largest impact?
- the first order upwind scheme or
- the $\theta$-method

% solution_start
The $\theta$-method.
% solution_end

**Question 8**

Which of the schemes gives a non-negative solution?

% solution_start
The FTBS scheme. (Note: other schemes produce negative values in the front of the solution!)
% solution_end

## Part III

**Question 9**

Provide here a figure of the results according to Task 3.1.

What is the mesh P&eacute;clet number?

**Question 10**

Provide here two figures from Tasks 3.2 and 3.3, respectively.

Derive the stability limit for the FTCS scheme. Show your derivation!

Provide here your explanation and conclusions based on your findings.

**Question 11**

Provide here two figures from Tasks 3.4 and 3.5, respectively.

Derive the stability limit for the FTBS scheme. Show your derivation!

Provide here your explanation and conclusions based on your findings.

**Question 12**

Provide a figure that shows three stable numerical solutions of the advection-diffusion equation with $v= 0.35$ m/s and $K = 55$ m<sup>2</sup>/s, namely,
- the one obtained from Crank-Nicolson with central differences (Task 3.1),
- the one obtained from stable FTCS scheme (Task 3.3), and
- the one obtained from stable FTBS scheme (Task 3.5).

Answer the following questions.

1. Which of the schemes is the most accurate one? Why?
2. Which of the numerical solutions has the largest maximum? Why?

% solution_start
1. The Crank-Nicolson scheme because it is second order accurate both in time and space and does not contain numerical diffusion.
2. The FTCS scheme because the forward Euler scheme produces *negative* amount of diffusion which implies a larger maximum.
% solution_end

**End of file.**
