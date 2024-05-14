# Python and Machine Learning.

## Python and programming

First off, install:
- Visual Studio Code. This is a text editor that supports many extensions to write code in many languages. Make sure to install Python extensions: in VSCode, learn the CTRL+Shift+P shortcut that gives you access to all commands. It's available in the Software Centre.
- Follow [this guide for using Python in Visual Studio Code](https://code.visualstudio.com/docs/languages/python) and make sure you learn the foundations, up until the Jupyter Notebook section (you can skip "Testing" and the below sections initially).
- Python. The guide above should point you in the right direction for installing it. In general, it should be ok to install the latest version from https://www.python.org/downloads/. We will use a few different versions during our work.

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
- Understand the Typing python module is and why it is useful in dynamic typing. Understand "Type Hints" and "Annotations" are. We use Typing a lot in our work.
- Try adding Typing to previous functions or class properties that you may have written. See how it works.


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
- Basics of descriptive statistics: mean, variance, stdev, covariance, correlation. Try computing them in Python using the Pandas package.
- ... TODO

## Basics of Machine Learning
- What is a statistical model
- Classical ML vs Neural Networks VS Reinforcement Learning
- ... TODO

### Classical ML
- Try linear regression
- Try polynomial regression
- Try clustering techniques
- ... TODO

### Neural networks
- ... TODO
