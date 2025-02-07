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

## Functions
A function is a reusable block of code designed to perform a specific task. Functions help organi<e your code into logical, manageable pieces, making it more readable, easier to maintain, and avoiding repetition. instead of writing the same piece of code multiple times, you write it once in a function and then "call" that function whenever you need it. 

#### Defining a Function 
You create a function using the **def** keyword, followed by the function''s name and a set of parentheses. inside the parentheses, you can include parameters - variables that accept values (called arguments) passed into the function.
The function's code block is indented underneath the definition line. 

```python
def greet(name):
  print("Hello, "+ name + "!"
```

#### Calling a Function
To use a function, just write its name followed by a pair of parantheses. if the function has parameters, provide them as arguments inside the parentheses. 

```python
greet("Alice")   #Prints: Hello, Alice! 
greet("Bob")     #Prints: Hello, Bob! 
```
When you call greet ("Alice"), the value Alice" is passed to the name parameter, and the function executes its code using that value. 

#### Returning Values 
Functions can also return calues using the **return** keyword. this allows you to store the result of a function call in a cariable and use it later. 

```python
def add_numbers(a, b):
  result = a + b
  return result
sum_of_numbers = add_numbers(3, 5) #sum_of_numbers now holds 8
print(sum_of_numbers) #Prints: 8
```
Here, add_numbers(3, 5) returns the value 8. without the return statement, the function would perform its calculation but wouldn't give us back a usable result. 

#### Multiple Parameters
A function can have multiple parameters: 
```python
def multiply(a, b, c):
  return a * b * c
product = multiply(2, 3, 4) #The product is now 24
```

## Arbitary Arguments 
Arbitary arguments in Python refer to a way of defining functions that can accept a variable number of arguments, rather than a fixed count. this is often useful when you're not sure in advance how many arguments will be passed to a function. 

There are two main types of arbitary arguments: 

**1. Arbitrary Positional Arguments (*args)**
using *args in a function definition allows you to pass any number of positional arguments to that functions. inside the function, args is treated like a tuple containing all the extra positional arguments. 

```python
def print_numbers(*args):
  for number in args:
    print(number)
print_numbers(1, 2, 3) #prints 1, 2, 3
print_numbers(10) #prints 10
print_numbers() # prints nothing (but doesn't error)
```
in this example, print_numbers can handle 0, 1, or many positional arguments. 

**2. Arbitary Keyword Arguments** 
Using **kwargs lets your function accept any number of keyword arguments. inside the function, kwargs is treated like a dictionary, where each key-value pair correspons to a passed keyword argument and its value. 

```python
def print_info(**kwargs):
  for key, value in kwargs.items():
    print(f"{key}: {value}")
print_info(name="Alice", age=30, city="New York")
```

#### Why Use Arbitrary Arguments? 
- **Flexibility:** your function can handle a wide range of inputs
- **Convenience:** Sometimes you don't know how many arguments you'll need up front.
- **Forwarding Arguments:** They're useful when building wrapper functions or decorators that accept arguments and pass them on to other functions.

##### Important Notes: 
You can combine regular parameters with *args and **kwargs in a function definition, but *args must come after regular positional parameters, and **kwargs must come last. 
```python
def mixed_function(required, *args, **kwargs):
  print("Required:", required)
  print("Args:", args)
  print("Kwargs:", kwargs)
mixed function(42,1,2,3, name="Alice",age=30)
```

*args and **kwargs in the function definition means "Take all extra positional arguments that wheren't explicitly declared and put them into a tuple called args" 
```python
def print_all(*args):
  for arg in args:
    print(arg)
print_all(1,2,3)
print_all("apple", "banana") 
```

#### Key points: 
- args is a tuple
- you don't have to name it args; any valid identifier works, but args is the conventional choice.
- if you define other positional parameters, they must come before *args

#### Combine with regular arguments: 
```python
def describe_person(name, *hobbies):
  print("Name:", name)
  print("Hobbies:", hobbies)
describe_person("Alice", "reading", "gardening")
```

## **Kwargs 
#### Definition_ 
using **kwargs in the function definition means "take all extra keyword arguments that weren't explicitly declared and put them into a dictionary called kwargs". 
```python
def print_date(**kwargs):
  for key, value in kwargs.items():
    print(f"{key}:{value}")
print_data(name="Alice", age=30, city="New York")
```

#### Key Points: 
- kwargs is a dictionary
- The key are the argument names, and the values are the argument values you passed in.
- kwargs is useful when you want to allow for optional or flexible keyword-based inputs
- like *args, the name doesn't have to be kwargs, but it's the standard convention.
```python
def describe_product(name, price, **extras):
  print("product Name:", name)
  print("price:" price)
  print("Extras:", extras)
describe_product("Laptop", 999.99, color="silver", warranty="2 Years"
```

#### Using both *args and *kwargs
it's possible to use both in the same function definition, but the order in the function signature matters: 
- positional parameters (if any) first
- *args second
- **kwargs last

```python
def process_order(order_id, *items, **details):
  print("Order ID:" order_id)
  print("Items:", items)
  print("Details:", details)
process_order(1001, "apple", "banana", "cherry", status="pending", priority="high")
```

#### When yo use *args and **kwargs?
- **Flexibility:** if you don't know the exact number of arguments your function will receive
- **Wrapper Functions:** When writing decorators or wrapper functions, you can pass through any arguments .
- **Extendability:** Function can evolve over time without breaking existing calls. Adding new parameters without affecting existing code is easier with **kwargs

## Lambda Functions
Lambda functions in python are small, anonymous functions defined without a name. They are often referred to as anonymous functions because they're not declared in the standard manner by using the def keyword. instead, they use the lambda keyword. lambda functions are typically used for short, simple tasks, and are most helpful when you need a small function for a brief time, often as an argument to higher-order functions like map(), filter(), or sorted(). 

#### Syntax of a Lambda Functions 
The basix syntax of a lmbda function is: 
```python
lambda arguments: expression 
```
- **arguments:** The inputs to the function. you can have zero, one, or multiple arguments, separated by commas
- **expressions:** A single expression that the lambda function evaluates and returns. Lambda functions are limited to a single expression, which means you can't write multi-line logic directly inside them.

```python
add_ten = lambda x: x + 10
print(add_ten(5)) #Outputs 15
```
```python
average = lambda x: sum(x)/len(x)
print(average([3,6,9]))
Resulting: 6.0
```
#### Characteristics of Lambda Functions: 
1. Anonymous: They don't require a name (although you can assin them to a variable)
2. Single expression: They're meant for concise operations. complex logic that spans multiple lines is usually better served by a regular function defined with def.
3. useful inline: lambda functions are commonly used inline with bult-in functions that expect a function as an argument.

#### Common use cases 
- **With** map() and filter()=:
```python
#map: apply a function to every element in a list.
numbers = [1, 2, 3, 4]
squared = list(map(lambda x: x**2, numbers))
print(squared) #1,4,9,16

evens = list(filter(lambda x: x%2 ==0, numbers))
print(evens) #[2,4]
```
- **With** sorted() for custom sorting:
```python
people [("Alice", 30), ("Bob", 25), ("Charlie", 35)]
#Sort by age using a lambda as key
sorted_people = sorted(people, key=lambda person: person[1])
print(sorted_people) 
```

#### Using Lambda with Map () 
the map() function applies a given function to each item in an iterable (like list or tuple) and returns a map object (which can be converted into a list) a Lambda is perfect when the transformation you want to apply is simple 

## Error handling 
Error handling in python allows you to anticipate, detect, and gracefully respond to situations where something goes wrong in your code's execution. Rather than letting the program crash or produce incorrect results without explanation, proper error handling ensures your code can recover, inform the user, or take corrective actions. 

#### Exceptions and the try-except Block
When python encounters an error that it cannot handle, it raises an exception. an exception is a spceial kind of error object that interrupts the normal flow of the program. common examples includes: 
- **ValueError:** Raised when a function receives an argument of the correct type but an inapporpriate value
- **TypeValue:** Raised when an operation is applied to an object of an inappropriate type
- **ZeroDivisionError:** Raised when attempting to devide by zero
- **FileNotFoundError:** Raised when trying to open a file that doesn't exists.

you can handle these exceptions usin a try-except block. the basic structure is: 

```python
try:
  #code that might raise an exception
  result = 10 / 0
except ZeroDivisionError:
  #code that runs if the specified exeption occurs.
  print("You Tried to devide by zero") 
```

##### How it works: 
1. Python executes the code in the try block
2. if no exeception occurs, the exept block is skipped
3. if an exception of the type listed in except occurs, the code in the try block stops at the point of the error, and execution jumpos to the except block
4. if the exception doesn't match the except type, python looks for another except block that matches or, if none is found, the exception is unhandled and the program may terminate with an error message.

#### Catching multiple exceptions: 
```python
try:
  number = int(input("Enter a number: "))
  result = 10 / number
except ValueError:
  print("that's not a valid integer!")
except ZeroDivisionError:
  print("You cant divide by Zero!")
```

## The importance of flat files: 
in data science, flat files(such as CSV, TSV, and other text-based formats) are cucial because they provide a simple, portable, and language-agnostic way to store and exchange data, they're essentially structured text files without any hierarchical or relational schema embedded within them, making them highly accessible and easy to work with for a wide variety of data-processing tasks. 

here are several reasons why flat files are important: 

1. Simplicity and Accessibility:
Flat files store data as plain text, this simple format makes them straight forward to create, read, and modify. anyone can open a CSV in a basic text editor or spreadsheet application. this ease of access makes them an ideal starting point for beginners and a concenient fallback for experienced data scientists.

2. Broad Compability:
Becaus flat files are language and platform agnostic, they can be easily used accross different tools, systems, and programming languages, whether you're using Python, R, SQL, or even legacy tools, chances are you can work seamlessly with a CSV or TSV file. This universality streamlines collaboration among team members who may use different tools or programming languages.

3. Portability and sharing:
Transferring a large database or proprietary data can be challenging, but sharing a flat file is as easy as sending an email. or uploading it to a shared driver. flat files are often the format of choice when exchanging data between organizations, departments, or teams.

4. Data ingestion and preprocessing:
Many data processing pipelines start by loading data from a flat file. Tools like pandas in Python provide straightforward methods (e.g.,read_csv()) to load flat files and quickly get started on data cleaning, transformation and analysis. Flat files serve as a neutral intermediary format, allowing data scientists to quickly plug the data into their workflow.

5. Archiving and version control:
Since they're human-readable, flat files can be stored and version-controlled with systems like Git. This makes it easier to track changes over time, roll back to previous versions, and understand the historical modifications to a dataset, all while keeping it in a diff-friendly format.

6. integration with Big Data Tools:
While more complex or large-scale tasks might require databases or distrubuted systems (like Hadoop or Spark), these systems often support flat files as an ingestion format. Converting data into CSV or JSON is frequently the first step before loading it into more specialized data engines. 


## Pickled files in Pythons 
Pickled files in Python are a way to serialize and save Python objects to a file, which can later be deserialied and loaded back into memory. this process is handled by Python's **pickle** module, which provides a means to convert Python objects into a byte strema and vice versa. 
Here's a detailed explenation: 

#### What is Pickling:
** - Pickling:** The process of converting a Python object into a byte stream.
** - Unpickling:** The process of converting the byte stream back into the original Python object. 

Pickling is useful for saving data structures (e.g., dictonarie, lists, custom objects) to a file for future use or for sending Python object over a network: 

#### Common Use Cases 
1. Saving data for later use:
   - Store machine learning models
   - Sace intermediate data in workflows.

2. Sharing objects:
   - Exchange Python objects between processes.

3. Checkpointing:
   - Sace the state of program to resume later.
  
#### How to use the pickle module: 
##### Pickling (Sacing an object)
```python
Import pickle
data = {'name': 'Alice', 'age':30, 'job': Data Scientist'}

#Save to a file:
with open('data.pkl', 'wb') as f:
    pickle.dump(data, f)
#wb mode = write binary, as pickled data is stored in binary format:

```
##### Unpickling (loading an object)
```python
#load from a file
with open('data.pkl','rb') as f:
    loaded_data = pickle.load(f)
print(loaded_data)
```

#### Limitations: 
1. Python-specific:
   - Pickled files are only compatible with python and not portable accross other programming languages:

2. security risk:
   - unpickling data from an untrusted source is risky as it may execute arbitrary code.

3. Version Compatibility:
   - Pickled files may not work seamlessly across different Python Versions

#### Alternatives: 
1. JSON:
   - More human-readable and language-independent.
   - Limited to serializing basic data types (no support for complex Python object like classes)

2. Joblib:
   - Optimized for storing large numerical arrays, such as models in scikit-learn

3. HDF5 / Feather / Parquet:
   - Better for large datasets, especially in data science applications.

## HDF5 - Hiearchical Data Format Version 5 
HDF5 is a versatile file format for storing large amounts of data. it is wiedly used in scientific computing, data analysis, and machine learning for its ability to store complex data hierarchcally and efficiently. Python provides excellent support for working with HDF5 files through libraries like h5py and pandas. 

### What is an HDF5 File? 
**- Hierarchical Structure:** Similar to a file system, HDF5 organizes data into groups (like directories) and datasets (like files) 
**- Efficient:** Optimized for large datasets, allowing fast reading/writing and compression
**- Portable:** Platform-independents format.
**- Scalabale:** Handles small and extremely large datasets alike. 

### Use Cases

1. Data Storage: Store large numerical datasets efficiently (e.g., images, arrays, or tabular data).
2. Machine learning: Save and load model weights or datasets.
3. Scientific computing: Store experimeental or simulation data.

#### Key components: 
1. Groups:
   - Like directories in a file system
   - can contain datasets or other groups
   - Root group / is the starting point

2. Datasets:
   - Multi-dimensional arrays of data
   - Analogous to files in a directory
  
3. Attributes:
   - metadata associated with groups or datasets (like file metadata).

### Working with HDF5 in Python: 

```python
Import h5py
Import numpy np

#create an HDF5 file:
with h5py.File('ecample.h5', 'w') as hdf:
    #create a group
    group = hdf.create_group('group1')

    #Create a dataset
   data=np.arrange(10)
    group.create_dataset('dataset1', data=data)

    #add an attribute
    group.attrs['description'] = 'This is a test group'

#Read an HDF5 file
with h5py.File('example.g5', 'r') as hdf:
  print(list(hdf.keys())) #output: ['group1]
  group =hdf['group1']
  print(list(group.keys())) #output: ['dataset1']
  print(group['dataset1'][:]) #output: [0 1 2 3 4 5]
  print(group.attrs['description]) # output: This is a test group
```

### Using pandas
```python
import pandas as pd

#save a DataFrame to an HDF5 file
df = pd.DataFrame({'A': range(5), 'B': range (5,10)})
df.to_hdf('data.h5', key='dataframe', mode='w'

#read the data frame back
df_loaded = pd.read_hdf('data.h5' key='dataframe')
print(df_loaded)
```

### Features of HDF5 
1. Compression:
   - Support data compression to save storage space
   - example: use compression='gzip' when creating dataset
2. Partial i/o:
   - Load subsets of data without reading the entire file (important for large datasets)
5. Extensibility:
   - Datasets can be resized dynamically if needed

### Advantages 
- **Performance:** Optimized for both storage and compution.
- **Hierarchical Structure:** Makes data organization intuitive
- **Compatibility:** works seamlessly accross multiple platforms and programming languages

### Limitations
1. **Complecity:** Steeper learning curve compared to simpler formats like CSV
2. **Overkill for Smal Datasets:** Best suited for large or complex datasets
3. **Binary Format:** Not human-readable like CSV or JSON


## Creating a database engine in Python
Creating a database engine in Python can be achieved by using the SQLAlchemy library, which is a powerful and flexible SQL toolkit and object-relationalMapping (ORM) library. A database engine is essentially a connection interface to a database that allows tou to perform SQL operations programmatically. 

Here's a step-by-step guide to creating a working with a database engine in python: 

#### importing required modules
```python
#pip3 install sqlalchemy

from sqlalchemy import create_engine, MetaData, Table, Column, Integer, String
```

#### Create a database engine
```python
#example: SQLite
engine = create_engine('sqlite:///example.db')

#For other databases (postgreSQL, MySQL, etc) use the appropriate connection string
# PostgreSQL: Create_enginge('posgresql://user:password@localhost/dbname')
# MySQL: create_engine('mysql+pymysql://user:password@localhost/dbname')
```

#### Define Schema 
```python
from sqlalchemy import Table, Column, Integer, String, MetaData

metadata = MetaData()

#define a table
users = Table(
'users, metadata,
Column('id', integer, primary_key=True),
column('name', String)
column('age', Integer)
)
```

#### Create Tables 
```python
metadata.create_all(enginge) #this creates all tables defined in the metadata object
```
#### Insert Data into the Database 
```python
with enginge.connect() as conn:
  #insert a row
  conn.execute(users.insert().values(name='Alice' age=30))
  conn.execute(users.insert().values(name='Bob', age=25))
```

#### Query data 
```python
with enginge.connect() as conn:
#query data
result = conn.execute(users.select())
for row in result:
  print(row) #output: (1, 'Alice', 30),(2, 'Bob', 25)
```

#### update or delete Data 

```python
#Update
with engine.connect() as conn:
  conn.execute(users.update().where(users.c.name=='Alice').values(age=31))

#Delete:
with engine.connect() as conn:
  conn.execute(users.delete().where(users.c.name== 'Bob'))
```

## Querying relational databases in python 

```python
from sqlalchemy import create_engine
import pandas as pd
engine = create_engine('sqlite:///Northwind.sqlite')
con = encinge.connect()
rs = con.execute('SELECT * FROM Orders')

con.close()
```
Using SQLAlchemy and Pandas togheter allows you to leverage SQLAlchemy's powerful database connection and query capabilities while benefiting from from Pandas data manipulation and analysis features. here's how you can integrate the two effecitevly:

### Overview: 
1. use SQLAlchemy to connect to a database and execute queries
2. Use Pandas to read data from the database and manupulate it
3. Optionally, use Pandas to write DataFrames back to the database:

#### Setting up SQLAlchemy 
```python
from sqlalchemy import create_eninge

#SQLite example
engine = create_engine('sqlite:///example.db')

```

#### Reading Data into Pandas 
You can execute SQL queries using Pandas and load the result directly into a DataFrame 

```python
import pandas as pd
"read data using a raw SQL query
query = 'SELECT * FROM users'
df = pd.read_sql(query, con=engine)
print(df)
```

#### Write Data from Pandas to Database 
You can also write Pandas DataFrame directly into a datbase table. 
```python
data = {'name':['Alice', 'Bob'], 'age':[30,25]}
df = pd.DataFrame(data)

#Write to the database (if the tbale exists, replace it)
df.to_sql('users', con=engine, if_exists='replace', index=False)

# Options for `if_exists`:
# - 'fail': Raise an error if the table exists.
# - 'replace': Drop the table if it exists and create a new one.
# - 'append': Add new rows to the existing table. 
```

#### Updating Data with Pandas 
To update specific rows, fetch the data into a DataFrame, modify it, and write it back 
```python
df = pd.read_sql('SELECT * FROM users', con=engine)

#modify the dataframe
df.loc[df['name'] == 'Alice' , 'age'] = 31

#write the updated DataFrame back to the database
df.to_sql('users', con=engine, if_exists='replace',index=False)
```

#### A Complete Workflow example: 
```python
from sqlalchemy import create_engine, MetaData, Table, Column, Integer, String
import pandas as pd

# Connect to SQLite
engine = create_engine('sqlite:///example.db')

# Define a new table
metadata = MetaData()
users = Table(
    'users', metadata,
    Column('id', Integer, primary_key=True),
    Column('name', String),
    Column('age', Integer)
)

# Create the table
metadata.create_all(engine)

# Insert initial data
data = pd.DataFrame({'name': ['Alice', 'Bob', 'Charlie'], 'age': [30, 25, 35]})
data.to_sql('users', con=engine, if_exists='replace', index=False)

# Query and load into Pandas
df = pd.read_sql('SELECT * FROM users', con=engine)
print("Original Data:")
print(df)

# Update data in Pandas
df.loc[df['name'] == 'Alice', 'age'] = 31

# Write the updated data back
df.to_sql('users', con=engine, if_exists='replace', index=False)

# Verify the update
df = pd.read_sql('SELECT * FROM users', con=engine)
print("\nUpdated Data:")
print(df)
```

## Connect to an API - HTTP requests to import files from the web

- HTTP = HyperTextTransferProtocol
- HTTPS - More secure form of HTTP
- Goint to a website = sending HTTP requests
    - GET request
- **urlretrieve()* perfroms a GET request

```python
from urllib.request import urlopen, Request
url = 'https://www.wikipedia.org/'
request = Reguest(url)
response = urlopen(request)
html = response.read()
respones.close()
```

GET Requests using requests 
```python
import requests
url = 'https://www.wikipedia.org/'
r = requests.get(url)
text = r.text
```

## Scraping the web in Python 
web scraping in Python involves extracting data from websites by fetching their HTML content and parsing it to extract relevant information. here's an overview of how it works and a guide to get started. 

### How Web Scraping Works 
1. Fetch web content
   - Use HTTP requests to get the HTML content of a webpage
2. Parse the HTML:
   - Analyze the structure of the webpage (HTML tags) to find the data you need.
3. Extract data:
   - Using paring libraries to extraxt specific elements (e.g., text, images, links) from the HTML
4. Store data:
   - Save the extracted data in a desired format (CSV, database, etc) for further analysis.

### Libraries for Web Scraping in python 
- **requests:** for making HTTP requests to fetch webpage content.
- **BeautifulSoup:** for paring and extracting HTML/XML data.
- **Selenium:** for scraping dynamic pages requiring JavaScript rendering
- **Scrapy:** a robust web scraping framework for large-scale projects.

#### An basic webscraping example
```python
import requests
from bs4 import BeautifulSoup
# URL of the webpage to scrape
url = 'https://wikipedia.org/'

#Fetch the webpage content
response = Requests(url)

#Check if the request was successful
if response.status_code == 200:

  #parse the HTML content
  soup = BeautifulSoup(response.text, 'html.parser')

  #Extracting article titles (assume titles are in <h2>
  titles = soup.find_all('h2')

  #print the titles
  for title in titles:
    print(title.text.strip())
else:
  print(f'Failed to fetch the page. Statuscode: {response.status_code}')
  
```


#### Storing scraped data 

```python
#Save to CSV
import csv
data = [["Title 1", "Description 1",], ["Title 2", "Description 2"]]

#write data to a CSV file
with open ('data.csv', 'w', newline = '') as file:
  writer = csv.writer(file)
  writer.writerow(["Title", "Description"]) #Header row
  writer.writerrows(data)

# Save to Panads DataFrame:
import pandas as pd
#convert list of dictionaries to a DataFrame
df = pd.DataFrame(data, columns=["Title", "Description"]
df.to_csv("data.csv", index=False) 
```

## APIs and JSONs
#### API: 
- API = Application Programming Interface
- Protocols and routines
  - Building and interacting with software applications
Is a set of rules and protocols that allow different software systems to communicate with each other. it acts as a bridge between applications, enabling them to share data and functionality.

##### Key Features of an API: 
- **Request and Response:** APIs work by sending requests (e.g., GET, post) and receiving responses, often in a structured format like JSON.
- **Endpoint:** a specific URL where the API can be accessed
- **HTTP Methods:**
    - GET: Retrieve data.
    - POST: send data
    - PUT: Update data
    - DELETE: remove data


#### JSON
- JavaScript Object Notation
- Real-Time server-to-browser communication

is a lightweigted data-interchange format that's easy for humans to read and write, and easy for machines to parse and generate. it is the most common format for exchanging data with APIs 

##### Loading JSONs in python 
```python
import json
with open("snakes.json", "r") as json_file:
  json_data=json.load(json_file)

# for exploring:
for key, value in json_data.items():
  print(key + ":", value) 
```

##### API Example: Step by step: 
```python
import requests

#define the API endpoint
URL = "https://wikipedia.org/"

#Make a GET request to the API
response = request.get(url)

#Chek the response status
if response.status_code == 200:
  print("API Request successful!")
  #parse JSON data
  data = response.json()
  print(data[:5]) #print the first 5 items
else:
  print(f"API request failed with status code: {response.status_code}")

``` 

```python
[
  {"userId": 1, "id": 1, "title": "Post 1", "body": "This is the first post"},
  {"userId": 1, "id": 2, "title": "Post 2", "body": "This is the second post"}
]
```

```python
# Extract specific data from the JSON
for post in data[:5]:  # Loop through the first 5 posts
    print(f"Title: {post['title']}")
    print(f"Body: {post['body']}\n")

```

#### Real-World API and JSON use Cases 
1. Weather Data - Fetch currenct weather using APIs like OpenWeatherMap
2. Finanfical Data - Use APIs like Alpha Vantage or Yahoo Finance to get stock prices
3. Social Media - Use APIS from twitter or instagram to analyze trends
4. News Aggregation - Fetch News headlines from APIs like NewsAPI

#### Best Practices for APIs and JSON 
1. API Keys - many APIs require authentication using an API key. Keep it secure.
2. Rate Limits - Respect the API's rate limit to avoid getting blocked
3. Error Handling - Always check the response status code and handle errors gracefully
4. Documentation - Read the API documentation carefully to understand its endpoints, parameters, and response format. 
