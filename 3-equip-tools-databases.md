# 3- Equip: Modeling Tools & Databases

## What are geochemical modeling programs used for?

Geochemical modeling programs are used for multiple purposes including:
- **Plotting of activity, calculation of thermodynamic constants, or phase stability diagrams-equilibrium constants (K) of reaction** fO<sub>2</sub>-pH, logaK<sup>+</sup>/H<sup>+</sup>, logaSiO<sub>2</sub>, P-T diagrams
- **Equilibrium speciation calculations in natural waters** 
	- Aqueous speciation, pH, and mineral saturation indices
- **Complex geochemical processes** 
	- mineral solid solutions, surface complexation, nucleation & growth kinetics
- **Inverse modeling – determine input for known outcome (products)**
	- CO<sub>2</sub> partial pressure, amount of HCl/NaOH to reach a certain pH, back-calculate downhole fluid chemistry before boiling
- **Forward reaction path modeling – predict the outcome for given input (reactants)**
	- Titration model with varying fluid/rock ratios
	- Dissolution of primary minerals, precipitation of secondary minerals (kinetics or equilibrium) - fluid evolution with increased reaction progress
- **Coupling with transport models:**
	- 1-D, 2-D, 3-D reactive mass and heat transport
	- Multiphase fluid flow and physical models (fracture networks, faults, permeability)

## Geochemical modeling program

Here is a list of popular modeling programs, including "Law of mass action (LMA)" and "Gibbs Energy Minimization (GEM)" based chemical solvers.

**Geochemical equilibrium solver -- LMA based**
- [PHREEQC](https://www.usgs.gov/software/phreeqc-version-3), USGS, D. Parkhurst & Appelo (1999) 
- [Geochemist's Workbench](https://www.gwb.com/index.php), Aqueous Solutions LLC, 
- SOLVEQ, M. Reed, N. Spycher, J. Palandri, U. Oregon; EQ3/6 (Wolery, 1983), MINTEQA2, CHESS (van der Lee et al., 2002), [Reaktoro](https://reaktoro.org/), ETHZ, (Leal), WATEQ4
**Geochemical equilibrium solver -- GEM based**
- [GEMS code package](http://gems.web.psi.ch/), Paul Scherrer Institute, D. Kulik, D. Miron
- [HCh](http://www1.geol.msu.ru/deps/geochems/soft/index_e.html), MSU, Y. Shvarov,  
**Reactive mass transport codes**
- [TOUGHREACT](https://tough.lbl.gov/software/toughreact/), LBL, E. Sonnenthal, N. Spycher, T. Xu 
**Other Tools:**
- [CHNOSZ](https://chnosz.net/) (R package for activity diagrams, thermo calc) 
- [ThermoFun](https://chnosz.net/) (open-source code to calc thermodynamic properties, equilibrium constants, plotting of diagrams)
- [WORM](https://worm-portal.asu.edu/) (open-source tools supporting thermodynamic calculations, plotting of diagrams, computing equilibrium constants)

## Law of mass action (LMA) and Gibbs Energy Minimization (GEM) based chemical solvers

These two methods for solving geochemical fluid-rock equilibrium problems have different approaches, which also translates in the overall way a chemical system is setup and a thermodynamic database is compiled. Some of the advantages/disadvantages are speed of calculations, and the complexity of the system (e.g. solid solutions, non-ideal multi-phase/component systems) that can be solved. For the sake of simplicity, I will briefly summarize a comparison between PHREEQC (LMA code) and GEMS (GEM code) in this comparison table:

```{list-table} This table title
:header-rows: 1
:name: example-table

* - LMA type code
  - GEM type code
* - Set of master species (Al<sup>3+</sup>, H<sup>+</sup>, OH<sup>-</sup>, H<sub>2</sub>O(aq))
  - Mass balance using (IC) independent components (H, O, Al, …) and electric charge (z)
* - Other species built from master species (Al<sup>3+</sup> + 4OH<sup>-</sup> = Al(OH)<sub>4</sub><sup>-</sup>)
  - Chemical species are (DC) dependent components (aqueous species, minerals, gases…) built from IC
* - Database with equilibrium constants (logKr) at T and at water saturation pressure
  - Database with standard Gibbs energy (G°) corrected at P-T
* - LMA to solve mass balance using Newton-Raphson method (Bethke, 1996)
  - GEM to solve mass balance using Interior Points method (Karpov et al. 2001)
* - Redox (Eh, pe or redox pair Fe(II)/Fe(III)) and pH (or element charge balance) must be set at input
  - pH and redox (pe, Eh) calculated from minimization and chemical potentials
* - Only limited (binary) solid solution models
  - Solve equilibrium for complex multisite non-ideal solutions
* - Fast convergence: kinetics rate laws and reactive transport model
  - Slower convergence, but more output data from a single calculation: e.g. phase volumes, fugacity, etc... 
```

A summary of chemical solvers numerical methods and comparison between LMA, GEM and newer approach such as extended LMA (xLMA) are summarized nicely by Leal et al.{cite}`leal2017`

## Limitations of geochemical modeling codes - not a "black-box"

Most of the geochemical modeling codes have naturally some limitations, many of which are related to the underlying thermodynamic databases and the existing or implementation of equations of state for complex phases and their stability as a function of pressure and temperature. This quote by {cite}`oelkers2009` gives an idea of the importance of not using geochemical modeling as a "black-box":

> All of these codes allow calculations/prediction of the equilibrium and/or evolution of geochemical systems as a function of reaction progress with the press of a few buttons. Such calculations appear to have an amazing accuracy; results of these computer codes are commonly reported to 4 or more significant digits. 
>  
> Therein lies the disadvantage of these computer codes as they give the appearance that the thermodynamic databases on which they are based are perfect and accurate beyond all imagination. For many species or minerals few data exist, and in many other cases, no experimental data exist at all. In such cases the thermodynamic ‘data’ were ‘created’ using correlations

Common limitations of geochemical modeling codes can be grouped in the following aspects:
- **Thermodynamic databases**
	- Availability and type of thermodynamic data (databases) -- most databases limit to 300 °C at saturated water vapor pressure
	- Element availability, activity coefficient models suitable for high ionic strength, internal consistency of data
	- Formats of thermodynamic databases – logKs (LMA type codes) vs. more flexible (GEM type codes) with Cp functions, phase transitions, logK lookup tables, etc.
- **Corrections for pressure (P) and temperature (T), and solutions mixing properties**
	- Equations of State (EoS) – used for calculating phase properties such as fugacities and volumes of gases or gas mixtures, properties of aqueous species at high P-T (HKF model, density model) 
	- Mixing properties and complexity of solutions – includes mineral solid solutions (binary, ternary, or more) and non-ideal gases mixing properties (e.g. CO2-H2O)
- **“User friendliness” and feature availability**
	- GUI, plotting of certain activity-activity diagrams, adding/editing of thermodynamic database, coupling to reactive transport

## Thermodynamic databases

Different approaches are being used to compile, evaluate, and curate thermodynamic databases in various formats. One of the key components is maintaining internal consistency, critical evaluation (reliability and uncertainty) of the data and methods to retrieve them, and testing of the data to real-world problems. It is also important to understand the validity limits of each databases and how they are retrieved. Hence a fundamental knowledge in thermodynamics is crucial for the seasoned geochemical modeler.

Here is a non-exhaustive list of some common thermodynamic databases used in geochemical modeling:

**Minerals, gases, aqueous species:**
- [MINES thermodynamic database](https://geoinfo.nmt.edu/mines-tdb/) {cite}`gysi_2023` NMBGMR/NMT (ore deposits, critical minerals, geothermal, CO2 sequestration, hydrothermal fluid-rock)
- SUPCRT92, slop98.dat, SUPCRTBL (Zimmer et al., 2016), Indiana U.
- Provided in PHREEQC (see review by Lu et al. {cite}`Lu2022`), many of these are also part of [GWB software](https://www.gwb.com/thermo.php): phreeqc.dat, llnl.dat, wateq4f.dat, carbfix.data, minteq.data, supcrtbl.dat, pitzer.dat, etc.
- Application specific: [PSI-NAGRA](https://www.psi.ch/en/les/database) and [THEREDA](https://www.thereda.de/en) (radioactive wastes), [Cemdata](https://cemgems.org/cemdata/about-cemdata/) (cement industry), [THERMODDEM](https://thermoddem.brgm.fr/page/project-evolutions) (wastes, geothermal, acid mine, cement)
**Mineral specific databases**
- Holland and Powell (1998, 2011) {cite}`holland1998,holland2011`, based on metamorphic phase equilibria, least-squares regression technique to optimize the thermodynamic parameters, minimizing inconsistencies between calculated and observed phase equilibria
- Gottschalk (1997) {cite}`gottschalk1997`, calorimetry, phase equilibria, solubility data, empirical estimations
- Berman and Brown (1985) {cite}`berman1985`, fitting and revised equation for heat capacity
- [Robie and Hemingway (1995)](https://doi.org/10.3133/b2131), USGS compilation and critical evaluation, based on calorimetric measurements

## Citations

```{bibliography}
:filter: docname in docnames
```


