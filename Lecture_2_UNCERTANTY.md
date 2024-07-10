
# Probability.
 
   * Uncertainty can be represented as a number of events and the likelihood, or probability, of each of them happening.

+ The probabilities of every possible event, when summed together, are equal to 1.
![alt text](/home/code/Downloads/lotp.png)

### Axioms in Probability

   * 0 < P(ω) < 1: every value representing probability must range between 0 and 1.

    - [ Zero ] is an ``impossible`` event-, like rolling a standard die and getting a 7.
    
    - [ One ] is an event that is ``certain`` to happen, like rolling a standard die and    getting a value less than 10.
    
    - In general, the higher the value, the more likely the event is to happen.

## Unconditional Probability.

   * for example rolling a dice an ask question about is an ``Unconditional Prob cos It did Not Depend on the PREVIOUS Event ``

## Conditional Probability.
   
   * Conditional probability is expressed using the following notation:`` P(a | b)``, meaning `` “the probability of event a occurring given that we know event b to have occurred,” ``

   * or, more succinctly, “the probability of a given b.” Now we can ask questions like what is the probability of rain today given that it rained yesterday 
   ``P(rain today | rain yesterday)``, or what is the probability of the patient having the disease given their test results ``P(disease | test results)``.


+ Mathematically, to compute the conditional probability of a given b, we use the following formula:
![alt text](conditional.png)

   * To put it in words, the probability that a given b is true is equal to the probability of a and b being true, divided by the probability of b. An intuitive way of reasoning about this is the thought “we are interested in the events where both a and b are true (the numerator), but only from the worlds where we know b to be true (the denominator).” Dividing by b restricts the possible worlds to the ones where b is true. The following are algebraically equivalent forms to the formula above:


 ## Random Variables. 

   *  random variable is a variable in probability theory with a domain of possible values that it can take on. For example, to represent possible outcomes when rolling a die, we can define a random variable Roll, that can take on the values {0, 1, 2, 3, 4, 5, 6}. To represent the status of a flight, we can define a variable Flight that takes on the values {on time, delayed, canceled}.
   
   * Often, we are interested in the probability with which each value occurs. We represent this using a probability distribution. For example,

            *. P(Flight = on time) = 0.6
            
            *. P(Flight = delayed) = 0.3
            
            *. P(Flight = canceled) = 0.1


    * A probability distribution can be represented more succinctly as a ``vector``. For example, 
    - P(Flight) = < 0.6, 0.3, 0.1 >. 
    
    For this notation to be interpretable, the values have a set order (in our case, on time, delayed, canceled).

## Independence

   * for Example Rolling a 2 Dice, the ``Result is  Independent from each other `` 

   * Rolling a 4 with the first die does not influence the value of the second die that we roll. 
   This is ``opposed to dependent events, like clouds in the morning and rain in the afternoon.`` If it is cloudy in the morning, it is more likely that it will rain in the morning, so these events are dependent.

   * Independence can be defined mathematically: events a and b are independent if and only if the probability of a and b is equal to the probability of a times the probability of b: 
      - P(a ∧ b) = P(a)P(b).

# Bayes’ Rule
   
   * Bayes’ rule is commonly used in probability theory to compute conditional probability. In words, Bayes’ rule says that the probability of b given a is equal to the probability of a given b, times the probability of b, divided by the probability of a.

   ![alt text](bayesrule.png)

   * For example, we would like to`` compute the probability of it raining in the afternoon if there are clouds in the morning, or P(rain | clouds)``. We start with the following information:

        *. 80% of rainy afternoons start with cloudy mornings, or P(clouds | rain).
        
        *. 40% of days have cloudy mornings, or P(clouds).
        
        *. 10% of days have rainy afternoons, or P(rain).

    * Applying Bayes’ rule, ``we compute (0.1)(0.8)/(0.4) = 0.2. That is, the probability that it rains in the afternoon given that it was cloudy in the morning is 20%``.

    
