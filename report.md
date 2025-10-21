# Report

*Please be concise, but include essential elements such as analyses, figures, and explanations that support your answers to the questions.*

## Part I

**Question 1.1**

*What is the truncation error of the Crank-Nicolson scheme?*

**Question 1.2**

Given the test equation

$$
  \frac{dy}{dt} = \lambda y
$$

*Why does $\lambda$ have to be negative?*

**Question 1.3**

Provide a short explanation with two figures of how you did obtained the final time steps with which the Crank-Nicolson scheme
and the forward Euler scheme are sufficiently accurate. Explain your findings based on the notion of *order of accuracy*.

*What are your conclusions?*

## Part II

**Question 2.1**

*Which of the schemes has the most numerical diffusion?*

**Question 2.2**

*For what value of $\theta$ is the numerical diffusion the largest?*

**Question 2.3**

*For what value of $\theta$ is there no numerical diffusion?*

**Question 2.4**

*Which of the two contributions to numerical diffusion has the largest impact?*
- the first order upwind scheme or
- the $\theta-$method

**Question 2.5**

*Which of the schemes gives a non-negative solution?*

## Part III

**Question 3.1**

Provide a figure of the results according to **Task 3.1**.

*What is the mesh P&eacute;clet number?*

**Question 3.2**

Derive the stability limit for the FTCS scheme and provide a figure of the stable FTCS result with a modified time step.

*Conclusion?*

**Question 3.3**

Derive the stability limit for the FTBS scheme and provide a figure of the stable FTBS result with a modified time step.

*Conclusion?*

**Question 3.4**

Provide a figure that shows three stable numerical solutions of the advection-diffusion equation with $v= 0.35$ m/s and $K = 55$ m$^2$/s, namely,
- the one obtained from Crank-Nicolson with central differences (Task 3.1),
- the one obtained from stable FTCS scheme (Task 3.3), and
- the one obtained from stable FTBS scheme (Task 3.5).

Answer the following questions in your report.

1. *Which of the schemes is the most accurate one? Why?*
2. *Which of the numerical solutions has the largest maximum? Why?*

**End of file.**
