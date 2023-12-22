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

# Title: 2,536 words 
## Stability and Bifurcatons in Irreversible Evolutionary Systems

## Variational Solvers for Nonlinear Bifurcation and Stability of Irreversible Systems

## Variational Solvers for Irreversible Evolutionary Systems
## Solvers for Irreversible Evolutionary Systems // the example of fracture

# Abstract/Summary

What are the consequences of the well-posedness of a mathematical problem?
Challenging the axiom "Natura non facit saltus", complex evolutionary systems show the coexistence of smooth, incremental, and continuous shifts with abrupt, sudden, and brutal transitions.

Picture Fracture, as a process: a paradigmatic occurrence of both modes of evolution whereby smooth, controlled, and incremental propagation of fractures are as commonplace as the sudden appearence of geometrically complex crack patterns, typically driven by brutal transitions

We implement, as a numerical platform, a general framework to model and understand the competition (for observability) of smooth continuous incremental transitions and rare, discontinuous events.

We confront the study of irreversible evolutionary processes with a general energetic notion of stability, and dedicate this contribution to releasing three nonlinear variational solvers as modular components that adress problems that are general enough to apply,  in principle, to a large variety of applications that may arise in diverse fields of science, including mechanics, technology, economy, and social sciences, ecology and quantum physics.

Our three nonlinear solvers address the solution of i) a variational inequality (akin to an obstacle problem), ii) a variational eigen-inequality in a vector space, and iii) a variational eigen-inequality in a convex cone. 

In practice, we show one stable solution of a system of two inequalities, one representing a (pointwise almost-everywhere) constraint of irreversibility, the other a global energy comparison in a special admissible space, this ultimately plays the role of a selection principle among admissible paths.

Taking the perspective of an evolution law allows us to investigate, in a variational framework, 
the existence and nature of solutions, their trajectories in phase space, their bifurcations, as well as the stability of states, structures, and bifurcation paths. 

Our investigation rests upon the application of direct energy methons in the calculus of variations to the study of (rate-indipendent) problems of the evolutionary type.
To fully exploit the variational/energetic mathematical structure of our problem, the notion of stability, introduced below, constitutes the core of our variational analysis.
From the mechanical perspective, in view of the applications for which these solvers are originally developed, namely a series of experimental validation tests of a variational theory of fracture,  a remark is in order to appreciate some of the difficulties against which we are testing our nonlinear solvers. 
In our conceptual model for the evolution of fractures, damage of the material plays a crucial role. 
As it increases it allows the material to soften. When this happens locally, the consequence is appearence of many energy-minima. This combination of nonconvexity and localisation renders these problems of fracture special instances of singularly-perturbed systems, chacterised by nonlinear  constraints which are typically _unknown_ (because depend on the current state, the _main unkown_) and the sudden appearence of infinite families of possible bifurcation paths among which to select.
The complexity of such systems is such that stability is a property that is difficult to verify - numerically, at large scales and for real structures.

We release our solvers as tools, useful to deploy a fully transparent numerical experimental platform to address the prediction of large scale fracture events. 

Think of Antarctica. [FOOTNOTE:]


<!-- For such systems structural effects play a key role, and stability is a property that is difficult to verify - numerically, at large scales for real structures, and analytically, in the infinite-dimensional framework. -->

<!-- of nonlinear which arise from the  ... -->

<!-- Domain of intended application of the conceptual model: evolution fracture mechanics -->

# Statement of Needs:

goal: validation,
technological transparent full stack
based on solid mathematical
mechanical theory
transparent interfaces 

We aim at developing a transparent platform for verification and validation expeiriments in the context of fracture mechanics, dedicated to predictive understanding of large scale natural fracture phenomena.

Quasi-static evolution problems arising in fracture and the associated softening damage models are strongly nonlinear. They can admit multiple solutions, or none.



The continuous-stability of a multiscale system along its nontrivial paths in phase space is a property that is difficult to check: numerically, at large scales with several material lengths involved, and analytically, in the infinite-dimensional setting.

A robust scientific numerical code is required to analyse and predict the stability of irreversibly evolving systems. 

Based on a simple global-energetic evolutionary models, and mathematical constructs,
this code offers a flexible toolkit for advanced stability analysis



in order to
improve the prediction of standard algorithms for the numerical solution of the evolution problem.
reliability 

# Introduce solvers


We introduce three objects/classes `HybridSolver` `BifurcationSolver,` and ` StabilitySolver`, which respectively implement the solution of the following three general purpose variational problems:
$$
P_1(E): \text{Find }y_t\in X_t: E'(y_t)(z-y_t)\geq 0, \quad \forall z\in V_0\times K^+_0
$$
<!-- % P_2(E): \text{Find }\lambda, w \in \mathbb R\times X: E''(y_t)(w, z)=\lambda \langle w, z\rangle , \quad \forall z\in V\times K^+  -->
$$
P_2(E):\text{given } y_*, \text{find }(\mu_t, w) \in \mathbb R\times X_t: E''(y_*)(w, z-y_*)=\mu_t \langle w, z-y_*\rangle, \quad \forall z\in X_0 
$$
<!-- 
Vatican Fine system:

mail Va to EE: 37 E, 14g
fine: 83 
    5d: -30%
    6->60d 120 E
    
    else: xfine 175+31 ship

another fine is coming up
-->
$$
P_2^+(E):\text{given } y_*, \text{find }(\lambda_t, {v}) \in \mathbb R/R^+\times X_t: E''(y_*)({v}, z-y_*) 
= \lambda_t  \langle {v}, z-y_*\rangle , \quad \forall z\in V_0\times K^+_0 
$$
==[otherwise get rid of the index $y_t$ if it is clearer]==
where $V_t$ is an affine Hilbert space, $V_0$ its associated vector space, $K^+_0$ is the convex cone of positive functions (in a Hilbert space), and
$V_t\times K^+_0$ is a convex set which is the ambient space for admissible perturbations, at time $t$, $E', E''$ denote the linear and bilinear forms associated to the directional derivative of the energy functional $E$.

$P_1(E)$ is the variational inequality that translates first order optimality conditions for unilateral minimality of the energy functional $E$, among admissible variations to be taken in the mixed space of test functions, constituted by the product of the ...
Crucially, as a consequence of the structural requirement of irreversibility on the internal variable $\alpha$, admissibility constrains test fields to the positive (cone) $K^+_0$

We use these three solvers to compute a map
$y_t \in X$ that is *Stable (in the sense specified below),
showing the existence of a sequence of time-discrete real numers $\lambda_t$, 

where $\lambda_t$ is the smallest eigenvalue in the cone ${K^+_0}$


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

### Technical details:
PETSc, SLEPc, NewtonBlock, Restrictions, EPS, Invert-shift, polar decomposition, 


## Science

For a system whose state can be described by the pair $(u, \alpha):=y \in X_t$, where the first state variable is a kinematic field (scalar or vector-valued) subject to time-dependent boundary conditions and the second quantity is an internal variable, we solve the problem
$$
P(0):\text{ Given } T >0, \text{ find } \text{ IRREVERSIBLE-CONSTRAINED EVOLUTION } y_t: t\in(0, T)\mapsto X_t  
\text{ such that}$$ 
$$\text{[Unilateral *Stability]} \qquad E(y_t) \leq E(y_t + z), \quad \forall z \in V_0 \times K^+_0$$

From the physical perspective, we are seeking maps: $y_t: [0, T]\mapsto X_t$, that are observable within a given horizon of parameters, in the sense that are (stable/local energy minima) with respect to admissible perturbations.

In practice, we numerically compute a quadruple $(y_t, \lambda_t, \rho_t, z_i^*)\in X_t \times \mathbb R^+ \times \{\text{True}, \text{False}\}\times (V_t\times K^+_0)$ for all $t \in [0, T]$
such that the problem P(0) is solved. In the solution tuple $y_t$
is the evolution map, $\lambda_t$ is a scalar whose positivity ensures that 
the inequality in P(0) is verified (with the strict sign), $\rho_t$ is a boolean marker that indicates whether or not the evolution path is unique, and  $z^*_i$ is the the optimal perturbation (or instability mode) at the $i$-th stability transition.
In the statement above, $\text{IRREVERSIBLE-CONSTRAINED}$ simply means that the solution is such that $\alpha_t$ is pointwise-a.e. non-decreasing with respect to the loading parameter $t$. 
 
We solve P(0) with the combined use of the variational solvers introduced above which allow us to provide a numerical proof of sufficiency for the existence of observable solutions for problem P(0) (existence of a $\lambda_t > 0, \forall t$).



In our case:
$$
E(y):= \int_\Omega AT_\ell(y) dx. \qquad AT_\ell(y):= \frac{1}{2}A(\alpha)e(u):e(u) + w_1 (w(\alpha) + \ell^2 |\nabla \alpha|^2) 
$$
adopting a widely used mechanical model of damage to represent the underlying brittle material. 
From a mechanical standpoint, challenging allows localisation, (separation of scales), softening, irreversibility.

Mechanical standpoint, constitutive assumptions

Our problem is an instance of a nonlinear, multiscale, nonconvex, and nonsmooth optimisation problem that contains a structural singularity.
The irreversible character of the sought evolution plays a crucial role in its formulation, enforcing a pointwise everywhere a system of unilateral constraints (up to zero measure sets).

The [Unilateral *Stability] principle introduces a functional notion of local energy minimality that has the role of a selection mechanism among evolutionary paths, allowing to discriminate among possible bifurcations via stability transitions.

### Methods 

We use standard finite element techniques for spatial discretisation,
but the approach is applicable to other methods.


## Software

FEniCS
enables wrapping high-level mathematical constructs (e.g., Energies, boundary conditions, ) without losing
full flexibility and configuration of the underlying linear algebra backend (PETSc/SLEPc). The ease-of-use of our solver API (see below) is designed designed to receive an abstract energy functional, and user-friendly description of the state (as an object in a functional space) and its associated constraints (in our case, pointwise almost everywhere). 

In our numerical implementation, first and second order solvers accept as arguments for instantiation

- **energy**: The total energy associated with the fracture problem.
- **state**: A dictionary containing the current state variables, crucial for the fracture analysis.
- **bcs**: A list of boundary conditions applied to the fracture problem, defining kinematic input data.
- **_parameters**: Additional numerical parameters for the solver (default: empty dictionary).

The `HybridFractureSolver` class, implements a hybrid (Staggered/Alternate Minimisation + Fully nonlinear Newton step) solver.
The first iterative phase is designed to exploit a standard algorithm which exploits the (partial) convexity of the mechanical model (* AT), then, once reached an accumulation/attraction point, it performs a fully nonlinear step for a block-matrix with Newton's method, allowing for a precise estimation of the convergence of the first-order nonlinear problem based on the norm of the (constrained) residual.

The instantiation of `HybridFractureSolver` involves the following parameters:

- **bounds**: A tuple specifying the bounds for the solution state variables. The default bounds are instances of `dolfinx.fem.function.Function`.
- **monitor**: An optional parameter for monitoring the solver's iterative progress (default: `None`).

Second order solvers (`BifurcationSolver` and `StabilitySolver`) inherit from a main class, `SecondOrderSolver`, which implements two different unilaterally constrained local minimization problems. The instantiation of this class involves the same parameters as the first orde solver, above plus 

- **nullspace** (optional): An optional parameter representing the nullspace of the linearised operator. Its default value is set to `None`.


`BifurcationSolver` is a variational eigenvalue solver which builds on SLEPc BlockXXX, to seek the lower section of the spectrum of the appropriate Hessian operator.
Typical threshold law,
performs the restriction of the Hessian matrix to the proper subset of indices where constraints are _inactive_, solving on the complementary domain the eigenvalue problem.
Returns a section of the spectrum, size `m`, to be specified in the parameters. 

`StabilitySolver`, solves variational eigenvalue inequality in a convex cone.
Starting from an initial guess $z_0^*$, it iteratively computes a series of pairs (eigenvalue, eigenvector) $\lambda_k, z_k$
converging to a limit $\lambda^*, z^*$
<!-- algorithm that implements a duality result in Hilbert spaces -->
projection and scaling algorithm [ref, Moreau, PdC], returns 

In the sense of P(0), the positivity of the smallest eigenvalue $\Lambda^*$ allows to conclude whether or not the current state is stable. In the latter case, the eigenmode 
$z^*$ 
constitutes the first instability mode.



Graph 1d convergence


confident that these solvers are applicable to simulations of physical systems (embodying readily measurable phenomena) and social and biological systems (for which data may be ill-defined).

how the solvers, in the case of fracture, are algorithmically combined and the continuation algorithm for unstable solutions at bifurcations is outside of the scope of this contribution.




<!-- 
- **energy**: The UFL energy form associated with the specific problem at hand.
- **state**: A dictionary containing the current state variables, providing the necessary context for the analysis.
- **bcs**: A list of Dirichlet boundary conditions to be applied.
- **_parameters** (optional): An optional parameter for fine-tuning of the second order eigen-solvers (convergence tolerances, number of modes, ...). The default value is also `None`. -->

<!-- This class, encapsulating both second order solvers, provides a versatile tool for  stability analysis of systems subject to (pointwise-everywhere) unilateral constraints. -->

<!-- The difficulties are of two sorts:
    - conceptual
    - numerical -->


```
➜  SOFTWARE-CODENAME: git:(release) ls -1
LICENSE
    free software ;)
README.md
__init__.py
algorithms/
    am.py: first order solvers
    so.py: second order solvers
data/
    Material data, student contributed
docker/
    computational containers
launcher.sh
    example of launcher on HPC scheduler
meshes/
    example meshes
models/
    example material models
notes/
    technical or scientific notes
playground/
    iteractive tutorials
practice/
    training problems
solvers/
    the core logic
test/
    unit, mechanical, and analytical tests
utils/
    utilities, visualisation, and auxiliary tools
```

## Verification

In order to verify the numerical implementation we test against analytical results in one-space dimension, capturing the main difficulties of the problem P(0)
1d bar in traction, the fundamental experiment
The focus is on the stability of the solution at each timestep.
It is easy to show that problems $P_2, P_2^+$ can be cast as the minimisation a variational ratio (R. r). Hence, we test our numerical code against the following problems:

$$
\min_{X_0} \mathcal R(z) \quad \text{and} \quad \min_{\mathcal K^+_0} \mathcal R(z), \quad \text{ where } \mathcal R(z):= \dfrac{\int a(\beta -bv')^2 + c(\beta')^2}{\int\beta^2}, X_0 = H^1_0 \times H^1, \mathcal K^+_0 = H^1_0 \times \{\beta \in H^1(0, 1), \beta \geq 0\} 
$$
and $a, b, c$ are coefficients which depend on the material model, cf. [ref] for completeness.
As key performance indicators we compare i) the critical load at which bifurcations occur (the evolution path is no longer uniquene), ii) the first modes of bifurcation, iii) the critical load at which the current state loses stability, iv) the first mode of instability.


Scalability vs. # dofs


## Remarks

We emphasise the importance of bridging theoretical gaps between smooth progression and abrupt transitions. The proposed numerical platform, grounded in advanced stability analysis and interdisciplinary adaptability, emerges as a valuable tool for unraveling the complexities of stability in evolutionary systems. The narrative embraces the paradoxes, challenges, and rare events that shape scientific inquiry.

Additionally, it should support the development of stable control systems, enable ecological modeling with a focus on resilience, and contribute to the stability considerations in quantum mechanics.


Link to a tutorial: we give an example of how these solvers can be used to approach problems of stability analysis in a modular manner, 
link of fenics on colab with some tests
Stability unpacked, in 1d. extra: interactive tutorial


# Acknowledgements

We acknowledge contributions .........
students of MEC647


# References

Bifurc Stab

Moreau

Variational Fracture, latest edition (in french)

Phase field models, latest review

Pham, issues of uniqueness and stability... 1d

Tanne et al

Xinyuan

<!-- Authors: ALB/PLC // US, TYL, AM,  -->