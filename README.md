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


## Some Leetcode questions
 Easy Level
Two Sum (LeetCode #1)
Problem: Find two numbers in an array that add up to a target.
Solution:

```
def twoSum(nums, target):
    num_dict = {}
    for i, num in enumerate(nums):
        diff = target - num
        if diff in num_dict:
            return [num_dict[diff], i]
        num_dict[num] = i
```
Reverse a String (LeetCode #344)

```
def reverseString(s):
    return s[::-1]  # Pythonic way
Merge Two Sorted Lists (LeetCode #21)
Problem: Merge two sorted linked lists.

```
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

def mergeTwoLists(l1, l2):
    if not l1 or not l2:
        return l1 or l2
    if l1.val < l2.val:
        l1.next = mergeTwoLists(l1.next, l2)
        return l1
    else:
        l2.next = mergeTwoLists(l1, l2.next)
        return l2
```
🔹 Medium Level
Longest Substring Without Repeating Characters (LeetCode #3)
Solution: Sliding Window

```
def lengthOfLongestSubstring(s):
    char_index = {}
    left = 0
    max_length = 0

    for right in range(len(s)):
        if s[right] in char_index and char_index[s[right]] >= left:
            left = char_index[s[right]] + 1
        char_index[s[right]] = right
        max_length = max(max_length, right - left + 1)

    return max_length
```
Binary Search in Rotated Sorted Array (LeetCode #33)

```
def search(nums, target):
    left, right = 0, len(nums) - 1
    while left <= right:
        mid = (left + right) // 2
        if nums[mid] == target:
            return mid
        if nums[left] <= nums[mid]:
            if nums[left] <= target < nums[mid]:
                right = mid - 1
            else:
                left = mid + 1
        else:
            if nums[mid] < target <= nums[right]:
                left = mid + 1
            else:
                right = mid - 1
    return -1
```

Find the Duplicate Number (LeetCode #287)
Solution: Floyd's Tortoise and Hare (Cycle Detection)

```
def findDuplicate(nums):
    slow, fast = nums[0], nums[0]
    while True:
        slow = nums[slow]
        fast = nums[nums[fast]]
        if slow == fast:
            break
    slow = nums[0]
    while slow != fast:
        slow = nums[slow]
        fast = nums[fast]
    return slow
```
🔹 Hard Level
Median of Two Sorted Arrays (LeetCode #4)
Solution: Binary Search on Shorter Array

```
def findMedianSortedArrays(nums1, nums2):
    A, B = sorted((nums1, nums2), key=len)
    m, n = len(A), len(B)
    imin, imax, half_len = 0, m, (m + n + 1) // 2

    while imin <= imax:
        i = (imin + imax) // 2
        j = half_len - i
        if i < m and A[i] < B[j-1]:
            imin = i + 1
        elif i > 0 and A[i-1] > B[j]:
            imax = i - 1
        else:
            max_of_left = max(A[i-1] if i > 0 else float('-inf'), B[j-1] if j > 0 else float('-inf'))
            if (m + n) % 2 == 1:
                return max_of_left
            min_of_right = min(A[i] if i < m else float('inf'), B[j] if j < n else float('inf'))
            return (max_of_left + min_of_right) / 2
```
Trapping Rain Water (LeetCode #42)
Solution: Two-Pointer Approach

```
def trap(height):
    left, right = 0, len(height) - 1
    left_max, right_max = 0, 0
    water = 0

    while left < right:
        if height[left] < height[right]:
            if height[left] >= left_max:
                left_max = height[left]
            else:
                water += left_max - height[left]
            left += 1
        else:
            if height[right] >= right_max:
                right_max = height[right]
            else:
                water += right_max - height[right]
            right -= 1
    return water
```
