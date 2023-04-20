---
layout: page
title: project 1
description: a project with a background image
img: /assets/img/pendulum.gif
importance: 1
category: work
header-includes:
  - \usepackage{algorithm2e}
---

# Adaptive exploration of physical systems



## Exploring an unknown system

In nonlinear dynamical systems, the state $x \in \R^d$ and the input $u \in \R^m$ are governed by an equation of the form
$$
        \frac{\mathrm{d} x}{\mathrm{d} t}  = f_\star(x, u),
$$
where $f$ is a nonlinear function modeling the dynamics. This function is unknown or partially unknown, and our objective is to learn it from data, with as few samples as possible.
What is observed in practice is a finite number of discrete, noisy observations of the dynamics:
$$
    x_{t+1} = x_t + \mathrm{d} t f(x_t, u_t) + w_t, \quad 0 \leq t \leq T-1,
$$
where  $\mathrm{d} t$ is a known time step, $T$ is the number of observations, $x_t \in \R^{d}$ is the state vector, ${w_t \sim \mathcal{N}(0, \sigma^2 I_d)}$ is a normally distributed isotropic noise with known variance $\sigma^2$, and the control variables $u_t \in \R^m$ are chosen by the agent with the constraint ${\Vert u_t \Vert_2 \leq \gamma}$. We assume that $f$ is a differentiable function.

A more general desciption would take the form
$$x_{t+1} = F_\star(x_t, u_t)$$ 
$$y_t = G_\star(x_t) + w_t.$$



## Optimal experimental design

# Algorithm 1
Just a sample algorithmn
\begin{algorithm}[H]
\DontPrintSemicolon
\SetAlgoLined
\KwResult{Write here the result}
\SetKwInOut{Input}{Input}\SetKwInOut{Output}{Output}
\Input{Write here the input}
\Output{Write here the output}
\BlankLine
\While{While condition}{
    instructions\;
    \eIf{condition}{
        instructions1\;
        instructions2\;
    }{
        instructions3\;
    }
}
\caption{While loop with If/Else condition}
\end{algorithm} 
