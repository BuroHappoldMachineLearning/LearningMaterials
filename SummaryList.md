# Python and Machine Learning topic list with references

This is a (somewhat) comprehensive list of topics that I could think of as useful to contribute to our work in the Machine Learning R&D space.

I left links to useful resources wherever I could, but in general you may need to Google additional resources on the below-mentioned topics.  
Anything works really, as long as you get a general understanding of the subject and you are comfortable in using Python and its ecosystem to achieve certain things. 

**You don't need to become an expert in these topics**, and _you don't need to do **everything** in this list_. However, please do make some effort to read about many of these, and trying out some code for them, in particular for _the ones that interest you the most_, and possibly the ones marked with [IMPORTANT] ❗.  
The more you familiarise yourself with, the more you'll be able to contribute to our work.

Remember to reach out to others for help, questions and feedback! We are all continously learning 🚀

## Python and programming


### Visual Studio code and Python initial setup

Visual Studio Code (VSCode) is a text editor that supports many extensions to write code in many languages, and it's our editor of choice for Python. 

- [IMPORTANT] ❗ Follow [this guide for using Python in Visual Studio Code](https://code.visualstudio.com/docs/languages/python) and make sure you learn the foundations, up until the _Jupyter Notebook_ section (you can skip "Testing" and the below sections initially). It covers some of the points listed below in the "Basics of Python" section. The "Basics of Python" includes a link to another Tutorial resource to delve more into Python itself, while the guide above focuses on how Python can be used from VSCode.

- Python. This is our language of choice for scripting and programming around ML tasks. The guide above should point you in the right direction for installing it. In general, it should be ok to install the latest version from https://www.python.org/downloads/. We will use a few different versions during our work.

- We mostly work on remote Virtual Machines or Workstation computers, because they are more powerful and we can centralise our data there. We connect to them using SSH. See [this guide to learn basic SSH set-up and connection](https://github.com/BuroHappoldMachineLearning/ML_Documentation/blob/main/Azure/VM_user_guides.md). Ask for help when you start developing for our codebase. This guide doesn't require you to use our Virtual Machines or Workstations, you can just use your laptop to try these things on your own.

### Basics of Python

This [beginners tutorial](https://code.visualstudio.com/docs/python/python-tutorial) is a good reference for beginners in Python.

In general, you should make sure you cover and understand the following points:

- Basic syntax in Python. Define variables.
- [IMPORTANT] ❗ [Control flow](https://www.pythoncheatsheet.org/cheatsheet/control-flow) structures: comparison operators, boolean operators, if-else, loops (`for` and `while`), `continue` and `break` keywords, `range` command.
- [IMPORTANT] ❗ [Define functions](https://www.w3schools.com/python/python_functions.asp); feel free to skip (don't do) `*args` and `**kwargs` which I personally consider a bad code practice.
- [List comprehensions](https://www.w3schools.com/python/python_lists_comprehension.asp): they can be complicated and difficult to read, but in some places they may be handy (e.g. when [filtering values from a list](https://realpython.com/list-comprehension-python/#filter-values-from-a-list)). Don't worry too much about them.
- [IMPORTANT] ❗ Basic built-in data structures: 
	- [Lists](https://www.w3schools.com/python/python_lists.asp). Understand that they are _ordered_.
	- [Tuples](https://www.w3schools.com/python/python_tuples.asp). Understand that [they can be used as a return type of functions](https://pieriantraining.com/python-tuples-how-to-return-them-like-a-pro), although _you shouldn't do it_: prefer `dataclass`es, or at least always type-hint them (see [Intermediate Python section](#intermediate-python) below).
	- [Dictionaries](https://www.w3schools.com/python/python_dictionaries.asp). Understand that [they are _unordered_ (in many cases)](https://stackoverflow.com/a/39980744/3873799) and that it can be better to treat them as unordered, and what that can imply for your code.

- [IMPORTANT] ❗ What is [PIP](https://www.w3schools.com/python/python_pip.asp)? Try using it to install some packages. Where are those packages installed (in what folder of your machine)?
- [IMPORTANT] ❗ Understand that when you install Python you effectively install a Python runtime executable (an .exe, in Windows), which is the program that runs your Python scripts/programs. This is called a Python "interpreter". Understand that there are many different versions of Python interpreters (we mostly use 3.10.xx and/or 3.8.xx).

#### Python environments
- [IMPORTANT] ❗ What is a [virtual environment](https://realpython.com/python-virtual-environments-a-primer/) in Python? Understand why **it's important to _always_ develop code in an environment**. Where do packages installed with PIP end on your machine, when you call PIP from an environment? You need to make sure an environment is always enabled when you code, and you understand that by installing packages in an environment you are adding _dependencies_. In our work, we use _shared_ environments on the same machine (workstations) and you must make sure you only install packages in shared environments only if really necessary, and possibly after consulting with other developers.
- [IMPORTANT] ❗ Learn that Python has many ways of managing environments, mainly PIP environments (VENV) and Conda Environments. We mostly use Conda environments, but when we can't avoid it we also install PIP packages in Conda environments.
- If you need to try out things by yourself, you must use an environment of your own. Learn how to clone environments if you need to create a new environment for your use based on another existing environment.
- [IMPORTANT] ❗ Learn to create an environment and activate/deactivate it. See [this guide](https://code.visualstudio.com/docs/python/python-tutorial#_create-a-python-source-code-file) that explains how environments are integrated in VSCode.


### Basics of Git
- [IMPORTANT] ❗ What is a Git repository ("repo").
- Create a Git repository for your learning and exercises. You can create a free GitHub account and create a repo there.
- Clone the repository on your machine.
- [IMPORTANT] ❗ [What is a branch](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-branches)? Understand what are the differences between a the default "`main`" branch and other branches used for development.
- [IMPORTANT] What does it meant to Fetch? What does it mean to Pull from a repo?
- [IMPORTANT] ❗ What does it meant to Stage? What does it mean to Commit? What does it mean to Push to a repo?
- Understand [how to work with branches](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-branches#working-with-branches). We always work with branches in our code. A developer must always create his own branch for targeting a specific (or a few specific) issues that they want to do code about.
- [IMPORTANT] ❗ What is a Pull Request (PR)? We always use PRs to update the main branch when an issue is resolved. PRs are reviewed by other developers to make sure the code is correct before merging to `main`.
- What is the [`.gitignore`](https://www.w3schools.com/git/git_ignore.asp?remote=github) file?
- Create an environment for your repository and do exercises there.


### Basics of Object-oriented Python
- [IMPORTANT] ❗ What is a [class](https://www.w3schools.com/python/python_classes.asp) in Python? What are properties (this is the more exact name, but in Python, they're called "attributes") of a class? What is an object (= instance of a class)? What is a constructor (sometimes shortened as "ctor")? Define a class, do exercises.
- [IMPORTANT] ❗ What are [getters and setters](https://realpython.com/python-getter-setter/) in Python? Understand the `self` keyword.
- [Private methods](https://www.geeksforgeeks.org/private-methods-in-python/) VS Public methods and fields. What is the difference, how can you do that in Python?
- ["Python is a dynamic programming language"](https://www.bairesdev.com/blog/static-vs-dynamic-typing/), understand what that means. Understand the difference with static typed languages (e.g. C#). You don't need to know another language, but to understand the difference it helps to try another out (e.g. just declaring variables/classes in a static language like C#).

### Intermediate Python

- [IMPORTANT] ❗ Understand what a Python module is. Understand "imports". Try creating a module.
- [IMPORTANT] ❗ What is a package in Python. Difference with a module.
- What are decorators, how can decorators be useful. Try writing a decorator.
- Understand [pass-by-value and pass-by-reference](https://www.geeksforgeeks.org/pass-by-reference-vs-value-in-python/) in Python.
- The following two are very important; **we rely on them a lot, because they are of fundamental importance when creating larger programs, and we expect you to use them in our work**:
    - [IMPORTANT] ❗ Understand ["Type Hints"](https://realpython.com/lessons/type-hinting/) and try them in some scripts. Understand how they help in reducing the issues with Dynamic programming languages, see below.
    - [IMPORTANT] ❗ Understand what [Annotations](https://blog.logrocket.com/understanding-type-annotation-python/) are (basically, advanced type hints) and try them.
    - [IMPORTANT] ❗ Understand the [Typing python module](https://realpython.com/python-type-checking/) is and why it is useful in dynamic typing.
- Try adding Typing to previous functions or class properties that you may have written. See how it works.
- [IMPORTANT] ❗ Understand [basic guidelines](https://www.linkedin.com/advice/3/how-can-you-write-modular-python-code-efficient-data-scjdf) to write good functions and Python code.
- [IMPORTANT] ❗ Understand the [`if __name__ == "__main__"](https://realpython.com/if-name-main-python/) Python statement and what is a Python module VS Script.
- [IMPORTANT] ❗ Understand the Debugger and how it works in Python. See [this guide](https://code.visualstudio.com/docs/python/python-tutorial#_configure-and-run-the-debugger).

#### Intermediate Object-oriented Python
- [IMPORTANT] ❗ What is [inheritance](https://realpython.com/inheritance-composition-python/). How can it be useful. Do exercises.
- [IMPORTANT] ❗ What are [DataClasses](https://www.dataquest.io/blog/how-to-use-python-data-classes/)? Try them out. We use them a lot in our code.
- What is an [object reference](https://stackoverflow.com/questions/35488769/what-is-an-object-reference-in-python)?
- What is [shallow cloning and what is deep cloning](https://realpython.com/copying-python-objects/). Differences. How to do either in Python.
- [IMPORTANT] ❗ Understand [object identity in Python](https://realpython.com/courses/python-is-identity-vs-equality/); wow does the equality operator `==` VS `is` behave when comparing objects (e.g. for class instances, how does it work?)
- [IMPORTANT] ❗ Learn how to use the [`type()` operator](https://switowski.com/blog/type-vs-isinstance/), and the [`isinstance()` operator](https://www.w3schools.com/python/ref_func_isinstance.asp) and how it differs from `is`; we use all of them a lot.
- [IMPORTANT] ❗ [Mutable VS immutable types](https://realpython.com/python-mutable-vs-immutable-types/) in Python: learn the difference (e.g. can you modify a list? Can you modify a tuple?)


### Algorithms and data structures

- Understand what an algorithm complexity is. Get an idea of Time and space complexity. Get an idea of the Big-O notation.
- Understand the [Time-space tradeoff](https://www.geeksforgeeks.org/time-space-trade-off-in-algorithms/).
- [IMPORTANT] ❗ Understand what recursion is, maybe following the example for the [Fibonacci function](https://realpython.com/fibonacci-sequence-python/). Understand how it can be implemented with and without recursion.
- [IMPORTANT] ❗ Understand what [memoisation](https://kyleshevlin.com/memoization/) is and try rewriting the [Fibonacci with simple memoisation](https://realpython.com/fibonacci-sequence-python/#memoizing-the-recursive-algorithm) strategy.

- Understand [why data structures are useful](https://www.linkedin.com/advice/0/why-data-structures-important-computer-science-cl85c) in solving some problems.

Data structures and algorithms can be complex, but you can just try and understand some basics for the following ones; in general, don't get stuck on them if you find them too difficult, but do have a read on them:
- Understand what a Stack is. Try implementing one using a list and/or in other ways.
- Understand what a Queue is. Try implementing one using a list and/or in other ways.
- Understand what a Linked List is. Try implementing one.
- Understand what a HashTable is and how it is the backing data structure of Dictionaries.
- Understand what a Binary Tree is, and that it is a specific simple case of a more general graph structure. Try implementing one.
- Try solving some exercises that require you to write Data Structures and get an idea of the complexity of your solution.


# Data science and Machine Learning

If you want to help also with Data Science and Machine Learning-related tasks, you should cover the following points too.  
Otherwise, you can stop at the points above and you'll still be able to contribute to Software Engineering-related tasks.

## Basics of statistics
- [IMPORTANT] ❗ [Basics of descriptive statistics](https://www.tutorialspoint.com/python_pandas/python_pandas_descriptive_statistics.htm): mean, variance, stdev, covariance, correlation. Try computing them in Python using the Numpy, Pandas or similar packages (e.g. see [standard deviation with Numpy](https://numpy.org/doc/stable/reference/generated/numpy.std.html)).
- [IMPORTANT] ❗ [Function approximation; differences between Classification and Regression models](https://machinelearningmastery.com/classification-versus-regression-in-machine-learning/).
- [IMPORTANT] ❗ Understand well [what is a Classifier](https://deepai.org/machine-learning-glossary-and-terms/classifier) and its related evaluation metrics (Accuracy, Precision, etc.), including what is a [Confusion Matrix](https://www.geeksforgeeks.org/confusion-matrix-machine-learning/) and True Positives, False Positives, True Negatives, False Negatives (we use all of these in our work).
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
- Read about the [COCO format](https://www.v7labs.com/blog/coco-dataset-guide); we use it in our work, and we focus on the Object Detection task. Check also the [Format](https://cocodataset.org/#format-data).


### Knowledge representation
- What is a [Schema](https://www.computerhope.com/jargon/s/schema.htm)? Understand that a schema can be defined in various ways, e.g. as a Database Schema for a relational database (e.g. SQL) or as a set of OOP classes (e.g. C# classes, like in BHoM), or in many other ways (e.g. [RDFS](https://en.wikipedia.org/wiki/RDF_Schema)).
- [What is an **ontology**, and what are the differences with a schema](http://www.dl.edi-info.ir/Ontology%20and%20database%20schema,%20What%20is%20the%20difference.pdf)? Understand that the fundamental focus of an ontology is to specify and share meaning, while the fundamental focus for a database schema is to describe data, but they are [essentially the same thing](https://www.w3.org/wiki/SchemaVsOntology).
- What is a [Knowledge Graph](https://www.ontotext.com/knowledgehub/fundamentals/what-is-a-knowledge-graph/)? You can think of it as an instance of an Ontology, much like an Object is an instance of a Class in an OOP language schema.
- What is a [Knowledge Base](https://blog.diffbot.com/knowledge-graph-glossary/knowledge-base/) and how does it differ from a Knowledge Graph? Understand that all knowledge graphs are knowledge bases, while not every knowledge base qualifies as a knowledge graph.
