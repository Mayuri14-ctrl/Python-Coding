# Python-Coding

### Count the Occurrences of Each Element in a List
```from collections import Counter

def count_occurrences(lst):
    return dict(Counter(lst))

print(count_occurrences([1, 2, 2, 3, 3, 3, 4]))  
# Output: {1: 1, 2: 2, 3: 3, 4: 1}
```
without Counter
```
def count_occurrences(lst):
  count={}
  for num in lst:
    count[num]=count.get(num,0)+1
    return count
```

### Regex to find all emails
```
import re
re.findall(r'[a-zA-Z0-9._%+-]+@[a-zA-Z0-9,-]+\.[a-zA-Z]{2,}',text)
```
```
[a-zA-Z0-9._%+-]+   → Matches the local part (before @) with letters, numbers, dots, underscores, etc.
@                   → Matches the @ symbol.
[a-zA-Z0-9.-]+      → Matches the domain name (e.g., "example", "mycompany").
\.                  → Matches the dot before the domain extension.
[a-zA-Z]{2,}        → Matches the domain extension (e.g., "com", "org", "net").

```

### Regex to find all text between quotes
```
import re
re.findall(r'["\'](.*?)["\']',text)
```
```
["']       → Matches either a single (`'`) or double (`"`) quote.
(.*?)      → Captures everything inside the quotes (non-greedy match).
["']       → Ensures the match ends with the same quote type.

```

### Slice and Index a NumPy array
```
print(arr[1, :])  # Second row → [40 50 60]
print(arr[:, 0])  # First column → [10 40 70]

```

### Why is a class method used?
A class method is used when we want a method to operate on the class itself rather than an instance of the class. It is defined using the @classmethod decorator and takes cls as the first parameter instead of self.
```
class Example:
    count = 0  # Class variable

    @classmethod
    def increment_count(cls):
        cls.count += 1  # Modifies the class variable

Example.increment_count()
print(Example.count)  # Output: 1
```
### What is open-closed functionality?
The Open-Closed Principle (OCP) states that a class should be open for extension but closed for modification. This means that we should be able to extend functionality without modifying existing code.
```
class Shape:
    def area(self):
        pass

class Circle(Shape):
    def __init__(self, radius):
        self.radius = radius

    def area(self):
        return 3.14 * self.radius * self.radius

class Rectangle(Shape):
    def __init__(self, width, height):
        self.width = width
        self.height = height

    def area(self):
        return self.width * self.height
```
### What is single-line functionality?
This could refer to:

Lambda functions: Anonymous functions in one line.
List comprehensions: Creating lists in a single line.
Ternary operators: Conditional expressions in one line.
```
# Lambda function
square = lambda x: x**2
print(square(4))  # Output: 16

# List comprehension
squares = [x**2 for x in range(5)]
print(squares)  # Output: [0, 1, 4, 9, 16]

# Ternary operator
x = 10
y = "Even" if x % 2 == 0 else "Odd"
print(y)  # Output: Even
```

### 4. Count length of word and count of word in a list

```
from collections import Counter

words = ["code", "is", "fun", "python"]
length_counts = Counter(len(word) for word in words)

print(length_counts)  # Output: {4: 2, 2: 1, 6: 1}
```
### List comprehension/dictionary to append odd words as values and even words as keys
```
words = ["hello", "world", "python", "is", "fun"]
word_dict = {word: len(word) for word in words if len(word) % 2 == 0}  # Even word as key

print(word_dict)  # Output: {'hello': 5, 'python': 6}
```
### Sort values in a multidimensional list
```
data = [[1, 3], [4, 1], [2, 2]]
data.sort(key=lambda x: x[1])  # Sort by second element

print(data)  # Output: [[4, 1], [2, 2], [1, 3]]
```

### Write a generator function to find the square of an element in a list
```
def square_generator(lst):
    for num in lst:
        yield num**2  # Yielding square of each element

nums = [2, 3, 4, 5]
gen = square_generator(nums)

# Get the 3rd element (index 2)
for i in range(3):
    result = next(gen)  # Iterate till the 3rd element

print(result)  # Output: 16
```
### What is a Decorator in Python?
A decorator in Python is a function that takes another function (or method) as input and extends its behavior without modifying its original structure. It is commonly used in logging, authentication, and timing functions.
def my_decorator(func):
    def wrapper():
        print("Something before the function executes")
        func()
        print("Something after the function executes")
    return wrapper

@my_decorator
def say_hello():
    print("Hello!")

say_hello()
