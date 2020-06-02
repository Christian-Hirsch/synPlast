# A Random Network Model for Synaptic Plasticity
[This notebook](./simulation.ipynb) provides Python code for simulating a [A spatial Small-World model for synaptic plasticity arising from activity-based reinforcement](https://link.springer.com/chapter/10.1007/978-3-030-25070-6_8).

<p align="center">
<img src="evolFig.gif" /></a>
</p>

We consider a conceptually simplified random network model for the phenomenon of [synaptic plasticity](https://en.wikipedia.org/wiki/Synaptic_plasticity). We model the synaptic weight by a stochastic process on a fixed graph <img src="http://latex.codecogs.com/svg.latex?G = (V, E)" />  thought of as a collection of neurons interconnected by synapses.

More precisely, consider the set of neurons <img src="http://latex.codecogs.com/svg.latex?V = \mathbb{Z} \times \mathbb{Z}_{\ge 0}" /> , which we think of copies of <img src="http://latex.codecogs.com/svg.latex?\mathbb{Z}" />  organized in layers. The set of synapses <img src="http://latex.codecogs.com/svg.latex?E " /> is obtained by connecting each neuron <img src="http://latex.codecogs.com/svg.latex?(k, h)" />  in layer <img src="http://latex.codecogs.com/svg.latex?h \ge 0 " />  to all neurons of the form  <img src="http://latex.codecogs.com/svg.latex?(\ell, h + 1)" /> with <img src="http://latex.codecogs.com/svg.latex?|\ell - k| \le" /><img src="http://latex.codecogs.com/svg.latex?a^h" /> for a model parameter <img src="http://latex.codecogs.com/svg.latex? a > 1" /> . Loosely speaking, <img src="http://latex.codecogs.com/svg.latex?a" />  governs the speed at which the visibility scope of a neuron increase, when moving to higher layers.

Additionally, the neurons feature iid heavy-tailed fitnesses <img src="http://latex.codecogs.com/svg.latex?\{F_v\}_v" /> with a tail index <img src="http://latex.codecogs.com/svg.latex?\gamma < 1" /> . 

On this marked network, we now define dynamically evolving synaptic weights <img src="http://latex.codecogs.com/svg.latex?\{W_t(e)\}_{e, t}" />  as follows. Each of the neurons is equipped with a Poisson clock. When the clock rings at neuron <img src="http://latex.codecogs.com/svg.latex?v " /> at time <img src="http://latex.codecogs.com/svg.latex?t \ge 0" /> , then the corresponding neuron fires and the weight of one of the incident synapses (v, w) leading to the next layer increases by 1. The crux of the model lies in the selection mechanism. The selection of the synapse occurs at random with probability proportional to 
<img src="http://latex.codecogs.com/svg.latex?F_wW_t(v, w)^\beta." /> 

Hence, the model incorporates two effects. First, the fitter the neuron, the higher the probability that it is selected. Second, if a synapse was used frequently in the past, then it means that it is of importance and should be selected again with a higher probability in the future.

