## Introduction

Let's say we have a list of book recommendations for a specific user.
We've already associated a rank for each of the books in the list
(the rank is with respect to that specific user and the other books in the list).
We want to present them to the user in a sorted
order so that the best recommendation will be placed on the top and so on (ordered ascending by the rank).
We have some good recepies for doing that (sorting objects in a list based on some key).
We call those recepies __algorithms__.
Those algorithms are series of software instructions to the machine what to do step by step.

You've probably heard of __Machine Learning__ (ML). For example to distinguish between two identical twins.
How to develop an algorithm that, given images captured by a digital camera,
can tell if we're looking at Bob or at Charlie? Maybe we can come up with an algorithm that does that.
It is certainly not going to be easy (try this mentally exercise)
even if it is known that Bob is a little bit taller than Charlie.
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

As a side note, the training of a specific __model class__ is often an algorithm in the classic context 
and so is the related prediction process. But the learning is achieved by adjusting parameters and those are determined
from examples by means of optimizing a goal or minimizing discrepancies among desired predictions and current predictions. Examples for model classes are a __Random Forest__ and a __Neural Network__.

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

Where does __Reinforcement Learning__ (RL) fit into those exciting development in software engineering? RL is a ML way of learning the control logic for automated-agents.
What we learn with RL is a controller, or a __policy__ that the agent then follows and thus achieves one or more
desired behavior in the environment in which it is operating.
We will dive more into the relations among RL and other types of ML and software paradigms in  [Chapter 1](chapter-01.md).

Few more words on ML. When I was first introduced to ML and __Data Science__, I came to believe that we have __Supervised Learning__, __Unsupervised Learning__, and the ultimate RL. At the time, I was scared away from RL, and was encouraged to study first supervised learning, and if I am brave enough then maybe also unsupervised learning. Supervised learning is the settings in which we learn to predict based on labeled examples, for example, house price from some information about the house and previous examples with prices. Another common example is spam filterring. Given a mail should it go to the spam folder or to the inbox. This can be done by examinging the text the email and comparing it to previously categoried emails. When we described above distiguising between twins, is was presented as supervised learning. Unsupervised learning is a setting where we do not have labels. We can still do a lot by studying the structure of the data, finding patterns, observing natural clusters, and much more. There are many ways to solve a computation challenge with a combination of methods from both paradigms. For example, sometimes we can destill features with unsupervised learning to be used in a later stage of the __pipeline__ with supervised learning. In __Natural Language Processing__ (NLP), a first step can be learning a __Language Model__. Language model is for example, the ability to guess well the next word in a partial sentence. When language model is achieved it can help with other NLP tasks. The way we learn language models, is by automaticly creating "labels" from a large corpose of text. There is no necessarily a label, but rather a word that appears in an example text is used as the label. And hence learning language model, can be considered unsupervied learning. Now that I dared to touch also RL, I see that it is not that fritening. Also I see that it is not a clear cut. The settings and tools are somewhat different, yet given a task, one can consider sometimes addressing it as supervised learning, as RL, or any combination of steps in a pipeline. For example, if we want to present an advertisement to a visitor, we can rank few candidate ads, and pick the best. We can also decide to create a smart __recommender system__, that chooses actions on additional commemrcial and ethical considerations. The system need to be controlled, and learn by "interacting" with the visitors in the numerous sessions. Recommender systems, may be built on __Collaborative Filtering__ paradigm, which is an unsupervised learning for finding similar users and similar prefereces, or the latent "genres" and "themes" of the items, and what users should be shown which.
More than this. When using RL, we'll need sometimes to use supervied and unsupervised learning. The other direction, may also exist. For example, RL can be used to decide what additional samples are best to be labeled in an __Active Learning__ setting as part of a supervised learning predictor.

A similar experience with regarding to getting started with ML was with neural networks, or if you really want to leave impression, __Deep Neural Networks__ (DNN)<sup>1</sup>. I'm happy that I've started with simpler to understand model classes, such as a Decision Tree, k-Nearest Neighbours, or a Linear Regression. With the simpler model classes, __Feature Engineering__ is a good practice. This is the process of understanding the problem and the data, and helping the model in gettting access to the information. Neural networks are more flexible, and they can be used to learn a task, while automaticly extracting features without implicit guidance. With todays software support, neural networks are very accessible and often the most promissing direction. But the moral should be that RL is orthogonal to neural networks for example, and should be learned as its own paradigm, and then when we get to solving tasks we'll pick the right tools and use them as needed.

**Footnotes:**

1. A neural network has an input layer and an output layer. The more hidden layers it has in between, the deeper it is.