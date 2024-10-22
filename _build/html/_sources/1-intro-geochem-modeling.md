# 1-Introduction to Geochemical Modeling
## What is geochemical modeling?

Geochemical modeling is a tool that can be used to interpret fluid-rock interaction in natural geologic systems. Throughout this book we will cover different types of models and refine this definition with a focus on fluid-rock reaction path modeling. In essence, these models are based on thermodynamics and focus on the evolution of chemistry of fluids (water and gases) and mineralogy and can be linked to physical models to understand porosity, permability, and fluid flow networks. During alteration primary rock-forming minerals dissolve, solutes form aqueous species, and secondary minerals become saturated. The modeler understand what controls the formation of alteration zones, what affects the mobility of these elements, and the factors influencing the evolution of geofluids. 

```{note}
Geochemical modeling provide you with a powerful tool to interpret these and many more processes with important applications in geosciences such as ore formation, environment and water, critical minerals, engineering, hydrology, etc.).
```

## Learning by doing

Several examples will be used to apply what you learn to real-world problems. Topics of interest include:
- Speciation and mineral solubility in geothermal waters – Iceland/Yellowstone
- Seawater-basalt interaction in hydrothermal vent fluids – analogues to volcanic hosted massive sulfide deposits 
- CO<sub>2</sub> sequestration into basaltic rock formations – Carbfix project Iceland.

## 5 Steps to Geochemical Modeling Mastery

To guide you on your geochemical modeling journey, I will give provide you with a systematic and motivating method. **The 5-step approach includes: Define, Equip, Understand, Construct, and Predict.**

- **(Step 1) Define: Conceptualization & Problem Definition**
	- **What's the problem?** Clearly state your research question or the issue you want to address.
	- **Set the scene:** Describe the geological environment (rock types, fluids, temperature, pressure).
	- **Gather clues:** Collect and assess relevant data (water chemistry, minerals, maps).
	- **Example:** CO<sub>2</sub> sequestration in basalts – what happens when we inject CO<sub>2</sub> into basalt rock? What data do we need to understand this process?

- **(Step 2) Equip: Geochemical Modeling Tools &  Databases**
	- **Choose your tools:** Explore different geochemical modeling software (PHREEQC, Geochemist's Workbench, GEMS) – each has pros and cons.
	- **Find good data:** Accurate thermodynamic data is crucial. Learn about different databases (EQ3/6, SUPCRT92, MINES).
	- **Get started:** Learn the basics of your chosen software and how to input data.

- **(Step 3) Understand: Thermodynamic Framework**
	- **Aqueous Speciation:** How do dissolved chemicals behave in water? Understand activity, ionic strength, and speciation diagrams.
	- **Mineral Solubility:** Will minerals dissolve or precipitate? Learn about solubility products, saturation indices, and activity diagrams.
	- **Redox Reactions:** Electron transfers can significantly impact the system. Eh-pH diagrams are your friends!
	- **Reaction Kinetics:** How fast do reactions occur? Explore factors that influence reaction rates.

- **(Step 4) Construct: Model Construction & Calibration**
	- **Build your model:** Translate your research question into a conceptual model with key processes and parameters.
	- **Reaction Path Modeling:** Simulate how the system changes over time due to fluid-rock interaction.
	- **Check your work:** Calibrate and validate your model by comparing it to real-world data.

- **(Step 5) Predict: Advanced Real-world Applications & Predictions**
	- **Go further:** Explore advanced techniques like reactive transport modeling.
	- **Real-world predictions:** Use your model to understand complex scenarios like ore formation or the long-term impacts of CO<sub>2</sub> sequestration.
	- **Make an impact:** Apply geochemical modeling to solve real-world problems and contribute to our understanding of Earth processes.

## Define the problem & conceptualize it into a model

The first step in your geochemical modeling journey:
- **Define: Conceptualization & Problem Definition**
    - Clearly defining the research question or problem
    - Identifying the relevant geological context (e.g., rock types, fluid compositions, temperature, pressure)
    - Gathering and evaluating existing data (e.g., water chemistry, mineralogy, geological maps)

**How do we define a problem and conceptualize it?** Looking at fluid-rock systems the key is to recognize the key processes and segment it into subsystems. Ask yourself the following questions: What are the source(s) of the fluids? How many phases are involved?
What is the P-T range of the fluids? What is the unaltered/altered rock made of? Do we find alteration zoning?

**Example - Oceanic crust alteration: seawater-basalt interaction, hydrothermal vent fluids, and ore formation in volcanogenic hosted sulfide (VMS) deposits**
Conduct some search to find what databases are available. Ideally we search information on fluid chemistry (cations, anions, pH), temperature, metal concentrations/ratios in sulfide ore zones, alteration mineralogy and zoning from drill cores in modern systems or geology and fossil mineral deposits. 

The information gathered of fluid-rock systems generally boil down to:
- Pressure (P) – Temperature (T) – composition (x)
- Phases to be considered (what minerals, gases, water)
	- Primary rock types, mineralogy and bulk compositions
	- Alteration zoning & Minerals
- Processes
	- cooling, mixing, boiling, fluid-rock reaction
	- redox reactions, for example precipitation of sulfides and reduction of SO<sub>4</sub><sup>2-</sup> to H<sub>2</sub>S
	- equilibrium vs. kinetics, such as the dissolution rates of basaltic glass playing a role during weathering or CO<sub>2</sub> sequestration vs. equilibrium mineral assemblages observed in geothermal systems

## Citations

Here are a couple of references for the topics/examples covered in Lecture 1:
- Oceanic crust alteration: seawater-basalt interaction, hydrothermal vent fluids, and ore formation in volcanogenic hosted sulfide (VMS) deposits {cite}`pierre_al_2018,hurtig_al_2024`
- The role of hydrocarbons in Mississipi Valley-Type Zn-Pb ore formation {cite}`hurtig_al_2018`
- CO<sub>2</sub> sequestration into basaltic rock formation – Carbfix project, Iceland {cite}`aradottir_al_2012, gysi_2017`


```{bibliography}
```


