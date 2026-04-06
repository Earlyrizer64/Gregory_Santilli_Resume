
INSERT IMAGES ABOVE

***
<div align="center">
  
  # Oven Thermal Design Study
  
</div>

| Project Overview | Images |
|:-----------------|:-------|
| This project was based on a real engineering constraint where an industrial baking process required reduced cook time to meet production demand without purchasing additional ovens.  We first performed a steady-state thermal analysis of the oven at an internal operating temperature of 350°F, modeling heat loss through a thermal resistance network with various insulation configurations. The goal was to ensure that heat input exceeded losses to maintain stable operating conditions.| <img src="Oven_Thermal_Design_Study_Files/Resistive_Network_Pt_1.png" width="5000" height="5000"> |
| Next, we developed a transient lumped capacitance model in MATLAB to simulate the cooking process of a food item with thermally similar properties to chicken. This allowed estimation of internal temperature evolution and baseline cook time predictions.| <img src="Oven_Thermal_Design_Study_Files/Resistive_Network_Pt_2.png" width="5000" height="5000"> |
| Finally, the system was modeled in SolidWorks Thermal Simulation to capture spatial temperature gradients and geometric effects not included in simplified models. This step was used to evaluate design modifications aimed at reducing cook time and improving thermal efficiency, ultimately targeting reduced production bottlenecks and avoiding capital equipment expansion. | <img src="Oven_Thermal_Design_Study_Files/Original_Model_Image.png" width="5000" height="5000"> |

***
<div align="center">
  
  # Steady-State Thermal Analysis of Oven

  Steady-state MATLAB thermal model using a resistance network was used to evaluate oven heat loss at 350°F. A parametric sweep over insulation materials and thicknesses was performed, followed by a cost vs performance optimization to select the most efficient insulation design.

<img src="Oven_Thermal_Design_Study_Files/Resistive_Network_Pt_1.png" width="2000" height="1000">
<a href="https://github.com/Earlyrizer64/Gregory_Santilli_Resume/raw/main/Oven_Thermal_Design_Study_Files/Mid_Term_Oven_Part1
.zip"> <img src="https://img.shields.io/badge/Resistive_Network_Pt_1-blue" width="150" height="100"> </a>

</div>

| Insulation Type | Thermal Conductivity, k (W/m·K) | Thickness (in) | Max Allowable Temp (°F) | Surface Temp (Simscape) (°C) | Surface Temp (MATLAB Hand Calc) | Rate of Heat Loss (W) |
|:---------------:|:-------------------------------:|:--------------:|:-----------------------:|:----------------------------:|:-------------------------------:|:---------------------:|
| Cellular Glass | 0.058 | 3 | 900 | 31.86 | 31.85 | 3,596.46 |
| Perlite, Expanded | 0.042 | 2 | 1200 | 32.71 | 32.70 | 3,860.09 |
| Calcium Silicate | 0.060 | 2 | 1200 | 32.20 | 32.19 | 3,702.66 |


| Insulation Type | Area Needed (ft²) | Thickness Needed (in) | Unit Price ($/ft² for required thickness) | Total Cost ($) |
|:---------------:|:-----------------:|:---------------------:|:-----------------------------------------:|:--------------:|
| Cellular Glass | 378 | 3 | ~15 | 5,670 |
| Perlite Expanded | 378 | 2  | ~4 | 1,512 |
| Calcium Silicate | 378 | 2 | ~6 | 2,268 |

<div align="center">
Expanded perlite was selected as the optimal insulation due to its lowest cost while satisfying the minimum heat loss requirement of approximately 1200 W across all tested materials.
</div>

***
<div align="center">

# Transient Thermal Model (Lumped Capacitance – MATLAB/Simulink)

A transient lumped capacitance model was implemented in MATLAB/Simulink to simulate the cooking of a chicken-like thermal mass. Cook time and temperature evolution were predicted under convective, radiative, and conductive heating conditions. The validity of the lumped assumption was verified using the Biot number criterion (Bi < 0.1).  

<img src="Oven_Thermal_Design_Study_Files/Resistive_Network_Pt_2.png" width="1500" height="800">
<a href="https://github.com/Earlyrizer64/Gregory_Santilli_Resume/raw/main/Oven_Thermal_Design_Study_Files/Mid_Term_Oven_Part2
.zip"> <img src="https://img.shields.io/badge/Resistive_Network_Pt_2-blue" width="150" height="100"> </a>

## Parameters Used for Transient Analysis

| Block | Temp (°F) | Area (in²) | Heat Transfer Coefficient, h (W/m²·K) | Thickness (in) | Thermal Conductivity, k (W/m·K) | Radiation Coefficient, εσ (W/m²·K⁴) | Mass (kg) | Specific Heat, c (J/kg·K) |
|:-----:|:---------:|:----------:|:-------------------------------------:|:--------------:|:-------------------------------:|:-----------------------------------:|:--------:|:-------------------------:|
| T_oven_internal   | 350       | --          | --                                     | --             | --                               | --                                   | --       | --                        |
| Rad, Oven to Cake | --        | 576         | --                                     | --             | --                               | 0.95 * 5.67e-8                       | --       | --                        |
| Conv, Oven to Cake| --        | 576         | 10                                     | --             | --                               | --                                   | --       | --                        |
| Rad, Oven to Tray | --        | 965.6135    | --                                     | --             | --                               | 0.3 * 5.67e-8                        | --       | --                        |
| Conv, Oven to Tray| --        | 965.6135    | 10                                     | --             | --                               | --                                   | --       | --                        |
| Cond, Tray to Cake| --        | 578.4025    | --                                     | 0.025          | 16.6                             | --                                   | --       | --                        |
| Cake Thermal Mass | 68        | --          | --                                     | --             | --                               | --                                   | 39.644   | 3560                      |
| Tray Thermal Mass | 68        | --          | --                                     | --             | --                               | --                                   | 3.156    | 512                       |

The cake reached 160°F in ~55 minutes. The Biot number (1.281 > 0.1) indicated that internal temperature gradients were significant, violating the lumped capacitance assumption and limiting the accuracy of the model. This motivated a transition to 3D SolidWorks thermal simulation to capture spatial temperature variations. 

***
# Thermal Design Optimization (SolidWorks FEA)

Following the thermal analysis of the baseline cake-and-tray system, a design optimization study was conducted to reduce overall cooking time. Multiple tray geometries were evaluated in SolidWorks thermal simulations to modify heat transfer pathways and improve thermal response. The objective was to identify a configuration that minimized cook time while maintaining uniform heating of the product.

## Original Model (Baseline Cook Time)

INSERT IMAGE

This original model took 

</div>
















