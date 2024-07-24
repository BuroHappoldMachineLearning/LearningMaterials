# Python and Machine Learning.

I left links to useful resources wherever I could, but in general please Google any resource you can find on the below-mentioned topics.  
Anything works really, as long as you get a general understanding of the subject and you are comfortable in using Python and its ecosystem to achieve certain things. 

You don't need to become an expert, and you don't need to do everything in this list. But please do make some effort in reading about these subjects, in particular the ones that interest you the most. The more you familiarise yourself with, the more you'll be able to contribute to our work.

## Python and programming


### Visual Studio code and Python initial setup

Visual Studio Code (VSCode) is a text editor that supports many extensions to write code in many languages, and it's our editor of choice for Python. 

- Follow [this guide for using Python in Visual Studio Code](https://code.visualstudio.com/docs/languages/python) and make sure you learn the foundations, up until the _Jupyter Notebook_ section (you can skip "Testing" and the below sections initially). It covers some of the points listed below in the "Basics of Python" section. The "Basics of Python" includes a link to another Tutorial resource to delve more into Python itself, while the guide above focuses on how Python can be used from VSCode.

- Python. This is our language of choice for scripting and programming around ML tasks. The guide above should point you in the right direction for installing it. In general, it should be ok to install the latest version from https://www.python.org/downloads/. We will use a few different versions during our work.

### Basics of Python

This [beginners tutorial](https://code.visualstudio.com/docs/python/python-tutorial) is a good reference for beginners in Python.

In general, you should make sure you cover and understand the following points:

- Basic syntax in Python. Define variables.
- Control flow structures: if-else
- Define functions
- Basic built-in data structures: 
	- Lists
	- Tuples
	- Dictionary
- Understand what a Python module is. Understand "imports". Try creating a module.
- What is a package in Python. Difference with a module.
- What is PIP? Try using it to install some packages. Where are those packages installed (in what folder of your machine)?
- Understand that when you install Python you effectively install a Python runtime executable (an .exe, in Windows), which is the program that runs your Python scripts/programs. This is called a Python "interpreter". Understand that there are many different versions of Python interpreters (we mostly use 3.10.xx and/or 3.8.xx).
- What is an environment in Python? Understand why it's important to **always** work in an environment. Where do packages installed with PIP end on your machine, when you call PIP from an environment?
- Learn to create an environment and activate/deactivate it. See [this guide](https://code.visualstudio.com/docs/python/python-tutorial#_create-a-python-source-code-file) that explains how environments are integrated in VSCode.
- Understand the Debugger and how it works in Python. See [this guide](https://code.visualstudio.com/docs/python/python-tutorial#_configure-and-run-the-debugger).


### Basics of Git
- What is a Git repository ("repo").
- Create a Git repository for your learning and exercises. You can create a free GitHub account and create a repo there.
- Clone the repository on your machine.
- What is a branch?
- What does it mean to commit.
- What does it meant to Pull and Push from/to a repo.
- What is the .gitignore file?
- Create an environment for your repository and exercises.


### Basics of Object-oriented Python
- What is a class?
- What is an object (= instance of a class)?
- What are properties (fields) of a class 
- What are getters and setters
- Private VS Public methods and fields. What is the difference, how can you do that in Python?
- What is a constructor
- Define a class, do exercises


### Intermediate Python

- What are decorators, how can decorators be useful. Try writing a decorator.
- Mutable VS immutable types in Python: learn the difference (e.g. can you modify a list? Can you modify a tuple?)
- Understand pass-by-value and pass-by-reference (e.g. https://www.geeksforgeeks.org/pass-by-reference-vs-value-in-python/)
- "Python is a dynamic programming language", understand what that means. Understand the difference with static typed languages (e.g. C#). You don't need to know another language, but to understand the difference it helps to try another out (e.g. just declaring variables/classes in a static language like C#).
- The following two are very important; **we rely on them a lot, because they are of fundamental importance when creating larger programs, and we expect you to use them in our work**:
    - [IMPORTANT] ❗ Understand ["Type Hints"](https://realpython.com/lessons/type-hinting/) and try them in some scripts. Understand how they help in reducing the issues with Dynamic programming languages, see below.
    - [IMPORTANT] ❗ Understand what [Annotations](https://blog.logrocket.com/understanding-type-annotation-python/) are (basically, advanced type hints) and try them.
    - [IMPORTANT] ❗ Understand the [Typing python module](https://realpython.com/python-type-checking/) is and why it is useful in dynamic typing.
- Try adding Typing to previous functions or class properties that you may have written. See how it works.
- Understand [basic guidelines](https://www.linkedin.com/advice/3/how-can-you-write-modular-python-code-efficient-data-scjdf) to write good functions and Python code.
- Undrestand the [`if __name__ == "__main__"](https://realpython.com/if-name-main-python/) Python statement and what is a Python module VS Script.


### Intermediate Object-oriented Python
- What is inheritance. How can it be useful. Do exercises.
- What are DataClasses
- Write some dataclasses, do exercises
- What is an object reference
- What is shallow cloning and what is deep cloning. Differences. How to do either in Python.
- How does the equality operator == behave when comparing objects (e.g. for class instances, how does it work?) 


### Algorithms and data structures.
- Understand what recursion is. Try define a function that calculates the Fibonacci sequence with and without recursion.
- Understand what "memoisation" means and try rewriting the Fibonacci solutions by adding some simple memoisation strategy.
- Understand why data structures are useful in solving some problems.
- Understand what is complexity. Time and Space complexity.
- Understand what a Stack is. Try implementing one using a list and/or in other ways.
- Understand what a Queue is. Try implementing one using a list and/or in other ways.
- Understand what a Linked List is. Try implementing one.
- Understand what a HashTable is and how it is the backing data structure of Dictionaries.
- Understand what a Binary Tree is, and that it is a specific simple case of a more general graph structure. Try implementing one.
- Understand what an algorithm complexity is. Get an idea of Time and space complexity. Get an idea of the Big-O notation.
- Try solving some exercises that require you to write Data Structures and get an idea of the complexity of your solution.


# Data science and Machine Learning

## Basics of statistics
- [Basics of descriptive statistics](https://www.tutorialspoint.com/python_pandas/python_pandas_descriptive_statistics.htm): mean, variance, stdev, covariance, correlation. Try computing them in Python using the Pandas package or similar ones.
- [Function approximation; differences between Classification and Regression models](https://machinelearningmastery.com/classification-versus-regression-in-machine-learning/).
- What is a [statistical modelling](https://www.simplilearn.com/tutorials/statistics-tutorial/what-is-statistical-modeling)? Differences/similarities with Machine Learning.

## Basics of Machine Learning

The following can be done using any Python package that supports them:
- Try [linear regression](https://www.w3schools.com/python/python_ml_linear_regression.asp)
- Try [polynomial regression](https://www.w3schools.com/python/python_ml_polynomial_regression.asp)
- Try clustering techniques, e.g.: [K-means](https://www.w3schools.com/python/python_ml_k-means.asp), [others](https://scikit-learn.org/stable/modules/clustering.html)
- Understand and try [Decision Trees](https://www.w3schools.com/python/python_ml_decision_tree.asp)
- Understand and try [Random Forests](https://www.geeksforgeeks.org/random-forest-regression-in-python/) and how they improve on Decision Trees
- Understand what [Bootstrapping](https://www.statology.org/bootstrapping-in-python/) is and try it

### Deep Learning/Neural networks
- Understand [what is Deep Learning (DL)](https://www.ibm.com/topics/deep-learning)
- Understand [when Deep Learning is useful](https://blog.dataiku.com/when-and-when-not-to-use-deep-learning), rather than non-DL approaches.
- Understand how DL can be done via Python frameworks (e.g. learn about common frameworks). Have a look at [Pytorch](https://pytorch.org/docs/stable/index.html), [Tensorflow](https://www.tensorflow.org/learn), [Scikit-learn](https://scikit-learn.org/stable/modules/neural_networks_supervised.html), [Keras](https://keras.io/getting_started/intro_to_keras_for_engineers/). You don't need to try them all, just understand there are many frameworks and that they differ in many ways; we focus on using Pytorch.
- Try this [60-minute Pytorch tutorial](https://pytorch.org/tutorials/beginner/deep_learning_60min_blitz.html#goal-of-this-tutorial).
- Understand that there are many types of Neural Network (NN) architectures. We are mostly interested in Recurrent and Convolutional Neural Networks.
- Understand the differences between [**Predictive VS Generative AI**](https://www.coursera.org/articles/generative-ai-vs-predictive-ai). We won't do Generative AI, we focus only on Predictive AI. 

### Computer vision
We use mostly computer vision in our work.
- Understand [what is Computer Vision](https://www.simplilearn.com/computer-vision-article)
- Understand the [common tasks in Computer vision](https://www.smart-interaction.com/2022/07/14/computer-vision-the-ultimate-guide-on-the-4-main-tasks/)
- Read about the COCO format (we use it in our work)
