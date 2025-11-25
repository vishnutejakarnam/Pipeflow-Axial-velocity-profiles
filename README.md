# Pipeflow-Axial-velocity-profiles
A reproducible CFD project using ANSYS Fluent to study laminar pipe flow. Includes outlet axial velocity profiles for three meshes 100*5, 100*10 and 100*20 and velocity development at five axial locations with a fine mesh. Analytical comparisons highlight mesh dependence and flow development.

# Run Instructions for PipeFlow-Axial-Velocity-Profile

## Problem statement
- **Q1:** Plot axial velocity profiles at the outlet for three uniform meshes (100×5, 100×10, 100×20) using **second‑order upwind**, and compare with the analytical parabolic           profile.  
- **Q2:** Plot velocity profiles at five axial stations (x = 0.5, 1.5, 2.5, 5.0, 7.5 m) and outlet using the fine mesh (100×20), to show how the flow develops.

---
## Case constants
- Pipe length: **L = 8.0 m**  
- Diameter: **D = 0.2 m**  
- Fluid: **ρ = 1.25 kg/m³**, **μ = 1×10⁻³ kg/(m·s)**(Dynamic Viscosity)
- Reynolds number: **Re = 120.9**  
- Inlet velocity:  
  \[
  U_{in} = \frac{Re \cdot \mu}{\rho \cdot D} = 0.4836 \ \text{m/s}
  \]

---

## Step 1: Launch Fluent
1. Open ANSYS Fluent (2D, steady, pressure‑based solver).
2. Select **double precision** if available.

---

## Step 2: Import mesh
- For Q1: import `mesh_100x5.msh`, `mesh_100x10.msh`, `mesh_100x20.msh`.  
- For Q2: import `mesh_100x20.msh`.

Menu path: **File → Read → Mesh → select file**.

---

## Step 3: Define fluid and boundary conditions
- **Material:** Air with ρ = 1.25, μ = 1×10⁻³.  
- **Inlet:** Velocity inlet, set **Uin = 0.4836 m/s**.  
- **Outlet:** Pressure outlet, gauge pressure = 0 Pa.  
- **Walls:** No‑slip.

---

## Step 4: Solver setup
- **Pressure–velocity coupling:** SIMPLE.  
- **Discretization:** Momentum → **Second‑order upwind**.  
- **Initialization:** Standard initialization from inlet.  
- **Convergence criteria:** residuals ≤ 1×10⁻⁶ and stable mass flow, centerline velocity, wall shear.

---

## Step 5: Run simulations
- **Q1:**  
  - Run each mesh until convergence, suggested iterations > 1500
  - At outlet, create a line probe across diameter.  
  - Export axial velocity vs radial position as CSV (`results/q1_mesh100x5_outlet.csv`, etc.).  

- **Q2:**  
  - Run fine mesh (100×20), Suggested iterations > 1500  
  - Create line probes at x = 0.5, 1.5, 2.5, 5.0, 7.5 m, and outlet.  
  - Export velocity profiles as CSV (`results/q2_x0.5.csv`, etc.).

Menu path: **Surface → Line/Rake → Define probe → Report → XY Plot → Write to File**.



