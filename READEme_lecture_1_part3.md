# Resolution

* Resolution is a powerful inference rule that states that if one of two atomic propositions in an Or proposition is false, the other has to be true. 

    + for example:
    . “Logan is in UK” Or “Ksi is in Uk”, in addition to the proposition “Logan is not in  UK,” . we can conclude that “Ksi is in UK.” More formally, we can define resolution the following way: 

        - 
            P v Q

              ¬P
           _________
               Q
        -
    
    * Resolution relies on Complementary Literals, two of the same atomic propositions where one is negated and the other is not, such as P and ¬P.


    * Resolution can be further generalized. Suppose that in addition to the proposition “Logan is in the UK” Or “ Ksi is in UK”, we also know that “Logan is not in the UK ” Or “Jake is a Cunt” We can infer from this, using resolution, that “Ksi is in UK” Or “jake is a Cunt.” To put it in formal terms:

        -
            P v Q
            ¬P v R
          ___________
            Q v R
        -
###### A Clause is a disjunction of literals (a propositional symbol or a negation of a propositional symbol, such as P, ¬P). 
    * A disjunction consists of propositions that are connected with an Or logical connective (P ∨ Q ∨ R). A conjunction, on the other hand, consists of propositions that are connected with an And logical connective (P ∧ Q ∧ R). Clauses allow us to convert any logical statement into a Conjunctive Normal Form (CNF), which is a conjunction of clauses, for example: (A ∨ B ∨ C) ∧ (D ∨ ¬E) ∧ (F ∨ G).

    ------------------------------------------
 - Steps in Conversion of Propositions to Conjunctive Normal Form

   *  Eliminate biconditionals
        Turn (α ↔ β) into (α → β) ∧ (β → α).
    
   *  Eliminate implications
        Turn (α → β) into ¬α ∨ β.
    
   *  Move negation inwards until only literals are being negated (and not clauses), using De Morgan’s Laws.
        Turn ¬(α ∧ β) into ¬α ∨ ¬β

    -------------------------------------------
- Here’s an example of converting (P ∨ Q) → R to Conjunctive Normal Form:

    (P ∨ Q) → R
    ¬(P ∨ Q) ∨ R /Eliminate implication
    (¬P ∧ ¬Q) ∨ R /De Morgan’s Law
    (¬P ∨ R) ∧ (¬Q ∨ R) /Distributive Law
    
    
    `At this point, we can run an inference algorithm on the conjunctive normal form. Occasionally, through the process of inference by resolution, we might end up in cases where a clause contains the same literal twice. In these cases, a process called factoring is used, where the duplicate literal is removed. For example, (P ∨ Q ∨ S) ∧ (¬P ∨ R ∨ S) allow us to infer by resolution that (Q ∨ S ∨ R ∨ S). The duplicate S can be removed to give us (Q ∨ R ∨ S)`

    * Resolving a literal and its negation, i.e. ¬P and P, gives the empty clause ().  The empty clause is always false, and this makes sense because it is impossible that both P and ¬P are true. This fact is used by the resolution algorithm.

    ____________________________________
    
    
    - To determine if KB ⊨ α:
        Check: is (KB ∧ ¬α) a contradiction?
            If so, then KB ⊨ α.
            Otherwise, no entailment.
    
    ____________________________________

    * Proof by contradiction is a tool used often in computer science. If our knowledge base is true, and it contradicts ¬α, it means that ¬α is false, and, therefore, α must be true. More technically, the algorithm would perform the following actions:

    ---------------------------------------
- To determine if KB ⊨ α:

    * Convert (KB ∧ ¬α) to Conjunctive Normal Form.
    * Keep checking to see if we can use resolution to produce a new clause.
    *    If we ever produce the empty clause (equivalent to False), congratulations! We have arrived at a contradiction, thus proving that KB ⊨ α.
    *    However, if contradiction is not achieved and no more clauses can be inferred, there is no entailment.

    ---------------------------------------


* Here is an example that illustrates how this algorithm might work:
    
    ---------------------------------------
    Does (A ∨ B) ∧ (¬B ∨ C) ∧ (¬C) entail A?

    First, to prove by contradiction, we assume that A is false. Thus, we arrive at (A ∨ B) ∧ (¬B ∨ C) ∧ (¬C) ∧ (¬A).
    Now, we can start generating new information. Since we know that C is false (¬C), the only way (¬B ∨ C) can be true is if B is false, too. Thus, we can add (¬B) to our KB.
    Next, since we know (¬B), the only way (A ∨ B) can be true is if A is true. Thus, we can add (A) to our KB.
    Now our KB has two complementary literals, (A) and (¬A). We resolve them, arriving at the empty set, (). The empty set is false by definition, so we have arrived at a contradiction.
    ---------------------------------------

# First Order Logic.

* First order logic is another type of logic that allows us to express more complex ideas more succinctly than propositional logic. First order logic uses two types of symbols: Constant Symbols and Predicate Symbols. Constant symbols represent objects, while predicate symbols are like relations or functions that take an argument and return a true or false value.


