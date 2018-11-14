
# Partitioning and Law of Total Probabilities - Lab

## Introduction 
In this lab, we shall look at the law of total probability. In probability theory, the law (or formula) of total probability is a fundamental rule relating **marginal probabilities** to conditional probabilities. It expresses the total probability of an outcome which can be realized via several distinct events, hence the name.

## Objectives

You will be able to:
* Understand and explain the concept of event space and partitioning 
* State the law of total probabilities based on a partitioned event space
* Understand and able to perform partitioning based on known and unknown probabilities to solve a problem

## Exercise 1
Suppose we have two hats: one has 4 red balls and 6 green balls, the other has 6 red and 4 green. We toss a fair coin, if heads, pick a random ball from the first hat, if tails from the second. 

What is the probability of getting a red ball?


```python
# Your solution
0.5*(4/10) + 0.5*(6/10)
```




    0.5



## Exercise 2
A soccer team wins 60% of its games when it scores the first goal, and 10% of its games when the opposing team 
scores first. 

If the team scores the first goal about 30% of the time, what fraction of the games does it win?


```python
# Your solution
# P(W|scored_first)
0.30 * 0.60 + 0.70 * 0.10
```




    0.25



## Exercise 3

In Europe, except for regular gas, cars regularly run on Diesel as well. At a gas station in Paris; 


* 40% of the customers fills up with Diesel (event G1) 
* 35% with gas "Super 95" (event G2)
* 25% with gas "Super 98" (event G3). 


* 30% of the customers who buy Diesel fill their tank completely (event F). 
* For "Super 95" and "Super 98", these numbers are  60% and 50% respectively.


- Compute the probability that the next customer completely fills their tank and buys Super 95. 
- Compute the probability that the next customer completely fills their tank
- Given that the next customer fills their tank completely, compute the probability that they bought Diesel. 

Hint: Consult the theorems for conditional probability, check for dependence or independence of events


```python
# Your solution
# P(fills and buys super 95) = P(fills) * P(super95)
print("Probability that the next customer completely fills their tank and buys Super 95 is:")
print((0.35*0.60))


# P(fills) = sum [P(fill_i)]*[P(gas_i)]
print("\nProbability that the next customer fills their tank is:")
p2 = (0.40 * 0.30) + (0.35*0.60) + (0.25 * 0.50)
print(p2)

print("\nProbability that a customer bought Diesel given that they fill their tank is:")
# P(Diesel|filled)
print(0.40 * 0.30/p2)
```

    Probability that the next customer completely fills their tank and buys Super 95 is:
    0.21
    
    Probability that the next customer fills their tank is:
    0.45499999999999996
    
    Probability that a customer bought Diesel given that they fill their tank is:
    0.26373626373626374


## Exercise 4

United airlines operates flights from JFK to Amsterdam, to Brussels and to Copenhagen. As you might know, flights are overbooked fairly often. Let's denote the probability of the flight to Amsterdam being overbooked equal to 40%, the probability of the flight to Brussels being overbooked equal to 25%, and the probability of the flight to Copenhagen to be overbooked being equal to 35%. 

- Compute the probability that all the flights are overbooked.
- Compute the probability of having at least one flight which is not overbooked.
- Compute the probability that exactly one flight is overbooked.

Hint: Consult the theorems for conditional probability, check for dependence or independence of events


```python
# Your solution
problem1 = "P(all flights are overbooked)"
prob1 = (0.40)*(0.25)*(0.35)

problem2 = "P(at least one flight is not overbooked)"
prob2 = 1-prob1

problem3 = "P(exactly one flight is overbooked)"
prob3 = 0.60*0.65*0.25 + 0.60*0.35*0.75 + 0.40*0.65*0.75

problems = [problem1, problem2, problem3]
probs = [prob1, prob2, prob3]

for problem, prob in zip(problems, probs):
    print("{} = {}".format(problem, prob))
    print("\n")
```

    P(all flights are overbooked) = 0.034999999999999996
    
    
    P(at least one flight is not overbooked) = 0.965
    
    
    P(exactly one flight is overbooked) = 0.45
    
    


## Exercise 5
You have three bags that each contain 100 marbles:

- Bag 1 has 75 red and 25 blue marbles;
- Bag 2 has 60 red and 40 blue marbles;
- Bag 3 has 45 red and 55 blue marbles.

You choose one of the bags at random and then pick a marble from the chosen bag, also at random. 

What is the probability that the chosen marble is red?



```python
# Your solution
import numpy as np
problem = "P(red is chosen first)"
prob = np.sum(1/3 * np.array([0.75, 0.60, 0.45]))
print("{} = {}".format(problem, prob))
```

    P(red is chosen first) = 0.6


## Summary 

In this lab we practiced around conditional probability and its theorem with some simple problems. The key takeaway from this lab is to to be able to identify random events as dependent or independent and calculating the probability of their occurrence using appropriate methods. Next we'll start focusing on the Bayes theorem, building on the knowledge we have thus far. 
