# Python-basics

## Python data types

Python is an object-oriented programming (OOP) language, and its standard implementation is written in C. Thus, in Python each object actually refers to a C structure, where information about its value, data type and other relevant details are contained.<br>    

| Type | Description | Data <br>Type | Example | Conversion <br>function |
|---|---|---|---|---|
| int | integer: a number without a fractional part. | Numeric | 100 | int() |
| float | floating point: a number that has both an integer <br>and fractional part, separated by a point. | Numeric | 1.1 | float() |
| str | string: a type to represent text. | Text | string, text | str() |
| bool | boolean: a type to represent logical values.<br>Can only be True or False (**Capital are important**) | Boolean | True; False | bool() |
<br>

> **Note** <br>
> You can use the type() function to inspect the type of a value or a variable.

## Python list

In Python a list is the standard mutable multi-element container. In Python we can create a list with heterogeneous type elements (i.e., bool, str, float, int). Thus, a list is a composite data type, a collection of values that can contain any data type, and different data types, including other lists. To achieve this flexible structure, in Python each element of a list contains its own information, such as data type and others. Thus, each element within a list is a full Python object. The Python list is in fact a pointer that guides to a block of pointers, each of which references a full Python object such as a Python integer, or Python str.<br>

Example:<br> 

**Python Code** <br>
```python
In[1]:  List_misc = [True, "4", 4.5, 4]<br>
In[2]:  [type(i) for i in List_misc]<br>
Out[1]: [<class 'bool'>, <class 'str'>, <class 'float'>, <class 'int'>]
```
<br>

### Subsetting List

> **Warning** <br>
> Python use zero-indexing (all list start at zero). 

You can subset a list as follow:<br>

Example list<br>

**Python Code** <br>
```python
list = [a, b, c, d, e, f, g]
```
<br>

| Command  | Explanation                  | Output |
|----------|------------------------------|--------|
| list[0]  | It will return from index 0  | 'a'    |
| list[3]  | It will return from index 3  | 'd'    |
| list[4]  | It will return from index 4  | 'e'    |
| list[-3] | It will return from index 4  | 'e'    |
| list[5]  | It will return from index 5  | 'f'    |
| list[-1] | It will return from index 5  | 'f'    |
<br>

### List Slicing

> **Warning** <br> 
> The syntax for list slicing in Python is interpreted as follows:<br> 
>
> * list[ **Start**:**End** ]<br>
>
> Where the **Start** point is **included** in the output, but the **End** point is **excluded**.<br><br>

| Command     | Explanation                      | Output                              |
|-------------|----------------------------------|-------------------------------------|
| list        | It will return from index 0 to 6 | ['a', 'b', 'c', 'd', 'e', 'f', 'g'] |
| list[:]     | It will return from index 0 to 6 | ['a', 'b', 'c', 'd', 'e', 'f', 'g'] |
| list[:4]    | It will return from index 0 to 3 | ['a', 'b', 'c', 'd']                |
| list[2:]    | It will return from index 2 to 6 | ['c', 'd', 'e', 'f', 'g']           |
| list[2:4]   | It will return from index 2 to 3 | ['c', 'd']                          |
| list[-5:-3] | It will return from index 2 to 3 | ['c', 'd']                          |
| list[3:6]   | It will return from index 3 to 5 | ['d', 'e', 'f']                     |
| list[-4:-1] | It will return from index 3 to 5 | ['d', 'e', 'f']                     |
<br>

### Subsetting lists of lists

To make a subset from a nested list, you must select the index of the list and then select the index of the list items, as in the following codes.<br><br> 

> **Warning** <br>
> Python use zero-indexing (all list start at zero). the index of the nested list also starts at zero.

Example list<br>

**Python Code** <br>
```python
lxl = [["a", "b", "c"], 
       ["d", "e", "f"], 
       ["g", "h", "i"], 
       ["j", "k", "l"]]
```
<br>

| Command    | Explanation                                           | Output                                 |
|------------|-------------------------------------------------------|----------------------------------------|
| lxl[0]     | It will return list index 0                           | ['a', 'b', 'c']                        |
| lxl[-1]    | It will return list index -1 or 3                     | ['j', 'k', 'l']                        |
| lxl[2:]    | It will return from list index 2 to last              | [['g', 'h', 'i'], <br>['j', 'k', 'l']] |
| lxl[0][2]  | It will return index 2 from list index 0              | 'c'                                    |
| lxl[2][0]  | It will return index 0 from list index 2              | 'g'                                    |
| lxl[2][1:] | It will return from index 1 to last from list index 2 | ['h', 'i']                             |
| lxl[2][:2] | It will return from index 0 to 1 from list index 2    | ['g', 'h']                             |
<br>

### Inner workings of lists

Lists are pointers to a collection of Python objects, so if the same list of objects is referenced from two separate lists, modifying one of the lists will modify the items in both lists. To avoid this behavior, it is necessary to create an explicit copy of the list items. You can create explicit copies of a list using the following list() or [:] syntax. <br>

Example list<br>

**Code** <br>
```python
x = ["a", "b", "c", "d"]
```
<br>

| Command              | Action | Explanation                            | Output                                   |
|----------------------|--------|----------------------------------------|------------------------------------------|
| x_copy = list(x)     | Copy   | Create a copy from list x              | ['a', 'b', 'c', 'd']                     |
| x_copy = x[:]        | Copy   | Create a copy from list x              | ['a', 'b', 'c', 'd']                     |
| del(x[1])            | Delete | Delete item with index 1 from list x   | ['a', 'c', 'd']                          |
| del x[1]             | Delete | Delete item with index 1 from list x   | ['a', 'c', 'd']                          |
| del x                | Delete | Remove list x                          | NameError: name 'x' is not defined       |
| x.clear()            | Delete | Clear list x                           | []                                       |
| x.pop(1)             | Delete | Delete item with index 1 from list x   | ['a', 'c', 'd']                          |
| x.remove("c")        | Delete | Delete item "c" from list x            | ['a', 'b', 'd']                          |
| x.append("e")        | Add    | Add item to a list                     | ['a', 'b', 'c', 'd', 'e']                |
| x.insert(1, "f")     | Add    | Add item to a list at index position 1 | ['a', 'f', 'b', 'c', 'd', 'e']           |
| x_1 = x + ["e", "f"] | Add    | Add items to a list                    | ['a', 'b', 'c', 'd', 'e', 'f']           |
| x2 = x + x           | Add    | Add a list of items to a list          | ['a', 'b', 'c', 'd', 'a', 'b', 'c', 'd'] |
<br>

## Python Dictionary

In Python, dictionaries are similar to lists, but instead of being indexed by a range of numbers like Python lists, Python dictionaries are indexed by unique values called keys. But when should I use lists or dictionaries to store my data? When searching for data must be fast and if unique keys can be specified, a dictionary is preferable to lists. However, if you are looking to easily select a subset of your data, or when the order of the elements matters, you should prefer lists. A dictionary, like a list, can be composed of multiple dictionaries (dictionary of dictionaries).<br>

The basic syntax to create a dictionary is the following:

Example:<br> 

**Python Code** <br>
```python
# Basic syntax
dictionary = { "key1":"value", "key2":"value"}

# Dictionary
europe = {'Spain':'Madrid', 
          'France':'Paris', 
          'Germany':'Berlin', 
          'Norway':'Oslo' }

# Dictionary of dictionaries
europe = { 'Spain': { 'capital':'Madrid', 'population':46.77 },
           'France': { 'capital':'Paris', 'population':66.03 },
           'Germany': { 'capital':'Berlin', 'population':80.62 },
           'Norway': { 'capital':'Oslo', 'population':5.084 } }
```
<br>

| Command                   | Action  | Explanation                           |
|---------------------------|---------|---------------------------------------|
| europe['Italy'] = 'Milan' | Add     | Add key-value pair to dictionary      |
| europe['Italy'] = 'Rome'  | Modify  | Modify the value of a key-value pair  |
| print('Italy' in europe)  | Confirm | Assert the addition of key-value pair |
| del(europe['Italy'])      | Delete  | Delete key-value pair from dictionary |
<br>

## Python Functions

List of Python built-in functions.<br>

| Function       | Description                                                                                   |
|----------------|-----------------------------------------------------------------------------------------------|
| abs()          | Returns the absolute value of a number                                                        |
| all()          | Returns True if all items in an iterable object are true                                      |
| any()          | Returns True if any item in an iterable object is true                                        |
| ascii()        | Returns a readable version of an object. Replaces none-ascii characters with escape character |
| bin()          | Returns the binary version of a number                                                        |
| bool()         | Returns the boolean value of the specified object                                             |
| bytearray()    | Returns an array of bytes                                                                     |
| bytes()        | Returns a bytes object                                                                        |
| callable()     | Returns True if the specified object is callable, otherwise False                             |
| chr()          | Returns a character from the specified Unicode code.                                          |
| classmethod()  | Converts a method into a class method                                                         |
| compile()      | Returns the specified source as an object, ready to be executed                               |
| complex()      | Returns a complex number                                                                      |
| delattr()      | Deletes the specified attribute (property or method) from the specified object                |
| dict()         | Returns a dictionary (Array)                                                                  |
| dir()          | Returns a list of the specified object's properties and methods                               |
| divmod()       | Returns the quotient and the remainder when argument1 is divided by argument2                 |
| enumerate()    | Takes a collection (e.g. a tuple) and returns it as an enumerate object                       |
| eval()         | Evaluates and executes an expression                                                          |
| exec()         | Executes the specified code (or object)                                                       |
| filter()       | Use a filter function to exclude items in an iterable object                                  |
| float()        | Returns a floating point number                                                               |
| format()       | Formats a specified value                                                                     |
| frozenset()    | Returns a frozenset object                                                                    |
| getattr()      | Returns the value of the specified attribute (property or method)                             |
| globals()      | Returns the current global symbol table as a dictionary                                       |
| hasattr()      | Returns True if the specified object has the specified attribute (property/method)            |
| hash()         | Returns the hash value of a specified object                                                  |
| help()         | Executes the built-in help system                                                             |
| hex()          | Converts a number into a hexadecimal value                                                    |
| id()           | Returns the id of an object                                                                   |
| input()        | Allowing user input                                                                           |
| int()          | Returns an integer number                                                                     |
| isinstance()   | Returns True if a specified object is an instance of a specified object                       |
| issubclass()   | Returns True if a specified class is a subclass of a specified object                         |
| iter()         | Returns an iterator object                                                                    |
| len()          | Returns the length of an object                                                               |
| list()         | Returns a list                                                                                |
| locals()       | Returns an updated dictionary of the current local symbol table                               |
| map()          | Returns the specified iterator with the specified function applied to each item               |
| max()          | Returns the largest item in an iterable                                                       |
| memoryview()   | Returns a memory view object                                                                  |
| min()          | Returns the smallest item in an iterable                                                      |
| next()         | Returns the next item in an iterable                                                          |
| object()       | Returns a new object                                                                          |
| oct()          | Converts a number into an octal                                                               |
| open()         | Opens a file and returns a file object                                                        |
| ord()          | Convert an integer representing the Unicode of the specified character                        |
| pow()          | Returns the value of x to the power of y                                                      |
| print()        | Prints to the standard output device                                                          |
| property()     | Gets, sets, deletes a property                                                                |
| range()        | Returns a sequence of numbers, starting from 0 and increments by 1 (by default)               |
| repr()         | Returns a readable version of an object                                                       |
| reversed()     | Returns a reversed iterator                                                                   |
| round()        | Rounds a numbers                                                                              |
| set()          | Returns a new set object                                                                      |
| setattr()      | Sets an attribute (property/method) of an object                                              |
| slice()        | Returns a slice object                                                                        |
| sorted()       | Returns a sorted list                                                                         |
| staticmethod() | Converts a method into a static method                                                        |
| str()          | Returns a string object                                                                       |
| sum()          | Sums the items of an iterator                                                                 |
| super()        | Returns an object that represents the parent class                                            |
| tuple()        | Returns a tuple                                                                               |
| type()         | Returns the type of an object                                                                 |
| vars()         | Returns the __dict__ property of an object                                                    |
| zip()          | Returns an iterator, from two or more iterators                                               |
<br>

## Python Methods

> **Note** <br>
> The dot notation allows you to access the properties of a Python object. To use dot notation, you must specify the object by its name, followed by a dot (.), followed by the method name. The methods you can apply to an object will depend on the type of object.

### String Methods

| Method         | Description                                                                                   |
|----------------|-----------------------------------------------------------------------------------------------|
| capitalize()   | Converts the first character to upper case                                                    |
| casefold()     | Converts string into lower case                                                               |
| center()       | Returns a centered string                                                                     |
| count()        | Returns the number of times a specified value occurs in a string                              |
| encode()       | Returns an encoded version of the string                                                      |
| endswith()     | Returns true if the string ends with the specified value                                      |
| expandtabs()   | Sets the tab size of the string                                                               |
| find()         | Searches the string for a specified value and returns the position of where it was found      |
| format()       | Formats specified values in a string                                                          |
| format_map()   | Formats specified values in a string                                                          |
| index()        | Searches the string for a specified value and returns the position of where it was found      |
| isalnum()      | Returns True if all characters in the string are alphanumeric                                 |
| isalpha()      | Returns True if all characters in the string are in the alphabet                              |
| isascii()      | Returns True if all characters in the string are ascii characters                             |
| isdecimal()    | Returns True if all characters in the string are decimals                                     |
| isdigit()      | Returns True if all characters in the string are digits                                       |
| isidentifier() | Returns True if the string is an identifier                                                   |
| islower()      | Returns True if all characters in the string are lower case                                   |
| isnumeric()    | Returns True if all characters in the string are numeric                                      |
| isprintable()  | Returns True if all characters in the string are printable                                    |
| isspace()      | Returns True if all characters in the string are whitespaces                                  |
| istitle()      | Returns True if the string follows the rules of a title                                       |
| isupper()      | Returns True if all characters in the string are upper case                                   |
| join()         | Converts the elements of an iterable into a string                                            |
| ljust()        | Returns a left justified version of the string                                                |
| lower()        | Converts a string into lower case                                                             |
| lstrip()       | Returns a left trim version of the string                                                     |
| maketrans()    | Returns a translation table to be used in translations                                        |
| partition()    | Returns a tuple where the string is parted into three parts                                   |
| replace()      | Returns a string where a specified value is replaced with a specified value                   |
| rfind()        | Searches the string for a specified value and returns the last position of where it was found |
| rindex()       | Searches the string for a specified value and returns the last position of where it was found |
| rjust()        | Returns a right justified version of the string                                               |
| rpartition()   | Returns a tuple where the string is parted into three parts                                   |
| rsplit()       | Splits the string at the specified separator, and returns a list                              |
| rstrip()       | Returns a right trim version of the string                                                    |
| split()        | Splits the string at the specified separator, and returns a list                              |
| splitlines()   | Splits the string at line breaks and returns a list                                           |
| startswith()   | Returns true if the string starts with the specified value                                    |
| strip()        | Returns a trimmed version of the string                                                       |
| swapcase()     | Convert uppercase characters to lowercase and vice versa                                      |
| title()        | Return a version of the string where each word is titlecased                                  |
| translate()    | Replace each character in the string using the given translation table                        |
| upper()        | Return a copy of the string converted to uppercase                                            |
| zfill()        | Fills a numeric string with zeros on the left, to fill a field of the given width             |
<br>

### List Methods

| Method    | Description                                                                  |
|-----------|------------------------------------------------------------------------------|
| append()  | Adds an element at the end of the list                                       |
| clear()   | Removes all the elements from the list                                       |
| copy()    | Returns a copy of the list                                                   |
| count()   | Returns the number of elements with the specified value                      |
| extend()  | Add the elements of a list (or any iterable), to the end of the current list |
| index()   | Returns the index of the first element with the specified value              |
| insert()  | Adds an element at the specified position                                    |
| pop()     | Removes the element at the specified position                                |
| remove()  | Removes the first item with the specified value                              |
| reverse() | Reverses the order of the list                                               |
| sort()    | Sorts the list                                                               |
<br>

### Dictionary Methods

| Method       | Description                                                                                                 |
|--------------|-------------------------------------------------------------------------------------------------------------|
| clear()      | Removes all the elements from the dictionary                                                                |
| copy()       | Returns a copy of the dictionary                                                                            |
| fromkeys()   | Returns a dictionary with the specified keys and value                                                      |
| get()        | Returns the value of the specified key                                                                      |
| items()      | Returns a list containing a tuple for each key value pair                                                   |
| keys()       | Returns a list containing the dictionary's keys                                                             |
| pop()        | Removes the element with the specified key                                                                  |
| popitem()    | Removes the last inserted key-value pair                                                                    |
| setdefault() | Returns the value of the specified key. If the key does not exist: insert the key, with the specified value |
| update()     | Updates the dictionary with the specified key-value pairs                                                   |
| values()     | Returns a list of all the values in the dictionary                                                          |
<br>

## Python Install and Import Packages

### Install Packages

First install pip (Package Installer for Python). Installation of pip is required once. If you already have pip installed, you can go to the next step in the list.<br>

#### Instalation in Python2.7

**Bash Code** <br>
```bash
## 1) Install pip.py
sudo apt install python-pip

## 2) Then with pip instaled install required packages
## Install numpy package
pip install numpy

## 3) Verify packages instalation 
pip show numpy

## 4) Update package (if necessary)
pip install --upgrade numpy

```

#### Instalation in Python3

**Bash Code** <br>
```bash
## 1) Install pip.py
sudo apt install python3-pip

## 2) Then with pip instaled install required packages
## Install numpy, pandas, matplotlib packages
pip3 install numpy
pip3 install pandas
pip3 install matplotlib

## 3) Verify packages instalation 
pip3 show numpy
pip3 show pandas
pip3 show matplotlib

## 4) Update package (if necessary)
pip3 install --upgrade numpy
pip3 install --upgrade pandas
pip3 install --upgrade matplotlib

```
<br>

### Import Packages

**Python Code** <br>
```python
# General imports
# Import complete numpy package functions
import numpy

# General imports with local aliases
# Import complete numpy package functions with an shortcut aliases
import numpy as np

# Selective import
# Import solely the array function of the numpy package
from numpy import array

```
<br>

# Python Packages

## NumPy 

Numpy package provides<br>
1. An array object of arbitrary homogeneous items<br>
1. Fast mathematical operations over arrays<br>
1. Linear Algebra, Fourier Transforms, Random Number Generation<br>

The NumPy array is a new Python type, an alternative to the Python list, that is faster and capable of performing operations on arrays more easily than on lists. The NumPy array comes with its own methods, which may behave differently from the methods of other types. But the NumPy array can only contain values of a single type, while a Python list can contain different types of data. If elements of different types are included, Numpy array will transform those elements to end up with an array of homogeneous type, this is also known as **type coercion**. In this type coercion, for example, the bool type value **True** becomes 1, and the bool type value **False** becomes 0, if coerced to a numeric array.<br>

Features
- Easy handling of missing data in floating point as well as non-floating point data.<br>
- Size mutability: columns can be inserted and deleted from DataFrame and higher dimensional objects.<br>
- Automatic and explicit data alignment: objects can be explicitly aligned to a set of labels, or the user can simply ignore the labels and let 'Series', 'DataFrame', etc. automatically align the data for you in computations.<br>
- Powerful, flexible group by functionality to perform split-apply-combine operations on data sets, for both aggregating and transforming data.<br>
- Make it easy to convert ragged, differently-indexed data in other Python and NumPy data structures into DataFrame objects.<br>
- Intelligent label-based slicing, fancy indexing, and subsetting of large data sets.<br>
- Intuitive merging and joining data sets.<br>
- Flexible reshaping and pivoting of data sets.<br>
- Hierarchical labeling of axes (possible to have multiple labels per tick).<br>
- Robust IO tools for loading data from flat files (CSV and delimited), Excel files, databases, and saving/loading data from the ultrafast HDF5 format.<br>
- Time series-specific functionality: date range generation and frequency conversion, moving window statistics, date shifting and lagging.<br><br>

### Import NumPy Package

**Python Code** <br>
```python
# General imports with local aliases
# Import complete numpy package functions with an shortcut aliases
import numpy as np

```
<br>

## Pandas 

*pandas* is a Python package providing fast, flexible, and expressive data structures designed to make working with "relational" or "labeled" data both easy and intuitive. It aims to be the fundamental high-level building block for doing practical, **real world** data analysis in Python. Additionally, it has the broader goal of becoming **the most powerful and flexible open source data analysis / manipulation tool available in any language**. It is already well on its way toward this goal.<br>

### Import Pandas Package

**Python Code** <br>
```python
# Selective import with local aliases
# Import Pandas package functions with an shortcut aliases
import pandas as pd

```
<br>

## Matplotlib

 *matplotlib.pyplot* is a state-based interface to matplotlib. It provides an implicit,  MATLAB-like, way of plotting.  It also opens figures on your screen, and acts as the figure GUI manager.<br>

### Import Matplotlib Package

**Python Code** <br>
```python
# Selective import with local aliases
# Import Matplotlib package pyplot function with an shortcut aliases
import matplotlib.pyplot as plt

```
<br>



# References

- [DataCamp](https://app.datacamp.com/learn/) 
- [W3Schools](https://www.w3schools.com/python/) 
- [Python.org](https://www.python.org)