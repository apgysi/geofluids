# 2- Reaction Path Modeling

## Introduction to reaction path modeling

The concept of reaction path modeling in fluid-rock interactions can be traced back to the seminal work of Helgeson and his co-workers in the late 1960s.
- Helgeson, H. C. (1968). Evaluation of irreversible reactions in geochemical processes involving minerals and aqueous solutions-I. Thermodynamic relations. Geochimica et Cosmochimica Acta 32, 853-877. {cite}`helgeson1968`  
- Helgeson, H. C., Garrels, R. M., & Mackenzie, F. T. (1969). Evaluation of irreversible reactions in geochemical processes involving minerals and aqueous solutions-II. Applications. Geochimica et Cosmochimica Acta 33, 455-481.  {cite}`helgeson1969`

Reaction path modeling aims to predict how the compositions of both rocks and fluids change as they interact over time. It's like a step-by-step simulation of the chemical reactions occurring as water flows through rocks and minerals.

```{note}
Reaction path modeling is a dynamic view of fluid-rock interaction – how system changes as a function of reaction progress (time or amount of reacted rock)
```

Applications of reaction path modeling are numerous and include:
- Geothermal systems: Understanding the evolution of hot springs and geothermal reservoirs.
- Ore deposit formation: Simulating the transport and precipitation of metals to form ore deposits.
- Contaminant transport: Predicting the fate of pollutants in groundwater systems.
- CO2 sequestration: Evaluating the potential for storing carbon dioxide in geological formations.
- Weathering and diagenesis: Modeling the alteration of rocks at the Earth's surface and in sedimentary basins.

## Fluid-rock interaction as an acid-base titration problem

We can make an analogy between fluid-rock interaction and an acid-base titration for understanding reaction path modeling. In a typical geothermal system, as shown in the image below from Iceland, interaction of geothermal fluids with basalts leads to the formation of various alteration zones depending on the amount of reaction progress (i.e., basalt reacted with the fluid). For simplification we will talk about "fluid-buffered" and "rock-buffered", the latter indicating that more rock has reacted with the fluid.

![cover](./images/alteration-Iceland.png)

The pH of these geothermal waters strongly depends on the degree of fluid-rock interaction or rock-buffering. This is true for other systems, including ore-forming processes at depth closer to a magma chamber, or surface processes such as rock weathering and interaction with rainwater containing carbonic acid. If we simplify this further, the following holds true for most fluid-rock interaction processes:

- The fluid acts as the acid (HCl, H<sub>2</sub>SO<sub>4</sub>, H<sub>2</sub>S, CO<sub>2</sub>) that releases protons (H<sup>+</sup>)

**acid dissociation reactions** 

HCl(aq) = H<sup>+</sup> + Cl<sup>-</sup>

H<sub>2</sub>CO<sub>3</sub>(aq) = H<sup>+</sup> + HCO<sub>3</sub><sup>-</sup>

- The rock acts as the base and consumes or neutralizes protons (H+) during rock alteration.

**mineral solubility reactions** 

3KAlSi<sub>3</sub>O<sub>8</sub> (K-feldspar)+2H<sup>+</sup> = KAl<sub>3</sub>Si<sub>3</sub>O<sub>10</sub>(OH)<sub>2</sub>(muscovite)+6SiO<sub>2</sub>(quartz)+2K<sup>+</sup>

Hence one can see that reaction of the rock with a fluid that contains the acids progressively shifts the pH to higher values by neutralization of these protons. This is also commonly expressed by the cation to proton activity ratios (e.g. log aK<sup>+</sup>/aH<sup>+</sup>). We will come back to the concept of activity in the next chapter and briefly introduce this below for the hydrolysis of feldspar.
## Feldspar hydrolysis model

A typical modeling example can be used to illustrate the concept of reaction path modeling and the link to acid-base titration. The feldspar hydrolysis model considers the alteration of feldspar reacting with water. Titration of K-feldspar into water results in a sequence of equilibrium alteration minerals including Gibbsite, Kaolinite, and Muscovite. At each step of the titration a small amount of K-feldspar is added to water, which increased the overall reaction progress of the fluid-rock system. Here are the expected steps:
- Initially K-feldspar (Kfs) added to water dissolves congruently (in stoichiometric proportion) to release Al to the water until Gibbsite (Al hydroxide) becomes saturated and precipitates
- Further addition of Kfs results in the saturation  and precipitation of Kaolinite (Al-Si mineral) and dissolution of Gibbsite
- Further addition of Kfs results in the saturation and precipitation of Muscovite (K-Al-Si mineral) and dissolution of Kaolinite
- Finally, when the system pH is increased enough, equilibrium with Kfs is reached. At this step the system is pH is buffered by equilibrium with feldspar.

Below is an example titration model using the GEMS code package and the MINES thermodynamic database taken from  Module 2 in our [gitbook GEMS modeling tutorial](https://apgysi.github.io/gems-mines-tutorial/).

![cover](./images/fsp-titration-model.png)

The overall reaction sequence above results in the "pH steps" observed in a pH vs. moles or g feldspar added diagram. These indicate a buffering of pH by different mineral assemblages, which is also a convenient way to understand more complex fluid-rock systems. We will come back to this later, once Steps 1-3 have been presented, and the time comes to construct a complex model (Step 4).

## Citations

```{bibliography}
:filter: docname in docnames
```


