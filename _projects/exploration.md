---
layout: page
title: exploration
description: a project with a background image
img: /assets/img/publication_preview/pendulum.gif
importance: 1
category: work
header-includes:
  - \usepackage{algorithm2e}
---

# Adaptive exploration of physical systems



## Exploring an unknown system


In nonlinear dynamical systems, the state $$x \in \mathbb{R}^d$$ and the input $$u \in \mathbb{R}^m$$ are governed by an equation of the form
\begin{equation}
        \frac{\mathrm{d} x}{\mathrm{d} t}  = f_\star(x, u),
    \label{eq:controlled_dynamics}
\end{equation}
where $$f_\star$$ is a nonlinear function modeling the dynamics. This function is unknown or partially unknown, and our objective is to learn it from data, with as few samples as possible.
What is observed in practice is a finite number of discrete, noisy observations of the dynamics \eqref{eq:controlled_dynamics}:
\begin{equation}
    \label{eq:dynamics}
    x_{t+1} = x_t + \mathrm{d}t f_\star(x_t, u_t) + w_t, \quad 0 \leq t \leq T-1,
\end{equation}
where  $$\mathrm{d} t$$ is a known time step, $$T$$ is the number of observations, $$x_t \in \mathbb{R}^{d}$$ is the state vector, $${w_t \sim \mathcal{N}(0, \sigma^2 I_d)}$$ is a normally distributed isotropic noise with known variance $$\sigma^2$$, and the control variables $$u_t \in \mathbb{R}^m$$ are chosen by the agent with the constraint $${\Vert u_t \Vert_2 \leq \gamma}$$. We assume that $$f_\star$$ is a differentiable function.

### Practical considerations

Adaptivity, speed, flexiblity.


## Optimal experimental design


