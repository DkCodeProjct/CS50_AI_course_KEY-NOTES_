
# Backtracking Search

   * Backtracking  is a type of a search algorithm that takes into account the structure of a constraint satisfaction search problem. In general, it is a recursive function that attempts to continue assigning values as long as they satisfy the constraints. If constraints are violated, it tries a different assignment. Let’s look at the pseudocode for it:



- function Backtrack(assignment, csp):

 -------------------------
        if assignment complete:
            return assignment
        var = Select-Unassigned-Var(assignment, csp)
        for value in Domain-Values(var, assignment, csp):
            if value consistent with assignment:
                add {var = value} to assignment
                result = Backtrack(assignment, csp)
                if result ≠ failure:
                    return result
                remove {var = value} from assignment
        return failurs
 
 -------------------------

   *  backtracking, attempts to find a solution to a constraint satisfaction problem by assigning values to variables one at a time. If an assignment is complete and satisfies all constraints, it returns the solution. 
   
   * If not, it assigns a value to an unassigned variable and recursively checks if the resulting assignment works. If it leads to failure, the algorithm backtracks by removing the last assignment and trying a different value. This process continues until a solution is found or all possibilities have been exhausted, indicating no solution exists.

  
   * - **Backtracking Algorithm**: Begins with an empty assignment, assigns values to variables one by one, and checks if the assignments satisfy the constraints. If an assignment fails, the algorithm backtracks and tries a different value. If all possible assignments fail, the problem is unsolvable.

   * - **Maintaining Arc-Consistency (MAC)**: Combines backtracking with the AC-3 algorithm. After each new assignment in backtracking, the MAC algorithm enforces arc consistency by checking the consistency of arcs related to the newly assigned variable. This approach increases efficiency by reducing the search space and avoiding unnecessary backtracking.



   * :: function Backtrack(assignment, csp):
  ---------------------

        if assignment complete:
            return assignment
        var = Select-Unassigned-Var(assignment, csp)
        for value in Domain-Values(var, assignment, csp):
            if value consistent with assignment:
                add {var = value} to assignment
                inferences = Inference(assignment, csp)
                if inferences ≠ failure:
                    add inferences to assignment
                result = Backtrack(assignment, csp)
                if result ≠ failure:
                    return result
                remove {var = value} and inferences from assignment
        return failure
 --------------------

