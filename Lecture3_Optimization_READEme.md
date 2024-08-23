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

   
   * Consider another example. `Each of students 1-4 is taking three courses from A, B, …, G. Each course needs to have an exam`, and the possible days for exams are Monday, Tuesday, and Wednesday. However, `the same student can’t have two exams on the same day. In this case, the variables are the courses,` the domain is the days, and `the !
constraints are which courses can’t be scheduled to have an exam on the same day because the same student is taking them.` This can be visualized as follows:

[constraintsatisfaction1](https://github.com/user-attachments/assets/15b76847-7b53-4f2b-ad10-534b0096a125)


   * This problem can be solved using constraints that are represented as a graph. Each node on the graph is a course, and an edge is drawn between two courses if they can’t be scheduled on the same day. In this case, the graph will look this:


![constraintsatisfaction2](https://github.com/user-attachments/assets/2231db55-828e-43ba-9d48-ae876f1e20e9)


   * A few more terms worth knowing about constraint satisfaction problems:

    1. A Hard Constraint is a constraint that must be satisfied in a correct solution.
    
    2. A Soft Constraint is a constraint that expresses which solution is preferred over others.
    
    3. A Unary Constraint is a constraint that involves only one variable. In our example, a unary constraint would be saying that course A can’t have an exam on Monday {A ≠ Monday}.
    
    4. A Binary Constraint is a constraint that involves two variables. This is the type of constraint that we used in the example above, saying that some two courses can’t have the same value {A ≠ B}.


# Node Consistency

   * Node consistency is when all the `values in a variable’s domain satisfy the variable’s unary constraints.`

      : **For example,:
          let’s take two courses, A and B. The domain for each course is {Monday, Tuesday, Wednesday}, and the constraints are `{A ≠ Mon, B ≠ Tue, B ≠ Mon, A ≠ B}.` Now, neither A nor B is consistent, because the existing constraints prevent them from being able to take every value that’s in their domain. However, `if we remove Monday from A’s domain, then it will have node consistency.` To achieve node consistency in B, we will have to remove both Monday and Tuesday from its domain.

# Arc Consistency

   * Arc consistency is when all the v`alues in a variable’s domain satisfy the variable’s binary constraints (note that we are now using “arc” to refer to what we previously referred to as “edge”).` In other words, to make `X arc-consistent with respect to Y,` remove elements from X’s domain until every choice for X has a possible choice for Y.


-----------------------------------
            
            
            function Revise(csp, X, Y):

               revised = false
               for x in X.domain:
                  if no y in Y.domain satisfies constraint for (X,Y):
                        delete x from X.domain
                        revised = true
               return revised


-----------------------------------


* This algorithm, known as AC-3 (Arc Consistency 3), ensures that all arcs in a constraint satisfaction problem are consistent by repeatedly applying the Revise algorithm. It checks if values in the domain of variable X can be paired with values in the domain of variable Y according to the constraints. 
  
* If X's domain is revised (changed), it rechecks consistency with X's neighbors. The algorithm simplifies the problem by ensuring arc consistency but may not fully solve it, especially in problems with complex, interconnected constraints.

   *  This algorithm starts with tracking whether any change was made to X’s domain, using the variable revised. Then, the code repeats for every value in X’s domain and sees if Y has a value that satisfies the constraints. If yes, then do nothing, if not, remove this value from X’s domain.

   * Often we are interested in making the whole problem arc-consistent and not just one variable with respect to another. In this case, we will use an algorithm called 
   
   `AC-3, which uses Revise:`

-----------------------------------
         function AC-3(csp):

         queue = all arcs in csp
         while queue non-empty:
            (X, Y) = Dequeue(queue)
            if Revise(csp, X, Y):
                  if size of X.domain == 0:
                     return false
                  for each Z in X.neighbors - {Y}:
                     Enqueue(queue, (Z,X))
         return true

-----------------------------------






