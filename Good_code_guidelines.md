# Guidelines for Good code
These guidelines should be followed whenever coding in our Machine Learning organisation. When you raise a PR, your code will be reviewed following this criteria (in addition to code correctness and other measures).

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

And add the text in a concise but comprehensive way:

![image](https://github.com/user-attachments/assets/526dee4d-528d-4dcc-9945-03bc42d5b3c9)



## 1. Add type-hints (annotations) for every input and output parameter of your functions, _whenever possible_. 

Learn about [Type-hinting and the Typing module](https://realpython.com/lessons/type-hinting/) in Python if you don't know it.

Here, I've added `: int` to the input parameter, and `-> float` to indicate the type of the output:

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

### Note on Type-hinting: in some cases, typing classes may not be available directly within the Python package you are dealing with, e.g. OpenCV. Still try to add type-hinting if you can.

For example, in [OpenCV, you need to use an additional module to allow for Typing](https://stackoverflow.com/a/73261016/3873799): `cv2.typing`.

```python
import cv2

def my_opencv_function(input_image: cv2.typing.MatLike) -> None:
    # Your function here
```

However, this module is known to cause dependency issues, so it's fine if you want to skip annotating it.  
This really depends on the situation and comes with experience. Always strive to type-hint (annotate) every parameter that you can.

## 2. Make sure you set optional parameters (e.g. with a default value) is marked with the `Optional` type information and that the default value doesn't cause errors in your code.

Use `from typing import Optional` as below to annotate (type-hint) optional parameters, which should always have a default value assigned (e.g. `= something`):

```python
from typing import Optional

def my_function(required_integer: int, optional_integer : Optional[int] = 0) -> int:
    # Your function here
```


## 3. _Null checks_. At the start of the function, make sure to check that any non-Optional (e.g. without default value) input parameters for functions is "not None" or invalid:

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

## 4. Make sure that the inputs are of the correct type, based on what your type-hints. Use `isinstance()` to check for the type and raise `TypeError`.

Learn about [`isinstance()`](https://www.w3schools.com/python/ref_func_isinstance.asp) if you don't know it.  
It's always better to use `isinstance()` rather than `if type(object) == SomeType` because it allows to [check subclasses too](https://stackoverflow.com/a/1549814/3873799).

```python
def my_function(some_string: str) -> str:
    if not isinstance(some_string, str):
        # This interrupts execution with a meaningful error if it the input value is not of the correct type.
        raise TypeError(f"The input 'some_string' should be of type String, but was of type {type(some_string)}.")
```

## 5. _Test your code_. If you are using some code to try out your function, e.g. a `"if __name__ == "__main__"` code block, consider using its content as a pytest unit test.

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



## 6. If coding in the ML_CAD_Assistant repository, make sure that you have your files in the repository /data path in the correct way.

In the ML_CAD_Assistant repository, we organise all data in the `data` folder of the repository.  
This folder is divided in 3 subfolders: 
- `development` for data that is used to develop functionality. This folder is supposed to be as large as needed, the largest of the 3. For this reason, it is not tracked in the GitHub repository (i.e. it is not uploaded in the repository, it's [`gitignore`d](https://www.w3schools.com/git/git_ignore.asp?remote=github)). We must manually copy this folder and link it in any development enviroment (Virtual Machine or Workstation/Laptop) that we use for development. More info about this below. Note that we considered using [`git-lfs`](https://git-lfs.com/) but decided not to use it (reach out if you are curious why).
- `testing` for data that is used for unit tests or general testing. This folder is supposed to be smaller than the `development` folder in total size, but larger than the `production` one. It should contain a copy of any data required for testing. The data needs to be copied (not linked) because this data is required by the test automation suites that will clone our repository. For this reason, this folder is tracked in git (e.g. actually uploaded to the repository).
- `production` for data that must be present when we deploy our functionality. This should be the smallest of the three folders in terms of size, and contain only essential files that should be present when running the code in production. We typically deploy using Docker. 

The way you should place your data is as follows:

5.1 copy all the files that you need for development in the development data folder.

5.2 of those files, add a copy of the ones that you need for _testing_ in the test data folder, using the same folder structure.

5.3 of those files, copy the files that you need for _production_ in the production data folder, using the same folder structure.


## 7. If coding in the ML_CAD_Assistant repository, make sure that any filepath is referenced via the _globals DATA_PATH variable.

The code should access the data folders (see above) in a flexible way.  
For this reason, we centralised the data access functionality in the `_globals.py` file, that is located at the root `src` code directory of the repository.

We centralise most settings in a `_globals.py` file, in particular, settings regarding data in filepaths.

[TODO finish writing]





