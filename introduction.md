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
We will dive more into the relations among RL and other types of ML and software paradigms in  [Chapter 1](chapter-01.md).
