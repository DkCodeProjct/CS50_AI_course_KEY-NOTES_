# Knowledge Engineering

---------------------------------------------------------

// Add the clues to the KB
knowledge = And(

    // Start with the game conditions: one item in each of the three categories has to be true.
    Or(mustard, plum, scarlet),
    Or(ballroom, kitchen, library),
    Or(knife, revolver, wrench),

    // Add the information from the three initial cards we saw
    Not(mustard),
    Not(kitchen),
    Not(revolver),

    // Add the guess someone made that it is Scarlet, who used a wrench in the library
    Or(Not(scarlet), Not(library), Not(wrench)),

    // Add the cards that we were exposed to
    Not(plum),
    Not(ballroom)
)

// More Of These on cs50AI Notes---->

---------------------------------------------------------

# Inference Rules

- Model Checking is not an efficient algorithm because it has to consider every possible model before giving the answer (a reminder: a query R is true if under all the models (truth assignments) where the KB is true, R is true as well). Inference rules allow us to generate new information based on existing knowledge without considering every possible model.

    `Inference rules are usually represented using a horizontal bar that separates the top part, the premise, from the bottom part, the conclusion. The premise is whatever knowledge we have, and the conclusion is what knowledge can be generated based on the premise.`

    if ksi rich, then he is richCunt

            ksi is Rich
        ____________________

          ksi is a richCunt 
- In this example, our premise consists of the following propositions:

    If ksi rich, then ksi is a richCunt.
    Ksi is rich.

- Based on this, most reasonable humans can conclude that.
    
    Ksi is rich cunt


## Modus Ponens
- The type of inference rule we use in this example is Modus Ponens, which is a fancy way of saying that if we know an implication and its antecedent to be true, then the consequent is true as well.
    
    `if A is true then B is true as well,`

## And Elimination
    - If an And proposition is true, then any one atomic proposition within it is true as well. For example:
        
        `if ksi is freind with randolf and simonMinter,
        we can conclude that ksi is freinds with simon`

## Double Negation Elimination

    - A proposition that is negated twice is true. For example, consider the proposition, [' it is not true that ksi is an idiot'], We can parse it the following way: “It is not true that (ksi is an idiot)”, or “¬(ksi is an idiot)”, and, finally “¬(¬(ksi is an IDIOT)).” The two negations cancel each other, marking the proposition “KSI IS AN GENIUS” as true.

## Implication Elimination
    
    - An implication is equivalent to an Or relation between the negated antecedent and the consequent. As an example, the proposition “If ksi is Rich, he is an richCunt” is equivalent to the proposition “(ksi is not rich raining) or (ksi is a richCunt).”

    This one can be a little confusing. However, consider the following truth table:

	
P       Q       P → Q¬  P ∨ Q
false	false	true	true
false	true	true	true
true	false	false	false
true	true	true	true
`
    Since P → Q and ¬P ∨ Q have the same truth-value assignment, we know them to be equivalent logically. Another way to think about this is that an implication is true if either of two possible conditions is met: first, if the antecedent is false, the implication is trivially true (as discussed earlier, in the section on implication). This is represented by the negated antecedent P in ¬P ∨ Q, meaning that the proposition is always true if P is false. Second, the implication is true when the antecedent is true only when the consequent is true as well. That is, if P and Q are both true, then ¬P ∨ Q is true. However, if P is true and Q is not, then ¬P ∨ Q is false.

`

## Biconditional Elimination

    - A biconditional proposition is equivalent to an implication and its inverse with an And connective. For example,:
     
        `` ksi is dumb if and only if he is try to be smart `` is 
        equivalent to (`` if ksi dumb, he's try to be smart`` And ``if ksi is try to be smart , ksi is dumb ``)

## De Morgan’s Law

    - It is possible to turn an And connective into an Or connective. Consider the following proposition: 
        
        "it is not true that both simon and ksi is Rich" From this, it is possible to conclude that "it is not True that ksi is rich" Or 
        "it is not True that simon is Rich"

        - That is, for the And proposition earlier to be true, at least one of the propositions in the Or propositions must be true.
    

    ``Similarly, it is possible to conclude the reverse. Consider the proposition “It is not true that ksi and simon both rich.” This can be rephrased as “ksi is not rich” And “simon is not rich.”``
        
## Distributive Property

    A proposition with two elements that are grouped with And or Or connectives can be distributed, or broken down into, smaller units consisting of And and Or.


#### Knowledge and Search Problems

- Inference can be viewed as a search problem with the following properties:

   *  Initial state: starting knowledge base
   *  Actions: inference rules
   *  Transition model: new knowledge base after inference
   *  Goal test: checking whether the statement that we are trying to prove is in the KB
   *  Path cost function: the number of steps in the proof

This shows just how versatile search algorithms are, allowing us to derive new information based on existing knowledge using inference rules.
