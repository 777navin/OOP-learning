# Python Notes — Lecture 3
## Lists and Tuples | Hinglish Study Notes

> **Source:** College PDF, *Python Notes (Lecture 3)*, 7 pages.  
> Is file mein original lecture ke topics, code examples, outputs, aur practice questions preserve kiye gaye hain. Interview/OA preparation ke liye extra questions aur explanations clearly **Extra Practice** ke naam se add kiye gaye hain.

---

## Table of Contents
1. [Lists in Python](#1-lists-in-python)
2. [List Slicing](#2-list-slicing)
3. [List Methods](#3-list-methods)
4. [Tuples in Python](#4-tuples-in-python)
5. [Tuple Methods](#5-tuple-methods)
6. [List vs Tuple](#6-list-vs-tuple)
7. [Lecture Practice Questions with Answers](#7-lecture-practice-questions-with-answers)
8. [Interview Questions and Answers](#8-interview-questions-and-answers)
9. [OA / Coding Practice](#9-oa--coding-practice)
10. [Python Revision Checklist](#10-python-revision-checklist)

---

## 1. Lists in Python

### Definition
Python mein **list** ek built-in data type hai jo multiple values ko ek collection mein store karti hai. List ko square brackets `[]` ke andar likhte hain. Ek list mein different data types, jaise integer, float, string, etc. store ho sakte hain.

```python
marks = [87, 64, 33, 95, 76]
student = ["Karan", 85, "Delhi"]

print(marks)
print(student)
print(marks[0])       # First element
print(student[2])
```

**Output**
```text
[87, 64, 33, 95, 76]
['Karan', 85, 'Delhi']
87
Delhi
```

### Indexing
- Indexing `0` se start hoti hai.
- `marks[0]` first element deta hai.
- Negative indexing mein `-1` last element, `-2` second-last element hota hai.

### Lists are Mutable
List **mutable** hoti hai, yaani create karne ke baad uske elements update kar sakte hain.

```python
student = ["Karan", 85, "Delhi"]
student[0] = "Arjun"
print(student)
print(len(student))
```

**Output**
```text
['Arjun', 85, 'Delhi']
3
```

`len(student)` list mein total elements ki count return karta hai.

---

## 2. List Slicing

Slicing se list ka ek portion nikaal sakte hain.

### Syntax
```python
list_name[starting_idx : ending_idx]
```

**Important:** `ending_idx` include nahi hota. Slicing mein start included aur end excluded hota hai.

```python
marks = [87, 64, 33, 95, 76]

print(marks[1:4])
print(marks[:4])       # Same as marks[0:4]
print(marks[1:])       # Same as marks[1:len(marks)]
print(marks[-3:-1])    # Negative indexes
```

**Output**
```text
[64, 33, 95]
[87, 64, 33, 95]
[64, 33, 95, 76]
[33, 95]
```

### Quick slicing rules
- `nums[a:b]`: index `a` se `b-1` tak.
- `nums[:b]`: beginning se `b-1` tak.
- `nums[a:]`: index `a` se end tak.
- Negative indexes list ke end se count karte hain.

---

## 3. List Methods

List methods ko dot `.` ke saath call karte hain. Is lecture ke methods original list ko modify karte hain, except `copy()` which creates a copy.

| Method | Kaam |
|---|---|
| `nums.append(el)` | End mein ek element add karta hai |
| `nums.sort()` | Ascending order mein sort karta hai |
| `nums.sort(reverse=True)` | Descending order mein sort karta hai |
| `nums.reverse()` | Current order reverse karta hai, sort nahi karta |
| `nums.insert(idx, el)` | Given index par element insert karta hai |
| `nums.remove(el)` | Element ki first matching occurrence remove karta hai |
| `nums.pop(idx)` | Given index ka element remove karke return karta hai |
| `nums.copy()` | List ki shallow copy banata hai |

### 3.1 `append()`

```python
nums = [2, 1, 3]
nums.append(4)
print(nums)
```

Output:
```text
[2, 1, 3, 4]
```

### 3.2 `sort()`

```python
nums = [2, 1, 3]
nums.sort()
print(nums)
```

Output:
```text
[1, 2, 3]
```

Descending order:
```python
nums = [2, 1, 3]
nums.sort(reverse=True)
print(nums)
```

Output:
```text
[3, 2, 1]
```

### 3.3 `reverse()`

```python
nums = [2, 1, 3]
nums.reverse()
print(nums)
```

Output:
```text
[3, 1, 2]
```

**Interview point:** `sort()` values ko order ke according arrange karta hai, jabki `reverse()` existing order ko ulta karta hai.

### 3.4 `insert()`

```python
nums = [2, 1, 3]
nums.insert(1, 5)  # Index 1 par 5 insert hoga
print(nums)
```

Output:
```text
[2, 5, 1, 3]
```

### 3.5 `remove()`

```python
nums = [2, 1, 3, 1]
nums.remove(1)  # Sirf first occurrence remove hoti hai
print(nums)
```

Output:
```text
[2, 3, 1]
```

### 3.6 `pop()`

```python
nums = [2, 1, 3, 1]
nums.pop(2)  # Index 2 ka element remove hota hai
print(nums)
```

Output:
```text
[2, 1, 1]
```

`pop()` bina index ke call karoge, toh last element remove aur return hota hai:
```python
nums = [10, 20, 30]
removed = nums.pop()
print(removed)  # 30
print(nums)     # [10, 20]
```

### Important tip
Variable ka naam `list` mat rakho, kyunki isse Python ka built-in `list()` function shadow ho jayega. Better names: `nums`, `items`, `marks`.

---

## 4. Tuples in Python

### Definition
**Tuple** ek built-in data type hai jo values ka ordered, **immutable** sequence store karta hai. Tuple ko usually round brackets `()` mein likhte hain. Create karne ke baad tuple ke elements ko directly change nahi kar sakte.

```python
tup = (87, 64, 33, 95, 76)

print(tup[0])
print(tup[1:3])
print(len(tup))
```

Output:
```text
87
(64, 33)
5
```

### Tuple immutable hota hai

```python
tup = (87, 64, 33, 95, 76)
tup[0] = 43
```

Output/error:
```text
TypeError: 'tuple' object does not support item assignment
```

### Tuple create karna

```python
tup1 = ()       # Empty tuple
tup2 = (1,)     # Single-element tuple: comma required
tup3 = (1, 2, 3)

print(type(tup2))
print(type((1)))
```

Output:
```text
<class 'tuple'>
<class 'int'>
```

**Yaad rakho:** `(1,)` tuple hai, lekin `(1)` sirf integer expression hai. Single-element tuple ke liye comma zaroori hai.

---

## 5. Tuple Methods

Lecture mein do tuple methods cover kiye gaye hain:

| Method | Kaam |
|---|---|
| `tup.index(el)` | Element ki first occurrence ka index return karta hai |
| `tup.count(el)` | Element kitni baar aaya hai, count return karta hai |

```python
tup = (2, 1, 3, 1)

print(tup.index(1))
print(tup.count(1))
```

Output:
```text
1
2
```

Agar `index()` mein element present nahi hai, toh `ValueError` aata hai.

---

## 6. List vs Tuple

| Feature | List | Tuple |
|---|---|---|
| Syntax | Square brackets `[]` | Round brackets `()` commonly |
| Mutability | Mutable, elements change ho sakte hain | Immutable, elements directly change nahi hote |
| Methods in lecture | `append`, `sort`, `reverse`, `insert`, `remove`, `pop`, etc. | `index`, `count` |
| Slicing | Supported | Supported |
| Indexing | Supported | Supported |
| Example | `[1, 2, 3]` | `(1, 2, 3)` |
| Use case | Jab collection ko modify karna ho | Jab sequence fixed rakhna ho |

---

## 7. Lecture Practice Questions with Answers

### Q1. User ke 3 favourite movies input lo aur list mein store karo.

```python
movies = []

movies.append(input("Enter 1st movie: "))
movies.append(input("Enter 2nd movie: "))
movies.append(input("Enter 3rd movie: "))

print(movies)
```

Sample run:
```text
Enter 1st movie: 3 Idiots
Enter 2nd movie: Dangal
Enter 3rd movie: Inception
['3 Idiots', 'Dangal', 'Inception']
```

### Q2. Check karo ki list palindrome hai ya nahi.

Palindrome ka matlab: forward aur backward read karne par same sequence.

```python
nums = [1, 2, 3, 2, 1]

copy_nums = nums.copy()  # Original list safe rahegi
copy_nums.reverse()      # Copy ko reverse karo

if nums == copy_nums:
    print("Palindrome")
else:
    print("Not a palindrome")
```

Output:
```text
Palindrome
```

Alternative:
```python
nums = [1, 2, 3, 2, 1]
if nums == nums[::-1]:
    print("Palindrome")
else:
    print("Not a palindrome")
```

**Why `copy()`?** `reverse()` list ko in-place modify karta hai. Copy banane se original sequence preserve hota hai.

### Q3. Tuple mein `"A"` grade kitni baar hai, count karo.

```python
grades = ("C", "D", "A", "A", "B", "B", "A")
print("Students with A grade:", grades.count("A"))
```

Output:
```text
Students with A grade: 3
```

### Q4. Grades ko list mein store karke A se D tak sort karo.

```python
grades = ["C", "D", "A", "A", "B", "B", "A"]
grades.sort()
print(grades)
```

Output:
```text
['A', 'A', 'A', 'B', 'B', 'C', 'D']
```

---

## 8. Interview Questions and Answers

### Q1. Python list kya hai?
**Answer:** List ek ordered, mutable collection hai. Ismein duplicate values aur different data types ho sakte hain. Example: `items = [10, "Python", 10]`.

### Q2. Mutable ka meaning kya hai?
**Answer:** Object create hone ke baad uski value ya contents change kar sakte hain. List mutable hai.

### Q3. Tuple kya hai?
**Answer:** Tuple ek ordered sequence hai jiske elements ko directly reassign nahi kar sakte. Example: `point = (10, 20)`.

### Q4. List aur tuple mein main difference?
**Answer:** List mutable hoti hai aur `[]` use karti hai. Tuple immutable hota hai aur usually `()` use karta hai.

### Q5. List indexing kis number se start hoti hai?
**Answer:** `0` se. Last element ke liye `-1` use kar sakte hain.

### Q6. Slicing mein ending index include hota hai?
**Answer:** Nahi. `items[1:4]` indices `1, 2, 3` deta hai, index `4` include nahi hota.

### Q7. `append()` aur `insert()` mein difference?
**Answer:** `append(x)` element ko end mein add karta hai. `insert(i, x)` element ko specified index par insert karta hai.

### Q8. `remove()` aur `pop()` mein difference?
**Answer:** `remove(value)` first matching value delete karta hai. `pop(index)` specified index ka item delete karke return karta hai. `pop()` without index last item remove karta hai.

### Q9. `sort()` aur `reverse()` mein difference?
**Answer:** `sort()` values ko ascending/descending order mein arrange karta hai. `reverse()` current order ko ulta karta hai.

### Q10. `count()` kya karta hai?
**Answer:** Given value ki total occurrences return karta hai.

### Q11. `index()` kya karta hai?
**Answer:** Given value ki first occurrence ka index return karta hai. Value missing ho toh `ValueError` aata hai.

### Q12. Single-element tuple kaise banate hain?
**Answer:** Trailing comma use karke: `x = (5,)`. `x = (5)` integer hai.

### Q13. `len()` kya return karta hai?
**Answer:** List ya tuple mein total elements ki count.

### Q14. `copy()` kyun use karte hain?
**Answer:** List ki separate shallow copy banane ke liye. Isse simple flat list par changes/reverse karte waqt original list preserve ki ja sakti hai.

### Q15. Kya tuple ke andar list ho sakti hai?
**Answer:** Haan. Example: `t = ([1, 2], 3)`. Tuple ke andar stored list mutable reh sakti hai, lekin tuple ke slots ko reassign nahi kar sakte.

### Q16. List mein duplicate elements allowed hain?
**Answer:** Haan. Example: `[1, 1, 2]`.

### Q17. `list` naam ka variable kyun avoid karna chahiye?
**Answer:** Ye built-in `list()` ko shadow kar sakta hai aur baad mein list conversion ya creation mein confusion/error ho sakta hai.

### Q18. Kya tuple ko slice kar sakte hain?
**Answer:** Haan. Example: `(10, 20, 30, 40)[1:3]` output `(20, 30)` deta hai.

---

## 9. OA / Coding Practice

Ye section lecture ke concepts ko Online Assessment (OA) aur coding-round style practice se connect karta hai. Ye extra practice questions hain, original PDF ka part nahi.

### Q1. List ka sum calculate karo
**Problem:** Integers ki list di hai. Saare elements ka sum print karo.

```python
nums = [10, 20, 30, 40]
total = 0

for num in nums:
    total += num

print(total)
```

Output:
```text
100
```

**Approach:** Har element par loop chalao aur running total update karo.  
**Time Complexity:** `O(n)`  
**Space Complexity:** `O(1)` extra space.

### Q2. Maximum element find karo without `max()`

```python
nums = [12, 7, 31, 4, 19]

largest = nums[0]
for num in nums[1:]:
    if num > largest:
        largest = num

print(largest)
```

Output:
```text
31
```

**OA tip:** Empty list ke case ko handle karna ho, toh pehle `if not nums:` check karo.

### Q3. Even numbers ki list banao

```python
nums = [1, 2, 3, 4, 5, 6, 8]
evens = []

for num in nums:
    if num % 2 == 0:
        evens.append(num)

print(evens)
```

Output:
```text
[2, 4, 6, 8]
```

### Q4. List mein target ki frequency count karo

```python
nums = [1, 2, 2, 3, 2, 4]
target = 2

count = 0
for num in nums:
    if num == target:
        count += 1

print(count)
```

Output:
```text
3
```

### Q5. Duplicates remove karo, order preserve karke

```python
nums = [3, 1, 3, 2, 1, 4]
unique = []

for num in nums:
    if num not in unique:
        unique.append(num)

print(unique)
```

Output:
```text
[3, 1, 2, 4]
```

**Complexity note:** `num not in unique` list membership check karta hai, isliye worst-case time `O(n^2)` ho sakta hai. Large input ke liye set-based approach useful hai, lekin order preserve karne ka dhyan rakho.

### Q6. Second-largest distinct number find karo

```python
nums = [10, 5, 8, 10, 7, 8]

unique_nums = sorted(set(nums))

if len(unique_nums) < 2:
    print("Second-largest distinct value does not exist")
else:
    print(unique_nums[-2])
```

Output:
```text
8
```

**Interview note:** `set()` duplicates remove karta hai. Sorting ki complexity `O(n log n)` hai. OA mein kabhi-kabhi sorting ke bina `O(n)` solution expected hota hai.

### Q7. List ko reverse karo without `reverse()`

```python
nums = [1, 2, 3, 4, 5]
reversed_nums = nums[::-1]
print(reversed_nums)
```

Output:
```text
[5, 4, 3, 2, 1]
```

### Q8. Do lists ke common elements find karo

```python
a = [1, 2, 3, 4]
b = [3, 4, 5, 6]

common = []
for item in a:
    if item in b and item not in common:
        common.append(item)

print(common)
```

Output:
```text
[3, 4]
```

### Q9. Palindrome check with function

```python
def is_palindrome(items):
    return items == items[::-1]

print(is_palindrome([1, 2, 3, 2, 1]))
print(is_palindrome([1, 2, 3]))
```

Output:
```text
True
False
```

### Q10. Rotate list right by one position

```python
nums = [1, 2, 3, 4, 5]

if nums:
    nums = [nums[-1]] + nums[:-1]

print(nums)
```

Output:
```text
[5, 1, 2, 3, 4]
```

### More OA questions to solve independently
1. List mein second-smallest distinct element find karo.
2. Zeroes ko end mein move karo while baaki elements ka order preserve ho.
3. Sorted list se duplicates remove karo.
4. Do sorted lists merge karo.
5. List ke elements ki frequency dictionary banao.
6. Pair find karo jinka sum target `k` ho.
7. List ko left rotate by `k` positions.
8. Check karo list sorted hai ya nahi.
9. Missing number find karo from `0` to `n`.
10. Tuple ke elements ka sum aur average calculate karo.
11. List mein positive, negative aur zero values count karo.
12. Consecutive duplicate values compress karo.
13. Nested list ko one-level flatten karo.
14. Do lists equal hain ya nahi, order ke saath check karo.
15. List ke unique elements print karo.

---

## 10. Python Revision Checklist

Lecture 3 ke liye interview/OA se pehle ye checklist complete karo:

- [ ] List syntax: `[]`
- [ ] Indexing: positive aur negative
- [ ] Mutable list elements update karna
- [ ] `len()` use karna
- [ ] Slicing: `[start:end]`, open-ended slices, negative indexes
- [ ] `append()`, `insert()`, `remove()`, `pop()`
- [ ] `sort()`, `sort(reverse=True)`, `reverse()`
- [ ] `copy()` aur original list ko preserve karna
- [ ] Tuple syntax: `()`
- [ ] Tuple immutability
- [ ] Single-element tuple mein comma: `(1,)`
- [ ] Tuple `index()` aur `count()`
- [ ] List vs tuple explain kar pana
- [ ] Palindrome program bina dekhe likhna
- [ ] OA practice mein sum, maximum, frequency, duplicates aur rotation solve karna

## Quick Memory Sheet

```python
nums = [3, 1, 2]

nums.append(4)          # End mein add
nums.insert(1, 9)       # Index 1 par add
nums.remove(3)          # Value 3 ki first occurrence remove
nums.pop()              # Last item remove + return
nums.sort()             # Ascending sort
nums.sort(reverse=True) # Descending sort
nums.reverse()          # Existing order reverse
copy_nums = nums.copy() # Shallow copy

tup = (2, 1, 3, 1)
tup.index(1)            # First occurrence index: 1
tup.count(1)            # Occurrences: 2
```

**Study strategy:** Pehle original lecture examples run karo, phir har code ko bina dekhe type karo, aur last mein OA questions ko timer laga kar solve karo. Python mein output predict karne ki practice bhi karo.
