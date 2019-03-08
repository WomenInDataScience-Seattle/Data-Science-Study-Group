Untitled
================

``` python
def hello_world(name):
    print("hello world! My name is {}".format(name))
    
hello_world("Dora")
```

    ## hello world! My name is Dora

``` python
x = hello_world
x("Scott")
```

    ## hello world! My name is Scott

``` python
def greetings(func, name):
    func(name)

greetings(hello_world, "Emily")
```

    ## hello world! My name is Emily
