# Python Notes --- Lecture 1

## Python Basics, Interview Practice aur Online Assessment (OA) Preparation

**Language:** Hinglish (English terms + Hindi explanation)\
**Source:** Uploaded *Python Notes (Lecture 1)* PDF. Original lecture ke
topics aur examples ko preserve kiya gaya hai. Interview/OA practice
section additional study material hai.

------------------------------------------------------------------------

## Contents

1.  Programming kya hoti hai?
2.  Python kya hai?
3.  First Python Program
4.  Python Character Set
5.  Variables
6.  Identifiers ke Rules
7.  Data Types
8.  Keywords
9.  Sum Program
10. Comments
11. Operators
12. Type Conversion
13. Type Casting
14. User Input
15. Lecture Practice Questions with Answers
16. Interview Questions with Answers
17. Python Coding Practice for OA
18. Quick Revision Sheet
19. Practice Checklist

------------------------------------------------------------------------

# 1. Programming kya hoti hai?

**Programming** ka matlab computer ko instructions dena hai taaki woh
koi task perform kar sake. Hum instructions Python jaise programming
language mein likhte hain.

Computer internally machine code, yani `0` aur `1`, samajhta hai. Isliye
programming code ko machine code mein translate karne ke liye translator
ki zaroorat hoti hai.

-   **Compiler:** Poore program ko ek saath translate karta hai, phir
    run karta hai.
-   **Interpreter:** Program ko line-by-line translate aur execute karta
    hai. Lecture notes ke mutabik Python interpreter use karta hai.

**Flow:**
`Your Code → Translator (Compiler / Interpreter) → Machine Code`

> Interview note: Python ko commonly interpreted language kaha jata hai.
> CPython implementation mein source code bytecode mein compile hota
> hai, jise Python Virtual Machine execute karti hai. Beginner level par
> "Python interpreter use karta hai" yaad rakhein.

# 2. Python kya hai?

Python ek programming language hai. Iski main features:

-   **Simple and easy to learn:** Syntax English jaisi readable hoti
    hai.
-   **Free and open source:** Isse freely use aur modify kiya ja sakta
    hai.
-   **High-level language:** Programmer ko memory aur hardware ki
    low-level details manually manage karne ki zaroorat aam taur par
    nahi hoti.
-   **Developed by:** Guido van Rossum.
-   **Portable:** Python program ko Windows, macOS aur Linux par chalaya
    ja sakta hai, agar required Python/runtime aur dependencies
    available hon.

Python ka use scripting, automation, web development, data analysis,
AI/ML aur bahut se doosre areas mein hota hai.

# 3. Our First Program

Python mein `print()` function output screen par display karta hai.

``` python
print("Hello World")
```

**Output**

``` text
Hello World
```

Text ko quotes ke andar likhte hain. `print()` mein multiple values
comma se separate kar sakte hain.

``` python
print("Python", "is", "fun")
print(10 + 5)
```

**Output**

``` text
Python is fun
15
```

**Yaad rakhein:** - `"Hello"` string/text hai. - `10 + 5` arithmetic
expression hai; iska result `15` print hota hai. - `print()` values ko
display karta hai; yeh khud user se input nahi leta.

# 4. Python Character Set

Python source code mein commonly ye characters use hote hain:

-   **Letters:** `A-Z`, `a-z`
-   **Digits:** `0-9`
-   **Special symbols:** `+ - * / % = ( ) [ ] { } # : , .` etc.
-   **Whitespace:** blank space, tab, carriage return, newline, form
    feed
-   **Other characters:** Python data/literals mein ASCII aur Unicode
    characters process kar sakta hai.

Whitespace aur indentation Python mein important hain. Especially blocks
define karne ke liye indentation use hoti hai.

# 5. Variables

**Variable** ek naam hai jiske through hum program mein value ko refer
karte hain aur baad mein use kar sakte hain.

``` python
name = "Shradha"
age = 23
price = 25.99

print(name)
print(age)
print(price)
```

**Output**

``` text
Shradha
23
25.99
```

`=` assignment operator hai. Isse right side ki value left side ke
variable name ko assign hoti hai.

``` python
age = 23
age = 24  # value updated
print(age)
```

**Output**

``` text
24
```

Python mein variable ka type value ke saath associated hota hai;
variable ko baad mein doosre type ki value bhi assign ki ja sakti hai.

``` python
value = 10
value = "ten"
print(value)
```

Output: `ten`

# 6. Rules for Identifiers

**Identifier** variable, function, class ya kisi named object ka naam
hota hai.

Rules: 1. Uppercase letters, lowercase letters, digits aur underscore
(`_`) use kar sakte hain. 2. Identifier digit se start nahi ho sakta. 3.
`! # @ % $` jaise special symbols aur spaces allowed nahi hote. 4.
Identifier ki fixed maximum length ka rule nahi hai, practical
readability maintain karein. 5. Python keyword ko identifier ke roop
mein use nahi kar sakte. 6. Identifiers **case-sensitive** hain: `age`
aur `Age` alag names hain.

``` python
myVariable = 10       # Valid
variable_1 = 20       # Valid
variable_for_print = 30  # Valid

# 1variable = 10  # Invalid: digit se start hota hai
# my-var = 10     # Invalid: hyphen
# my var = 10     # Invalid: space
```

**Good practice:** Python mein variable names ke liye `snake_case`
common convention hai, jaise `student_name`, `total_marks`.

# 7. Data Types

Python mein har value ka ek type hota hai.

  Type         Meaning                           Example
  ------------ --------------------------------- ------------------------
  `int`        Whole number / integer            `age = 23`
  `float`      Decimal / floating-point number   `pi = 3.14`
  `str`        Text/string, quotes mein          `name = "Shradha"`
  `bool`       Boolean: `True` ya `False`        `is_adult = True`
  `NoneType`   Value absent/none                 `result = None`
  `complex`    Complex number                    `complex_num = 2 + 3j`

`type()` function value ka type check karta hai.

``` python
age = 23
pi = 3.14
complex_num = 2 + 3j
A = True
name = "Shradha"
x = None

print(type(age))
print(type(pi))
print(type(complex_num))
print(type(A))
print(type(name))
print(type(x))
```

**Output**

``` text
<class 'int'>
<class 'float'>
<class 'complex'>
<class 'bool'>
<class 'str'>
<class 'NoneType'>
```

**Interview points:** - `True` aur `False` Boolean values hain aur
capital letters se start hote hain. - `"23"` string hai, jabki `23`
integer hai. - `None` ka matlab "no value" hai; yeh `0` ya empty string
ke equal nahi hota.

# 8. Keywords

**Keywords** Python ke reserved words hain jinka special meaning hota
hai. Inhe variable names ke roop mein use nahi karna chahiye.

Lecture notes mein listed keywords:

``` text
and       as        assert    break     class
continue  def       del       elif      else
except    finally   for       from      global
if        import    in        is        lambda
nonlocal  not       or        pass      raise
return    try       while     with      yield
True      False     None
```

Notes ka point: `True`, `False` aur `None` capital letter se start hote
hain; baaki listed keywords lowercase hain.

Python version ke hisaab se keyword list badal sakti hai. Current
interpreter mein keywords dekhne ke liye:

``` python
import keyword
print(keyword.kwlist)
```

# 9. Print Sum

Do numbers variables mein store karke add karna:

``` python
a = 5
b = 10
sum = a + b
print("Sum is", sum)
```

**Output**

``` text
Sum is 15
```

**Coding convention:** Built-in function `sum()` ke naam ko variable ke
roop mein overwrite na karna behtar hai. Isliye real code mein `total`
naam use kar sakte hain:

``` python
a = 5
b = 10
total = a + b
print("Sum is", total)
```

# 10. Comments

Comments program ke andar explanation/notes hote hain. Python unhe
executable statement ki tarah run nahi karta.

### Single-line comment

`#` se start hota hai.

``` python
# This is a single-line comment
print("Hello")  # comment after code
```

### Triple-quoted text

Lecture notes multi-line comment ke example mein triple quotes dikhate
hain:

``` python
"""
This is a
multi-line comment
"""
print("Comments make code easy to understand")
```

**Important distinction:** Triple-quoted text technically string literal
hota hai, dedicated comment syntax nahi. Agar kisi function/class/module
ke start mein ho, to woh docstring ban sakta hai. Normal explanation ke
liye `#` comments sabse straightforward hain.

# 11. Types of Operators

**Operator** ek symbol/keyword hai jo values par operation karta hai.
Values ko operands kehte hain.

## 11.1 Arithmetic Operators

Operators: `+`, `-`, `*`, `/`, `%`, `**`

``` python
a, b = 10, 3

print(a + b)   # addition
print(a - b)   # subtraction
print(a * b)   # multiplication
print(a / b)   # division
print(a % b)   # remainder
print(a ** b)  # power: 10 to the power 3
```

**Output**

``` text
13
7
30
3.3333333333333335
1
1000
```

  Operator   Meaning                                Example result
  ---------- -------------------------------------- ------------------
  `+`        Addition                               `10 + 3 = 13`
  `-`        Subtraction                            `10 - 3 = 7`
  `*`        Multiplication                         `10 * 3 = 30`
  `/`        True division; normally float result   `10 / 3`
  `%`        Remainder                              `10 % 3 = 1`
  `**`       Exponent/power                         `10 ** 3 = 1000`

Extra useful operator: `//` floor division karta hai, jaise
`10 // 3 == 3`.

## 11.2 Relational / Comparison Operators

Operators: `==`, `!=`, `>`, `<`, `>=`, `<=`. Comparison ka result `True`
ya `False` hota hai.

``` python
a, b = 10, 3

print(a == b)
print(a != b)
print(a > b)
print(a < b)
print(a >= b)
print(a <= b)
```

**Output**

``` text
False
True
True
False
True
False
```

**Common interview confusion:** - `=` assignment karta hai. - `==`
equality compare karta hai.

## 11.3 Assignment Operators

Operators: `=`, `+=`, `-=`, `*=`, `/=`, `%=`, `**=`

``` python
num = 10
num += 5     # num = num + 5
print(num)
num *= 2     # num = num * 2
print(num)
num -= 10    # num = num - 10
print(num)
num **= 2    # num = num ** 2
print(num)
```

**Output**

``` text
15
30
20
400
```

## 11.4 Logical Operators

-   `and`: result `True` tabhi jab dono conditions true hon.
-   `or`: result `True` jab kam-se-kam ek condition true ho.
-   `not`: Boolean result ko reverse karta hai.

``` python
a, b = True, False

print(a and b)
print(a or b)
print(not a)
print((5 > 3) and (2 > 1))
```

**Output**

``` text
False
True
False
True
```

Quick truth table:

  A         B         `A and B`   `A or B`
  --------- --------- ----------- ----------
  `True`    `True`    `True`      `True`
  `True`    `False`   `False`     `True`
  `False`   `True`    `False`     `True`
  `False`   `False`   `False`     `False`

`not True` gives `False`, aur `not False` gives `True`.

# 12. Type Conversion

**Type conversion** mein ek data type ko doosre type mein convert kiya
jata hai.

### Implicit conversion

Python kuch operations mein automatically type convert kar sakta hai.

``` python
a, b = 1, 2.0
total = a + b  # int value float ke saath combine hoti hai
print(total)
```

**Output**

``` text
3.0
```

Lekin number aur string ko directly add nahi kar sakte:

``` python
a, b = 1, "2"
total = a + b  # TypeError
```

Representative error:

``` text
TypeError: unsupported operand type(s) for +: 'int' and 'str'
```

# 13. Type Casting

**Type casting / explicit conversion** mein programmer conversion
function call karta hai.

``` python
a, b = 1, "2"
c = int(b)       # "2" becomes integer 2
total = a + c
print(total)
```

**Output**

``` text
3
```

### Common conversion functions

  Function                Description
  ----------------------- ---------------------------------------------------------
  `int(y)`                Suitable value ko integer mein convert karta hai
  `float(y)`              Floating-point number mein convert karta hai
  `str(y)`                String representation banata hai
  `bool(y)`               Truth value deta hai
  `complex(real, imag)`   Complex number banata hai
  `list(y)`               List banata hai, agar input iterable ho
  `tuple(y)`              Tuple banata hai, agar input iterable ho
  `set(y)`                Set banata hai; duplicate elements remove ho sakte hain
  `dict(y)`               Key-value pairs se dictionary banata hai
  `ord(y)`                Single character ka Unicode code point deta hai
  `hex(y)`                Integer ko hexadecimal string mein convert karta hai
  `oct(y)`                Integer ko octal string mein convert karta hai

``` python
print(int("25"))
print(float(5))
print(str(100))
print(ord("A"))
print(hex(255))
print(oct(8))
```

**Output**

``` text
25
5.0
100
65
0xff
0o10
```

Invalid conversion error de sakta hai:

``` python
# int("hello")  # ValueError
```

**Useful nuance:** - `int(3.9)` returns `3` (fraction part truncate hota
hai; round nahi karta). - `bool("")` is `False`, aur `bool("False")` is
`True`, kyunki non-empty string truthy hoti hai. - `int("25")` valid
hai, lekin `int("25.5")` direct valid nahi; pehle `float("25.5")` karna
padta hai.

# 14. Input in Python

`input()` keyboard/user se value accept karta hai. **`input()` ka
returned value hamesha string hota hai.**

## 14.1 String input

``` python
name = input("Enter your name: ")
print("Hello,", name)
print(type(name))
```

Example interaction:

``` text
Enter your name: Aman
Hello, Aman
<class 'str'>
```

## 14.2 Integer input

``` python
age = int(input("Enter your age: "))
print("Next year you will be", age + 1)
```

Example:

``` text
Enter your age: 18
Next year you will be 19
```

## 14.3 Float input

``` python
price = float(input("Enter the price: "))
print("Price with 10% tax:", price * 1.1)
```

Example:

``` text
Enter the price: 50
Price with 10% tax: 55.00000000000001
```

Floating-point calculations mein tiny precision differences normal hain.
Display ke liye `round(value, 2)` use kar sakte hain:

``` python
price = 50.0
print(round(price * 1.1, 2))
```

Output: `55.0`

**OA tip:** Input integer hona chahiye to `int(input())`; decimal allow
karna hai to `float(input())`. Agar input invalid ho sakta hai, real
application mein `try/except ValueError` se handle karein.

# 15. Lecture Practice Questions --- Answers Included

## Q1. Do numbers input karke sum print karo.

``` python
a = int(input("Enter first number: "))
b = int(input("Enter second number: "))
print("Sum =", a + b)
```

Example:

``` text
Enter first number: 12
Enter second number: 8
Sum = 20
```

## Q2. Square ki side input karke area print karo.

Formula: `area = side × side`

``` python
side = float(input("Enter side of square: "))
area = side * side  # or side ** 2
print("Area =", area)
```

Example:

``` text
Enter side of square: 5
Area = 25.0
```

## Q3. Do floating-point numbers input karke average print karo.

Formula: `average = (a + b) / 2`

``` python
a = float(input("Enter first number: "))
b = float(input("Enter second number: "))
average = (a + b) / 2
print("Average =", average)
```

Example:

``` text
Enter first number: 4.5
Enter second number: 7.5
Average = 6.0
```

## Q4. Do integers `a` aur `b` input karo. `True` print karo agar `a >= b`, warna `False`.

``` python
a = int(input("Enter a: "))
b = int(input("Enter b: "))
print(a >= b)
```

Example:

``` text
Enter a: 10
Enter b: 7
True
```

Reason: `a >= b` khud Boolean result deta hai, isliye direct print kar
sakte hain.

------------------------------------------------------------------------

# 16. Interview Questions with Answers

## Fundamentals

### Q1. Programming kya hai?

**Answer:** Computer ko task perform karne ke liye instructions dena
programming hai. Instructions Python jaisi language mein likhi ja sakti
hain.

### Q2. Python kisne develop ki?

**Answer:** Guido van Rossum.

### Q3. Python ke main features kya hain?

**Answer:** Readable syntax, high-level nature, open source,
portability, aur wide ecosystem.

### Q4. Compiler aur interpreter mein difference?

**Answer:** Compiler traditionally poore program ko translate karke run
karne ke liye output banata hai. Interpreter code/instructions ko
execute karte hue translate/process karta hai. Actual language
implementations mein hybrid steps bhi ho sakte hain.

### Q5. `print()` kya karta hai?

**Answer:** Output display karta hai.

### Q6. Variable kya hai?

**Answer:** Value ko refer karne ke liye use kiya gaya name, jaise
`age = 20`.

### Q7. `=` aur `==` mein difference?

**Answer:** `=` assignment hai; `==` equality comparison hai.

### Q8. Identifier ke rules batao.

**Answer:** Letters, digits aur underscore allowed; digit se start nahi;
spaces/special symbols nahi; keyword nahi; case-sensitive.

### Q9. `age` aur `Age` same hain?

**Answer:** Nahi, Python case-sensitive hai.

### Q10. Basic built-in types kaun se hain?

**Answer:** `int`, `float`, `str`, `bool`, `NoneType`; lecture mein
`complex` bhi example ke roop mein diya gaya hai.

### Q11. `type()` ka use?

**Answer:** Object/value ka type inspect karne ke liye.

### Q12. Keyword kya hota hai?

**Answer:** Reserved word jiska Python mein special meaning hai, jaise
`if`, `for`, `class`.

### Q13. Comments kyun use karte hain?

**Answer:** Code ko explain/document karne ke liye. `#` single-line
comment start karta hai.

### Q14. `input()` ka return type kya hota hai?

**Answer:** `str`, chahe user digits type kare. Numeric operation ke
liye cast karna padta hai.

### Q15. Implicit aur explicit conversion mein difference?

**Answer:** Implicit conversion Python automatically karta hai; explicit
conversion programmer `int()`, `float()` etc. se karta hai.

### Q16. `int("hello")` ka kya hoga?

**Answer:** `ValueError`, kyunki string valid integer representation
nahi hai.

### Q17. `10 / 3` aur `10 // 3` mein difference?

**Answer:** `/` true division deta hai (`3.333...`); `//` floor division
deta hai (`3` for positive operands).

### Q18. `%` operator kya karta hai?

**Answer:** Remainder deta hai. Example: `10 % 3 == 1`.

### Q19. `**` ka use?

**Answer:** Exponent/power. Example: `2 ** 3 == 8`.

### Q20. `and`, `or`, `not` kya karte hain?

**Answer:** Boolean conditions combine ya reverse karte hain. `and` ko
dono conditions true chahiye; `or` ko kam-se-kam ek; `not` result
reverse karta hai.

### Q21. Kya `"2" + 2` valid hai?

**Answer:** Nahi, `str` aur `int` ko directly add karne par `TypeError`
aata hai. Convert karna hoga, context ke hisaab se `int("2") + 2` ya
`str(2) + "2"`.

### Q22. `bool("False")` ka result kya hai?

**Answer:** `True`, kyunki string empty nahi hai. String ke andar likha
word `"False"` Boolean `False` nahi hota.

### Q23. `None` kya represent karta hai?

**Answer:** Value absent/none ko represent karta hai. Iska type
`NoneType` hai.

### Q24. Kya variable ka type change ho sakta hai?

**Answer:** Haan, Python dynamically typed hai. Example: `x = 5` ke baad
`x = "hello"` assign kar sakte hain.

### Q25. `sum` ko variable name banana kyun avoid karte hain?

**Answer:** `sum()` Python ka built-in function hai. `sum = a + b`
likhne se current scope mein built-in function ka naam shadow ho jata
hai. `total` behtar naam hai.

------------------------------------------------------------------------

# 17. Python Coding Practice for OA (Online Assessment)

Neeche additional OA-style questions hain. Har question ke saath
solution diya hai. Pehle khud solve karne ki koshish karein, phir answer
dekhein.

## OA 1. Even ya Odd

**Question:** Integer input lo aur print karo number even hai ya odd.

``` python
n = int(input())
if n % 2 == 0:
    print("Even")
else:
    print("Odd")
```

**Example:** Input `7` → Output `Odd`\
**Logic:** Even number ko 2 se divide karne par remainder `0` hota hai.\
**Complexity:** Time `O(1)`, space `O(1)`.

## OA 2. Do numbers mein maximum

``` python
a = int(input())
b = int(input())
if a >= b:
    print(a)
else:
    print(b)
```

**Example:** `12`, `8` → `12`\
**Complexity:** `O(1)` time, `O(1)` extra space.

## OA 3. Teen numbers mein maximum

``` python
a = int(input())
b = int(input())
c = int(input())
print(max(a, b, c))
```

**Example:** `4`, `17`, `9` → `17`\
**Note:** `max()` built-in function hai. Interview mein bina `max()` ke
logic explain karne ko bhi kaha ja sakta hai.

## OA 4. Positive, negative ya zero

``` python
n = float(input())
if n > 0:
    print("Positive")
elif n < 0:
    print("Negative")
else:
    print("Zero")
```

## OA 5. 1 se N tak sum

**Question:** `N` input lo aur `1 + 2 + ... + N` calculate karo.

``` python
n = int(input())
total = n * (n + 1) // 2
print(total)
```

**Example:** Input `5` → Output `15`\
**Complexity:** `O(1)` time, `O(1)` space.\
**Assumption:** `N >= 0`. Agar question negative input allow karta hai
to constraints clarify karein.

## OA 6. Number ke digits ka sum

``` python
n = abs(int(input()))
total = 0

while n > 0:
    total += n % 10
    n //= 10

print(total)
```

**Example:** Input `482` → Output `14`\
**Complexity:** `O(d)` time, jahan `d` digits ki count hai; `O(1)` extra
space.\
**Note:** Is version mein input `0` ho to output `0` aata hai.

## OA 7. Number reverse karo

``` python
n = int(input())
sign = -1 if n < 0 else 1
n = abs(n)
reversed_num = 0

while n > 0:
    digit = n % 10
    reversed_num = reversed_num * 10 + digit
    n //= 10

print(sign * reversed_num)
```

**Example:** Input `1234` → Output `4321`\
**Note:** Reverse karne par leading zeroes numeric output mein preserve
nahi hote. Agar task string reverse karne ka hai to string slicing use
ho sakti hai.

## OA 8. Palindrome string

**Question:** Check karo string forward aur backward same hai ya nahi.

``` python
s = input().strip()
if s == s[::-1]:
    print("Palindrome")
else:
    print("Not Palindrome")
```

**Example:** `madam` → `Palindrome`\
**Complexity:** `O(n)` time aur slicing ki wajah se `O(n)` extra space.

## OA 9. Factorial

**Question:** Non-negative integer `n` ka factorial calculate karo.
`0! = 1`.

``` python
n = int(input())
if n < 0:
    print("Invalid input")
else:
    result = 1
    for i in range(2, n + 1):
        result *= i
    print(result)
```

**Example:** Input `5` → Output `120`\
**Complexity:** `O(n)` time, `O(1)` extra space (integer size growth ko
ignore karke).

## OA 10. Multiplication table

``` python
n = int(input())
for i in range(1, 11):
    print(f"{n} x {i} = {n * i}")
```

**Example:** Input `3` → `3 x 1 = 3` se `3 x 10 = 30` tak.

## OA 11. Count vowels

``` python
s = input().lower()
count = 0

for ch in s:
    if ch in "aeiou":
        count += 1

print(count)
```

**Example:** Input `Python Basics` → Output `3`\
**Logic:** Har character ko vowels `a, e, i, o, u` se check karte hain.\
**Complexity:** `O(n)` time, `O(1)` extra space.

## OA 12. List ke elements ka sum

``` python
numbers = list(map(int, input().split()))
print(sum(numbers))
```

**Example:** Input `1 2 3 4` → Output `10`\
**Concepts:** `input()`, `split()`, `map()`, `list()`, `sum()`.\
**Note:** Yeh one-line input format tab use karein jab OA statement
space-separated list expect karta ho.

## OA 13. List mein largest element

``` python
numbers = list(map(int, input().split()))
if not numbers:
    print("Empty list")
else:
    largest = numbers[0]
    for value in numbers[1:]:
        if value > largest:
            largest = value
    print(largest)
```

**Concept:** List traversal aur comparison.\
**Complexity:** `O(n)` time. Non-empty list assumption ke saath simple
version mein pehle element ko initial maximum le sakte hain.

## OA 14. FizzBuzz

**Question:** 1 se `N` tak numbers print karo. 3 se divisible par
`Fizz`, 5 se divisible par `Buzz`, dono se divisible par `FizzBuzz`.

``` python
n = int(input())
for i in range(1, n + 1):
    if i % 3 == 0 and i % 5 == 0:
        print("FizzBuzz")
    elif i % 3 == 0:
        print("Fizz")
    elif i % 5 == 0:
        print("Buzz")
    else:
        print(i)
```

**Interview point:** Pehle combined condition check karni chahiye, warna
15 jaise number ko sirf `Fizz` ya `Buzz` print kar sakte hain.

## OA 15. Simple calculator

``` python
a = float(input())
operator = input().strip()
b = float(input())

if operator == "+":
    print(a + b)
elif operator == "-":
    print(a - b)
elif operator == "*":
    print(a * b)
elif operator == "/":
    if b == 0:
        print("Cannot divide by zero")
    else:
        print(a / b)
else:
    print("Invalid operator")
```

**Concepts:** Input, type casting, conditions, operators, error case.

------------------------------------------------------------------------

# 18. Short Output-Based Interview Practice

Pehle output khud predict karein, phir answer check karein.

## Question 1

``` python
x = 5
x = x + 2
print(x)
```

**Answer:** `7` --- assignment ke baad `x` update hota hai.

## Question 2

``` python
print(10 % 4)
print(2 ** 3)
```

**Answer:**

``` text
2
8
```

## Question 3

``` python
print(type(input()))
```

**Answer:** `<class 'str'>` --- input digits ho tab bhi `input()` string
return karta hai.

## Question 4

``` python
print(5 > 3 and 2 < 1)
```

**Answer:** `False` --- `and` mein dono conditions true honi chahiye.

## Question 5

``` python
print(int(3.9))
```

**Answer:** `3` --- `int()` fractional part truncate karta hai.

## Question 6

``` python
print(bool(""))
print(bool("0"))
```

**Answer:**

``` text
False
True
```

Empty string falsey hai; non-empty string truthy hai.

## Question 7

``` python
a = 10
b = 3
print(a / b)
print(a // b)
```

**Answer:** Pehle `3.3333333333333335`, phir `3`.

## Question 8

``` python
print("Py", "thon")
```

**Answer:** `Py thon` --- `print()` default mein arguments ke beech
space deta hai.

## Question 9

``` python
x = None
print(type(x))
```

**Answer:** `<class 'NoneType'>`.

## Question 10

``` python
print(10 >= 10)
```

**Answer:** `True` --- greater-than-or-equal condition true hai.

------------------------------------------------------------------------

# 19. Quick Revision Sheet

-   `print(value)` → output display karta hai.
-   `input()` → hamesha string return karta hai.
-   `int(input())` → integer input; `float(input())` → decimal input.
-   `=` → assignment; `==` → equality comparison.
-   `type(x)` → type check.
-   `#` → single-line comment.
-   `int`, `float`, `str`, `bool`, `NoneType`, `complex` → common types.
-   Identifier digit se start nahi hota; spaces aur hyphens allowed
    nahi.
-   `+ - * / % **` → arithmetic operators.
-   `== != > < >= <=` → comparison operators.
-   `+= -= *= /= %= **=` → augmented assignment operators.
-   `and`, `or`, `not` → logical operators.
-   Implicit conversion automatic hota hai; explicit conversion `int()`,
    `float()`, `str()` se.
-   `int("hello")` → `ValueError`.
-   `10 / 3` → true division; `10 // 3` → floor division.
-   `10 % 3` → `1`; `2 ** 3` → `8`.
-   Python case-sensitive hai: `age` aur `Age` different hain.
-   Variable ke naam ke liye built-in function names, jaise `sum`, ko
    shadow karne se bachein.

# 20. OA Attempt Karne ki Strategy

1.  **Question carefully padho:** Input format, output format aur
    constraints note karo.
2.  **Examples manually trace karo:** Har variable ki current value
    likho.
3.  **Edge cases check karo:** `0`, negative number, equal values, empty
    input/list, invalid input---jo constraints ke andar ho.
4.  **Input type sahi choose karo:** `int` vs `float` vs `str`.
5.  **Output exact rakho:** Online judge ko extra prompts jaise
    `"Enter number:"` kabhi-kabhi reject ho sakte hain. OA mein
    statement agar raw input bataye, to aksar `input()` bina prompt use
    karein.
6.  **Boundary conditions:** `>=` aur `>` ka difference check karo;
    loops ke start/end values verify karo.
7.  **Complexity explain karo:** `O(1)`, `O(n)` jaise time/space
    complexity ka basic idea develop karo.
8.  **Code dry-run karo:** Ek normal example aur ek edge case se logic
    test karo.

# 21. Practice Checklist

-   [ ] `print()` aur `input()` use kar sakta/sakti hoon.
-   [ ] Variables aur valid identifiers likh sakta/sakti hoon.
-   [ ] `int`, `float`, `str`, `bool`, `None` identify kar sakta/sakti
    hoon.
-   [ ] Arithmetic, comparison, assignment aur logical operators
    samajhta/samajhti hoon.
-   [ ] Type conversion errors explain kar sakta/sakti hoon.
-   [ ] Sum, square area aur average programs bina notes ke likh
    sakta/sakti hoon.
-   [ ] Even/odd, maximum, digit sum, reverse aur factorial solve kar
    sakta/sakti hoon.
-   [ ] Code ka output manually trace kar sakta/sakti hoon.
-   [ ] OA ke exact input/output format ka dhyan rakhta/rakhti hoon.

------------------------------------------------------------------------

**End of Lecture 1 Notes**

*Source boundary:* Sections 1--15 preserve and explain the uploaded
lecture's topics/examples. Sections 16--21 add interview/OA practice and
a few clarifications for study; these additions are not claimed to be
part of the original PDF.
