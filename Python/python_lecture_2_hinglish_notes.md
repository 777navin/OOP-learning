# Python Notes --- Lecture 2

## Strings & Conditional Statements

### Hinglish Study Notes + Interview Q&A + Python OA Practice

**Source:** Uploaded *Python Notes (Lecture 2)* PDF.\
**Language:** Hinglish --- English technical terms ke saath Hindi
explanation.\
**How to use:** Is file ko VS Code mein `.md` ke roop mein open karein;
`Ctrl + Shift + V` se Markdown preview dekhein.

> **Content note:** Sections 1--7 mein source lecture ke topics, code
> aur sample outputs preserve kiye gaye hain. Baad ke interview/OA
> sections additional practice material hain, original PDF ka hissa hone
> ka claim nahi karte.

------------------------------------------------------------------------

## Table of Contents

1.  What is a String?
2.  Basic String Operations
3.  Indexing
4.  Slicing and Negative Indexing
5.  String Functions / Methods
6.  Lecture Practice: Strings
7.  Conditional Statements (`if-elif-else`)
8.  Grade Calculator Example
9.  Lecture Practice: Conditionals
10. Interview Questions with Answers
11. OA Coding Practice with Solutions
12. Output-Based Questions
13. Quick Revision
14. Practice Checklist

------------------------------------------------------------------------

# 1. What is a String?

**String** ek data type hai jo characters ki sequence store karta hai.
Python mein strings single quotes, double quotes ya triple quotes ke
andar likhi ja sakti hain.

``` python
str1 = "Apna College"
str2 = 'Python'
str3 = """This is a
multi-line string"""

print(str1)
print(str2)
print(str3)
```

**Output**

``` text
Apna College
Python
This is a
multi-line string
```

-   `"Apna College"` double quotes mein string hai.
-   `'Python'` single quotes mein string hai.
-   Triple quotes multi-line string likhne mein useful hain.
-   String text, names, messages aur user input represent karne ke kaam
    aati hai.

# 2. Basic String Operations

## 2.1 Concatenation

**Concatenation** ka matlab strings ko join karna. Python mein `+`
operator use kar sakte hain.

``` python
first = "hello"
second = "world"

print(first + second)
print(first + " " + second)
```

**Output**

``` text
helloworld
hello world
```

Dhyan dein: `"hello" + "world"` ke beech automatically space nahi aata.
Space chahiye to `" "` add karein.

## 2.2 Length of a String

`len()` function string mein characters ki count return karta hai.
Spaces bhi count hote hain.

``` python
name = "Apna College"
print(len(name))
```

**Output**

``` text
12
```

Reason: `Apna` ke 4 characters + 1 space + `College` ke 7 characters =
12.

# 3. Indexing

String ke har character ka ek position number hota hai jise **index**
kehte hain. Python mein positive indexing `0` se start hoti hai.

String: `"Apna_College"`

  Character     A   p   n   a   \_   C   o   l   l   e    g    e
  ----------- --- --- --- --- ---- --- --- --- --- --- ---- ----
  Index         0   1   2   3    4   5   6   7   8   9   10   11

``` python
s = "Apna_College"

print(s[0])
print(s[1])
print(s[5])
```

**Output**

``` text
A
p
C
```

## Strings are Immutable

Python strings **immutable** hoti hain. Matlab banne ke baad string ke
kisi character ko index ke through directly replace nahi kar sakte.

``` python
s = "Apna_College"
# s[0] = "B"  # Error: string item assign nahi kar sakte
```

Error:

``` text
TypeError: 'str' object does not support item assignment
```

Agar modified string chahiye, to new string create karein:

``` python
s = "Apna_College"
s = "B" + s[1:]
print(s)
```

Output:

``` text
Bpna_College
```

# 4. Slicing

**Slicing** string ka ek part nikalne ke liye use hoti hai.

Syntax:

``` python
string[starting_idx:ending_idx]
```

**Important:** Ending index include nahi hota. Slice `start` se shuru
hoti hai aur `end - 1` tak jaati hai.

``` python
s = "ApnaCollege"

print(s[1:4])  # index 1, 2, 3
print(s[:4])   # same as s[0:4]
print(s[4:])   # index 4 se end tak
```

**Output**

``` text
pna
Apna
College
```

Rules: - Starting index omit ho to start `0` se hota hai. - Ending index
omit ho to string ke end tak jaata hai. - `s[a:b]` mein `b` include nahi
hota.

## 4.1 Negative Indexing

Negative indexes string ke end se count karte hain. Last character ka
index `-1` hota hai.

String: `"Apple"`

  Character           A    p    p    l    e
  ---------------- ---- ---- ---- ---- ----
  Positive index      0    1    2    3    4
  Negative index     -5   -4   -3   -2   -1

``` python
s = "Apple"

print(s[-1])
print(s[-3:-1])  # index -3 aur -2
print(s[-3:])
```

**Output**

``` text
e
pl
ple
```

# 5. String Functions / Methods

String methods ko dot (`.`) notation se call karte hain.

  -----------------------------------------------------------------------
  Method                              Meaning
  ----------------------------------- -----------------------------------
  `s.endswith("er.")`                 `True` return karta hai agar string
                                      given substring se end hoti ho

  `s.capitalize()`                    First character ko capitalize karta
                                      hai aur baaki characters ko
                                      lowercase karta hai

  `s.replace(old, new)`               `old` ke occurrences ko `new` se
                                      replace karke new string return
                                      karta hai

  `s.find(word)`                      First occurrence ka index deta hai;
                                      na mile to `-1`

  `s.count("am")`                     Given substring ke non-overlapping
                                      occurrences count karta hai
  -----------------------------------------------------------------------

Example:

``` python
s = "i am a coder."

print(s.endswith("er."))
print(s.capitalize())
print(s.replace("coder", "student"))
print(s.find("a"))
print(s.count("am"))
```

**Output**

``` text
True
I am a coder.
i am a student.
2
1
```

**Important:** Strings immutable hoti hain, isliye ye methods original
string ko in-place modify nahi karti. Ye result return karti hain. Agar
result save karna ho:

``` python
s = "i am a coder."
s = s.replace("coder", "student")
print(s)
```

## Extra useful string methods

Ye additional revision topics hain:

``` python
text = "  Python Basics  "

print(text.lower())       # lowercase
print(text.upper())       # uppercase
print(text.strip())       # beginning/end spaces remove
print(text.split())       # words ki list
print("-".join(["a", "b", "c"]))  # a-b-c
```

Expected output:

``` text
  python basics  
  PYTHON BASICS  
Python Basics
['Python', 'Basics']
a-b-c
```

Note: `strip()` sirf start/end whitespace remove karta hai, beech ke
spaces nahi.

# 6. Lecture Practice --- Strings

## Q1. User ka first name input karo aur uski length print karo.

``` python
name = input("Enter your first name: ")
print("Length of your name is", len(name))
```

Example:

``` text
Enter your first name: Shradha
Length of your name is 7
```

## Q2. String mein `$` character kitni baar aata hai?

``` python
text = "Hi $ I am $ learning Python $"
print("Occurrences of $ :", text.count("$"))
```

Output:

``` text
Occurrences of $ : 3
```

------------------------------------------------------------------------

# 7. Conditional Statements --- `if`, `elif`, `else`

Conditional statements program ko decisions lene dete hain. Condition
`True` ya `False` hoti hai; uske according code execute hota hai.

General syntax:

``` python
if condition1:
    statement1
elif condition2:
    statement2
else:
    statementN
```

Rules: - Condition ke baad colon (`:`) lagta hai. - Indentation (usually
4 spaces) batati hai kaunsa statement kis block ka part hai. - Pehla
true condition block execute hota hai; uske baad ke blocks skip hote
hain. - `elif` aur `else` optional hain. - Multiple `elif` blocks ho
sakte hain. - `else` ke saath condition nahi likhte.

## 7.1 Traffic Light Example

``` python
light = "yellow"

if light == "red":
    print("Stop")
elif light == "yellow":
    print("Look")
elif light == "green":
    print("Go")
else:
    print("Light is broken")
```

Output:

``` text
Look
```

Explanation: `light == "yellow"` true hai, isliye `Look` print hota hai.

# 8. Example --- Marks ke Basis par Grade

Lecture table:

  Marks condition      Grade
  -------------------- -------
  `marks >= 90`        A
  `90 > marks >= 80`   B
  `80 > marks >= 70`   C
  `marks < 70`         D

Code:

``` python
marks = int(input("Enter marks: "))

if marks >= 90:
    grade = "A"
elif marks >= 80:
    grade = "B"
elif marks >= 70:
    grade = "C"
else:
    grade = "D"

print("Grade:", grade)
```

Example:

``` text
Enter marks: 84
Grade: B
```

**Why does `elif marks >= 80` work without `marks < 90`?** Agar marks
`90` ya zyada hote, to pehla `if` already execute ho chuka hota. `elif`
tabhi check hota hai jab previous condition false ho.

Note: Ye lecture ka grading rule hai; actual college grading scheme alag
ho sakti hai.

# 9. Lecture Practice --- Conditionals

## Q1. Number even hai ya odd?

``` python
num = int(input("Enter a number: "))

if num % 2 == 0:
    print("Even")
else:
    print("Odd")
```

Example:

``` text
Enter a number: 7
Odd
```

Logic: Even number ko `2` se divide karne par remainder `0` hota hai.

## Q2. User ke diye hue 3 numbers mein greatest find karo.

``` python
a = int(input("Enter first number: "))
b = int(input("Enter second number: "))
c = int(input("Enter third number: "))

if a >= b and a >= c:
    print("Greatest is", a)
elif b >= c:
    print("Greatest is", b)
else:
    print("Greatest is", c)
```

Example:

``` text
Enter first number: 12
Enter second number: 45
Enter third number: 30
Greatest is 45
```

Logic: 1. Check karo `a`, `b` aur `c` dono se bada ya equal hai. 2. Nahi
to check karo `b >= c`. 3. Otherwise `c` greatest hai. 4. `>=` use karne
se equal values bhi correctly handle hoti hain.

## Q3. Number 7 ka multiple hai ya nahi?

``` python
num = int(input("Enter a number: "))

if num % 7 == 0:
    print(num, "is a multiple of 7")
else:
    print(num, "is not a multiple of 7")
```

Example:

``` text
Enter a number: 49
49 is a multiple of 7
```

Logic: Agar `num % 7 == 0`, to number 7 se exactly divisible hai.

------------------------------------------------------------------------

# 10. Interview Questions with Answers

## Strings

### Q1. Python mein string kya hai?

**Answer:** String characters ki sequence hoti hai, jaise `"Python"` ya
`'Hello'`.

### Q2. String kaise create karte hain?

**Answer:** Single quotes, double quotes ya triple quotes se, jaise
`s = "Hello"`.

### Q3. String concatenation kya hai?

**Answer:** Do strings ko join karna. Example: `"Py" + "thon"` gives
`"Python"`.

### Q4. `len()` kya return karta hai?

**Answer:** String mein characters ki count, spaces samet. Example:
`len("A B")` gives `3`.

### Q5. String indexing kahan se start hoti hai?

**Answer:** Positive indexing `0` se; negative indexing `-1` se last
character ko refer karti hai.

### Q6. `s = "Python"` mein `s[0]` kya hai?

**Answer:** `"P"`.

### Q7. String immutable hone ka kya matlab?

**Answer:** Existing string ke character ko index assignment se change
nahi kar sakte. New string create kar sakte hain.

### Q8. `s[1:4]` ka end index include hota hai?

**Answer:** Nahi. Start include hota hai aur end exclude hota hai.

### Q9. `"Apple"[-1]` kya return karega?

**Answer:** `"e"`.

### Q10. `find()` aur `count()` mein difference?

**Answer:** `find()` first occurrence ka index deta hai (not found ho to
`-1`); `count()` occurrences ki count deta hai.

### Q11. `replace()` original string modify karta hai?

**Answer:** Nahi. Ye replacement ke saath new string return karta hai.

### Q12. `capitalize()` kya karta hai?

**Answer:** First character uppercase aur remaining characters lowercase
karta hai.

### Q13. `"hello" + "world"` ka result?

**Answer:** `"helloworld"`; beech mein space automatically nahi aata.

### Q14. `len("Apna College")` kya hai?

**Answer:** `12`, kyunki space bhi count hota hai.

### Q15. `$` ki occurrence kaise count karoge?

**Answer:** `text.count("$")`.

## Conditionals

### Q16. Conditional statement kyun use hota hai?

**Answer:** Condition ke result ke according program ka decision/flow
control karne ke liye.

### Q17. `if`, `elif`, `else` mein difference?

**Answer:** `if` first condition check karta hai; `elif` previous
conditions false hone par next condition check karta hai; `else` tab run
hota hai jab koi prior condition true na ho.

### Q18. Python mein colon aur indentation kyun important hain?

**Answer:** Colon block start indicate karta hai; indentation define
karti hai ki kaunsa code block ke andar hai.

### Q19. Even/odd ka logic?

**Answer:** `n % 2 == 0` ho to even; otherwise odd.

### Q20. Multiple of 7 kaise check karoge?

**Answer:** `n % 7 == 0`.

### Q21. Teen numbers ka maximum kaise find karoge?

**Answer:** `if`/`elif` comparisons se ya built-in `max(a, b, c)` se.
Interview mein dono approaches explain karne ke liye ready rahein.

### Q22. Grade conditions ko descending order mein kyun rakhte hain?

**Answer:** Pehle highest threshold check karne se high marks lower
grade mein incorrectly classify nahi hote.

### Q23. `if x = 5:` valid hai?

**Answer:** Nahi. Assignment `=` ko condition ki tarah use nahi kar
sakte. Equality check `if x == 5:` hota hai.

### Q24. Kya `elif` zaroori hai?

**Answer:** Nahi. Simple decision ke liye `if/else` enough ho sakta hai;
multiple mutually exclusive conditions ke liye `elif` useful hai.

### Q25. Agar 3 numbers equal hon to greatest program kya karega?

**Answer:** Given lecture code mein first condition `a >= b and a >= c`
true ho jaayegi aur `a` print hoga. Value greatest hi rahegi, chahe ties
hon.

------------------------------------------------------------------------

# 11. OA Coding Practice with Solutions

Ye additional practice questions hain jo strings aur conditionals ke
fundamentals build karte hain. OA platform ke instructions ke mutabik
input/output format adjust karein.

## OA 1. String reverse karo

``` python
s = input()
print(s[::-1])
```

Example: `python` → `nohtyp`\
**Concept:** Slicing.\
**Complexity:** `O(n)` time aur `O(n)` additional space.

## OA 2. Palindrome string check karo

``` python
s = input().strip()
if s == s[::-1]:
    print("Palindrome")
else:
    print("Not Palindrome")
```

Example: `madam` → `Palindrome`\
**Note:** Ye exact case-sensitive comparison hai; `Madam` ko lowercase
mein convert karna ho to `s = input().strip().lower()` use karein.

## OA 3. Vowels count karo

``` python
s = input().lower()
count = 0

for ch in s:
    if ch in "aeiou":
        count += 1

print(count)
```

Example: `Python` → `1`\
**Concept:** Loop, string membership, counter.

## OA 4. Uppercase aur lowercase conversion

``` python
s = input()
print(s.upper())
print(s.lower())
```

Example: `PyThOn`:

``` text
PYTHON
python
```

## OA 5. Spaces remove karo

``` python
s = input()
print(s.replace(" ", ""))
```

Example: `hello world` → `helloworld`\
**Note:** Ye normal space characters remove karta hai. Tabs/newlines
samet saare whitespace remove karne ke liye alag logic chahiye.

## OA 6. Character ki occurrence count karo

Input: pehli line text, doosri line target character.

``` python
text = input()
target = input()
print(text.count(target))
```

Example:

``` text
banana
a
3
```

Assumption: Target input ek character hai.

## OA 7. First name ki length

``` python
name = input().strip()
print(len(name))
```

Example: `Shradha` → `7`.

## OA 8. Do strings equal hain ya nahi?

``` python
a = input()
b = input()

if a == b:
    print("Equal")
else:
    print("Not Equal")
```

Comparison case-sensitive hai: `Python` aur `python` different hain.

## OA 9. Number divisible by 5 and 11

``` python
n = int(input())

if n % 5 == 0 and n % 11 == 0:
    print("Yes")
else:
    print("No")
```

Example: `55` → `Yes`.

## OA 10. Leap year check

``` python
year = int(input())

if year % 400 == 0:
    print("Leap Year")
elif year % 100 == 0:
    print("Not Leap Year")
elif year % 4 == 0:
    print("Leap Year")
else:
    print("Not Leap Year")
```

Rule: 400 se divisible year leap year hai; otherwise 100 se divisible
year leap year nahi; otherwise 4 se divisible year leap year hai.

## OA 11. Marks se grade

``` python
marks = int(input())

if marks >= 90:
    print("A")
elif marks >= 80:
    print("B")
elif marks >= 70:
    print("C")
else:
    print("D")
```

Example: `84` → `B`.\
Assumption: Marks valid range mein diye gaye hain; source lecture range
validation cover nahi karta.

## OA 12. Three numbers ka greatest

``` python
a = int(input())
b = int(input())
c = int(input())

if a >= b and a >= c:
    print(a)
elif b >= c:
    print(b)
else:
    print(c)
```

Example: `12`, `45`, `30` → `45`.

## OA 13. Multiple of 7

``` python
n = int(input())

if n % 7 == 0:
    print("Multiple of 7")
else:
    print("Not a multiple of 7")
```

Example: `49` → `Multiple of 7`.

## OA 14. Character vowel hai ya consonant?

``` python
ch = input().strip().lower()

if len(ch) != 1 or not ch.isalpha():
    print("Invalid input")
elif ch in "aeiou":
    print("Vowel")
else:
    print("Consonant")
```

**Note:** `isalpha()` Unicode letters bhi accept kar sakta hai;
English-only alphabet enforce karna ho to `"a" <= ch <= "z"` condition
use kar sakte hain.

## OA 15. Simple calculator with conditions

``` python
a = float(input())
op = input().strip()
b = float(input())

if op == "+":
    print(a + b)
elif op == "-":
    print(a - b)
elif op == "*":
    print(a * b)
elif op == "/":
    if b == 0:
        print("Cannot divide by zero")
    else:
        print(a / b)
else:
    print("Invalid operator")
```

Concepts: input, type casting, comparisons, `if-elif-else`,
division-by-zero case.

------------------------------------------------------------------------

# 12. Output-Based Questions

Pehle output predict karein; phir answer dekhein.

## Q1

``` python
s = "Python"
print(s[0])
print(s[-1])
```

**Answer**

``` text
P
n
```

## Q2

``` python
s = "ApnaCollege"
print(s[1:4])
print(s[:4])
print(s[4:])
```

**Answer**

``` text
pna
Apna
College
```

## Q3

``` python
s = "hello"
print(len(s))
print(s.count("l"))
```

**Answer**

``` text
5
2
```

## Q4

``` python
s = "i am a coder."
print(s.find("z"))
```

**Answer:** `-1`, kyunki `z` nahi milta.

## Q5

``` python
s = "Python"
s.replace("P", "J")
print(s)
```

**Answer:** `Python` --- returned string assign nahi ki gayi, original
unchanged hai.

## Q6

``` python
x = 7
if x % 2 == 0:
    print("Even")
else:
    print("Odd")
```

**Answer:** `Odd`.

## Q7

``` python
marks = 90
if marks >= 90:
    print("A")
elif marks >= 80:
    print("B")
else:
    print("C")
```

**Answer:** `A` --- first true block execute hota hai.

## Q8

``` python
print("abc"[::-1])
```

**Answer:** `cba`.

## Q9

``` python
print("banana".count("an"))
```

**Answer:** `2` --- `count()` non-overlapping occurrences count karta
hai.

## Q10

``` python
a, b, c = 5, 5, 3
if a >= b and a >= c:
    print(a)
elif b >= c:
    print(b)
else:
    print(c)
```

**Answer:** `5`.

## Q11

``` python
light = "blue"
if light == "red":
    print("Stop")
elif light == "yellow":
    print("Look")
elif light == "green":
    print("Go")
else:
    print("Light is broken")
```

**Answer:** `Light is broken`.

## Q12

``` python
print("Hello".capitalize())
print("HELLO".capitalize())
```

**Answer**

``` text
Hello
Hello
```

------------------------------------------------------------------------

# 13. Quick Revision Sheet

## Strings

-   String characters ki sequence hai.
-   Single, double aur triple quotes supported hain.
-   `+` strings concatenate karta hai.
-   `len(s)` length return karta hai; spaces count hote hain.
-   Positive index `0` se, negative index `-1` se start hota hai.
-   Slice `s[start:end]` mein `end` exclude hota hai.
-   Strings immutable hoti hain.
-   `endswith()`, `capitalize()`, `replace()`, `find()`, `count()` key
    methods hain.
-   `find()` not found par `-1` return karta hai.
-   String methods generally new result return karti hain.

## Conditionals

-   `if` condition check karta hai.
-   `elif` additional conditions check karta hai.
-   `else` tab run hota hai jab pehle koi condition true nahi.
-   Condition ke baad colon (`:`) zaroori hai.
-   Indentation Python syntax ka part hai.
-   Even: `n % 2 == 0`.
-   Multiple of 7: `n % 7 == 0`.
-   Teen values ka maximum comparisons se find kar sakte hain.
-   Grade conditions highest threshold se lowest threshold ki taraf
    rakhein.

## OA tips

-   Online judge mein exact input/output format follow karein.
-   Prompt text jaise `Enter number:` tabhi print karein jab problem
    statement maange.
-   Boundary values aur ties test karein.
-   String slicing aur negative indexes dry-run karein.
-   Conditions ka order check karein.
-   Constraints ke hisaab se edge cases handle karein.

# 14. Practice Checklist

-   [ ] Single/double/triple quotes se strings create kar sakta/sakti
    hoon.
-   [ ] Concatenation aur `len()` samajhta/samajhti hoon.
-   [ ] Positive aur negative indexing kar sakta/sakti hoon.
-   [ ] Slicing ke start/end rules explain kar sakta/sakti hoon.
-   [ ] String immutability explain kar sakta/sakti hoon.
-   [ ] `endswith`, `capitalize`, `replace`, `find`, `count` use kar
    sakta/sakti hoon.
-   [ ] `if`, `elif`, `else` aur indentation sahi likh sakta/sakti hoon.
-   [ ] Even/odd, greatest-of-three, multiple-of-seven solve kar
    sakta/sakti hoon.
-   [ ] Grade calculator code bina notes ke likh sakta/sakti hoon.
-   [ ] Output-based questions manually trace kar sakta/sakti hoon.

------------------------------------------------------------------------

**End of Lecture 2 Notes**

*Source boundary: Original lecture ke saare visible topics, examples,
practice questions aur sample outputs included hain. Interview
questions, extra methods, OA problems aur additional clarifications
supplementary learning material hain.*
