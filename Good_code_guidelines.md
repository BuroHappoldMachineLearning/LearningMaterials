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

```def
def divide_integer_by_two(input_integer):
    """Take an input integer and divide it by two. 
    The function will always return a float value, even if the input is an even number, because the division operation always returns a float value in Python.

    Args:
        input_integer (int): Input integer to be divided by two.

    Returns:
        float: Input integer divided by two.
    """
    return input_integer / 2
```


## 1. Add typing information for every input and output parameter of your functions, _whenever possible_. 

Learn about the Typing module in Python if you don't know it.

```python
def divide_integer_by_two(input_integer):
    """Take an input integer and divide it by two. 
    The function will always return a float value, even if the input is an even number, because the division operation always returns a float value in Python.

    Args:
        input_integer (int): Input integer to be divided by two.

    Returns:
        float: Input integer divided by two.
    """
    return input_integer / 2
```

In some cases, typing classes may not be available directly within the Python package you are dealing with, e.g. OpenCV. In [OpenCV, you need to use an additional module to allow for Typing](https://stackoverflow.com/a/73261016/3873799): `cv2.typing`.

```python
import cv2

def my_function(input_image: cv2.typing.MatLike) -> None:
    # Your code here
    pass
```

However, this module is known to cause dependency issues, so it's fine if you want to skip annotating it. This really depends on the situation and comes with experience. Always strive to annotate everything you can.

## 1.2 Make sure you set optional parameters (e.g. with a default value) is marked with the `Optional` type information and that the default value doesn't cause errors in your code.

```python

```



### 2. _Null checks_. Make sure to check that any non-Optional (e.g. without default value) input parameters for functions is not None and of the Correct type (use `isinstance()`):

```python

```

- Make sure that any filepath is referenced via the _globals DATA_PATH variable.
- Make sure that you have your files in the repository /data path in the correct way, which means:
   - copy all the files that you need for development in the development data folder.
   - of those files, copy the files that you need for testing in the test data folder, using the same folder structure.
   - of those files, copy the files that you need for production in the production data folder, using the same folder structure.
- If you are using a "if __name__ == "__main__" code block to try out your development code, consider copying that into a pytest function in a separate file.
