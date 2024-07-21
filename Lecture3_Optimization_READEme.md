# Optimization

   * Optimization is choosing the best option from a set of possible options. 

   ---------------------------------------------------------

## Local Search.

   * Local search is a search algorithm `that maintains a single node and searches by moving to a neighboring node`.   
   if we wanted to find the quickest way to the goal, local search is interested in finding the best answer to a question. Often, local search will bring to an `answer that is not optimal but “good enough,”` conserving computational power. 

img__house_image-here__----~~~~~

   * In this illustration, we are seeing a possible configuration of houses and hospitals. The distance between them is measured using Manhattan distance
   ...and the sum of the distances from each house to the nearest hospital is 17. 
   ...We call this the cost, because we try to minimize this distance. 

   * :Abstracting this concept, we can represent each configuration of houses and hospitals as the state-space landscape below. Each of the bars in the picture represents a value of a state, which in our example would be the cost of a certain configuration of houses and hospitals.

___landscape img here

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

      [[ more Images would be on online 
      -local minima/maxima-  ]]


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

      - function Simulated-Annealing(problem, max):
            current = initial state of problem
            for t = 1 to max:
               T = Temperature(t)
               neighbor = random neighbor of current
               ΔE = how much better neighbor is than current
               if ΔE > 0:
                     current = neighbor
               with probability e^(ΔE/T) set current = neighbor
            return current

