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
# SEARCH
- Agent:
    * in maze solve the algorithm would be an agent, try to find the path from a to be taking actions 

- State:
    * numbers that orderd in 15 Puzzle board is an state,
    - initial state:
        * in maze the point A or starting point would be an innitial state 
- Action:
    * in 15 puzzle the you can slide squres left right etc, in given state this would be an action ,,,
    { 
        - Action(S) - // get state[s] as input and returns as output the set of actions that can be excuted in state[s]
    }

- Transitional Model:
    * in 15 puzzle you slide squres or Take Action(s) in one state or squre, and the result or taking these actions or sliding squres Can Be An [Transitional Model].

    {
        - Result(s, a) - // recive state[s] and action[a] as inputs and returns the [state] resulting from performing action[a] in state[s]
    }

- State Space:
    *  in a 15 puzzle, the state space consists of all the 16!/2 configurations on the board that can be reached from any initial state. 
![alt text](image.png)
