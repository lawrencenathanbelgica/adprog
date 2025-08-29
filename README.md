# Python Programming Notes 

---

## 🧠 CHEAT SHEET 

- **Brackets & Symbols**
  - `()` → function calls, parameters, `print()`, `input()`
  - `[]` → lists, indexing/slicing: `arr[0]`, `s[1:4]`
  - `{}` → dictionaries & sets: `{"key": "value"}`, `{1,2,3}`
  - `:`  → starts a block → `if:`, `for:`, `while:`, `def:`
- **Indentation**: 4 spaces per code block (no `{}` in Python).
- **Key built-ins**: `type()`, `len()`, `int()`, `float()`, `str()`, `range()`, `print()`, `input()`
- **Operators**:
  - Arithmetic: `+ - * / // % **`
  - Comparison: `== != > < >= <=`
  - Logical: `and or not`
- **Data Types**: `int`, `float`, `str`, `bool`, `list`, `tuple`, `dict`, `set`
- **Common Errors**: `IndentationError`, `SyntaxError`, `TypeError`, `NameError`

---

## 1) PYTHON SYNTAX & RULES

### Indentation (CRUCIAL)
Python uses **indentation** to define blocks, not braces.
```python
# ✅ Correct
if True:
    print("Hello")

# ❌ Incorrect (missing indentation)
if True:
print("Hello")
```

### Case Sensitivity
`print` ≠ `Print`. Keywords are lowercase: `if`, `for`, `while`, `def`, `True`, `False`, `None`.

### Comments
```python
# single line
"""
multi-line comment or docstring
"""
```

---

## 2) VARIABLES & TYPES

- Python is **dynamically typed** (no need to declare type).
- Good names are lowercase_with_underscores.

```python
age = 20           # int
height = 5.7       # float
name = "Nathan"    # str
is_student = True  # bool

type(age)          # <class 'int'>
```

### Type Casting
```python
int(3.9)   # 3
float(5)   # 5.0
str(42)    # "42"
```

---

## 3) INPUT & OUTPUT

```python
name = input("Enter your name: ")      # returns str
age = int(input("Enter your age: "))   # cast to int

print("Hi", name, "— age:", age)
```

**Common Pitfall**
```python
# ❌ "23" (string concatenation)
a = input(); b = input()
print(a + b)

# ✅ 5 (integer addition)
a = int(input()); b = int(input())
print(a + b)
```

---

## 4) OPERATORS

```python
x, y = 10, 3
x + y   # 13
x - y   # 7
x * y   # 30
x / y   # 3.3333333333 (always float)
x // y  # 3 (floor division)
x % y   # 1 (remainder)
x ** y  # 1000 (power)
```

**Comparison & Logical**
```python
x == y, x != y, x > y, x < y, x >= y, x <= y
True and False, True or False, not True
```

**Analysis:** Prefer `//` when you need an integer result.

---

## 5) STRINGS (Text)

```python
s = "Advanced Programming"
len(s)            # length
s.lower()         # "advanced programming"
s.upper()         # "ADVANCED PROGRAMMING"
s.swapcase()      # aDVANCED pROGRAMMING
"gram" in s       # True (membership)
s.replace("m", "*")
s[1:8]            # slicing by index
s[::2]            # step slicing
```

**Formatting**
```python
txt = "I love {}"
txt.format("Python")
f"I love {s}"     # f-string (preferred)
```

---

## 6) COLLECTIONS

### 6.1 Lists (ordered, mutable) — `[]`
```python
fruits = ["apple", "banana", "cherry"]
fruits[0]              # "apple"
fruits[-1]             # "cherry"
fruits.append("mango")
fruits.insert(1, "orange")
fruits.remove("banana")
del fruits[0]
len(fruits)
```

**Slicing**
```python
nums = [9,7,4,5,8,1,2,5]
first, middle, last = nums[0], nums[1:-1], nums[-1]
# first = 9, middle = [7,4,5,8,1,2], last = 5
```

**List Comprehension (handy)**
```python
squares = [n*n for n in range(1,6)]   # [1,4,9,16,25]
```

### 6.2 Tuples (ordered, **immutable**) — `()`
```python
t = ("apple", "banana", "cherry")
t[1]            # "banana"
len(t)          # 3
# t[1] = "orange"  # ❌ TypeError (cannot modify)
```

### 6.3 Dictionaries (key–value) — `{}`
```python
student = {"name": "Nathan", "age": 20}
student["name"]         # "Nathan"
student.get("age")      # 20
student["course"] = "ECE"
student.keys()          # dict_keys([...])
student.values()
student.items()
student.pop("age")
student.popitem()       # removes last inserted pair
```

### 6.4 Sets (unordered, unique) — `{}`
```python
s = {"apple", "banana", "cherry", "cherry"}  # duplicates removed
s.add("orange")
s.update(["mango", "grapes"])
s.remove("banana")  # KeyError if missing
s.discard("banana") # safe remove (no error)
item = s.pop()      # removes a random element
```

**Analysis:** Use a **set** to deduplicate data quickly.

---

## 7) CONTROL FLOW

### If / Elif / Else
```python
grade = 85
if grade >= 90:
    print("A")
elif grade >= 80:
    print("B")
else:
    print("C or below")
```

**Analysis:** Each block ends with `:` and is **indented**.

---

## 8) LOOPS

### For Loop
```python
for i in range(5):   # 0..4
    print(i)

for ch in "abc":
    print(ch)

for fruit in ["apple", "banana"]:
    print(fruit)
```

### While Loop
```python
count = 0
while count < 3:
    print(count)
    count += 1
```

**Pitfall:** Don’t forget to update the condition → infinite loop.

---

## 9) FUNCTIONS

### Defining & Calling
```python
def greet(name):
    """Return a greeting for the given name."""
    return f"Hello, {name}!"

greet("Nathan")   # "Hello, Nathan!"
```

### Default Parameters
```python
def power(base, exp=2):
    return base ** exp

power(3)     # 9
power(3, 3)  # 27
```

### Multiple Returns
```python
def min_max(nums):
    return min(nums), max(nums)

lo, hi = min_max([3,1,9])
```

### Loop + Accumulator Pattern (classic)
```python
def squares_sum(n):
    total = 0
    for i in range(1, n+1):
        total += i**2
    return total
# squares_sum(5) -> 55
```

**Analysis**
- Put a **docstring** explaining purpose.
- Use `return` for values (printing is not returning).
- Keep functions small and focused.

---

## 10) COMMON ERRORS & HOW TO FIX

### IndentationError
```python
if True:
print("hi")          # ❌
# Fix:
if True:
    print("hi")      # ✅
```

### SyntaxError (missing `:`)
```python
def add(x, y)        # ❌
    return x + y
# Fix:
def add(x, y):
    return x + y
```

### TypeError (mixing types)
```python
"Age: " + 20         # ❌
"Age: " + str(20)    # ✅
```

### NameError (undefined variable)
```python
print(score)         # ❌ if score not defined
```

---

## 11) MINI PROJECTS (with explanations)

### 11.1 Alphabet Soup (sort letters)
**Goal:** Ask user for a word and output its letters in alphabetical order.
```python
word = input("Enter a word: ")
sorted_word = ''.join(sorted(word))
print(sorted_word)
# Analysis: sorted(word) returns a list of chars, join() makes it a string.
```

### 11.2 Emoticon Replacer
**Goal:** Replace certain words with emoticons.
```python
def emotify(phrase):
    mapping = {"smile": ":)", "grin": ":D", "sad": ":((", "mad": ">:("}
    for word, symbol in mapping.items():
        phrase = phrase.replace(word, symbol)
    return phrase

text = input("Enter a phrase: ")
print(emotify(text))
# Analysis: replace is case-sensitive; consider .lower() if needed.
```

### 11.3 Unpack List (first, middle, last)
```python
user_input = input("Enter numbers (e.g., 9 7 4 5 8 1 2 5): ")

if " " in user_input:
    lst = list(map(int, user_input.split()))
else:
    lst = list(map(int, user_input))   # treats each char as a digit

first, middle, last = lst[0], lst[1:-1], lst[-1]
print("first:", first)
print("middle:", middle)
print("last:", last)

# Analysis:
# - lst[1:-1] slices everything except first and last.
# - .split() splits by spaces; without spaces we map each char.
```

---

## 12) CODE REVIEW / ANALYSIS SCENARIOS

### A) Fix Indentation
```python
# ❌
for i in range(1, 6):
print(i)

# ✅
for i in range(1, 6):
    print(i)
```
**Why:** The `print` must be inside the loop block.

---

### B) Missing Colon
```python
# ❌
age = 20
if age >= 18
    print("Adult")

# ✅
age = 20
if age >= 18:
    print("Adult")
```
**Why:** Control statements end with `:`.

---

### C) List vs. Dictionary Access
```python
# ❌ list with key access
student = ["Nathan", 19, "ECE"]
# print(student["name"])  # KeyError

# ✅ either index the list
print(student[0])  # "Nathan"

# ✅ or use a dictionary
student = {"name": "Nathan", "age": 19, "course": "ECE"}
print(student["name"])
```
**Why:** Lists use indexes; dicts use keys.

---

### D) Tuple Immutability
```python
t = ("apple", "banana", "cherry")
# t[1] = "orange"  # ❌ TypeError
```
**Why:** Tuples cannot be modified. Convert to list if needed.

---

### E) Safe Set Removal
```python
s = {"a", "b"}
# s.remove("c")   # ❌ KeyError
s.discard("c")    # ✅ no error if missing
```

---

## 13) EXTRA: STRING & LIST TIPS

### Useful String Methods
```python
s.strip()       # remove whitespace ends
s.split()       # split by spaces -> list
",".join(list)  # join list into CSV
s.count("a")    # occurrences
s.find("pro")   # first index or -1
```

### Useful List Methods
```python
lst.append(x)
lst.extend([1,2,3])
lst.index(x)        # first index of x
lst.count(x)
lst.sort()          # in-place
sorted(lst)         # returns new sorted list
```

---

## 14) PRACTICE QUIZ (Self-Check)

**Q1.** What’s the output?
```python
print(20 // 6, 20 % 6)
```
<details><summary>Answer</summary>
3 2
</details>

**Q2.** Fix the code:
```python
name = input("Name: ")
print "Hello", name
```
<details><summary>Answer</summary>

```python
name = input("Name: ")
print("Hello", name)
```
</details>

**Q3.** Convert input strings to integers and add them:
```python
a = input(); b = input()
# your code:
```
<details><summary>Answer</summary>

```python
a = int(input()); b = int(input())
print(a + b)
```
</details>

**Q4.** Why does this error?
```python
t = (1,2,3)
t[0] = 9
```
<details><summary>Answer</summary>
Tuples are immutable; you cannot assign to an index.
</details>

**Q5.** Write a function `is_adult(age)` that returns `True` if `age >= 18`, else `False`.
<details><summary>Answer</summary>

```python
def is_adult(age):
    return age >= 18
```
</details>

---

## 15) QUICK REFERENCE TABLE

| Topic         | Must Remember                                               | Example                              |
|---------------|--------------------------------------------------------------|--------------------------------------|
| print         | Needs `()`                                                   | `print("Hi")`                        |
| input         | Returns `str` → cast if needed                               | `age = int(input())`                 |
| list          | `[]`, mutable, index/slice                                   | `a[0]`, `a[1:-1]`                    |
| tuple         | `()`, immutable                                              | `t = (1,2)`                          |
| dict          | `{}`, key-value, access by key                               | `d["key"]`                           |
| set           | `{}`, unique, unordered                                      | `{1,2,2} -> {1,2}`                   |
| if/elif/else  | ends with `:`, indented block                                | `if x: ...`                          |
| for           | iterate range/iterables                                      | `for i in range(5):`                 |
| while         | needs a changing condition                                   | `while x < 10:`                      |
| function      | `def name(params):` + `return`                               | `def add(a,b): return a+b`           |
| division      | `/` float, `//` floor, `%` remainder, `**` power             | `20//6`, `20%6`, `2**3`              |

---

**You got this. Review the cheat sheet, code the mini projects once, and answer the quiz without peeking.** 🚀
