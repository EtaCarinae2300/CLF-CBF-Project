# Read Me

This repository is for our ECEN 5738 Project. It is a MATLAB-based simulation and control framework 
implementing a Coupled Control Lyapunov Function (CLF) and Control Barrier Function (CBF) controller for an air-breathing hypersonic vehicle.
This project tries to reproduce and validate the results presented in a 2026 SciTech Paper by Vaknin and Idan.

## Dependencies

MATLAB Optimization Toolbox
MATLAB Control System Toolbox

## How to Execute Code

Before running anything within the repository, run Startup.m

The repository runs the following different tasks:

1. To run an evaluation of the Coupled CLF-CBF controller (ON vs OFF):

* Run "EvaluateController.m"
* This simulates a slight velocity perturbation from trim conditions at 85,000 ft and evaluates the trajectory with and without the CBF constraint active.
* (Start with a low tEnd, say 30s)

2. To test the pure CLF tracking controller:

* Run "CLF_Test.m"
* This simulates baseline trajectory tracking performance without the KKT CBF coupling.

## Folder Structure

* CLF: Contains the core CLF mathematics (Lie derivatives, PMN/QP control laws).
* Controllers: Contains the CBF implementation, KKT coupling, LQR/ARE weight formulation, and baseline PID.
* Models: Contains the vehicle dynamics, aerodynamics, thrust, and custom integrators.
* Plotting: Pretty self explanatory.

## Major Files of Relevance

* ModelParams.m Contains the master source of truth for all parameters in the project (aircraft properties, constraint bounds, and controller weights).
* EvaluateController.m Main script for evaluating the KKT CLF-CBF control strategies.
* CLF_Test.m Standalone script to test pure CLF tracking.
* Simulation.m Core simulation loop that calls the relevant integrators (RK4/ode45) and dynamics functions.
* CoupledCLF_CBF.m Contains the coupling of CLF and CBF using Karush-Kuhn-Tucker (KKT) conditions.
* calcCLFControl.m Contains the Pointwise Min-Norm (PMN) method implementation.
* getDynamics.m Contains the nonlinear equations of motion that govern the vehicle's flight dynamics.
* getFGDynamics.m Contains the control-affine $f(x) + g(x)u$ separation of the dynamics.
* ThingsToFix.txt Contains development notes, current issues, and planned improvements.
