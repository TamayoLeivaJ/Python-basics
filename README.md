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

## Python Install and Import Packages

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

The NumPy array is a new Python type, an alternative to the Python list, that is faster and capable of performing operations on arrays more easily than on lists. The NumPy array comes with its own methods, which may behave differently from the methods of other types. But the NumPy array can only contain values of a single type, while a Python list can contain different types of data.<br>