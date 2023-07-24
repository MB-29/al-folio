---
layout: page
title: Adaptive exploration of physical systems
description: A lightweight information maximization policy.
img: /assets/img/exploration/pendulum_trajectory.gif
importance: 1
category: work
---
<!-- <div style="text-align: center"> -->

<!-- #### Online greedy identification of linear dynamical systems, in [CDC2022](https://cdc2022.ieeecss.org/) | [[Paper]](https://arxiv.org/abs/2204.06375) | [[Code]](https://github.com/MB-29/greedy-identification) 

#### FLEX: an Adaptive Exploration Algorithm for Nonlinear Systems, in [ICML2023](https://icml.cc/Conferences/2023) | [[Paper]](https://arxiv.org/abs/2304.13426) | [[Code]](https://github.com/MB-29/exploration) 

#### [Matthieu Blanke](https://mb-29.github.io/), [Marc Lelarge](https://www.di.ens.fr/~lelarge/) -->
<!-- </div> -->

<!-- 

  <h4 style="text-align: center">
  Online greedy identification of linear dynamical systems 
  </h4>
  <h5 style="text-align: center">
  Matthieu Blanke, Marc Lelarge
  </h5>
  <h6 style="text-align: center">
  Inria Paris, DI ENS, PSL Research University
  </h6>
  <h5 style="text-align: center">
  in  
  CDC2022
  |
  <a href="https://arxiv.org/abs/2204.06375"> [Paper]</a> |
  <a href="https://github.com/MB-29/greedy-identification"> [Code]</a> 
  </h5>
  <h5 style="text-align: center">
  in
  ICML2023
   |
  <a href="https://arxiv.org/abs/2304.13426"> [Paper]</a> |
  <a href="https://github.com/MB-29/exploration"> [Code]</a> |
  <a href="https://www.youtube.com/watch?v=hGpkdz8-8vU"> [Demo]</a>   
  </h5>
  ---
  
-->

  <h4 style="text-align: center">
  FLEX: an Adaptive Exploration Algorithm for Nonlinear Systems
  </h4>
  <h5 style="text-align: center">
  Matthieu Blanke, Marc Lelarge
  </h5>
  <h6 style="text-align: center">
  Inria Paris, DI ENS, PSL Research University
  </h6>   
  <h5 style="text-align: center">
    
  <br>
  
  <!-- conference -->
  <a href="https://icml.cc/Conferences/2023/Dates"
   class="external-link dark-button">
  <span class="icon">
  <i class="far fa-images"></i>
  </span>
  <span>ICML2023</span>
  </a>
  <!-- paper -->
  <a href="https://arxiv.org/abs/2304.13426"
   class="external-link dark-button">
  <span class="icon">
  <i class="ai ai-arxiv"></i>
  </span>
  <span> Paper </span>
  </a>
  <!-- code -->
  <a href="https://github.com/MB-29/exploration"
   class="external-link dark-button">
  <span class="icon">
  <i class="fab fa-github"></i>
  </span>
  <span> Code </span>
  </a>
  <!-- demo -->
  <a href="https://www.youtube.com/watch?v=hGpkdz8-8vU"
   class="external-link dark-button is-normal is-rounded is-dark">
  <span class="icon">
  <i class="fab fa-youtube"></i>
  </span>
  <span> Demo </span>
  </a>
  </h5>

<!-- --- -->

  <!-- <h5 style="text-align: center">
  <a href="https://mb-29.github.io/"> Matthieu Blanke</a> |
  <a href="https://www.di.ens.fr/~lelarge/"> Marc Lelarge</a> 
  </h5> -->

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/exploration/random_flex.gif" title="flex_vs_random" class="img-fluid rounded" %}
    </div>
</div>

<h5 style="text-align: center">
Abstract
</h5>

Model-based reinforcement learning is a powerful tool, but collecting data to fit an accurate model of the system can be costly. Exploring an unknown environment in a sample-efficient manner is hence of great importance. However, the complexity of dynamics and the computational limitations of real systems make this task challenging. In this work, we introduce FLEX, an exploration algorithm for nonlinear dynamics based on optimal experimental design. Our policy maximizes the information of the next step and results in an adaptive exploration algorithm, compatible with generic parametric learning models and requiring minimal resources. We test our method on a number of nonlinear environments covering different settings, including time-varying dynamics. Keeping in mind that exploration is intended to serve an exploitation objective, we also test our algorithm on downstream model-based classical control tasks and compare it to other state-of-the-art model-based and model-free approaches. The performance achieved by FLEX is competitive and its computational cost is low. 


<section class="section" id="BibTeX">
  <div class="container is-max-desktop content">
    <h5 class="title">BibTeX</h5>
    <pre><code>@article{blanke2023flex,
  title={FLEX: an Adaptive Exploration Algorithm for Nonlinear Systems},
  author={Blanke, Matthieu and Lelarge, Marc},
  journal={International Conference on Machine Learning, 2023},
  year={2023}
}
</code></pre>
  </div>
</section>




<h5 style="text-align: center">
Results
</h5>

<h6 style="text-align: center">
Pendulum
</h6>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/exploration/pendulum.gif" title="pendulum" class="img-fluid rounded" %}
    </div>
</div>

<h6 style="text-align: center">
Cartpole
</h6>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/exploration/cartpole.gif" title="cartpole" class="img-fluid rounded" %}
    </div>
</div>

<h6 style="text-align: center">
Quadrotor
</h6>

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/exploration/quadrotor.gif" title="quadrotor" class="img-fluid rounded" %}
    </div>
</div>


<h5 style="text-align: center">
Exploration
</h5>

A sailor wants to explore the world aboard his boat. How should he choose his course in order to map the world as quickly as possible, based on what he observes along the way? This question sums up the problem of exploration, which arises in a similar way in the learning of physical systems, where the aim is to learn the dynamics of the system with as few experiments as possible.

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
        {% include figure.html path="assets/img/exploration/pendulum_map.png" title="pendulum_map" class="img-fluid rounded " %}
    </div>
</div>
<div class="caption">
    The damped simple pendulum and its phase portrait. In our analogy, the ship is the pendulum, the captain is the reinforcement learning agent, the world to map is the pendulum's phase portrait and the rudder is the torque applied to the ship.
</div>

## Exploring an unknown environment
Exploration is a central question in reinforcement learning, as the agent needs to learn about the environment before solving a control task. Even though prior theoretical knowledge might provide a model of the system, the model must always be adjusted with experimental data to be as faithful to reality as possible. Collecting observations to fit an accurate model
of the system can be costly:  consider for example an aircraft system, for which
running experiments costs a lot of energy and time. In this regard, active exploration (or system identification) aims at exciting the system in order to collect informative data and learn the system globally in a sample-efficient manner, prior to any control task.


