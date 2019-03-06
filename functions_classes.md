
# Function Definitions
At the core of modern programming are functions. In python, functions have:
a signature which includes:
	a unique function name
	a parameter list(can be empty)
a body
a return statement (can be none)

Functions in Python are First Class Objects, which means they can be passed and assigned as variables. This can be useful if we have similar logic for a set of circumstances that only differs in a function call-- simply pass in the desired function as a parameter and call it by its parameter name

(Note that we assign a function to a variable by leaving off the parenthesis that denotes the input parameters; if we keep them on, we instead assign the output of the function to the variable. We'll explore this more at the end)



```python
def hello_world(name):
    print("hello world! My name is {}".format(name))
    
hello_world("Dora")
x = hello_world
x("Scott")

def greetings(func, name):
    func(name)

greetings(hello_world, "Emily")
```

Function parameters in Python are PASS BY REFERENCE

This means that if you reassign what a parameter is, it will not stay past the function call.

However, if you change the underlying object it was referring to (say, appending to a list, or adding to a dict) then that will stay past the function call.

Rule of thumb: You can re-assign a paramet using a '=' pretty safely (this just updates the reference)
Calling a class function of a parameter could result in it changing (like list.append)


```python
def reassignment(some_int_param):
    some_int_param = 1
    print("Inside the function, the param is: {}".format(some_int_param))
    
x = 0
reassignment(x)
print("after the function, the param is: {}".format(x))
```


```python
def changing_the_reference_obj(some_list):
    some_list.append([4,5,6])
    print("Inside the function, the param is: {}".format(some_list))    

x = [1,2,3]
changing_the_reference_obj(x)
print("after the function, the param is: {}".format(x))
```


```python
def required(x):
    print("the variable x is required and has a value of: {}".format(x))
required(1)
#note that this is an example of 'duck typing'
required("foo")
required()
```


```python
def defaults(x, y=2):
    print("x is {} and y is {}".format(x,y))
defaults(1)
defaults(1,y="foo")
defaults(1,2)
```


```python
def var_sum(*args):
    sum = 0
    for arg in args:
        sum += arg
    print("sum is: {}".format(sum))
    return sum

sum = var_sum(1,2,3,4,5)

```


```python
def var_sum(*args, **kwargs):
    sum = 0
    for arg in args:
        sum += arg
        if 'verbose' in kwargs and kwargs['verbose'] is True:
            print("running sum is: {}".format(sum))
    print("sum is: {}".format(sum))
    return sum

sum = var_sum(1,2,3,4,5)
sum = var_sum(1,2,3,4,5, verbose=True)
sum = var_sum(1,2,3,4,5, unexpected_param=True) #Note that this does not throw an error-- we just don't do anything with it within the fn
```

## Type Hints: Available in Python 3.5+

These provide 'hints' about what the expected object type is for any given parameter in a function's parameter list


```python
from typing import List

def greeting(names: List[str]) -> str:
    '''
    greeting()
    names: A List of strings
    
    returns: a single string representing a concatenated greeting to names
    '''
    return 'Hello, {}'.format(', '.join(names))
 
greeting(['jane', 'john', 'judy'])
```

This does NOT stop someone from passing bad parameters, but can give someone who implements a function a better idea of what to expect!


```python
greeting("Rebel who plays by their own rules!")
```

# Class Anatomy
At the core of OO programming is the conceit of classes. A class is essentially a collection of variables and functions from which many unique class instantiations can be made. 



## Classes and Class Functions


```python
class MyClass():
    def hello_world(self):
        print("Hello World!")
```

## Class Instantiation and Invocation


```python
my_class = MyClass()
my_class.hello_world()
```


```python
MyClass().hello_world()
```


```python
MyClass.hello_world()

```





## The __init__ class function and 'self'


```python
class my_class():
    def __init__(self):
        self.x = [1,2,3]
        self.y = ["a", "b", "c"]
    
    def print_vars(self):
        print("x: {}\n y: {}".format(self.x, self.y))
        

```


```python
first_class = my_class()
print("default variables:")
first_class.print_vars()

first_class.x = 55
first_class.y = "direct variable interaction is icky"
print("variables after direct manipulation:")
first_class.print_vars()

first_class = my_class()
print("variables after reassigning to a new instance of my_class():")
first_class.print_vars()
```

## Some more special underscore functions

__str__() is a special class function that specifies how the class should be displayed when treated as a string (eg: when it is printed)


```python
class my_bland_class():
    def __init__(self):
        self.x = [1,2,3]
        self.y = ["a", "b", "c"]
    
    def print_vars(self):
        print(self)
        

```


```python
first_class = my_bland_class()
print(first_class)
print("----------")
first_class.print_vars()
```


```python
class my_fancy_class():
    def __init__(self):
        self.x = [1,2,3]
        self.y = ["a", "b", "c"]
        
    def __str__(self):
        return "my class\n x: {}\n y:{}".format(self.x, self.y)
    
    def print_vars(self):
        print(self)
        

```


```python
first_class = my_fancy_class()
print(first_class)
print("----------")
first_class.print_vars()

```

## Python uses Duck Typing: If it looks like a duck, and acts like a duck...
    


```python
class Bird:
    def fly(self):
        print("It's a bird!")
        
class Plane:
    def fly(self):
        print("It's a plane!")

class Batman:
    def nanana(self):
        print("Batman!")

def what_is_it(it):
    return it.fly()

bird = Bird()
plane = Plane()
batman = Batman()

what_is_it(bird)
what_is_it(plane)
what_is_it(batman)
```

## Private Functions in Python

These can not* be directly called from outside of the class that encapsulates it!
This allows the creator to control how a user of a class interacts with it.

Commonly, this is used to differentiate between what is *outwardly* useful: functions that perform end-to-end tasks and return meaningful output
and functions that are only *internally* useful: helper functions that reduce code duplication, or check whether certain conditions hold, etc.


```python
class Greeter:
    
    def __private_greeting(self, names: list) -> str:
        return 'Hello, {}'.format(', '.join(names))

    def greet(self, names: list) -> str:
        print(self.__private_greeting(names))
    
greeter = Greeter()
greeter.greet(["Huey", "Dewey", "Louie"])
greeter.__private_greeting(["Huey", "Dewey", "Louie"])
```


```python
greeter = Greeter()
print(dir(greeter)) #check the valid function names for the object
greeter._Greeter__private_greeting(["how did you do that???"])
```


## Lambda Functions

lambdas are anonymous (no formal 'def' statement) functions that allow for a quick function to be declared and called in place.



```python
def squared_fn(x):
    # x**2 is the notation for x^2
    return x*x
new_list = []
our_list = [1,2,3]
for i in our_list:
    new_list.append(squared_fn(i))
print(new_list)

#functions are assignable
squared = lambda x: x**2
print([squared(x) for x in our_list])

#lambdas can be declared and invoked in place!
print(list(map(lambda x: x**3, our_list)))


```


```python
def run_it(x, fn):
    return fn(x)

cats = 2
dogs = lambda x:x**4
mapped_lambda = lambda x: map(lambda y: 2**y, range(x))
run_it(5, lambda x: [print(i) for i in range(x)])

print(list(run_it(5, mapped_lambda)))
```


```python
ns = list((lambda x: map(lambda y: y**y, range(x)))(3))
print(ns)
```
