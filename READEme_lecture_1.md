# Lecture 1

## Knowledge

### Knowledge-Based Agents

Knowledge-based agents are agents that reason by operating on internal representations of knowledge.

**What does “reasoning based on knowledge to draw a conclusion” mean?**

Let's start answering this with a Harry Potter example. Consider the following sentences:

1. If it didn’t rain, Harry visited Hagrid today.
2. Harry visited Hagrid or Dumbledore today, but not both.
3. Harry visited Dumbledore today.

Based on these three sentences, we can answer the question, “Did it rain today?”, even though none of the individual sentences tells us directly about whether it rained today. Here is how we can go about it:

- Looking at sentence 3, we know that Harry visited Dumbledore.
- Looking at sentence 2, we know that Harry visited either Dumbledore or Hagrid, and thus we can conclude:
  - Harry did not visit Hagrid.
- Now, looking at sentence 1, we understand that if it didn’t rain, Harry would have visited Hagrid. However, knowing that Harry did not visit Hagrid, we conclude:
  - It rained today.

To come to this conclusion, we used logic. Today’s lecture explores how AI can use logic to reach new conclusions based on existing information.

### Sentence

A sentence is an assertion about the world in a knowledge representation language. A sentence is how AI stores knowledge and uses it to infer new information.

## Propositional Logic

Propositional logic is based on propositions, statements about the world that can be either true or false, as in sentences 1-3 above.

### Propositional Symbols

Propositional symbols are most often letters (P, Q, R) that are used to represent a proposition.

### Logical Connectives

Logical connectives are logical symbols that connect propositional symbols in order to reason in a more complex way about the world.

#### NOT (¬)

> “It is raining,” then ¬P: “It is not raining”.

| P     | ¬P    |
|-------|-------|
| false | true  |
| true  | false |

#### AND (∧)

Connects two different propositions. When these two propositions, P and Q, are connected by ∧, the resulting proposition P ∧ Q is true only in the case that both P and Q are true.

| P     | Q     | P ∧ Q |
|-------|-------|-------|
| false | false | false |
| false | true  | false |
| true  | false | false |
| true  | true  | true  |

#### OR (∨)

Is true as long as either of its arguments is true. This means that for P ∨ Q to be true, at least one of P or Q has to be true.

| P     | Q     | P ∨ Q |
|-------|-------|-------|
| false | false | false |
| false | true  | true  |
| true  | false | true  |
| true  | true  | true  |

#### Implication (→)

Represents a structure of “if P then Q.” For example, if P: “It is raining” and Q: “I’m indoors”, then P → Q means “If it is raining, then I’m indoors.” In the case of P implies Q (P → Q), P is called the antecedent and Q is the consequent.

| P     | Q     | P → Q |
|-------|-------|-------|
| false | false | true  |
| false | true  | true  |
| true  | false | false |
| true  | true  | true  |

#### Biconditional (↔)

Is an implication that goes both directions. You can read it as “if and only if.” P ↔ Q is the same as P → Q and Q → P taken together. For example, if P: “It is raining.” and Q: “I’m indoors,” then P ↔ Q means that “If it is raining, then I’m indoors,” and “if I’m indoors, then it is raining.” This means that we can infer more than we could with a simple implication. If P is false, then Q is also false; if it is not raining, we know that I’m also not indoors.

| P     | Q     | P ↔ Q |
|-------|-------|-------|
| false | false | true  |
| false | true  | false |
| true  | false | false |
| true  | true  | true  |



