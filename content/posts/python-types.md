---
title: "Python Types"
date: 2019-04-21T13:24:13+01:00
draft: false
toc: false
images:
tags: 
  - programming
  - python
---
The Zen of Python states:

> There should be one-- and preferably only one --obvious way to do it.

Yet python *for machine learning* is a language of choices:

- python 2 or python 3 (though this won't [last long](https://pythonclock.org/))
- Conda vs pip
- virtual_env vs pipenv vs venv... (and so many more)

The Python community seems incapable to work together on the a single tool for the benefit of all, it's fragmentation upon fragmentation. [^1] Don't get me wrong, I do like the language, libraries and ecosystem, but as with everything the more you get to know it, the more it starts annoying you.

Types for python seem to also allow us multiple options:

```python
# dynamic types
def left_pad(string, length, char=' '):
    if type(string) is not str:
        raise ValueError('string should be of type str')
    return string.rjust(length, char)

# type annotations
def left_pad(string: str, length: int, char: str = ' ') -> str:
    return string.rjust(length, char)

# type comments
def left_pad(string, length, char=' '):
    # type: (str, int, str) -> str
    return string.rjust(length, char)
```

However this by itself is not enough, in order to use types you need to either `pip install mypy` and run `mypy` which list any type inconsistencies:

```python
# cat test.py
def left_pad(string: str, length: int, char: str = ' ') -> str:
    return string.rjust(length, char)
print(left_pad(123, 13))
# mypy test.py
test.py:3: error: Argument 1 to "left_pad" has incompatible type "int"; expected "str"
```

Or fall back to your IDE (PyCharm) to inform you about type mismatches:

{{< figure src="/media/python-typings-pycharm-tooltip.png" title="PyCharm type tooltip" >}}

For the full documentation check [PEP 484 -- Type Hints](https://www.python.org/dev/peps/pep-0484/). There's also [The Ultimate Guide to Python Type Checking](https://realpython.com/python-type-checking/) which goes into more detail.





[^1]: <https://www.reddit.com/r/Python/comments/8tp5wc/alternative_to_pipenv/e1afmus/>

