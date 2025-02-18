---
layout: post
title: "Python Enhancers - Iterators, Generators and Decorators"
date: 2025-02-17
categories: Core Python
author: "Hardik Jaiswal"
tags: [Python, Programming]
---

![img](/assets/img/blog_img/python-enhancers.png)

So I started out with [Krish Naik's course](https://www.udemy.com/course/complete-machine-learning-nlp-bootcamp-mlops-deployment/?couponCode=24T4MT180225) on **_Complete Data Science,Machine Learning,DL,NLP Bootcamp_**, where I started revising programming funcdamentals form the very basics. At first everything seemed easy - variables, datatypes, loops, conditions: everything felt the same way, untill I encountered some python enhancers - _Iterators, Generators and Decorators_. 

In short these python enhancers are built to provide us with some efficient ways of handling different tasks in memory, without exhausting it all. 

### Iterators: The Backbone of Iteration  

An **iterator** is an object that implements the `__iter__()` and `__next__()` methods. It allows us to iterate over a sequence (like lists, tuples, etc.) one element at a time. Unlike lists, which store all elements in memory, iterators generate elements on demand, making them memory efficient.  

#### Example of an Iterator  

```python
class MyIterator:
    def __init__(self, n):
        self.n = n
        self.current = 0

    def __iter__(self):
        return self

    def __next__(self):
        if self.current < self.n:
            val = self.current
            self.current += 1
            return val
        else:
            raise StopIteration

it = MyIterator(5)
for num in it:
    print(num)
```

This prints:  

```
0  
1  
2  
3  
4  
```

### Generators: Iterators Made Easy  

While iterators require defining `__iter__()` and `__next__()`, Python provides a more elegant way to create iterators: **Generators**.  

A generator is simply a function that uses `yield` instead of `return`. Each time `yield` is encountered, the function saves its state and resumes from there the next time it is called.  

#### Example of a Generator  

```python
def my_generator(n):
    for i in range(n):
        yield i

gen = my_generator(5)
for num in gen:
    print(num)
```

This produces the same output as the iterator example but with much less code.  

**Why use Generators?**  
✅ _Memory Efficient_ – No need to store all values in memory.  
✅ _Lazy Evaluation_ – Values are generated on demand.  

### Decorators: Functions that Modify Functions  

A **decorator** is a higher-order function that takes another function as an argument and enhances or modifies its behavior without changing its actual code.  

Think of it as a **wrapper** around a function.  

#### Example of a Decorator  

```python
def my_decorator(func):
    def wrapper():
        print("Before function call")
        func()
        print("After function call")
    return wrapper

@my_decorator
def say_hello():
    print("Hello, World!")

say_hello()
```

**Output:**  
```
Before function call  
Hello, World!  
After function call  
```

The `@my_decorator` syntax is just a shortcut for writing:  

```python
say_hello = my_decorator(say_hello)
```


### When to Use Each?  

- **Iterators** → When you need a custom sequence that can be iterated over without holding all values in memory.  
- **Generators** → When you need a quick and efficient way to generate sequences lazily.  
- **Decorators** → When you want to modify function behavior dynamically (e.g., logging, timing functions, authentication).  

These Python enhancers make the language more **powerful, flexible, and memory-efficient**. They might feel tricky at first, but once you get the hang of them, you'll see how they simplify code and optimize performance. 🚀  

What are your thoughts on these enhancers? Have you used them in your projects? _Tune in the next time where I start discovering Eexploratory Data Analysis_.