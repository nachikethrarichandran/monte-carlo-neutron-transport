\# Monte Carlo Simulation of Thermal Neutron Transport



Monte Carlo simulation of thermal-neutron transport through shielding materials, including scattering, absorption, reflection, transmission, and transport across heterogeneous media.



The project models individual neutron histories using stochastic interaction sampling derived from microscopic cross sections and compares the resulting macroscopic transport behaviour across different materials and shielding configurations.



\## Overview



Neutron transport is inherently stochastic: a neutron propagating through matter undergoes random free flights followed by interactions such as scattering or absorption.



This project simulates these trajectories using Monte Carlo methods and investigates neutron transport through:



\- water

\- lead

\- graphite

\- multi-material shielding geometries



The simulation tracks individual neutron histories and estimates quantities such as:



\- absorption probability

\- reflection probability

\- transmission probability

\- attenuation with shielding thickness

\- effective transport length scales



\## Monte Carlo Transport Model



For a material with macroscopic interaction cross section \\(\\Sigma\\), the distance to the next interaction is sampled from the exponential distribution



\\\[

P(s) = \\Sigma e^{-\\Sigma s}.

\\]



Using inverse-transform sampling,



\\\[

s = -\\frac{\\ln \\xi}{\\Sigma},

\\]



where \\(\\xi\\) is a uniformly distributed random number in the interval \\((0,1)\\).



At each interaction, the neutron is probabilistically classified as scattered or absorbed according to the relative interaction cross sections.



\## Isotropic Scattering



Scattering directions are sampled isotropically in three dimensions.



Rather than drawing the polar angle uniformly, the simulation samples



\\\[

\\cos\\theta \\sim U(-1,1)

\\]



and



\\\[

\\phi \\sim U(0,2\\pi),

\\]



ensuring a uniform distribution over solid angle.



\## Homogeneous Slabs



The first simulations model neutron transport through slabs of individual materials.



For each incident neutron, the trajectory is followed until the neutron is:



\- absorbed inside the material

\- reflected through the entrance surface

\- transmitted through the opposite surface



Large ensembles of neutron histories are used to estimate the corresponding probabilities.



\## Validation



The stochastic sampling and transport model are tested against analytical expectations where possible.



This includes validation of:



\- exponential free-path sampling

\- isotropic direction generation

\- absorption-only attenuation

\- convergence with increasing Monte Carlo sample size



For simplified absorption-only transport, the simulation reproduces the expected exponential attenuation behaviour.



\## Shielding Thickness



Transmission is evaluated as a function of material thickness.



The resulting behaviour is used to compare the shielding properties of water, lead, and graphite and to estimate effective attenuation scales.



\## Heterogeneous Media and Woodcock Tracking



The project is extended to transport through adjacent materials using Woodcock, or delta, tracking.



A common majorant interaction coefficient is introduced,



\\\[

\\Sigma\_{\\max} \\geq \\Sigma(\\mathbf{x}),

\\]



allowing free paths to be sampled without explicitly stopping at every material boundary.



Candidate collisions are then classified as either:



\- real collisions

\- virtual collisions



depending on the local interaction coefficient.



The implementation is validated by comparing Woodcock transport in homogeneous configurations with the direct slab simulation.



\## Statistical Analysis



Monte Carlo estimates are reported together with statistical uncertainties derived from the finite number of simulated neutron histories.



Convergence tests are used to determine an appropriate number of histories and to balance numerical precision against computational runtime.



\## Technologies



\- Python

\- NumPy

\- Matplotlib

\- Monte Carlo methods

\- inverse-transform sampling

\- stochastic transport

\- statistical uncertainty estimation



\## Running the Project



Clone the repository:



```bash

git clone https://github.com/YOUR-USERNAME/monte-carlo-neutron-transport.git

cd monte-carlo-neutron-transport

