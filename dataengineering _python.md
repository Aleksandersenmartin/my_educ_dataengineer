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

## For Loops 
in Python, a for loop is used to iterate over sequences (like lists, tubples, strings) or other iterable ovjects (such as dictonaries or file objects). it allows you to execute a block of code repeatedly for each element in the sequence. unlike some other languages that use a traditional for loop structure (like for(int i = 0; i < n; i++)), python's for loops are more akin to "for each" loops that focus on elements rather dan indicies. 

```python
for element in iterable:
  #code block
```
- element: a temporary variable that takes on the value of each item in the iterable as the loop progresses
- iterable: an object capable of returning its elements one at a time, such as a list, tuple, string, rane, or a custom object that implements iteration methods.

##### Example 
```python
frutis = ["apple", "banana", "cherry]
for fruit in fruits:
  print(fruits)
```

##### Outcome 
```python
apple
banana
cherry
```

in this example, the loop will:
1. Assign fruit = "apple"
2. print"apple"
3. Assign fruit = "banana"
4. print"banana"
5. Assign fruit = "cherry"
6. print"cherry"

#### Iterating over different data types
##### List:
 ```python
my_list = [1,2,3,4]
for num in my_list:
  print(num)
```

##### Tuples: 
```python
my_tuple = (10,20,30)
for item in my_tuple:
  print(my_tuple)
```

##### Strings:
```python
for char in "hello":
  print(char)
```

##### Dictionaries: 
```python
my_dict = {"a":1, "b":2, "c":4}
for key in my_dict:
  print(key, my_dict[key])
```

##### Files: 
```python
with open("example.txt") as file: 
  for line in file:
    print(line)
```

#### using range() with For Loops 
if you need a numeric sequence, you can use the built-in range() function, which generates an artimetic sequence of integers: 
```python
for i in range(5):
  print(i)
```

#### Enumerating Over Iterables 
if you want the index along with the element, you can use the built-in enumerate() function: 
```python
fruits = ["apple", "banana", "cherry"]
for index, fruit in enumerated(fruits):
  print(index,fruit)
```
##### Outcome: 
0 apple
1 banana
2 cherry 

#### Nested For Loops 
You can nes for loops if you need to iterate over multiple dimensions or complex sturctures: 

```python
matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]
for row in matrix:
  for value in row:
    print(value)
```

#### The break and contionue statements 
- **Break:** stop the loop entierly and proceed to the next statement after the loop
```python
for i in range(10):
  if i == 5:
    break
print(i)
```

- **Continue:** Skip the rest of the current iteration and move on to the next iteration

```python
for i in range(5):
  if i == 2:
    continue
  print(i)

# This prints 0,1,3,4 (skipping 2) 
```

#### The else clause with For Loops 
A for loop can have an optional else clause. the else block executs if the loop finishes normally (i.e., without hitting a break): 
```python
for i in range(3):
  print(i)
else:
  print("Loop completed normaly"): 
```

```python
for i in range(3):
  if i == 1:
    break
  print(i)
else:
  print("loop completed normally")
```

## While Loops 
A while loop in python repeatedly executes a block of code as long as a given condition remains True. this makes it useful for scenarios where you don't know in advance how many times you need to iterate, but instead rely on a condition to continue or terminate the loop 

```python
while condition:
  #code block to execute repeatedly 
```

- **condition:** A Boolean expression that is evaluated before each iteration of the loop. if True, the loop's body executes; if False, the loop stops: 

```python
count = 0
while count < 5:
  print(count
  count += 1
```

#### Infinetie loops 
if the condition never becomes False, you'll get an infinite loop that never ends on its own: 

```python
while True:
  print("this will print forever!")
```

"This is useful in some cases (like running servers or waiting for user input), but generally, you want to make sure something inside tha loop can change to eventually break out of it. 

#### Controlling the flow: break and continue 
- **break:** immediaely exits the current loop

```python
count = 0
while True:
  print(count)
  count += 1
  if count == 3:
    break #stops the loop when count is 3 
```

- **continue:** Skips the rest of the current iteration and moves to the next iteration of the loop

```python
count = 0
while count < 5:
  count += 1
  if count == 3:
    countinue # skip printing when count is 3
  print(count
```
#### The else Clause with while loops 
Similar to for loops, a while loop can also have an else block. the else block executes only if the loop ends without a break

```python
count = 0
while count < 3
  printing(count += 1
else:
  print("Loop completed whithout break")

```

#### Common Patterns 
- Waiting for user input or a certain condition:
```python
while True:
  user_input = input("Enter 'quit' to stop:")
    break
```

- Loop until a certain computational condition is met:

```python
number = 1
while number < 1000:
  number = number * 2
print("Number is now:", number)
```

|Keyword|Function|
|-------|--------|
|and|Evaluate if multiple conditions are true|
|or|Evaluate one or more conditions are true|
|in|evaluate if a value is in a data structure|
|not|Evaluate if a value is not in a data structure|

## Function cheat sheet 
|Function|Returns|
|--------|-------|
|print()|Display an output, e.g., variable's value|
|max()|Find the larges value in a data structure|
|min()|Find the smallest calue in a data structure|
|sum()|Add up all elements in a data structure|
|round()|Trim a float to a specified number of decimal places|
|len()|Count the number of elements in a data structure|
|sorted()|Sort elements in a data structure in ascending order|
|help()|Get information about a function, variable, or value|

## Modules
