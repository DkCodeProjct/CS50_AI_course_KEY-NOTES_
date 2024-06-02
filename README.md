# Lecture 0: Search

## Artificial Intelligence

**Artificial Intelligence (AI):** Covers a range of techniques that appear as sentient behavior by the computer. For example, AI is used to recognize faces in photographs on your social media, beat the World’s Champion in chess, and process your speech when you speak to Siri or Alexa on your phone.

In this course, we will explore some of the ideas that make AI possible:

## Search

**Finding a solution to a problem:** Like a navigator app that finds the best route from your origin to the destination, or like playing a game and figuring out the next move.

### Key Concepts

- **Knowledge**
  - Representing information and drawing inferences from it.

- **Uncertainty**
  - Dealing with uncertain events using probability.

- **Optimization**
  - Finding not only a correct way to solve a problem, but a better—or the best—way to solve it.

- **Learning**
  - Improving performance based on access to data and experience. For example, your email is able to distinguish spam from non-spam mail based on past experience.

- **Neural Networks**
  - A program structure inspired by the human brain that is able to perform tasks effectively.

- **Language**
  - Processing natural language, which is produced and understood by humans.

## Search Problems

Search problems involve an agent that is given an initial state and a goal state, and it returns a solution of how to get from the former to the latter. A navigator app uses a typical search process, where the agent (the thinking part of the program) receives as input your current location and your desired destination, and, based on a search algorithm, returns a suggested path. However, there are many other forms of search problems, like puzzles or mazes.

### Components of Search Problems

- **Agent**
  - An entity that perceives its environment and acts upon that environment. In a navigator app, for example, the agent would be a representation of a car that needs to decide on which actions to take to arrive at the destination.

- **State**
  - A configuration of an agent in its environment. For example, in a 15 puzzle, a state is any one way that all the numbers are arranged on the board.

- **Initial State**
  - The state from which the search algorithm starts. In a navigator app, that would be the current location.

- **Actions**
  - Choices that can be made in a state. More precisely, actions can be defined as a function. Upon receiving state `s` as input, `Actions(s)` returns as output the set of actions that can be executed in state `s`. For example, in a 15 puzzle, the actions of a given state are the ways you can slide squares in the current configuration (4 if the empty square is in the middle, 3 if next to a side, 2 if in the corner).

- **Transition Model**
  - A description of what state results from performing any applicable action in any state. More precisely, the transition model can be defined as a function. Upon receiving state `s` and action `a` as input, `Results(s, a)` returns the state resulting from performing action `a` in state `s`. For example, given a certain configuration of a 15 puzzle (state `s`), moving a square in any direction (action `a`) will bring to a new configuration of the puzzle (the new state).

- **State Space**
  - The set of all states reachable from the initial state by any sequence of actions. For example, in a 15 puzzle, the state space consists of all the 16!/2 configurations on the board that can be reached from any initial state. The state space can be visualized as a directed graph with states, represented as nodes, and actions, represented as arrows between nodes.

- **Goal Test**
  - The condition that determines whether a given state is a goal state. For example, in a navigator app, the goal test would be whether the current location of the agent (the representation of the car) is at the destination. If it is — problem solved. If it’s not — we continue searching.

- **Path Cost**
  - A numerical cost associated with a given path. For example, a navigator app does not simply bring you to your goal; it does so while minimizing the path cost, finding the fastest way possible for you to get to your goal state.