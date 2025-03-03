# msc_ai_assigment

This description was generated using Chatgpt introducing the code and giving instructions to summirize our algorithm we have verified the content of this and is only used for oral explanation porpuses;

# Behavior of Genetic Algorithm (GA) for Traveling Salesman Problem (TSP)

## 1. **Initialization Phase** (`__init__` method)

- **Input Parameters**:
  - `nodes_list`: A list of cities (nodes).
  - `edges_w_list`: A list of edges with weights representing the distances between cities.
  - `population_number`: The size of the population, or the number of solutions generated at the start.
  - **Optional Parameters**:
    - **Crossover threshold** (`crossover_thd`): Controls how solutions are mixed during crossover.
    - **Mutation threshold** (`mutation_thd`): A probability (usually between 0 and 1) that dictates how often mutations (random changes) happen in solutions.
    - **Exploration terms**: The number of solutions randomly selected during the fitness evaluation phase to diversify the population.
  
- **Main Behavior**:
  1. **Create an initial population**: The algorithm generates a population of random potential solutions, where each solution is a random sequence (permutation) of cities.
  2. **Store costs between cities**: A dictionary is created to store the distance between each pair of cities. This will be used to evaluate the quality of each solution (the total travel distance).

## 2. **Step Phase** (`step` method)

This is the main phase where the algorithm evolves the population to find better solutions. Each step involves the following:

### 1. **Crossover and Mutation**
   - **Crossover**:
     - The algorithm systematically selects **all possible pairs** of solutions (parents) from the current population using **combinatorial pairing**.
     - For each pair of solutions, a crossover operation exchanges part of the sequence of cities from both solutions to create two new offspring. This systematically introduces new variations by exploring all pairwise combinations of routes.
   - **Mutation**:
     - For each offspring produced by the crossover, there is a random chance (based on `mutation_thd`) that two cities in the solution are swapped. 
     - This introduces randomness and helps explore new potential solutions that might not have been generated by the crossover process alone.

### 2. **Cost Evaluation**
   - The algorithm evaluates the quality of each solution by calculating the **total travel distance** (cost) for the path represented by the solution.
   - The goal is to **minimize** the total cost, meaning that solutions with shorter paths have better fitness.

### 3. **Fitness Calculation**
   - The fitness of each solution is determined based on its cost: the **lower the cost**, the **higher the fitness**.
   - **Random Exploration**:
     - A number of solutions are **randomly selected** based on the `exploration_terms` parameter.
     - These randomly selected solutions are guaranteed a chance to survive to the next step, regardless of their fitness, to ensure diversity in the population. This helps the algorithm avoid local optima and promotes exploration of different solutions.

### 4. **Selection**
   - The population is sorted by fitness, and the best-performing solutions are selected to form the new population for the next step.
   - Solutions selected through **random exploration** get a chance to remain in the population, even if they are not the fittest, to ensure diversity.

### 5. **Iteration**
   - The process of **crossover**, **mutation**, **cost evaluation**, **fitness calculation**, and **selection** is repeated for multiple steps.
   - Each step refines the population by gradually improving the overall quality of the solutions, i.e., reducing the total travel distance.

## Random Elements in the Algorithm
- **Random Initial Population**: The algorithm starts with a randomly generated population of potential solutions, providing a wide variety of initial candidates for the optimization process.
- **Mutation**: During the mutation step, there is a random chance of modifying a solution by swapping two cities. This introduces variability and helps the algorithm explore different paths.
- **Random Exploration Terms**: A number of solutions are randomly selected and preserved during the fitness calculation phase, regardless of their cost. This ensures diversity and prevents the algorithm from converging too quickly to suboptimal solutions.

---

### Summary
This Genetic Algorithm works iteratively to optimize the Traveling Salesman Problem by refining a population of potential solutions through:
1. **Systematic Crossover**: Combining all possible pairs of solutions to produce offspring.
2. **Random Mutation**: Introducing variability through random swaps in the cities.
3. **Cost Evaluation**: Assessing the total travel distance for each solution.
4. **Fitness Calculation and Random Exploration**: Assigning fitness based on cost and injecting randomness to ensure diversity.

This combination of crossover, mutation, and fitness-driven selection enables the algorithm to gradually converge toward an optimal or near-optimal solution.
