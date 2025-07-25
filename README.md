# Optimizing Smart Grid Energy Distribution

This repository contains a Python-based Jupyter Notebook that implements a Genetic Algorithm (GA) to optimize energy distribution in a simulated smart grid. The goal is to find the most efficient ways to allocate energy from various sources to different demand points over time, minimizing costs and transmission losses while ensuring all demand is met.

## Purpose of the Code

The `GeneticAlgo.ipynb` notebook serves the following purposes:

* **Smart Grid Optimization:** It models a simplified smart grid scenario with multiple energy sources, nodes (demand points), and time slots (e.g., a 24-hour cycle).
* **Genetic Algorithm Implementation:** It demonstrates how a Genetic Algorithm can be applied to solve the complex energy allocation problem, considering factors like source capacities, demand, energy costs, and transmission losses.
* **Multi-Objective Fitness Function:** The code features a sophisticated fitness function that balances multiple objectives, including minimizing operational cost, transmission loss, unmet demand, capacity violations, and over-fulfillment of demand.
* **Parallel Computing:** It showcases the use of parallel processing (via `pygad`'s built-in multiprocessing capabilities) to speed up the Genetic Algorithm's execution, particularly the computationally intensive fitness evaluation step.
* **Baseline Comparison:** A greedy energy allocation algorithm is implemented as a baseline to highlight the superior optimization capabilities of the Genetic Algorithm.
* **Performance Analysis:** The notebook analyzes and visualizes the GA's convergence, and compares the execution times of the parallel GA against serial execution, as well as comparing the GA's performance metrics against the greedy baseline.

## Installation

To run this code, you will need Python 3 and the following libraries.

1.  **Clone the repository (if you haven't already):**
    ```bash
    git clone [https://github.com/RijaBhomi/GeneticAlgorithm.git](https://github.com/RijaBhomi/GeneticAlgorithm.git)
    cd your-repo-name
    ```

2.  **Install the necessary Python packages:**
    ```bash
    pip install numpy pygad matplotlib seaborn
    ```

## Usage

The main part of the project is the Jupyter Notebook.

1.  **Start Jupyter Notebook:**
    ```bash
    jupyter notebook
    ```
2.  **Open the Notebook:** In your web browser, navigate to and open `GeneticAlgo.ipynb`.
3.  **Run All Cells:** Execute all cells in the notebook sequentially (e.g., by clicking "Cell" -> "Run All" in the Jupyter interface).

The notebook will:
* Set up smart grid parameters (number of nodes, sources, time slots).
* Generate synthetic demand, source capacity, cost, and transmission loss data.
* Define the core `fitness_func` for the Genetic Algorithm.
* Implement a `greedy_allocation_baseline` for comparison.
* Configure and run the Genetic Algorithm using `pygad`, with parallel processing enabled.
* Execute the greedy baseline algorithm.
* Print detailed results, including objective values, execution times, and a breakdown of costs for both the GA and the greedy approach.
* Display various plots, such as the GA convergence curve and energy distribution visualizations.

## Key Code Sections

The notebook is structured with clear headings, but here's a brief overview of the core components:

* **Parameter and Data Setup:** Defines grid dimensions (`num_nodes`, `num_sources`, `time_slots`) and generates all synthetic data like `demand`, `source_capacity`, `source_cost`, and `transmission_loss`.
* **`fitness_func(ga_instance, solution, solution_idx)`:** This function is the heart of the optimization. It decodes the GA's `solution` (chromosome) into energy allocations and calculates a weighted fitness score based on total cost, total loss, unmet demand, capacity violations, and over-fulfillment.
* **`greedy_allocation_baseline()`:** Implements a simpler, heuristic approach to energy allocation for comparison.
* **PyGAD GA Instance Setup:** Configures the Genetic Algorithm (`pygad.GA`) with parameters like `num_generations`, `sol_per_pop`, `mutation_percent_genes`, and importantly, `parallel_processing` to enable multi-core execution.
* **Execution and Results:** Runs both the GA and the greedy algorithm, then prints and visualizes their performance metrics and the resulting optimal (or near-optimal) energy distribution.
