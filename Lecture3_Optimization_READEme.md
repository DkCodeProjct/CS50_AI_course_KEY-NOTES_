# Optimization

   * Optimization is choosing the best option from a set of possible options. 

   ---------------------------------------------------------

## Local Search.

   * Local search is a search algorithm `that maintains a single node and searches by moving to a neighboring node`.   
   if we wanted to find the quickest way to the goal, local search is interested in finding the best answer to a question. Often, local search will bring to an `answer that is not optimal but “good enough,”` conserving computational power. 
   
![hospitals1](https://github.com/user-attachments/assets/8b27d60c-da06-4e88-ade0-fc9383901b35)

   * In this illustration, we are seeing a possible configuration of houses and hospitals. The distance between them is measured using Manhattan distance
   ...and the sum of the distances from each house to the nearest hospital is 17. 
   ...We call this the cost, because we try to minimize this distance. 

   * :Abstracting this concept, we can represent each configuration of houses and hospitals as the state-space landscape below. Each of the bars in the picture represents a value of a state, which in our example would be the cost of a certain configuration of houses and hospitals.

![statespace](https://github.com/user-attachments/assets/11aebf8b-557c-407e-8143-3f256e270e86)


   * Going off of this visualization, we can define a few important terms for the rest of our discussion:
      
       + An `Objective Function` is a function that we use to  `maximize the value` of the solution.
      
       +   A `Cost Function` is a function that we use to `minimize the cost` of the solution [[ we want to   minimiz the distance between house and hospotl so the cost would be low ]]

       +     A `Current State` is the state that is currently being considered by the function.

       + A `Neighbor State` is a state that the current state can transition to. 
   
   * Note that the way local search algorithms work is by `considering one node in a current state, and then moving the node to one of the current state’s neighbors`. This is unlike the minimax algorithm, for example, where every single state in the state space was considered recursively.

   ---------------------------------------------------

# Hill Climbing.

   * Hill climbing is one type of a local search algorithm. In this algorithm, `the neighbor states are compared to the current state, and if any of them is better, we change the current node from the current state` to that neighbor state.

   * A hill climbing algorithm will look the following way in pseudocode:

      - function Hill-Climb(problem):
            current = initial state of problem
            repeat:
               neighbor = best valued neighbor of current
               if neighbor not better than current:
                     return current
               current = neighbor


### Local and Global Minima and Maxima.

   * A hill climbing algorithm can get `stuck in local maxima or minima`. A local maximum (plural: maxima) is a state that has a higher value than its neighboring states. As opposed to that, a global maximum is a state that has the highest value of all states in the state-space.

![objectfuntion](https://github.com/user-attachments/assets/55b3b67d-ef41-4267-9087-bfd2ae0b1dff)


#### Hill Climbing Variants.
   
   * `Steepest-ascent`: choose the highest-valued neighbor. This is the standard variation that we discussed above.
   
   * `Stochastic`: choose randomly from higher-valued neighbors. Doing this, we choose to go to any direction that improves over our value. This makes sense if, for example, the highest-valued neighbor leads to a local maximum while another neighbor leads to a global maximum.
   
   * `First-choice`: choose the first higher-valued neighbor.
   
   * `Random-restart`: conduct hill climbing multiple times. Each time, start from a random state. Compare the maxima from every trial, and choose the highest amongst those.
   
   * `Local Beam Search`: chooses the k highest-valued neighbors. This is unlike most local search algorithms in that it uses multiple nodes for the search, and not just one.


# Simulated Annealing

  * Although we have seen variants that can improve hill climbing, but: once the algorithm reaches a local maximum, it stops running. `Simulated annealing `allows the algorithm to `“dislodge” itself if it gets stuck in a local maximum`.

  * Annealing is the process of` heating metal and allowing it to cool slowly`,. This is used as a metaphor for the simulated annealing algorithm, which starts with a high temperature, being more likely to make random decisions, and, as the temperature decreases, it becomes less likely to make random decisions, becoming more “firm.” This mechanism` allows the algorithm to change its state to a neighbor that’s worse than the current state, which is how it can escape from local maxima`.
  
  * The following is pseudocode for simulated annealing:
_______________________________________________________

    function Simulated-Annealing(problem, max):
            current = initial state of problem
            for t = 1 to max:
               T = Temperature(t)
               neighbor = random neighbor of current
               ΔE = how much better neighbor is than current
               if ΔE > 0:
                     current = neighbor
               with probability e^(ΔE/T) set current = neighbor
            return current
  _______________________________________________________

   * algorithm  inputs: `problem and max`, the number of times it should repeat itself. For each iteration, T i`s set using a Temperature function`.  `when t is low: returns a higher value` and when `t is high: lower value in later iterations`. Then, a random neighbor is selected,
   
   * ΔE is  how `better the neighbor state is than the current state`. 
   
   * If the neighbor state is better than the current state (ΔE > 0), as before, we set our current state to be the neighbor state. 
   
   * However, when the neighbor state is worse (ΔE < 0), we still might set our current state to be that neighbor state, and we do so with probability `e^(ΔE/T)`. 
   
   * the  more `negative ΔE` will result in `lower probability of the neighbor state being chosen`, and  `higher the temperature T `the higher  probability that the neighbor state will be chosen. 
   
   * The math behind this is as follows: e is a constant (around 2.72), and ΔE is negative (since this neighbor is worse than the current state). The more negative ΔE, the closer the resulting value to 0. The higher the temperature T is, the closer ΔE/T is to 0, making the probability closer to 1.


### Traveling Salesman Problem

   * In the traveling salesman problem, the task is to connect all points while choosing the shortest possible distance. This is, for example, what delivery companies need to do: find the shortest route from the store to all the customers’ houses and back.

img tsp -------

   * In this case, a neighbor state might be seen as a state where two arrows swap places. Calculating every possible combination makes this problem computationally demanding (having just 10 points gives us 10!, or 3,628,800 possible routes). By using the simulated annealing algorithm, a good solution can be found for a lower computational cost.


# Linear Programming

   * Linear programming is a `family of problems that optimize a linear equation `(an equation of the form y = ax₁ + bx₂ + …).

   * Linear programming will have the following components:

         + A `cost function` that we want t`o minimize: c₁x₁ + c₂x₂ + … + cₙxₙ. Here, each x₋ is a variable and it is associated with some cost c₋.`
         
         + A `constraint` that’s represented as a `sum of variables that is either less than or equal to a value (a₁x₁ + a₂x₂ + … + aₙxₙ ≤ b)` or precisely `equal to this value (a₁x₁ + a₂x₂ + … + aₙxₙ = b).` In this case, x₋ is a variable, and a₋ is some resource associated with it, and b is how much resources we can dedicate to this problem.
         
         + Individual` bounds on variables` (for example, t`hat a variable can’t be negative) of the form lᵢ ≤ xᵢ ≤ uᵢ.`

   * Consider the following example:

         + Two machines,` X₁ and X₂. X₁ costs $50/hour to run, X₂ costs $80/hour` to run. The goal is to minimize cost. This can be formalized as a cost function: `50x₁ + 80x₂.`

         + X₁ `requires 5 units of labor per hour. X₂ requires 2 units of labor` per hour. 
         
         + Total of 20 units of labor to spend. This can be formalized as a constraint: 5x₁ + 2x₂ ≤ 20.

         + X₁ produces 10 units of output per hour. X₂ produces 12 units of output per hour. Company needs 90 units of output. This is another constraint. Literally, it can be rewritten as` 10x₁ + 12x₂ ≥ 90`. However, constraints need to be of the form `(a₁x₁ + a₂x₂ + … + aₙxₙ ≤ b)` or `(a₁x₁ + a₂x₂ + … + aₙxₙ = b)`. Therefore, we multiply `by (-1) to get to an equivalent equation of the desired form: (-10x₁) + (-12x₂) ≤ -90`.

            ----------------------------------------------------------------

               import scipy.optimize


               // Objective Function: 50x_1 + 80x_2
               // Constraint 1: 5x_1 + 2x_2 <= 20
               // Constraint 2: -10x_1 + -12x_2 <= -90

               output = scipy.optimize.linprog(
                     [50, 80],  # Cost function: 50x_1 + 80x_2
                     AupperBoud = [[5, 2], [-10, -12]], # Coefficients for inequalities
                     BupperBound = [20, 90]  # Constraints for inequalities: 20 and -90
               )

               if output.success:
                  print(f'X1: {round(output.x[0], 2)} hours')
                  print(f'X1: {round(output.x[1], 2)} hours')
               else:
                  print('no solution')

            ----------------------------------------------------------------


## Constraint Satisfaction

   * Constraint Satisfaction problems are a `class of problems where variables need to be assigned values while satisfying some conditions`.

   * Constraints satisfaction problems have the following properties:

         + Set of variables` (x₁, x₂, …, xₙ)`
         + Set of domains for each variable` {D₁, D₂, …, Dₙ}`
         + Set of constraints `C`

   * `Sudoku` can be represented as a constraint satisfaction problem, `where each empty square is a variable`, the domain is the numbers 1-9, and the `constraints are the squares that can’t be equal to each other`.

   



