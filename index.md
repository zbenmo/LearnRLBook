# Learning Reinforcement Learning Book

## Introduction

Let's say we have a list of book recommendations for a specific user.
We've already associated a rank for each of the books in the list
(the rank is with respect to that specific user and the other books in the list).
We want to present them to the user in a sorted
order so that the best recommendation will be placed on the top and so on (ordered ascending by the rank).
We have some good recepies for doing that (sorting objects in a list based on some key).
We call those recepies algorithms.
Those algorithms are a series of software instructions to the machine what to do step by step.

You've probably heard of Machine Learning (ML). For example to distinguis between two identical twins.
How to develop an algorithm that, given images captured by a digital camera,
can tell if we're looking at Bob or at Charlie? Maybe we can come up with an algorithm that does that.
It is certainly not going to be easy (try this mentally exercise)
even if it is known that Bob is a bit taller than Charlie.
More than that, the work that will be put into building such an algorithm is huge and will not
generalize to telling between Anne and Debby
(while sorting books based on the given rank and sorting countries based on their given GDP
is about the same).
Luckily we have a new way to do tasks as above.
By collecting a training set with examples and the right answer, and feeding those into learning process.
The end results in a model of the task. Given the model,
a software wrapper around the model can achieve for example the goal of telling Bob from Charlie.
If we want to have a model for telling Anne from Debby we need to collect another training set,
and train another model. While it may be a little bit time consuming and may involve some cost to collect
the new set, to train, and to maintain a second model,
it is still very efficient way to having a machine that automaticlly achieve such complex task.

As a side note, the training of a specific model class is often an algorithm in the classic context 
and so is the related prediction process. But the learning is achieved by adjusting parameters and those are determined
from examples by means of optimizing a goal or minimizing discrepancies among desired predictions and current predictions. 

We can prove mathematically that for example the Quick-Sort algorithm will always succeed
in ordering the books in the
example correctly given the ranks, and will do that in finite time.
Proving correctness and guaranties for successful termination and resonable processing time are desirable
and are associated with trustworthy software (ex. for medical use, or for flight related control). 
Can we prove that a ML model will always succeed? We can often prove that the calculation will
be done within a finite time,
but we cannot guarantee that the answer will be correct 100% of the time,
we better refer to the model's outputs as best effort predictions.
There are few reason for that.
Sometimes even if you give Bob and Charlie a photo,
they cannot agree among themselves which of them is seen there.
Then even if they do agree they might be both wrong.
And the trained model itself, may be wrong. Just becasue it is not perfect,
or it is asked about a photo that is too far from the examples the model was trained on.
And yet since the model is useful, more accuracte than anything we managed to put our hand on,
and was developed with a fraction of the costs to manually create a tailored software solution,
we thus will most likely use it anyhow.

Let's look into other examples where we've learned to accept near optimal behaviour.
Imagine a rule-based system from preventing fraud with bank transactions.
Each transaction is passing through a set of rules. And that algorithm decides in a fraction of a second, wheather to allow the transaction
or to block it. Some frauds do manage to trick the system and go through.
A lot of times a legitimate transaction is blocked causing some frustration at the other end(s).
The financial institution is constantly looking for the best setting as to balance the risk and the benefits of the system.
If the checking was not automated, we could not have the online banking and shoping that we enjoy these days.
The scale of operations requires automation.

Where does Reinforcement Learning (RL) fit into this? RL is a ML way of learning the control logic for automated-agents.
What we learn with RL is a policy that the agent then follows and thus achieves one or more
desired behavior in the environment in which it is operating.
We will dive more into the relations among RL and other types of ML and software paradigms in Chapter 1.

## Chapter 1. Searching for the best course of action

Consider we're trying to automate a warehouse. We have a representation of the exact location of every item in the warehouse.
To retrieve a specific item, one may need to move first other items that are in the item's way (or above it for example).
Now, we're given a request for an item.
If the item is accessable, a robotic arm can reach for it, place it on the moving belt, and we'll collect it on the other end of the belt. If however the item is somewhat hidden behind other items, some planning is needed.
For example moving the blocking items to another place first, and so revealing the desired item. Once the item becomes accessible, the robotic arm can proceeed as before.
Planning can be done by searching the space of options. Options are actions such as picking an item and placing it in another place.
If the current warehouse representation is a state, then the warehouse as it will look after a potential action is another state.
Planning should come up with an efficient and effective series of actions that will lead in theory to the item being accessible.
Once the plan is computed by a search algorithm, it is then executed, moving items to reveal the desired item. If all goes well, the final locations of the items, reflected by the software representation, enables the robotic arm to fetch the desire item, and sending it to us using the moving belt.

To better understand the concept of search, let's think about the Chess game. We want to build a software that plays agaist a human and give a good fight. For the sake of discussion, we're in the initial board state and the software plays the White. The software can make any legitimate move, a thing that will hopefully bring it closer to victory. Once a move is done by the White, given that we haven't won yet, or the board is not a stalemate then the Black gets a change to make his move. The move of the Black also changes the state of the board of course. So a planning here should take into account also that the other player will also try to win, and hence we should avoid leaving the board in a winnable state (winnable for the other side). In some problems or puzzles it is possible to exlusively explore in reasonable time, all possible developments in the state space and select the best path (ex. potentially win while never lose in Tic-Tac-Toe). In Chess and in many other games or real world settings, a search is possible yet only to a certain depth. Therefore will not be able to see all future developments, and we must act based on some heuristic. For example we can estimate if a Chess board is good for us based on the number of squares that we are in control of minus the number of squares that the opponent is in control of. Such heuristic helps both in directing the search, and in choosing what seems to be as the best move or action.

Search and planning are considered Artificial Inteligence (AI). Under the wide umbrella of AI, we find approaces for solving problems, not by instructing the machine directly How to address a challenge, but rather What is a desired outcome.
With Chess we wanted to convey to the software to find the way to win. We show the machine what it means to win or to lose, and we want it to come up with the sequence of moves that will lead to the final winning move. Not everything is in our control. The opponent chooses its own moves. He/she also wants to win or at least to avoid a loss. More than that, knowning that our software cannot inspect all the possible branches from the current state to all final states (win/lose/statemate), we had to help the search by providing a hand tailured heuristic. In the example above, the heuristic is a real value representing the value of the board or state from the player viewpoint.

While Chess seams to be hard, the game is still well defined and controlled setting. The number of levers that a player can pull in any given turn is finite and small. A player can choose any one of a valid next move. Then he/she needs to wait for their next turn. When selecting a move, there is certenty regarding the next board state, as dictated by the game's rules. Both players have full knowledge of the current state, can write down past moves, and can plan and speculate about future moves. The only uncertenty is what the opponent will do next. And still Chess is very interesting as we cannot see all the possible futures and who will win.

A common introduction to RL is the k-armed Bandit. You are standing front of k slot machines in Las-Vegas. To play a machine you pay $1 and pull the relevant lever. You then collect the winning and continue if you wish and can afford it. It is known to you that each of those machines has a different reward expectation (average win). Would be nice to know which of those has the highest reward. Unfortunately there is no external hint. What you can do, is to try all and attempt to figure-out which one it is. The expected reward of a machine will not change over time, and that is nice to know. However since we're talking about expectations, we're never sure if we got it right. For example, you've tried the three machines and got $2, $0, $0 respectively. It seems that the first machine is the best, yet it might have been by chance. You're now left with a dilemma. To exploit your current belief and stick with the first machine, or explore a little more the other machines, just to be sure. What is the best policy here? Can we search for the optimal solution? With any additional exploration we increase our understanding of the environment, yet also waste a chance to exploit our knowledge. Assuming we are trying to maximizing the total amount of money we have in our pocket at the end of the day, we might decide to invest in exploration also, but probably not at the very end of the day when we make the last attempt.





