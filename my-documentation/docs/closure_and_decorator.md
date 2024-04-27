# Closures and Decorators.

Let's delve deeper into memory management and performance optimization in Python.

## 2.1 Closures:

Key Concepts:

### 2.1.1 Function Inside a Function:

Closures involve having a function inside another function. The inner function is the closure.

### 2.1.2 Access to Outer Function's Variables:

The inner function has access to the variables of the outer (enclosing) function, even after the outer function has completed execution.

### 2.1.3 Preservation of State:

Closures allow functions to "remember" the values of variables in the outer function's scope.

Example:

```python
def outer_function(x):
    def inner_function(y):
        return x + y
    return inner_function

closure_example = outer_function(10)
result = closure_example(5)  # Output: 15

```

Here, `inner_function` is a closure that remembers the value of x from the `outer_function`.

## 2.2 Decorators:

A decorator is a higher-order function that takes a function and extends or modifies its behavior. It allows you to wrap another function, adding some functionality before or after the original function
Key Concepts:

### 2.2.1 Functions as First-Class Citizens:

In Python, functions are first-class citizens, meaning they can be passed as arguments to other functions.

### 2.2.2 Wrapper Functions:

Decorators use wrapper functions to modify the behavior of the original function.

### 2.2.3 Syntactic Sugar:

Python provides a convenient syntax using the `@decorator` syntax to apply decorators to functions.

Example:

```python
def my_decorator(func):
    def wrapper():
        print("Something is happening before the function is called.")
        func()
        print("Something is happening after the function is called.")
    return wrapper

@my_decorator
def say_hello():
    print("Hello!")

say_hello()

```

Output:

```shell
Something is happening before the function is called.
Hello!
Something is happening after the function is called.

```

In this example, `my_decorator` is a decorator that wraps the `say_hello` function, adding behavior before and after its execution.

## 2.3 Combining Closures and Decorators:

You can combine closures and decorators for more flexible and reusable code. Closures can be used within decorators to capture and maintain additional state.

Example:

```python
def multiplier(factor):
    def decorator(func):
        def wrapper(*args, **kwargs):
            result = func(*args, **kwargs)
            return result * factor
        return wrapper
    return decorator

@multiplier(2)
def square(x):
    return x * x

@multiplier(3)
def cube(x):
    return x * x * x

print(square(4))  # Output: 32
print(cube(3))    # Output: 27

```

Here, `multiplier` is a closure-based decorator. It takes a `factor` as an argument and returns a decorator. The returned decorator (`wrapper`) multiplies the result of the original function by the specified factor. Applying `@multiplier(2)` and `@multiplier(3)` to `square` and `cube` functions demonstrates the flexibility of closures and decorators in creating reusable and adaptable code.
