# Python-basics

## Python data types

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

**Code** <br>
```
In[1]  List_misc = [True, "4", 4.5, 4]<br>
In[2]  [type(i) for i in List_misc]<br>
Out[1] [<class 'bool'>, <class 'str'>, <class 'float'>, <class 'int'>]<br>
```

### Subsetting List

> **Warning** <br>
> Python use zero-indexing (all list start at zero). 

You can subset a list as follow:<br>

Example list<br>

list = [a, b, c, d, e, f, g]<br><br>

| Command  | Explanation                  | Output |
|----------|------------------------------|--------|
| list[0]  | It will return from index 0  | 'a'    |
| list[3]  | It will return from index 3  | 'd'    |
| list[4]  | It will return from index 4  | 'e'    |
| list[-3] | It will return from index 4  | 'e'    |
| list[5]  | It will return from index 5  | 'f'    |
| list[-1] | It will return from index 5  | 'f'    |

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

lxl = [["a", "b", "c"], ["d", "e", "f"], ["g", "h", "i"], ["j", "k", "l"]]<br>

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

x = ["a", "b", "c", "d"]<br>

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