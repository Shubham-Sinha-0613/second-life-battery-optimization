# Second-Life Battery Techno-Economic Optimization  
*(Industry Project – Non-Confidential Summary)*

## Overview

This project develops a techno-economic optimization framework to evaluate the deployment of second-life electric vehicle (EV) batteries in industrial and commercial energy systems.

The objective is to determine optimal battery sizing and dispatch strategy under real load demand and tariff structures, while incorporating degradation-aware operational constraints.

The model is implemented in Python using Mixed Integer Linear Programming (MILP) and solved using Gurobi.

---

## Problem Statement

With increasing EV adoption, large volumes of batteries reach end-of-vehicle life while still retaining usable capacity. These second-life batteries present a lower-cost alternative to new energy storage systems.

However, their economic viability depends on:

- Industrial load profile characteristics  
- Electricity tariff structure (time-of-use pricing)  
- Operational dispatch strategy  
- Degradation behavior over time  
- Capital investment constraints  

This project formulates an optimization model to evaluate whether second-life batteries can provide cost-effective peak shaving and energy arbitrage in industrial environments.

---

## Optimization Framework

A Linear Programming (LP) model was developed using Python and Gurobi.

### Core Modeling Components

- Hourly industrial load demand modeling  
- Time-of-use tariff integration  
- State-of-Charge (SOC) tracking  
- Charging/discharging power limits  
- Energy capacity constraints  
- Degradation modeled as operational throughput constraint  

All decision variables were continuous.

---

## Objective Function

Minimize total annualized system cost:

Battery Investment Cost + Grid Electricity Cost − Arbitrage Savings

---

## Key Results

- ~35% effective extension in usable battery lifetime  
- Improved peak load shaving performance  
- Identified tariff differential thresholds required for positive return on investment  
- Demonstrated sensitivity of economic viability to degradation limits  

---

## Technical Stack

- Python  
- Gurobi Optimizer  
- NumPy / Pandas  
- Matplotlib  

---

## Professional Note

This repository demonstrates optimization architecture and engineering methodology only.  
Implementation details and datasets are confidential.
