
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

'''
This is a print function
'''

hello_world("Dora")
x = hello_world
x("Scott")

def greetings(func, name):
    func(name)

greetings(hello_world, "Emily")
```
