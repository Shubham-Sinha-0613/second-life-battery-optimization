# Technical Summary – Second-Life Battery Optimization

## 1. Problem Formulation

The objective is to minimize total annualized system cost while ensuring operational feasibility of second-life battery deployment in industrial energy systems.

The model evaluates battery dispatch under time-varying tariffs and degradation-aware constraints.

---

## 2. Optimization Classification

- Linear Programming (LP)
- Continuous decision variables
- Fully convex formulation
- Guaranteed global optimal solution

Solver: Gurobi  
Implementation: Python

---

## 3. Mathematical Formulation

### 3.1 Decision Variables (for each time step t)

- P_ch,t → Charging power  
- P_dis,t → Discharging power  
- P_grid,t → Grid import power  
- SOC_t → State of Charge  

All variables are continuous.

---

### 3.2 Objective Function

Minimize:

min Σ (C_grid,t · P_grid,t · Δt) + C_inv

Where:

- C_grid,t = electricity tariff at time t  
- P_grid,t = grid import power  
- C_inv = annualized battery investment cost  

Energy arbitrage benefits are captured implicitly through optimized dispatch.

---

### 3.3 Power Balance Constraint

P_grid,t + P_dis,t = P_load,t + P_ch,t

---

### 3.4 State of Charge Dynamics

SOC_t = SOC_{t-1}  
        + η_ch · P_ch,t · Δt  
        − (P_dis,t / η_dis) · Δt  

---

### 3.5 Operational Limits

SOC_min ≤ SOC_t ≤ SOC_max  

0 ≤ P_ch,t ≤ P_ch_max  

0 ≤ P_dis,t ≤ P_dis_max  

---

### 3.6 Degradation Throughput Constraint

Σ (P_ch,t + P_dis,t) · Δt ≤ E_throughput_max  

This constraint limits cumulative cycling and extends effective battery lifetime.

---

## 4. Modeling Decisions

- Linear structure chosen for convexity and computational efficiency  
- Continuous variables used to avoid binary switching complexity  
- Hourly resolution balances accuracy and scalability  
- Degradation modeled as operational constraint instead of nonlinear cost term  

---

## 5. Scenario & Sensitivity Analysis

The framework was evaluated under varying:

- Tariff differentials  
- Throughput degradation limits  
- Capital cost assumptions  
- Industrial load variability  

Sensitivity analysis identified economic viability thresholds.

---

## 6. Key Engineering Insights

1. Dispatch strategy significantly influences effective battery lifetime.  
2. Tariff spread is the dominant driver of ROI.  
3. Limiting deep cycling improves economic sustainability.  
4. Continuous LP dispatch can approximate realistic operation without integer variables.

---

## 7. Computational Characteristics

- Convex LP formulation  
- Scalable for extended time horizons  
- Suitable for integration into larger energy management systems  

---

## 8. Limitations

- Linear degradation approximation  
- Deterministic tariff assumption  
- No stochastic load modeling  
- No nonlinear aging cost integration  

---

## 9. Practical Applicability

The framework can be adapted for:

- Industrial facilities  
- Commercial energy systems  
- Microgrid configurations  
- Hybrid PV + storage systems  

---

## 10. Confidentiality

This document provides structural and methodological insight only.  
All implementation details and datasets remain confidential under NDA.
