---

title: 'Variational Solvers for Irreversile Evolutionary System'
tags:
  - Python
  - evolutions
  - stability
  - bifurcation
  - irreversibility
  - nonlinear
  - nonconvex
  - singular perturbations
authors:
  - name: Andres A Leon Baldelli
    corresponding: true
    orcid: 0000-0002-3019-602X
    equal-contrib: true
    affiliation: 1 # (Multiple affiliations must be quoted)
  - name: Pierluigi Cesana
    equal-contrib: true # (This is how you can denote equal contributions between multiple authors)
    affiliation: 2
affiliations:
 - name: d'Alembert Institute, CNRS, Sorbonne Universités, France
   index: 1
 - name: Kyushu University, Fukuoka, Japan
   index: 2
date: 20 December 2023
# bibliography: paper.bib

---


3,835 words 27,477 characters

# Title
## Stability and Bifurcatons in Irreversible Evolutionary Systems

# Abstract/Summary

Complex evolutionary systems show the coexistence of smooth, incremental, and continuous shifts with abrupt, sudden, and brutal transitions - challenging the axiom "Natura non facit saltus".

We implement, as a numerical platform, a general framework to model and understand the competition (for observability) of smooth continuous incremental transitions and rare, discontinuous events.

Fracture processes are a paradigmatic occurrence of both modes of evolution, whereby smooth, controlled, and incremental propagation of fractures are as commonplace as the sudden appearence of geometrically complex crack patterns, typically driven by brutal transitions.

We confront the study of irreversible evolutionary processes with a general energetic notion of stability, and dedicate this contribution to releasing three nonlinear variational solvers as modular components that adress problems that are general enough to apply,  in principle, to a large variety of applications that may arise in diverse fields of science, including mechanics, technology, economy, and social sciences, ecology and quantum physics.

Our three nonlinear solvers address the solution of i) a variational inequality (akin to an obstacle problem), ii) a variational eigen-inequality in a vector space, and iii) a variational eigen-inequality in a convex cone. 

which address the solution of a system of two inequalities, one representing a (pointwise almost-everywhere) stiff constraint, the other .... a global energy comparison which ultimately plays the role of a selection principle among admissible solutions.

Taking the perspective of an evolution law allows us to investigate, in a variational framework, 
the existence and nature of solutions, their trajectories in phase space, their bifurcations, as well as the stability of states, structures, and evolution paths. 

Our investigation rests upon the application of direct energy methons in the calculus of variations to the study of (rate-indipendent) problems of the evolutionary type.
To fully exploit its variational/energetic mathematical structure, a notion of stability, introduced below, constitutes the core of our variational analysis.
 <!-- of nonlinear which arise from the  ... -->

# Statement of Needs:


# Introduce solvers


The objects `HybridSolver` `BifurcationSolver, StabilitySolver`, and  implementations of 
the following general purpose variational problems:

$$
P_1(E): \text{Find }y\in X: E'(y)(z-y_t)\geq 0, \quad \forall z\in V_0\times K^+_0
$$
<!-- % P_2(E): \text{Find }\lambda, w \in \mathbb R\times X: E''(y)(w, z)=\lambda \langle w, z\rangle , \quad \forall z\in V\times K^+  -->
$$
P_2(E): \text{Find }\lambda, w \in \mathbb R\times X: E''(y)(w, z-y_t)\geq 0, \quad \forall z\in X_0 
$$

$$
P_2^+(E): \text{Find }\lambda, w \in \mathbb R^+\times X: E''(y)(w, z-y_t) 
= \lambda  \langle w, z-y_t\rangle , \quad \forall z\in V_0\times K^+_0 
$$
where $V_t$ is an affine Hilbert space, $V_0$ its associated vector space, $K^+_0$ is the convex cone of positive functions (in a Hilbert space), and
$V_t\times K^+_0$ is a convex set which is the ambient space for admissible perturbations, at time $t$.

We use these three solvers to show the existence of a map
$y_t \in X$ that is *Stable, characterised by the exidtence of a sequence of discrete real numers $\lambda_t > 0$, where
$\lambda_t$ is the smallest eigenvalue in the cone ${K^+_0}$


the main application of ____________ is in the study of evolutionary problems  
functional analysis of problems of bifurcation...posed in spaces of high or infinite dimension.
symmetry brealking bifurcations, 

.. 
simple enough so that it can be understood/played with by ... training extends beyond the classical methods 

nonlinear systems can have surprising and complecated behavuours


the solvers discussed in this contribution can be exgtended or adapted to other evolutionary systems arising from partial differential equations.
formation of spatial patterns in homogeneous systems, biological morophogenesis, discrete-time and discrete-space nonlinear systems (cellular automata) provide models for processes ranging from the micro (particle phusics) to patterned activity... in evolutionary systems

significant in comprehending evolution dynamics of complex systems. 


natural system, physical, chemical, or biological, 
phenomenolofical novelty




## Science

We solve the problem
$$
P(0):\text{ Given } T >0, \text{ find } \text{ IRREVERSIBLE-CONSTRAINED } y_t:(0, T)\mapsto X_t  
\text{ such that}$$ 
$$\text{[Unilateral *Stability]} \qquad E(y) \leq E(y + z), \quad \forall z \in V \times K^+_0$$

From the physical perspective, we are seeking maps: $y_t: [0, T]\mapsto X_t$, that are observable in the sense that are stable with respect to admissible perturbations, within a given horizon of parameters.

In practice, we show the existence
of a quadruple $(y_t, \lambda_t, \rho_t, z_i^*)\in X_t \times \mathbb R^+ \times \{0, 1\}\times V_t\times K^+_0$ for $t\in [0, T]$ such that the problem P(0) is solved. In the solution, $y_t$
is the evolution map, $\lambda_t$ is a scalar whose positivity ensures that 
the inequality in P(0) is verified, $\rho_t$ is a boolean marker that indicates whether or not the evolution map is unique, and  $z^*_i$ is the the optimal perturbation (or instability mode) at the $i$-th stability transition.
In the statement above, $\text{IRREVERSIBLE-CONSTRAINED}$ simply means that the solution .... is such that $\alpha_t \nearrow t$. 

We solve the problem above with the combined use of the variational solvers introduced above, which allow us to provide a numerical proof of sufficiency of the existence of observable solutions for problem P(0) (existence of a $\lambda_t > 0, \forall t$).

### Methods 


## Software

## Validation