# Join Probability 

   * Joint probability is the likelihood of multiple events all occurring.

   +  Let us consider the following example, concerning the probabilities of clouds in the morning and rain in the afternoon.:

            ----------------------------
                
                C = cloud
                0.4
                
                C = ¬cloud
                0.6
                
                R = rain
                0.1
                
                R = ¬rain
                0.9

            ----------------------------


   *   Looking at these data, we can’t say whether clouds in the morning 
      are related to the likelihood of rain in the         
      afternoon. To be able to do so, 
      we need to look at the joint probabilities of all the
      possible outcomes of the two variables. We can represent  
      this in a table as follows.:
            
            


         ----------------------------
                                
                C = cloud
                R = rain
                0.08
                R = ¬rain
                0.32
                
                C = ¬cloud
                R = rain
                0.02
                R = ¬rain
                0.58 

        ----------------------------
# Join Probability 

   * Joint probability is the likelihood of multiple events all occurring.

   +  Let us consider the following example, concerning the probabilities of clouds in the morning and rain in the afternoon.:

            ----------------------------
                
                C = cloud
                0.4
                
                C = ¬cloud
                0.6
                
                R = rain
                0.1
                
                R = ¬rain
                0.9

            ----------------------------


    + Looking at these data, we can’t say whether clouds in the morning are related to the likelihood of rain in the afternoon. To be able to do so, we need to look at the joint probabilities of all the possible outcomes of the two variables. We can represent this in a table as follows.:
            ----------------------------
                                
                C = cloud
                R = rain
                0.08
                R = ¬rain
                0.32
                
                C = ¬cloud
                R = rain
                0.02
                R = ¬rain
                0.58 
            ----------------------------

    * Using joint probabilities, we can deduce conditional probability. 
    EX: if we are interested  P(C | rain) = P(C, rain)/P(rain). 
    In words, ``we divide the joint probability of rain and clouds by the probability of rain.``

    * In the last equation, it is possible to view P(rain) as some constant by which 
    P(C, rain) is multiplied. Thus, we can `rewrite P(C, rain)/P(rain) = αP(C, rain), or α<0.08, 0.02>. Factoring out [ α ] leaves us with the proportions of the probabilities of the possible values of C given that there is rain in the afternoon`

    *  Namely, if there is rain in the afternoon, the proportion of the probabilities of clouds in the morning and no clouds in the morning is 0.08:0.02. Note that 0.08 and 0.02 don’t sum up to 1; however, since this is the probability distribution for the random variable C, we know that they should sum up to 1. Therefore, we need to ``normalize`` the values by computing α such that ``α0.08 + α0.02 = 1. Finally, we can say that P(C | rain) = <0.8, 0.2>.``


## Probability Rules.

#### Negation: 
 
  * P(¬a) = 1 - P(a). This stems from the fact that 
    the sum of the probabilities of all the possible worlds is 1,
    and the complementary literals a and ¬a include all the possible worlds. 

  * Let's consider a simple example of flipping a fair coin:

``  Event A: Getting heads.
    
    P(A)=0.5P(A)=0.5 (since there's a 50% chance of getting heads).
    
    P(¬A)P(¬A): Getting tails.
    
    P(¬A)=1−P(A)=1−0.5=0.5P(¬A)=1−P(A)=1−0.5=0.5 (since there's also a 50% chance of getting tails).``

    
  - 
    // Define the probability of event A
    P(A) = 0.5

    // Calculate the probability of the negation of event A
    P¬(A) = 1 - P(A)

    print(f"P(A) = {P(A)}")
    print(f"P(¬A) = {P¬(A)}")

    outPut: P(A) = 0.5
            P(¬A) = 0.5

#### Inclusion-Exclusion:

   *  P(a ∨ b) = P(a) + P(b) - P(a ∧ b). This can interpreted in the following way: the worlds in which a or b are true are equal to all the worlds where a is true, plus the worlds where b is true. However, in this case, some worlds are counted twice (the worlds where both a and b are true)). To get rid of this overlap, we subtract once the worlds where both a and b are true (since they were counted twice). 

    _______________________________________________________________
     
    
    Let's consider a simple example involving two events:

    Event A: Getting a head on a coin flip.
    Event B: Rolling a 1 on a six-sided die.

    Suppose:

        P(A)=0.5P(A)=0.5 (since there's a 50% chance of getting a head).
        P(B)=16≈0.167P(B)=6/1 ​≈ 0.167 (since there's a 1 in 6 chance of rolling a 1)   

    Assume the coin flip and die roll are independent events. Thus, the probability of both AA and BB happening together is:

        P(A∩B)=P(A)×P(B)=0.5×0.167=0.0835P(A∩B)=P(A)×P(B)=0.5×0.167=0.0835

    Now we can use the inclusion-exclusion principle:

        P(A∪B)=P(A)+P(B)−P(A∩B)P(A∪B)=P(A)+P(B)−P(A∩B)
        P(A∪B)=0.5+0.167−0.0835=0.5835P(A∪B)=0.5+0.167−0.0835=0.5835
        _______________________________________________________________
     
  - 
        // Define the probabilities
        P(A) = 0.5
        P(B) = 1/6

        // Calculate the probability of both A and B occurring
         P(a∧b) = P(A) * P(B)

        // Calculate the probability of A or B occurring using inclusion-exclusion principle
        P(a∨b) = P(A) + P(B) - P(a∧b)

        // Print the results
        print(f"P(A) = {P(A)}")
        print(f"P(B) = {P(B):.3f}")
        print(f"P(A ∧ B) = { P(a∧b):.3f}")
        print(f"P(A ∨ B) = { PP(a∨b):.3f}")
    

#### Marginalization: 

   * `P(a) = P(a, b) + P(a, ¬b)`. The idea here is that b and ¬b are disjoint probabilities. That is, the probability of b and ¬b occurring at the same time is 0. We also know b and ¬b sum up to 1. 
   Thus, when a happens, b can either happen or not. When we take the probability of both a and b happening in addition to the probability of a and ¬b, we end up with simply the probability of a.
  
 

+ Marginalization can be expressed for random variables the following way:
+ ![marginalization](https://github.com/user-attachments/assets/2bf9f86a-3e0b-48b8-bd4d-d9576de04d0c)
  * The left side of the equation means `“The probability of random variable X having the value xᵢ.”` For example, for the variable C we mentioned earlier, the two possible values are clouds in the morning and no clouds in the morning.` The right part of the equation is the idea of marginalization. P(X = xᵢ) is equal to the sum of all the joint probabilities of xᵢ and every single value of the random variable Y.` For example,` P(C = cloud) = P(C = cloud, R = rain) + P(C = cloud, R = ¬rain) = 0.08 + 0.32 = 0.4.`

## Conditioning: 
  *` P(a) = P(a | b)P(b) + P(a | ¬b)P(¬b)`. This is a similar idea to marginalization. The probability of event a occurring is equal to the probability of a given b times the probability of b, plus the probability of a given ¬b time the probability of ¬b.
