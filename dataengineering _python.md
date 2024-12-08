## Variables 

#### Definition: 
- A variable is a symbolic name associated with a value or data stored in memory
- Python is dynamically typed, meaning you don't need to specify the data type when declaring a variable

#### Characteristics 
- Variables are created when a value is assigned to them
- The type of variable can be determined using type(variable_name)

```python
varibale_name =value 
```
```python
x = 10 # Integer
name = "Alice #String
pi = 3.14 #Float
is_active = True  #Boolean

```

## Lists 

#### Definition 
- A list is a collection of ordered, mutable(changeable) items that can hold mixed data types

#### Characteristics
- Lists are defined using square brackets []
- indexing starts at 0
- supports slicing, appending, removing, and more

```python
list_name =[item1, item2, item3]
```

```python
numbers =[1, 2, 3, 4] # List of integers
mixed = [1, "Alice", 3.14] # List with mixed types 
nested = [[1, 2], [3, 4]] # Nested list
```

#### Common Operations 
```python
numbers.append(5) # Add an item
numbers.remove(2) # Remove an item
numbers[1] #Access an element (index 1)
numbers[1:3] # slicing
len(numbers) # Length of the list
```

## Tubles 

#### DEfinition 
- A tuble is a collection of ordered, immutable (unchangeable) items

#### Characteristics 
- Tubles are defined using parantheses ()
- Can hold mixed data types
- use tubles when the data should not be modified.

```python
tuple_name = (item1, item2, item3)
```

## Dictionaries 
#### Definition
- A dictionary is a collection of unordered, mutable key-value pairs

#### Characteristics 
- Defined using curly braces {}
- keys must be unique and imuutable (strings, numbers, or tubles)
- Values can be of any data type an can be duplicated

```python
dict_name = {key1: value1, key2: value2}
```

```python
persons{
  "name": "Alice",
  "age": 25,
  "is_student": True
```

## Conditional statements and operators

In python, conditional statements and operators are fundamental building blocks that allow you to control the flow of your program. by evalutating conditions - expressions that result in a Boolean value (true or False) - you can decide which block of code executed under certain circumstances. this lets you make your code dynamic and responsive to different inputs, states, or data values. 

### Conditional Statements 
#### The IF statement 
The if statement is the most basic form of conditional logic in Python. it checks whether a given condition is True and, if so, executes the code that follows: 

```python
age = 20
if age >= 30:
  print("You are old enough to vote")
```

#### The if-elif-else Chain 
Often, you'll have multiple mutally exclusive conditions to check. in that case, you can use elif (short for "else if") to stack multiple conditions: 

```python
grade = 85
if grade >= 90:
  print("A")
elif grade >= 80:
  print("B")
elif grade >= 70:
  print("C")
else:
  print("Below C")
```
