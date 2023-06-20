---
layout: page
title: Exploration
description: A fast and efficient search for maximal information.
img: /assets/img/publication_preview/pendulum.gif
importance: 1
category: work
---

<div style="text-align: center">

#### Online greedy identification of linear dynamical systems, in [CDC2022](https://cdc2022.ieeecss.org/) | [[Paper]](https://arxiv.org/abs/2204.06375) | [[Code]](https://github.com/MB-29/greedy-identification) 

#### FLEX: an Adaptive Exploration Algorithm for Nonlinear Systems, in [ICML2023](https://icml.cc/Conferences/2023) | [[Paper]](https://arxiv.org/abs/2304.13426) | [[Code]](https://github.com/MB-29/exploration) 

#### [Matthieu Blanke](https://mb-29.github.io/), [Marc Lelarge](https://www.di.ens.fr/~lelarge/)
</div>



<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/exploration/magellan.jpg" title="magellan" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/exploration/map.jpg" title="map" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Brierly, O. W., iscovery of the Straits of Magellan in 1520, and Frederik De Wit’s 1654 Dutch Sea Atlas. Image courtesy of the Harvard Map Collection.
</div>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/exploration/pendulum_map.png" title="pendulum_map" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    The damped simple pendulum and its phase portrait. In our analogy, the ship is the pendulum, the captain is the reinforcement learning agent, the world to map is the pendulum's phase portrait and the rudder is the torque applied to the ship.
</div>

A sailor wants to explore the world aboard his boat. How should he choose his course in order to map the world as quickly as possible, based on what he observes along the way? This question sums up the problem of exploration [1], which arises in a similar way in the learning of physical systems, where the aim is to learn the dynamics of the system with as few experiments as possible. In this post, we will describe this problem using information theory and experimental design, and then present our results on system identification and exploration in reinforcement learning [2, 3].




## Exploring an unknown environment
Exploration is a central question in reinforcement learning, as the agent needs to learn about the environment before solving a control task. Even though prior theoretical knowledge might provide a model of the system, the model must always be adjusted with experimental data to be as faithful to reality as possible. Collecting observations to fit an accurate model
of the system can be costly:  consider for example an aircraft system, for which
running experiments costs a lot of energy and time. In this regard, active exploration (or system identification) aims at exciting the system in order to collect informative data and learn the system globally in a sample-efficient manner, prior to any control task.
Let us express the problem of exploration of a dynamical system in mathematical terms.

#### Controlled dynamical system
In dynamical systems, the state $$x$$ and the input $$u$$ are governed by an equation of the form
\begin{equation}
        \frac{\mathrm{d} x}{\mathrm{d} t}  = f_\star(x, u),
    \label{eq:controlled_dynamics}
\end{equation}
where $$f_\star$$ is a function modeling the dynamics. This function is unknown or partially unknown, and our objective is to learn it from data, with as few samples as possible.
What is observed in practice is a finite number of discrete, noisy observations of the dynamics \eqref{eq:controlled_dynamics}:
\begin{equation}
    \label{eq:dynamics}
    x_{t+1} = x_t + \mathrm{d}t f_\star(x_t, u_t) + w_t, \quad 0 \leq t \leq T-1,
\end{equation}
where  $$\mathrm{d} t$$ is a known time step, $$T$$ is the number of observations, $$x_t \in \mathbb{R}^{d}$$ is the state vector, $${w_t \sim \mathcal{N}(0, \sigma^2 I_d)}$$ is a normally distributed isotropic noise with known variance $$\sigma^2$$, and the control variables $$u_t \in \mathbb{R}^m$$ are chosen by the agent with the constraint $${\Vert u_t \Vert_2 \leq \gamma}$$. We assume that $$f_\star$$ is a differentiable function.


#### Sequential learning

The dynamics function $$f_\star$$ is learned from past observations with a parametric function $${f}$$, whose parameters are gathered in a vector $$\theta \in \mathrm{R}^n$$. We denote a generic parametric model by a map $${f}(z, \theta)$$.
At each time $$t$$, the observed trajectory yields an estimate $${\theta_{t}= \hat{\theta}(x_{0:t+1}, u_{0:t})}$$ following a learning rule $$\hat{\theta}$$, such as maximum likelihood. At the end of the exploration, the agent returns a final value $$\theta_T$$. Although this learning problem is rich and of an independent interest, we will adopt simple, bounded-memory, online learning rules and focus in on the following decision making process.

#### Sequential decision making problem

The agent's decision takes the form of a policy $${\pi : (x_{0:t},u_{0:t-1}|\theta_t)\mapsto u_t}$$, mapping the past trajectory to the future input, knowing the current parameter $$\theta_t$$.
The goal of active exploration is to choose inputs that make the trajectory as informative as possible for the estimation of $$f_\star$$ with $${f}$$, as stated below.

For an arbitrary learning model of the dynamics $${f}$$ provided with a learning rule $$\hat{\theta}$$ and for a fixed number of observations $$T$$, the goal is to find an exploration policy $$\pi$$ for which the learned model is as close to $$f_\star$$ as possible at the end of exploration. Formally, we define the estimation error of parameter $$\theta$$ as

\begin{equation}
    \label{eq:performance_evaluation}
    \varepsilon(\theta) = \Vert {f}(., \theta) - f_\star \Vert_{L^2},
\end{equation}
and look for a policy yielding the best estimate of $$f_\star$$ at time $$T$$:
\begin{equation}
    \label{eq:exploration_objective}
    \underset{\pi \in \Pi_\gamma}{\min} \quad \mathbb{E} [\varepsilon(\theta_T) | \pi],
\end{equation}

where the expectation is taken over the stochastic dynamics \eqref{eq:controlled_dynamics} and possibly the randomness induced by the policy.

#### Practical constraints
In addition to the sample efficiency objective \eqref{eq:exploration_objective}, an exploration algorithm should satisfy the following practical requirements imposed by real-life applications. *Adaptivity*: as opposed to episodic
planning for which $$\pi(.|θ)$$ remains constant with respect
to $$\theta$$ throughout long time intervals, we want our policy to accommodate to new observations at each time step. *Computational efficiency*: evaluating the policy $$\pi$$ should require limited computational resources. *Flexibility*: our policy
should be valid for a broad class of models $$f$$.


## Information-theoretic view of exploration

We tackle exploration with an information-theoretic point of view, and analyze the choice of inputs through the lense of experimental design. 


$$y_t = f_\star(z_t) + w_t, \quad 0 \leq t \leq T-1$$.
design variables $$z_t \in \mathcal{Z}_t$$, noise  $$w_t \underset{\text{i.i.d}}{\sim} \mathcal{N}(0, \sigma^2)$$, likelihood $$ \ell(y, \theta)  = -\frac{1}{2\sigma^2} \sum\limits_{t=0}^{T-1}
    \left( f(z_t, \theta) -  y_{t}  \right)^2$$ yielding an estimate $$\displaystyle \hat{\theta} \in {\mathrm{argmax}}_\theta \; \ell(\theta)$$. 

*How to choose $$z$$ for an optimal estimation ?*

The **Fisher information** measures the curvature of the likelihood:
  
  $$\displaystyle I(y, \theta) := -\frac{\partial^2 \ell}{\partial \theta^2} (y, {\theta}) \in \mathrm{R}^{n \times n}$$.


<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/exploration/curvature.png" title="curvature" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

## References

[1] de la Fuente, José Manuel Núñez, and Fernão de Magalhães. Diario de Magallanes: el hombre que lo vio y anduvo todo. Ediciones Doce Calles, 2017.

[2] M. Blanke and M. Lelarge, "Online greedy identification of linear dynamical systems," 2022 IEEE 61st Conference on Decision and Control (CDC), Cancun, Mexico, 2022, pp. 5363-5368, doi: 10.1109/CDC51059.2022.9993030.

[3] M. Blanke and M. Lelarge, "FLEX: an Adaptive Exploration Algorithm for Nonlinear Systems," International Conference on Machine Learning (ICML), Hawaii 2023.

[4] Russ Tedrake. Underactuated Robotics: Algorithms for Walking, Running, Swimming, Flying, and Manipulation (Course Notes for MIT 6.832). Downloaded from https://underactuated.csail.mit.edu/
