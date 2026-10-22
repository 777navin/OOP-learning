# Python Notes — Lecture 5: Loops
## Hinglish Study Notes | Interview Practice | OA Preparation

> **Source:** College lecture notes, Lecture 5 (11 pages), topic: Python Loops.  
> **Language:** Hinglish (English keywords + Hindi explanation).  
> Is file mein lecture ke concepts, examples aur practice questions ko preserve kiya gaya hai. Interview/OA section mein extra practice questions aur answers clearly add kiye gaye hain.

---

## Contents
1. [Loops in Python](#1-loops-in-python)
2. [`while` Loop](#2-while-loop)
3. [Lecture Practice: `while`](#3-lecture-practice-while)
4. [`break` and `continue`](#4-break-and-continue)
5. [`for` Loop](#5-for-loop)
6. [`for-else`](#6-for-else)
7. [Lecture Practice: `for`](#7-lecture-practice-for)
8. [`range()`](#8-range)
9. [Lecture Practice: `for` and `range()`](#9-lecture-practice-for-and-range)
10. [`pass` Statement](#10-pass-statement)
11. [Sum and Factorial Practice](#11-sum-and-factorial-practice)
12. [Quick Revision Table](#12-quick-revision-table)
13. [Interview Questions with Answers](#13-interview-questions-with-answers)
14. [OA Practice Questions with Solutions](#14-oa-practice-questions-with-solutions)
15. [Extra Practice: Solve Yourself](#15-extra-practice-solve-yourself)
16. [Common Mistakes](#16-common-mistakes)
17. [Revision Checklist](#17-revision-checklist)

---

## 1. Loops in Python

**Loop** ka use instructions ko baar-baar repeat karne ke liye hota hai. Python mein do main loops hote hain:

- `while`
- `for`

Jab tak kisi condition ke true rehne ya sequence ke elements khatam hone tak kaam repeat karna ho, loop useful hota hai.

## 2. `while` Loop

`while` loop tab tak chalta hai jab tak uski condition `True` hoti hai.

### Syntax

```python
while condition:
    # some work
```

### Example 1: `"hello"` ko 5 times print karna

```python
count = 1

while count <= 5:
    print("hello")
    count += 1
```

**Output**
```text
hello
hello
hello
hello
hello
```

**Samjho:** `count` 1 se start hota hai. Har iteration ke baad `count += 1` usko 1 se increase karta hai. Jab `count` 6 ho jata hai, condition false hoti hai aur loop stop ho jata hai.

### Example 2: Numbers 1 se 5 tak print karna

```python
i = 1

while i <= 5:
    print(i)
    i += 1
```

**Output**
```text
1
2
3
4
5
```

### Iterator kya hota hai?

`i` ya `count` jaise variable ko yahan **iterator/counter** keh sakte hain. Har round mein update hota hai aur aakhir condition ko `False` bana deta hai.

### Infinite loop

Agar condition true rahe aur iterator update hi na ho, loop kabhi end nahi hoga.

```python
i = 1

while i <= 5:
    print(i)  # i kabhi increase nahi hota: infinite loop!
```

VS Code ya terminal mein infinite loop ko stop karne ke liye **Ctrl + C** press kar sakte ho.

> **OA tip:** `while` loop likhte waqt teen cheezein check karo: initialization, condition, update.

---

## 3. Lecture Practice: `while`

### Q1. Numbers 1 se 100 tak print karo

```python
i = 1

while i <= 100:
    print(i)
    i += 1
```

**Output:** `1, 2, 3, ... 100`

### Q2. Numbers 100 se 1 tak print karo

```python
i = 100

while i >= 1:
    print(i)
    i -= 1
```

**Output:** `100, 99, 98, ... 1`

### Q3. Number `n` ka multiplication table print karo

```python
n = int(input("Enter a number: "))

i = 1
while i <= 10:
    print(n, "x", i, "=", n * i)
    i += 1
```

**Example input:** `5`

**Output**
```text
5 x 1 = 5
5 x 2 = 10
5 x 3 = 15
...
5 x 10 = 50
```

### Q4. List ke elements loop se print karo

```python
nums = [1, 4, 9, 16, 25, 36, 49, 64, 81, 100]

idx = 0
while idx < len(nums):
    print(nums[idx])
    idx += 1
```

**Explanation:** List indexing `0` se start hoti hai. `len(nums)` list ki length deta hai. Valid index `0` se `len(nums) - 1` tak hota hai.

### Q5. Tuple mein `x` search karo

```python
nums = (1, 4, 9, 16, 25, 36, 49, 64, 81, 100)
x = 36

idx = 0
while idx < len(nums):
    if nums[idx] == x:
        print("Found at index", idx)
    idx += 1
```

**Output**
```text
Found at index 5
```

Is version mein match milne ke baad bhi loop aage check karta hai. Agar sirf first match chahiye, `break` use kar sakte hain.

---

## 4. `break` and `continue`

### `break`

`break` loop ko turant terminate kar deta hai.

```python
nums = (1, 4, 9, 16, 25, 36, 49, 64, 81, 100)
x = 36

idx = 0
while idx < len(nums):
    if nums[idx] == x:
        print("Found at index", idx)
        break
    idx += 1

print("End of search")
```

**Output**
```text
Found at index 5
End of search
```

### `continue`

`continue` current iteration ka remaining code skip karta hai aur next iteration par chala jata hai.

**1 se 10 tak numbers print karo, lekin multiples of 3 skip karo:**

```python
i = 0

while i < 10:
    i += 1
    if i % 3 == 0:
        continue
    print(i)
```

**Output**
```text
1
2
4
5
7
8
10
```

**Important:** `while` loop mein `continue` se pehle counter update karna ya kisi tarah progress guarantee karna zaroori hai. Agar update skip ho gaya, loop stuck ho sakta hai.

---

## 5. `for` Loop

`for` loop sequence ke har item par sequentially iterate karta hai—jaise list, string ya tuple.

### Syntax

```python
for element in sequence:
    # some work
```

### List example

```python
nums = [1, 2, 3]

for el in nums:
    print(el)
```

**Output**
```text
1
2
3
```

### String ke characters par loop

```python
for ch in "Python":
    print(ch)
```

**Output**
```text
P
y
t
h
o
n
```

**Hinglish explanation:** Har iteration mein `ch` string ka next character hold karta hai.

---

## 6. `for-else`

Python mein loop ke saath `else` bhi use ho sakta hai.

**Rule:** `else` tab run hota hai jab loop normally complete ho. Agar loop `break` se stop hua, to `else` run nahi hota.

### Normal completion

```python
nums = [1, 2, 3]

for el in nums:
    print(el)
else:
    print("END")
```

**Output**
```text
1
2
3
END
```

### `break` ke saath

```python
nums = [1, 2, 3]

for el in nums:
    if el == 2:
        break
    print(el)
else:
    print("END")
```

**Output**
```text
1
```

`el == 2` hone par `break` chalta hai, isliye `else` block skip hota hai.

### Search mein `for-else` ka use

```python
nums = (1, 4, 9, 16, 25, 36, 49, 64, 81, 100)
x = 49

idx = 0
for num in nums:
    if num == x:
        print("Found at index", idx)
        break
    idx += 1
else:
    print("Not found")
```

**Output**
```text
Found at index 6
```

Agar value nahi milti aur loop naturally finish ho jata hai, `Not found` print hoga.

---

## 7. Lecture Practice: `for`

### Q1. List ke elements print karo

```python
nums = [1, 4, 9, 16, 25, 36, 49, 64, 81, 100]

for num in nums:
    print(num)
```

**Output:** `1, 4, 9, ... 100`

### Q2. Tuple mein `x` search karo

```python
nums = (1, 4, 9, 16, 25, 36, 49, 64, 81, 100)
x = 49

idx = 0
for num in nums:
    if num == x:
        print("Found at index", idx)
        break
    idx += 1
else:
    print("Not found")
```

**Output**
```text
Found at index 6
```

---

## 8. `range()`

`range()` numbers ki sequence provide karta hai. Stop value include nahi hoti.

### Syntax

```python
range(start, stop, step)
```

- `start`: sequence kahan se shuru hogi; default `0`.
- `stop`: sequence is value se pehle rukegi; **stop included nahi hota**.
- `step`: kitne ka jump hoga; default `1`.

### Example 1: `range(5)`

```python
for el in range(5):
    print(el)
```

**Output:** `0 1 2 3 4`

### Example 2: `range(1, 5)`

```python
for el in range(1, 5):
    print(el)
```

**Output:** `1 2 3 4`

### Example 3: `range(1, 10, 2)`

```python
for el in range(1, 10, 2):
    print(el)
```

**Output:** `1 3 5 7 9`

### Countdown

```python
for i in range(100, 0, -1):
    print(i)
```

Negative step se countdown hota hai. `0` stop hai, isliye output `1` tak aata hai.

---

## 9. Lecture Practice: `for` and `range()`

### Q1. 1 se 100 tak print karo

```python
for i in range(1, 101):
    print(i)
```

### Q2. 100 se 1 tak print karo

```python
for i in range(100, 0, -1):
    print(i)
```

### Q3. Multiplication table

```python
n = int(input("Enter a number: "))

for i in range(1, 11):
    print(n, "x", i, "=", n * i)
```

**Example input:** `7`

**Output**
```text
7 x 1 = 7
7 x 2 = 14
...
7 x 10 = 70
```

---

## 10. `pass` Statement

`pass` ek **null statement** hai—ye kuch nahi karta. Jab future mein code likhna ho lekin abhi block empty rakhna ho, tab placeholder ke roop mein use hota hai. Python empty loop/block allow nahi karta.

```python
for el in range(10):
    pass  # code baad mein likhenge

print("Program continues")
```

**Output**
```text
Program continues
```

Lecture note ke mutabik `pass` exception handling mein bhi use hota hai, jo aage padhaya jayega.

---

## 11. Sum and Factorial Practice

### Q1. First `n` natural numbers ka sum (`while`)

```python
n = int(input("Enter n: "))

total = 0
i = 1

while i <= n:
    total += i
    i += 1

print("Sum =", total)
```

**Input:** `5`  
**Output:** `Sum = 15`

**Dry run for `n = 5`:**

| `i` | `total` before add | `total` after add |
|---:|---:|---:|
| 1 | 0 | 1 |
| 2 | 1 | 3 |
| 3 | 3 | 6 |
| 4 | 6 | 10 |
| 5 | 10 | 15 |

### Q2. Factorial of `n` (`for`)

Factorial: \(n! = 1 \times 2 \times 3 \times \cdots \times n\), aur convention ke according `0! = 1`.

```python
n = int(input("Enter n: "))

fact = 1
for i in range(1, n + 1):
    fact *= i

print("Factorial =", fact)
```

**Input:** `5`  
**Output:** `Factorial = 120`

Calculation: `1 × 2 × 3 × 4 × 5 = 120`.

> **Note:** Basic lecture code non-negative `n` assume karta hai. Production/interview code mein negative input ko validate karna chahiye.

---

## 12. Quick Revision Table

| Feature | Meaning | Key point |
|---|---|---|
| `while` | Condition true hone tak repeat | Initialization, condition, update |
| `for` | Sequence ke items traverse karna | List/string/tuple/range |
| `break` | Loop turant stop | First match par useful |
| `continue` | Current iteration skip | `while` mein update miss mat karo |
| `range(stop)` | `0` se `stop - 1` | Stop exclusive |
| `range(start, stop)` | Start se `stop - 1` | Step default `1` |
| `range(start, stop, step)` | Custom increment/decrement | Negative step countdown |
| `for-else` | Normal completion par `else` | `break` hua to `else` nahi |
| `pass` | No-op placeholder | Empty block ke liye |

### Loop choose kaise karein?

- **`for` use karo:** Jab list/string/tuple ke har item par jaana ho ya known range mein iteration karna ho.
- **`while` use karo:** Jab repeat karna condition par depend kare aur iteration count pehle se fixed na ho.
- Dono loops se bahut se tasks solve ho sakte hain; readable code choose karo.

---

## 13. Interview Questions with Answers

### Q1. Loop kya hota hai?
**Answer:** Loop instructions ko repeat karta hai. Python mein `while` condition-based aur `for` sequence-based iteration ke liye commonly use hota hai.

### Q2. `for` aur `while` mein difference?
**Answer:** `for` sequence/range ke items traverse karne mein convenient hai. `while` tab tak run karta hai jab tak condition true hai; counter/update manually manage karna pad sakta hai.

### Q3. Infinite loop kya hai?
**Answer:** Aisa loop jo terminate nahi hota, kyunki condition kabhi false nahi hoti ya exit condition tak progress nahi hoti.

### Q4. `break` vs `continue`?
**Answer:** `break` poora loop stop karta hai. `continue` sirf current iteration ka remaining code skip karta hai.

### Q5. `range(1, 5)` kya produce karta hai?
**Answer:** `1, 2, 3, 4`; stop value `5` include nahi hoti.

### Q6. `range(5)` ka output?
**Answer:** `0, 1, 2, 3, 4`.

### Q7. `range(10, 0, -2)` kya produce karega?
**Answer:** `10, 8, 6, 4, 2`.

### Q8. Python mein loop ka `else` kab execute hota hai?
**Answer:** Jab loop normally finish hota hai. `break` se exit hone par `else` skip hota hai.

### Q9. `pass` aur `continue` mein difference?
**Answer:** `pass` kuch nahi karta aur execution aage badhta hai. `continue` current iteration ke baaki statements skip karke next iteration shuru karta hai.

### Q10. `while` loop mein counter update kyun zaroori ho sakta hai?
**Answer:** Counter condition ko eventually false banata hai. Update na hone par infinite loop ho sakta hai.

### Q11. `len(nums)` kya deta hai?
**Answer:** Sequence mein total items ki count.

### Q12. Python list indexing kahan se start hoti hai?
**Answer:** Index `0` se.

### Q13. `for ch in "Python"` mein `ch` kya hoga?
**Answer:** Har iteration mein string ka ek character.

### Q14. Factorial ka base case?
**Answer:** `0! = 1` aur `1! = 1`. Isliye factorial accumulator `1` se initialize hota hai.

### Q15. Loop ki time complexity kaise estimate karte hain?
**Answer:** Agar `n` items ek baar visit hue to usually `O(n)`. Fixed 10 iterations ho to `O(1)` with respect to input size. Nested loops ka cost generally iterations ke product par depend karta hai.

---

## 14. OA Practice Questions with Solutions

Ye additional OA-style questions lecture ke loop concepts par based hain. Har question ke saath approach, code aur complexity di gayi hai.

### OA Q1. Sum of digits

**Problem:** Ek non-negative integer `n` diya hai. Uske digits ka sum return/print karo.

**Example:** `n = 583` → `16`

```python
n = int(input())
n = abs(n)
total = 0

while n > 0:
    total += n % 10
    n //= 10

print(total)
```

**Approach:** `% 10` last digit deta hai; `// 10` last digit remove karta hai.  
**Complexity:** Time `O(d)`, where `d` digits ki count hai; auxiliary space `O(1)`.  
**Edge case:** `n = 0` ke liye output `0`.

### OA Q2. Count even and odd numbers

**Problem:** List mein even aur odd numbers count karo.

```python
nums = list(map(int, input().split()))
even = 0
odd = 0

for x in nums:
    if x % 2 == 0:
        even += 1
    else:
        odd += 1

print("Even =", even)
print("Odd =", odd)
```

**Example input:** `1 2 3 4 6`  
**Output:** `Even = 3`, `Odd = 2`  
**Complexity:** Time `O(n)`, extra space `O(1)` apart from input storage.

### OA Q3. Reverse a number

**Problem:** Integer ke digits reverse karo.

```python
n = int(input())
sign = -1 if n < 0 else 1
n = abs(n)
rev = 0

while n > 0:
    digit = n % 10
    rev = rev * 10 + digit
    n //= 10

print(sign * rev)
```

**Example:** `1234` → `4321`  
**Complexity:** Time `O(d)`, extra space `O(1)`.  
**Note:** Leading zeroes numeric output mein preserve nahi hote.

### OA Q4. Palindrome number check

**Problem:** Check karo ki number reverse karne par same rehta hai ya nahi.

```python
n = int(input())

if n < 0:
    print("Not Palindrome")
else:
    original = n
    rev = 0

    while n > 0:
        rev = rev * 10 + n % 10
        n //= 10

    if original == rev:
        print("Palindrome")
    else:
        print("Not Palindrome")
```

**Example:** `121` → `Palindrome`; `123` → `Not Palindrome`.  
**Complexity:** Time `O(d)`, extra space `O(1)`.

### OA Q5. Find maximum without `max()`

**Problem:** Non-empty list mein largest element find karo.

```python
nums = list(map(int, input().split()))
largest = nums[0]

for x in nums[1:]:
    if x > largest:
        largest = x

print(largest)
```

**Example:** `-3 8 2 5` → `8`  
**Complexity:** Time `O(n)`, extra space `O(1)` excluding input/list slicing. For strict `O(1)` auxiliary space without slicing, use an index loop.

### OA Q6. Count occurrences of target

**Problem:** List mein target kitni baar aata hai?

```python
nums = list(map(int, input().split()))
target = int(input())
count = 0

for x in nums:
    if x == target:
        count += 1

print(count)
```

**Example:** list `1 2 2 3 2`, target `2` → `3`  
**Complexity:** Time `O(n)`, extra space `O(1)` excluding input.

### OA Q7. Multiplication table

**Problem:** `n` ka table 1 se 10 tak print karo.

```python
n = int(input())

for i in range(1, 11):
    print(f"{n} x {i} = {n * i}")
```

**Complexity:** 10 iterations, input size ke respect mein `O(1)`.

### OA Q8. First number divisible by both 7 and 5

**Problem:** `1` se `n` tak first number find karo jo 5 aur 7 dono se divisible ho. Nahi mile to `-1`.

```python
n = int(input())
answer = -1

for i in range(1, n + 1):
    if i % 5 == 0 and i % 7 == 0:
        answer = i
        break

print(answer)
```

**Example:** `n = 100` → `35`  
**Complexity:** Worst-case time `O(n)`, extra space `O(1)`.

### OA Q9. Count vowels in a string

```python
s = input().lower()
count = 0

for ch in s:
    if ch in "aeiou":
        count += 1

print(count)
```

**Example:** `OpenAI` → `4`  
**Complexity:** Time `O(n)`, extra space `O(1)` for fixed vowel set.

### OA Q10. Print a right triangle pattern

**Input:** `n = 4`

**Output**
```text
*
**
***
****
```

```python
n = int(input())

for i in range(1, n + 1):
    for j in range(i):
        print("*", end="")
    print()
```

**Complexity:** Time `O(n^2)` because total stars `1 + 2 + ... + n`; auxiliary space `O(1)`.

---

## 15. Extra Practice: Solve Yourself

Pehle khud attempt karo. Neeche answer key ke short hints hain; code solutions section 14 ke patterns se derive karne ki koshish karo.

1. `1` se `n` tak all numbers ka sum.
2. `n` ka factorial.
3. `1` se `n` tak even numbers print karo.
4. `1` se `n` tak odd numbers ka sum.
5. Number mein digits count karo.
6. Number ke digits ka product find karo.
7. Number Armstrong hai ya nahi, check karo.
8. Number prime hai ya nahi, check karo.
9. Fibonacci series ke first `n` terms print karo.
10. List ka minimum element find karo.
11. List ke elements ka sum aur average find karo.
12. List mein target ka first index find karo; absent ho to `-1`.
13. String ko loop se reverse karo.
14. String palindrome hai ya nahi, check karo.
15. Multiples of `k` ko `1` se `n` tak print karo.
16. `1` se `n` tak 3 aur 5 dono se divisible numbers print karo.
17. Loop se duplicate count karo (target ki frequency).
18. Nested loops se `n × n` star square print karo.
19. `for-else` use karke list mein target search karo.
20. `while` aur `for` se same problem solve karo.

### Short hint / answer key

1. Running total: `total += i`.
2. Product accumulator `fact = 1`.
3. `range(2, n + 1, 2)` ya condition `i % 2 == 0`.
4. Odd condition: `i % 2 != 0`.
5. Repeated `n //= 10`; `0` ko separately handle karo.
6. Har step par `product *= n % 10`.
7. Har digit ka `digit ** number_of_digits` sum original ke equal check karo.
8. Divisors `2` se `sqrt(n)` tak check karna sufficient hai.
9. `a, b = 0, 1`; update `a, b = b, a + b`.
10. Initial value first element rakho.
11. Running sum; average = sum / number of elements (empty list handle karo).
12. Index loop + `break`, ya `for-else`.
13. Reverse string accumulator ya slicing `s[::-1]` (loop practice ke liye accumulator use karo).
14. Original aur reversed string compare karo.
15. `range(k, n + 1, k)` for positive `k`.
16. `i % 3 == 0 and i % 5 == 0`.
17. Counter ko match par increment karo.
18. Outer loop rows, inner loop columns.
19. Match par `break`; `else` mein not found.
20. Pehle counter/condition identify karo, phir loop choose karo.

---

## 16. Common Mistakes

1. **`range()` stop inclusive samajhna:** `range(1, 5)` mein `5` nahi aata.
2. **Counter update bhoolna:** `while` infinite ho sakta hai.
3. **Off-by-one error:** `1` se `n` tak print karne ke liye `range(1, n + 1)`.
4. **Index out of range:** Last valid list index `len(nums) - 1` hai.
5. **`continue` se pehle update miss karna:** `while` mein stuck ho sakte ho.
6. **`break` aur `continue` confuse karna:** Ek loop end karta hai, doosra current iteration skip.
7. **Factorial ko 0 se initialize karna:** Product accumulator `1` se start karo.
8. **Empty list:** `nums[0]` access karne se pehle ensure karo list empty nahi hai.
9. **Negative input:** Factorial/sum-of-digits jaise tasks mein constraints clarify/validate karo.
10. **Nested loop complexity:** `n × n` iteration generally `O(n^2)` hoti hai.

---

## 17. Revision Checklist

- [ ] `while` syntax aur counter update explain kar sakta/sakti hoon.
- [ ] Infinite loop identify aur stop kar sakta/sakti hoon.
- [ ] List/tuple indexing aur `len()` use kar sakta/sakti hoon.
- [ ] `for` se list, tuple aur string traverse kar sakta/sakti hoon.
- [ ] `break`, `continue`, `pass` ka difference explain kar sakta/sakti hoon.
- [ ] `for-else` ka behaviour predict kar sakta/sakti hoon.
- [ ] `range(start, stop, step)` ke outputs manually nikal sakta/sakti hoon.
- [ ] Sum aur factorial ke dry runs kar sakta/sakti hoon.
- [ ] Basic loop OA questions solve kar sakta/sakti hoon.
- [ ] Time aur auxiliary-space complexity estimate kar sakta/sakti hoon.

---

## Study Plan (3 sessions)

**Session 1 — Basics (30–45 min):** `while`, iterator, infinite loop, 1–100, countdown, multiplication table.

**Session 2 — Control flow (30–45 min):** `break`, `continue`, `for`, `for-else`, `range()`, `pass`. Har code ka output predict karo.

**Session 3 — Interview/OA (45–60 min):** Sum, factorial, digit questions, palindrome, frequency, max/min, vowels, patterns. Har problem ko pehle brute-force loop se solve karo aur complexity likho.

> **Final advice:** Code ko sirf read mat karo. VS Code mein type karo, input change karo, dry run likho, phir bina notes dekhe dobara solve karo.
