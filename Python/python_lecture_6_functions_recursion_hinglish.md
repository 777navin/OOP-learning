# Python Notes — Lecture 6: Functions and Recursion
## Hinglish Study Notes | Interview Practice | OA Preparation

> **Source:** Uploaded college lecture notes, Lecture 6 (6 pages), covering Functions and Recursion.
> Lecture ke concepts, examples, code aur outputs include hain. Extra interview/OA practice clearly separate hai.

## Contents
1. [Functions in Python](#1-functions-in-python)
2. [Types of Functions](#2-types-of-functions)
3. [Default Parameters](#3-default-parameters)
4. [Lecture Practice: Functions](#4-lecture-practice-functions)
5. [Recursion](#5-recursion)
6. [Lecture Practice: Recursion](#6-lecture-practice-recursion)
7. [Quick Revision](#7-quick-revision)
8. [Interview Questions and Answers](#8-interview-questions-and-answers)
9. [OA Practice Questions with Solutions](#9-oa-practice-questions-with-solutions)
10. [Extra Practice Questions](#10-extra-practice-questions)
11. [Common Mistakes](#11-common-mistakes)
12. [Revision Checklist](#12-revision-checklist)

---

## 1. Functions in Python

**Function** statements ka ek block hota hai jo specific task perform karta hai. Ek baar define karke ise multiple times call kar sakte hain.

### Syntax

```python
def func_name(param1, param2):
    # some work
    return val

func_name(arg1, arg2)
```

- `def` function definition start karta hai.
- **Parameters** definition mein likhe names hain.
- **Arguments** function call ke time pass ki gayi actual values hain.
- `return` calculated value caller ko wapas deta hai.
- Function tab execute hota hai jab usse call kiya jata hai.

### Example: Sum of two numbers

```python
def calc_sum(a, b):
    s = a + b
    return s

print(calc_sum(2, 3))
print(calc_sum(10, 20))
```

Output:
```text
5
30
```

`calc_sum(2, 3)` mein `a = 2`, `b = 3`, isliye `5` return hota hai. Same function ko different arguments ke saath reuse kar sakte hain.

### Function without `return`

Explicit `return` nahi likha ho to Python implicitly `None` return karta hai.

```python
def greet(name):
    print("Hello,", name)

result = greet("Aman")
print(result)
```

Output:
```text
Hello, Aman
None
```

**Difference:** `print()` screen par value display karta hai; `return` value caller ko deta hai.

---

## 2. Types of Functions

| Built-in functions | User-defined functions |
|---|---|
| Python mein already available | Programmer khud banata hai |
| `print()`, `len()`, `type()`, `range()` | `calc_sum()` jaise functions |

**Tip:** Function ka naam built-in function jaisa mat rakho. `sum` ya `len` ko naam banane se current scope mein built-in shadow ho sakta hai.

---

## 3. Default Parameters

Parameter ko default value de sakte hain. Call mein argument omit karne par default use hota hai.

```python
def calc_product(a=1, b=2):
    return a * b

print(calc_product())      # both defaults
print(calc_product(5))     # a = 5, b default = 2
print(calc_product(5, 6))
```

Output:
```text
2
10
30
```

### Default parameter order

Default ke bina parameters pehle, default wale baad mein:

```python
def f(a, b=2):  # valid
    return a + b

# Invalid syntax:
# def f(a=1, b):
#     return a + b
```

---

## 4. Lecture Practice: Functions

### Q1. List ki length print karne wala function

```python
def print_len(items):
    print(len(items))

cities = ["Delhi", "Mumbai", "Pune"]
print_len(cities)
```

Output: `3`

### Q2. List ke elements ek line mein print karo

```python
def print_list(items):
    for item in items:
        print(item, end=" ")
    print()

print_list(["Delhi", "Mumbai", "Pune"])
```

Output:
```text
Delhi Mumbai Pune
```

`end=" "` `print()` ko newline ke bajay space ke saath end karwata hai.

### Q3. Function se factorial calculate karo

```python
def factorial(n):
    fact = 1
    for i in range(1, n + 1):
        fact *= i
    return fact

print(factorial(5))
```

Output: `120`

Factorial: `n! = 1 × 2 × ... × n`, and `0! = 1`. Ye basic code non-negative integer input assume karta hai.

### Q4. USD ko INR mein convert karne wala function

```python
def usd_to_inr(usd, rate=83):
    return usd * rate

print(usd_to_inr(10))      # default rate
print(usd_to_inr(10, 88))  # explicitly passed rate
```

Output:
```text
830
880
```

Lecture mein `83` illustrative default hai, current exchange rate nahi. Exchange rate badalta rehta hai; use karte waqt current rate pass karein.

---

## 5. Recursion

**Recursion** tab hoti hai jab function apne aap ko call karta hai. Har recursive function ko **base case** chahiye—condition jahan recursion stop ho. Base case na ho/reach na ho to Python `RecursionError` raise kar sakta hai.

- **Base case:** Stop condition.
- **Recursive case:** Function simpler/smaller input par khud ko call karta hai.

### Example 1: `n` se `1` tak backwards print karo

```python
def show(n):
    if n == 0:       # base case
        return
    print(n)
    show(n - 1)      # recursive call

show(5)
```

Output:
```text
5
4
3
2
1
```

Call flow: `show(5)` → `show(4)` → `show(3)` → `show(2)` → `show(1)` → `show(0)` par stop.

### Example 2: Factorial using recursion

Formula: `n! = n × (n-1)!`, with `0! = 1! = 1`.

```python
def fact(n):
    if n == 0 or n == 1:  # base case
        return 1
    else:
        return n * fact(n - 1)

print(fact(5))
```

Output: `120`

### Dry run: `fact(4)`

```text
fact(4) = 4 * fact(3)
        = 4 * 3 * fact(2)
        = 4 * 3 * 2 * fact(1)
        = 4 * 3 * 2 * 1
        = 24
```

Calls pehle base case tak jaati hain; phir return values unwind hote waqt multiply hoti hain.

---

## 6. Lecture Practice: Recursion

### Q1. First `n` natural numbers ka sum recursively calculate karo

```python
def calc_sum(n):
    if n == 0:       # base case
        return 0
    return n + calc_sum(n - 1)

print(calc_sum(5))
```

Output: `15`

`calc_sum(5) = 5 + 4 + 3 + 2 + 1 + 0 = 15`.

### Q2. Recursion se list ke elements print karo

List aur index parameters use karo.

```python
def print_list(items, idx=0):
    if idx == len(items):  # base case: reached end
        return
    print(items[idx])
    print_list(items, idx + 1)

print_list(["mango", "apple", "banana"])
```

Output:
```text
mango
apple
banana
```

Dry run:
- `idx = 0` → `mango`
- `idx = 1` → `apple`
- `idx = 2` → `banana`
- `idx = 3`, length `3` → base case, return.

---

## 7. Quick Revision

| Concept | Meaning | Key reminder |
|---|---|---|
| `def` | Function define karta hai | Call hone par execute hota hai |
| Parameter | Definition ka variable name | `def f(x)` mein `x` |
| Argument | Call ki actual value | `f(10)` mein `10` |
| `return` | Value caller ko deta hai | `print()` se different |
| No explicit return | Python `None` deta hai | Print hona return hona nahi |
| Built-in | Python-provided | `len()`, `type()`, `range()` |
| User-defined | Programmer-defined | `calc_sum()` |
| Default parameter | Missing argument ka fallback | Non-default parameters pehle |
| Recursion | Function self-call karta hai | Base case compulsory |
| Base case | Stop condition | Missing base case bug ban sakta hai |

---

## 8. Interview Questions and Answers

### Q1. Function kya hota hai?
**Answer:** Reusable code block jo specific task karta hai. Code duplication kam hoti hai aur program modular banta hai.

### Q2. Function define aur call karne mein difference?
**Answer:** `def` se function define hota hai; `function_name(...)` se execute/call hota hai.

### Q3. Parameter aur argument?
**Answer:** Parameter definition ka name; argument call ke time actual value.

### Q4. `return` aur `print()` mein difference?
**Answer:** `print()` display karta hai; `return` value caller ko deta hai jise store ya further calculation mein use kar sakte hain.

### Q5. Function `return` nahi karta to?
**Answer:** Python implicitly `None` return karta hai.

### Q6. Built-in vs user-defined?
**Answer:** Built-in Python se milta hai (`len()`); user-defined programmer `def` se banata hai.

### Q7. Default parameter?
**Answer:** Definition mein di hui fallback value jo argument omit hone par use hoti hai.

### Q8. `def f(a=1, b)` invalid kyun?
**Answer:** Non-default parameter `b` default parameter ke baad hai. `def f(a, b=1)` valid hai.

### Q9. Recursion kya hai?
**Answer:** Function ka apne aap ko call karna, aksar smaller subproblem ke saath.

### Q10. Base case kyun zaroori hai?
**Answer:** Recursion ko stop karne ke liye. Base case na ho/reach na ho to `RecursionError` ho sakta hai.

### Q11. Recursive factorial complexity?
**Answer:** Time `O(n)`, recursive call stack space `O(n)`.

### Q12. Recursive sum complexity?
**Answer:** Time `O(n)`, stack space `O(n)`.

### Q13. Recursion hamesha loop se better hai?
**Answer:** Nahi. Recursion readable ho sakti hai, lekin stack overhead aur recursion limit hoti hai. Simple counting/factorial ke liye loop space-efficient ho sakta hai.

### Q14. Function ko test kaise karoge?
**Answer:** Normal inputs, edge cases (`0`, `1`, empty list) aur invalid inputs test karunga; expected aur actual output compare karunga.

### Q15. Infinite recursion kaise avoid karein?
**Answer:** Correct base case rakho aur har recursive call input ko base case ke closer le jaye.

---

## 9. OA Practice Questions with Solutions

Ye additional coding assessment practice hai; original lecture se alag extra questions hain.

### OA Q1. Function se even/odd check karo

```python
def even_or_odd(n):
    if n % 2 == 0:
        return "Even"
    return "Odd"

print(even_or_odd(12))
print(even_or_odd(7))
```

Output:
```text
Even
Odd
```

Time `O(1)`, extra space `O(1)`.

### OA Q2. Three numbers ka maximum

```python
def maximum_of_three(a, b, c):
    largest = a
    if b > largest:
        largest = b
    if c > largest:
        largest = c
    return largest

print(maximum_of_three(10, 25, 17))
```

Output: `25`. Time `O(1)`, extra space `O(1)`.

### OA Q3. Iterative factorial with validation

```python
def factorial(n):
    if n < 0:
        raise ValueError("n must be non-negative")

    fact = 1
    for i in range(1, n + 1):
        fact *= i
    return fact

print(factorial(5))
print(factorial(0))
```

Output:
```text
120
1
```

Time `O(n)`, extra space `O(1)`.

### OA Q4. Recursive sum of digits

```python
def digit_sum(n):
    n = abs(n)
    if n < 10:
        return n
    return n % 10 + digit_sum(n // 10)

print(digit_sum(583))
```

Output: `16`. Time `O(d)`, stack `O(d)`, where `d` is digit count.

### OA Q5. Fibonacci using recursion

```python
def fib(n):
    if n < 0:
        raise ValueError("n must be non-negative")
    if n <= 1:
        return n
    return fib(n - 1) + fib(n - 2)

print(fib(6))
```

Output: `8`.

Naive recursion ka time exponential (approximately `O(2^n)`) aur stack depth `O(n)` hai. Interview follow-up: memoization ya iterative DP se optimize karo.

### OA Q6. Recursive list traversal

```python
def print_items(items, idx=0):
    if idx >= len(items):
        return
    print(items[idx])
    print_items(items, idx + 1)

print_items([10, 20, 30])
```

Output:
```text
10
20
30
```

Time `O(n)`, stack `O(n)`.

### OA Q7. Power recursively calculate karo

```python
def power(a, p):
    if p < 0:
        raise ValueError("p must be non-negative")
    if p == 0:
        return 1
    return a * power(a, p - 1)

print(power(2, 5))
```

Output: `32`. Time `O(p)`, stack `O(p)`. Optimization: exponentiation by squaring se `O(log p)`.

### OA Q8. String palindrome function

```python
def is_palindrome(s):
    return s == s[::-1]

print(is_palindrome("level"))
print(is_palindrome("python"))
```

Output:
```text
True
False
```

Time `O(n)`; reverse string ke liye extra space `O(n)`.

---

## 10. Extra Practice Questions

Pehle khud attempt karo; phir hints dekho.

1. Two numbers ka average return karne wala function.
2. List ka sum return karne wala function.
3. List ka maximum return karne wala function.
4. Number prime hai ya nahi.
5. Number mein digits count karo.
6. String ke vowels count karo.
7. Recursion se `n` se `1` print karo.
8. Recursion se `1` se `n` print karo.
9. Recursion se list ka sum calculate karo.
10. Recursion se string reverse karo.
11. Recursion se power calculate karo.
12. Fibonacci loop se solve karo aur recursion se compare karo.
13. Factorial ke iterative aur recursive versions.
14. Empty aur single-element list handle karne wala maximum function.
15. Invalid inputs ke liye validation add karo.

### Hints
- Average = total / count; empty list handle karo.
- Prime check: `n < 2` prime nahi; divisors `2` se `sqrt(n)` tak test kar sakte ho.
- Digit count mein `0` ko special case handle karo.
- Recursive list sum: end index par `0` return karo.
- String reverse recursion: last character + remaining prefix, empty string base case.
- Fibonacci ke liye memoization/iteration compare karo.

---

## 11. Common Mistakes

1. Function define karke call na karna: definition se execute nahi hota.
2. `print` ko `return` samajhna.
3. `return` bhoolna: function `None` de sakta hai.
4. Parameter aur argument confuse karna.
5. Default parameter ka wrong order.
6. Built-in names overwrite karna (`sum`, `len`, `list`).
7. Recursion mein base case miss karna.
8. Recursive input ko smaller na banana.
9. Factorial accumulator `0` se start karna; product ke liye `1` chahiye.
10. Negative factorial allow karna; input validate karo.
11. Large `n` par naive Fibonacci chalana; bahut expensive ho sakta hai.
12. Lecture exchange-rate example ke `83` ko current rate samajhna.

---

## 12. Revision Checklist

- [ ] `def`, function call aur indentation samajh aata hai.
- [ ] Parameter vs argument explain kar sakta/sakti hoon.
- [ ] `return` vs `print()` explain kar sakta/sakti hoon.
- [ ] Built-in aur user-defined functions identify kar sakta/sakti hoon.
- [ ] Default parameters ka correct order likh sakta/sakti hoon.
- [ ] List length aur elements print karne wale functions likh sakta/sakti hoon.
- [ ] Iterative factorial implement kar sakta/sakti hoon.
- [ ] Recursion aur base case explain kar sakta/sakti hoon.
- [ ] Recursive factorial, sum aur list traversal dry-run kar sakta/sakti hoon.
- [ ] Time/space complexity estimate kar sakta/sakti hoon.
- [ ] OA ke liye edge cases aur constraints test kar sakta/sakti hoon.

---

## Suggested Study Plan

**Session 1 — Functions (30–45 min):** `def`, parameters/arguments, `return`, `print`, built-ins, default parameters. Lecture practice Q1–Q4 type karke run karo.

**Session 2 — Recursion (45 min):** Base case, recursive case, `show(n)`, factorial, natural-number sum aur list traversal. Call stack paper par draw karo.

**Session 3 — Interview/OA (45–60 min):** Even/odd, max of three, digit sum, Fibonacci, power, palindrome. Har solution ke edge cases, time aur space complexity likho.

> **Best learning rule:** Code khud type karo, dry run karo, inputs badlo, phir notes band karke dobara implement karo.
