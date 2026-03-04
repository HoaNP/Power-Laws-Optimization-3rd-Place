# Power Laws: Optimizing Demand-side Strategies (3rd Place Solution)

This repository contains the **3rd place winning solution** for the [Power Laws: Optimizing Demand-side Strategies](https://www.drivendata.org/competitions/53/optimize-photovoltaic-battery/) competition hosted by DrivenData.

## Achievement
* **Rank:** 3rd Place worldwide out of 350+ participants.
* **Winner Spotlight:** Featured in the official DrivenData blog post: [Meet the Winners: Power Laws Optimization](https://drivendata.co/blog/power-laws-optimization-winners).

## Project Overview
The goal of this competition was to develop an algorithm to optimize the charging and discharging of a battery system. The objective is to minimize electricity costs for a building by effectively using solar energy (PV) and managing grid consumption based on load forecasts.

## Technical Approach
Our solution focuses on robust optimization using Linear Programming to handle the uncertainty of energy forecasts.

### 1. Linear Programming Model
We formulated the battery control problem as a Linear Programming (LP) model using **Google OR-Tools** with the **GLOP solver**.
* **Objective:** Minimize the total cost of energy purchased from the grid over a given horizon.
* **Constraints:** We integrated battery capacity limits, charge/discharge efficiency, and power limits as primary constraints.

### 2. Strategy for Uncertainty (Scattering)
To mitigate the risk of forecast errors, we implemented a "scattering" technique. Instead of aggressive charging or discharging based on potentially inaccurate future points, the energy is distributed across multiple steps to avoid superfluous grid purchases.

### 3. Data Refinement
* **PV Forecast Cleaning:** We implemented logic to filter noise in PV forecasts, such as setting values below 20 (often found at midnight in raw forecasts) to zero to prevent irrational battery behavior.

## Repository Structure
* `solution/`: Core logic including `battery_controller.py`.
* `simulation_engine/`: The environment provided by DrivenData to test and evaluate the model.
* `docs/`: Full technical documentation and methodology write-up.

## How to Run
1.  **Install dependencies:**
    ```bash
    pip install ortools
    ```
    *(Note: See `simulation_engine/requirements.txt` for full environment setup)*
2.  **Execute simulation:**
    Navigate to the `simulation_engine` directory and run the engine to see the controller in action.

## Authors
* **Hoa Nguyen Phuong** - Computer Science Graduate, FPT University.
* **Huyen Tran Ngoc Nhat** - Computer Science Graduate, FPT University.
