# Pipeflow-Axial-velocity-profiles
A reproducible CFD project using ANSYS Fluent to study laminar pipe flow. Includes outlet axial velocity profiles for three meshes 100 * 5, 100 * 10 and 100 * 20 and velocity development at five axial locations with a fine mesh. Analytical comparisons highlight mesh dependence and flow development.

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

## Step 2: create a rectangular pipe with the mentioned dimesions using any CAD software and import into the geometry section in ANSYS FLUENT
## Step 3: Open Mesh section
- In this section the geometry will be meshed with 500 elements. That is, the pipe will be divided into
  100 elements in the axial direction and 5 elements in the radial direction.
- In order to begin the meshing process, go to the Workbench Project Page, then (Double Click) Mesh
  and wait for the meshing window to open.
**Face Meshing**
 - Sometimes the default mesh has irregular elements. We are interested in creating a grid style of mesh that can be
mapped to a rectangular domain. This meshing style is called **Face Meshing**. In order to incorporate this
right-click on Mesh in the outline tree and select Insert > Face Meshing.
-  Now, the Face Meshing still must be applied to the pipe geometry. In order to do so, first click on the pipe body
(rectangle) which should then highlight green. Next, (Click) No Selection and then Apply in the Details of Face
**Edge Sizing**
- An Edge Sizing needs to be inserted. First, (Click) Mesh> Insert and then Sizing.
Now, the geometry and the number of divisions need to be specified. First (Click) Edge Selection Filter,
Then hold down the "Control" button (in PC keyboard) and then click the bottom and top edge of the rectangle.
Both sides should highlight green.
- Then, set Number of Divisions to 100.
Follow the same procedure as for the edge sizing in the axial direction (right Click) Mesh > Insert >
Sizing, then Click Edge Selection Filter, , then hold down the "Control" button and then click the left and
right side - both sides should highlight green. Next, hit Apply under the Details of Sizing and set the Number
of Division to 5, and press return. Then, click Generate Mesh, and then Mesh.
- In the mesh above there are 535 elements, when there should be only 500. Mesh statistics can be
found by clicking on Mesh in the Tree and then by expanding Statistics under the Details of Mesh table. In order
to get the desired 500 element mesh, the Behavior needs to be changed from Soft to Hard for both Edge Sizing's.
In order to carry this out, in the tree outline click Edge Sizing and ensure that **Capture Curvature is set to No**
which enables the Behavior option under the Details of Edge Sizing table. Then change **Behavior to Hard**.

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
  - Export axial velocity vs radial position as CSV .  

- **Q2:**  
  - Run fine mesh (100×20), Suggested iterations > 1500  
  - Create line probes at x = 0.5, 1.5, 2.5, 5.0, 7.5 m, and outlet.  
  - Export velocity profiles as CSV .

Menu path: **Surface → Line/Rake → Define probe → Report → XY Plot → Write to File**.



