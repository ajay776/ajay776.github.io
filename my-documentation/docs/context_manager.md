# Context Manager:

A context manager in Python is an object that is used to set up and tear down resources, such as opening and closing files, acquiring and releasing locks, or connecting and disconnecting from a network. It helps manage resources efficiently by ensuring that they are properly initialized and cleaned up.

## 3.1 Context Manager with with Statement:

Key Concepts:

### 3.1.1 Entering the Context:

When you use the `with` statement, it calls the `__enter__` method of the context manager. This method sets up the necessary resources and returns an object that represents the context.

### 3.1.2 Executing Code:

The indented block of code under the `with` statement is then executed. This is the part where you work with the acquired resources.

### 3.1.3 Exiting the Context:

After the code block completes (either normally or due to an exception), the `__exit__` method of the context manager is called. This method ensures that any necessary cleanup or resource release is performed.

Example:

Let's take the example of opening and working with a file:

```python
# Without using a context manager
file = open("example.txt", "r")
content = file.read()
print(content)
file.close()  # Need to remember to close the file explicitly

# Using a context manager (with statement)
with open("example.txt", "r") as file:
    content = file.read()
    print(content)

# No need to explicitly close the file; it's taken care of by the context manager


```

In the second example, the `with` statement ensures that the file is properly opened and closed. If an error occurs during the code block, the `__exit__` method is still called to handle any cleanup.
