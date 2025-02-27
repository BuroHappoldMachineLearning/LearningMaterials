# Guidelines for Good code

You can use this guide as a _checklist_ to make sure your code is of good quality, so it's easier to collaborate with each other and create a robust codebase.

When you raise a PR, your code will be reviewed following this criteria (in addition to code correctness and other criteria).

## Before starting

Make sure you have Visual Studio Code fully configured for Python development, and the environments in place:
- See [this guide for configuring VSCode](SummaryList.md#visual-studio-code-and-python-initial-setup).
- Ask someone in the team which Python environments you should be using ([learn about them](https://github.com/BuroHappoldMachineLearning/LearningMaterials/blob/main/SummaryList.md#python-environments)) and how you can make a new one. We typically use Conda to manage our environments and we have different (shared) ones depending on the machine/workstation.


## 0. Create clearly scoped functions with a meaningful name that reflect what they do. Add a description to them.
You functions can be long, but you will often find that short functions are clearer and reusable. E.g.:
```python
def divide_integer_by_two(input_integer):
    return input_integer / 2
```

Make sure to add a DocString description to your functions, including input parameter descriptions, and that their name corresponds before raising a PR.  
You can install the ["AutoDocString" Visual Studio Code extension](https://marketplace.visualstudio.com/items?itemName=njpwerner.autodocstring) to help you stub the description. Just type three `"""` characters at the start of your function:

![image](https://github.com/user-attachments/assets/b31a45f5-31b5-48fd-8451-0e41ea366e85)

Then press Enter:

![image](https://github.com/user-attachments/assets/dfe6f00f-9d71-4073-9077-1b7eaa034f5f)

Checklist:
- Add the text in a concise but comprehensive way, see example below. The function description should clearly state what is the target of the function and what are the expected inputs, and explain what can happen in particular situations for the inputs (e.g. if it does not support numbers below 0).
- Make sure to add type information regarding your inputs and outputs.  
- Make sure that the names of the input parameters in the description matches those in the function declaration. 

![image](https://github.com/user-attachments/assets/526dee4d-528d-4dcc-9945-03bc42d5b3c9)

## 1. Avoid complex input or output types, e.g. no nested data structures, no tuples

### 1.1 Avoid using complex data structures like List of Dictionaries, Dictionaries of Dictionaries, and similar, for your function inputs and outputs.

Always prefer [_dataclasses_](https://github.com/BuroHappoldMachineLearning/LearningMaterials/blob/main/SummaryList.md#basics-of-python) in these cases. They are much simpler to understand for others and they can be used/reused easily. Remember to add descriptions to your dataclasses to help others understand what they are about.

### 1.2 Avoid returning Tuples from your functions

You may be often tempted to [return multiple outputs from your Python function](https://stackoverflow.com/q/354883/3873799), for example using Tuples, e.g.:

```python
def function_returning_multiple_outputs():
    # some code
    return output1, output2, output3 # DON'T DO THIS
```

While this is valid Python code, it is incredibly hard for others to use, even if you type-hint the output tuple. Always prefer dataclasses (see above point).

[Named Tuples](https://www.geeksforgeeks.org/namedtuple-in-python/) are also a bad idea. Dataclasses are much easier to understand, to manage and to reuse.

### 1.3 For input or output Dictionaries, please strive to type-annotate them.

Dictionaries are ok as an output or input, but please strive to type-annotate them. Please see the below point.

## 2. Add type-hints (annotations) for every input and output parameter of your functions, _whenever possible_. 

Learn about [Type-hinting and the Typing module](https://realpython.com/lessons/type-hinting/) in Python if you don't know it.

In the example below, I've added `: int` to the input parameter, and `-> float` to indicate the type of the output:

```python
def divide_integer_by_two(input_integer : int) -> float:
    """Take an input integer and divide it by two. 
    The function will always return a float value, even if the input is an even number, because the division operation always returns a float value in Python.

    Args:
        input_integer (int): Input integer to be divided by two.

    Returns:
        float: Input integer divided by two.
    """
    return input_integer / 2
```

### 2.1 **Make sure to type-hint dictionaries** and describe what their key/value are supposed to represent.

All Dictionaries should be type-annotated, and a comment should be left to say what their key and value are supposed to represent.

For dictionaries that are input or outputs of a function, you should write their key/value description in the function input or output description.

For example:

```python
def divide_values_by_two(input_data : Dict[str, int]) -> Dict[str, float]:
    """Take an input Dictionary where its values must be integers, iterate all its keys,
    get the corresponding values and individually divide them by two.
    Return a new Dictionary where the keys are the same as the original Dictionary, and the values are the original Dictionary's values divided by 2. 

    Args:
        input_data (Dict[str, int]): Input Dictionary where its values must be integers.

    Returns:
        Dict[str, float]: Output Dictionary where the keys are the same as the input Dictionary and its values are the individual input Dictionary values divided by two.
    """
    output_data : Dict[str, float] = {} # Add a description here. E.g. the key represent the name of the number, the value represents a measure of something.
    
    for k, v in input_data:
        output_data[k] = v / 2
    
    return output_data
```

### 2.2 **If type hints are not available for your package**. 

In some cases, typing classes may not be available directly within the Python package you are dealing with, e.g. OpenCV. Still try to add type-hinting if you can.

For example, in [OpenCV, you need to use an additional module to allow for Typing](https://stackoverflow.com/a/73261016/3873799): `cv2.typing`.

```python
import cv2

def my_opencv_function(input_image: cv2.typing.MatLike) -> None:
    # Your function here
```

However, this module is known to cause dependency issues, so it's fine if you want to skip annotating it.  
This really depends on the situation and comes with experience. Always strive to type-hint (annotate) every parameter that you can.

### 2.3 If your function returns nothing (e.g. only prints stuff), type-annotate `-> None`

E.g.
```python
def my_printing_function() -> None:
    # code
```

## 3. Make sure you set optional parameters (e.g. with a default value) is marked with the `Optional` type information and that the default value doesn't cause errors in your code.

Use `from typing import Optional` as below to annotate (type-hint) optional parameters, which should always have a default value assigned (e.g. `= something`):

```python
from typing import Optional

def my_function(required_integer: int, optional_integer : Optional[int] = 0) -> int:
    # Your function here
```


## 4. _Null checks_. At the start of the function, make sure to check that any non-Optional (e.g. without default value) input parameters for functions is "not None" or invalid:

Null checks (verification that an input is not `None`) are extremely useful to return meaningful errors when an input is invalid.  
Without them, your function may misbehave and return a difficult-to-understand error, especially when it is called from another function.

Learn about Python Errors if you're not familiar with them. Useful Errors are `ValueError` and `FileNotFoundError`, but there are many more useful ones.  
Try to use the most appropriate one depending on the situation.

```python
from typing import Optional

def my_function(required_string: str, optional_string : Optional[str] = "") -> str:
    if required_string is None:
        raise ValueError("The input 'required_string' should not be None.") # this interrupts execution with a meaningful error if it is invalid.

    # 'optional_string' does not need to be checked for nullity because it's Optional.
```

## 5. Make sure that the inputs are of the correct type, based on what your type-hints. Use `isinstance()` to check for the type and raise `TypeError`.

Learn about [`isinstance()`](https://www.w3schools.com/python/ref_func_isinstance.asp) if you don't know it.  
It's always better to use `isinstance()` rather than `if type(object) == SomeType` because it allows to [check subclasses too](https://stackoverflow.com/a/1549814/3873799).

```python
def my_function(some_string: str) -> str:
    if not isinstance(some_string, str):
        # This interrupts execution with a meaningful error if it the input value is not of the correct type.
        raise TypeError(f"The input 'some_string' should be of type String, but was of type {type(some_string)}.")
```

## 6. _Test your code_. If you are using some code to try out your function, e.g. a `"if __name__ == "__main__"` code block, consider using its content as a pytest unit test.

When developing/debugging, you may be using a piece of code to call your function with some prepared input parameters, e.g. in an [`if __name__ == "__main__"` block](https://realpython.com/if-name-main-python/). For example:

```python
def divide_integer_by_two(input_integer):
    return input_integer / 2

if __name__ == "__main__":
    print(divide_integer_by_two(2)) # prints 1.0
    print(divide_integer_by_two(3)) # prints 1.5
```

This is useful in combination with Visual Studio Code [debugging features](https://code.visualstudio.com/docs/python/debugging).

However, your "test" code there very useful and it can (and should) be used in a [unit test](https://code.visualstudio.com/docs/python/testing).  
Unit tests are extremely useful because they can be run automatically by Bots and GitHub actions. We should strive to always create unit tests whenever possible, to obtain good [test coverage](https://en.wikipedia.org/wiki/Code_coverage).  
This is because, in the future, other people may modify other functions that your function depends on.  
At the moment, we don't have test automations set in place, but we will try and create them in the near future. For this reason, it's important to create unit tests whenever possible.  
Unit tests also help people understand how your function is supposed to work, in a variety of scenarios (one scenario, e.g. input combination, per test).  

For example, you can take the content of the `"if __name__ == "__main__"` code block above and place it in a separate file called `test_my_new_functionality.py`, where you can do:

```python
import pytest
from my_module import divide_integer_by_two

def test_divide_integer_by_two_with_even_number_input():
    """
    Check that the function divide_integer_by_two returns the correct value when an even number is input.
    """
    assert divide_integer_by_two(2) == 1.0


def test_divide_integer_by_two_with_odd_number_input():
    """
    Check that the function divide_integer_by_two returns the correct value when an odd number is input.
    """
    assert divide_integer_by_two(3) == 1.5
```

These two tests can then be run by automated test suites to periodically check for code robustness, e.g. every time we raise a PR.
Check these code guidelines to create good tests and always strive to do Unit tests when you create new functionality.
You can also do [Test-Driven Development (TDD)](https://testdriven.io/blog/modern-tdd/) e.g. you first thik about the main use cases for your function, and create the test first, which can call an empty stub for your function (a `divide_integer_by_two()` function that does nothing).
You can use those tests to inform the content of your function. You can run your tests first and check that they all _fail_. Then, you develop your code accordingly, and your function will be correct when all tests have passed.

### 6.1 Provide descriptions to your test functions whenever possible.

It's generally useful to leave a description about what your test is about, unless it's particularly clear from the code itself. See examples above.


## 7. If coding in the ML_CAD_Assistant repository, make sure that you have your files in the repository /data path in the correct way.

In the ML_CAD_Assistant repository, we organise all data in the `data` folder of the repository.  
This folder is divided in 3 subfolders: 
- `development` for data that is used to develop functionality. This folder is supposed to be as large as needed, the largest of the 3. For this reason, it is not tracked in the GitHub repository (i.e. it is not uploaded in the repository, it's [`gitignore`d](https://www.w3schools.com/git/git_ignore.asp?remote=github)). We must manually copy this folder and link it in any development enviroment (Virtual Machine or Workstation/Laptop) that we use for development. More info about this below. Note that we considered using [`git-lfs`](https://git-lfs.com/) but decided not to use it (reach out if you are curious why).
- `testing` for data that is used for unit tests or general testing. This folder is supposed to be smaller than the `development` folder in total size, but larger than the `production` one. It should contain a copy of any data required for testing. The data needs to be copied (not linked) because this data is required by the test automation suites that will clone our repository. For this reason, this folder is tracked in git (e.g. actually uploaded to the repository).
- `production` for data that must be present when we deploy our functionality. This should be the smallest of the three folders in terms of size, and contain only essential files that should be present when running the code in production. We typically deploy using Docker. 

The way you should place your data is as follows:

- copy all the files that you need for development in the development data folder.

- of those files, add a copy of the ones that you need for _testing_ in the test data folder, using the same folder structure.

- of those files, copy the files that you need for _production_ in the production data folder, using the same folder structure.


## 8. If coding in the ML_CAD_Assistant repository, make sure that any filepath is referenced via the _globals DATA_PATH variable.

The code should access the data folders (see above) in a flexible way.  
For this reason, we centralised the data access functionality in the `_globals.py` file, that is located at the root `src` code directory of the repository.

We centralise most settings in a `_globals.py` file, in particular, settings regarding data in filepaths.

[TODO finish writing]





