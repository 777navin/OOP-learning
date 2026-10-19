# Python Notes — Lecture 4
## Dictionaries and Sets | Hinglish Notes + Interview + OA Practice

> **Source:** Uploaded college PDF, *Python Notes (Lecture 4)*, 7 pages.  
> Is file mein original lecture ke topics, code snippets, outputs aur 4 practice questions included hain. Interview/OA section mein extra questions clearly additional practice ke roop mein diye gaye hain.

---

## Table of Contents
1. [Dictionaries in Python](#1-dictionaries-in-python)
2. [Nested Dictionaries](#2-nested-dictionaries)
3. [Dictionary Methods](#3-dictionary-methods)
4. [Sets in Python](#4-sets-in-python)
5. [Set Methods](#5-set-methods)
6. [Lecture Practice Questions with Answers](#6-lecture-practice-questions-with-answers)
7. [Interview Questions and Answers](#7-interview-questions-and-answers)
8. [OA Coding Practice with Solutions](#8-oa-coding-practice-with-solutions)
9. [More Practice Questions](#9-more-practice-questions)
10. [Revision Checklist](#10-revision-checklist)

---

## 1. Dictionaries in Python

### Definition
Python dictionary data ko **key-value pairs** mein store karta hai. Dictionary ko curly brackets `{}` se define karte hain.

Important points:
- **Mutable:** items ko add, update aur remove kar sakte hain.
- **Unique keys:** duplicate key repeat hone par latest value purani value ko replace kar deti hai.
- **Values any type ki ho sakti hain:** string, number, list ya another dictionary.
- Dictionary ke values ko key se access karte hain.

```python
info = {
    "name": "shradha",
    "cgpa": 9.6,
    "marks": [98, 97, 95],
}

print(info["name"])
print(info["cgpa"])
print(info["marks"])
```

Output:
```text
shradha
9.6
[98, 97, 95]
```

### Value update karna aur new key add karna

`dict_name["key"] = value` se existing value update ya new key-value pair add hota hai.

```python
info = {"name": "shradha", "cgpa": 9.6}

info["cgpa"] = 9.8       # Existing value update
info["city"] = "Delhi"   # New key-value pair add
print(info)
```

Output:
```text
{'name': 'shradha', 'cgpa': 9.8, 'city': 'Delhi'}
```

**Tip:** Variable ka naam `dict` mat rakho, kyunki Python ka built-in `dict()` function shadow ho jayega.

---

## 2. Nested Dictionaries

Ek dictionary ke andar doosri dictionary ko value ke roop mein store kar sakte hain. Isse **nested dictionary** kehte hain.

```python
student = {
    "name": "shradha",
    "score": {
        "chem": 98,
        "phy": 97,
        "math": 95,
    },
}

print(student["score"])
print(student["score"]["math"])
```

Output:
```text
{'chem': 98, 'phy': 97, 'math': 95}
95
```

`student["score"]["math"]` ka meaning:
1. `student["score"]` se inner dictionary access karo.
2. Uske `"math"` key ki value access karo.

---

## 3. Dictionary Methods

| Method | Kaam |
|---|---|
| `d.keys()` | Saari keys return karta hai |
| `d.values()` | Saari values return karta hai |
| `d.items()` | `(key, value)` pairs deta hai |
| `d.get("key")` | Key ki value deta hai; missing key par default `None` |
| `d.update(new_dict)` | Dictionary mein multiple items add/update karta hai |

### `keys()`, `values()`, `items()`

```python
student = {"name": "shradha", "cgpa": 9.6}

print(student.keys())
print(student.values())
print(student.items())
print(list(student.keys()))  # Keys ko normal list mein convert karo
```

Output:
```text
dict_keys(['name', 'cgpa'])
dict_values(['shradha', 9.6])
dict_items([('name', 'shradha'), ('cgpa', 9.6)])
['name', 'cgpa']
```

Note: `keys()`, `values()` aur `items()` dictionary views return karte hain. `list(...)` se keys ko list mein convert kar sakte hain.

### `get()` aur missing keys

```python
student = {"name": "shradha", "cgpa": 9.6}

print(student.get("name"))
print(student.get("age"))       # Missing key: None
# print(student["age"])         # Missing key: KeyError
```

Output:
```text
shradha
None
```

`get()` ka benefit ye hai ki missing key par default `None` deta hai, jabki `student["age"]` `KeyError` raise karega.

Custom default bhi de sakte hain:
```python
print(student.get("age", 0))  # Output: 0
```

### `update()`

```python
student = {"name": "shradha", "cgpa": 9.6}
student.update({"city": "Delhi", "cgpa": 9.8})
print(student)
```

Output:
```text
{'name': 'shradha', 'cgpa': 9.8, 'city': 'Delhi'}
```

---

## 4. Sets in Python

### Definition
Set ek **unordered collection** hai jo unique elements store karta hai. Set ko curly brackets `{}` se likh sakte hain, provided usmein elements hon.

Important points:
- Duplicate elements automatically remove ho jaate hain.
- Set ke elements hashable hone chahiye, jaise numbers, strings aur tuples (agar tuple ke elements bhi hashable hon).
- List ko directly set ke element ke roop mein store nahi kar sakte.
- Set indexed nahi hota, isliye `nums[0]` supported nahi hai.
- Set mutable hota hai, yaani `add()` aur `remove()` se elements change kar sakte hain.

```python
nums = {1, 2, 3, 4}
set2 = {1, 2, 2, 2}  # Duplicate values ek hi baar rahengi

print(nums)
print(set2)
print(len(set2))
```

Output:
```text
{1, 2, 3, 4}
{1, 2}
2
```

**Note:** Set ka display order fixed nahi hota. Output mein elements ka order different ho sakta hai.

### Empty set vs empty dictionary

Empty set `set()` se banta hai. `{}` empty dictionary create karta hai.

```python
null_set = set()
print(type(null_set))
print(type({}))
```

Output:
```text
<class 'set'>
<class 'dict'>
```

---

## 5. Set Methods

| Method | Kaam |
|---|---|
| `s.add(el)` | Element add karta hai |
| `s.remove(el)` | Element remove karta hai; absent ho toh `KeyError` |
| `s.clear()` | Saare elements remove karke set empty karta hai |
| `s.pop()` | Set se ek arbitrary element remove karke return karta hai |
| `s.union(set2)` | Dono sets ke unique elements ka new set |
| `s.intersection(set2)` | Dono sets ke common elements ka new set |

### `add()`, duplicate add aur `remove()`

```python
nums = {1, 2, 3}

nums.add(4)
nums.add(2)  # 2 already present hai, set change nahi hoga
print(nums)

nums.remove(3)
print(nums)

nums.clear()
print(nums)
```

Output (set order vary kar sakta hai):
```text
{1, 2, 3, 4}
{1, 2, 4}
set()
```

### `union()` and `intersection()`

```python
set1 = {1, 2, 3}
set2 = {2, 3, 4}

print(set1.union(set2))
print(set1.intersection(set2))
```

Output:
```text
{1, 2, 3, 4}
{2, 3}
```

**OA tip:** Set membership checking average case mein list membership se generally faster hoti hai, isliye duplicates, unique values aur common elements ke problems mein sets useful hote hain.

---

## 6. Lecture Practice Questions with Answers

### Q1. Word meanings ko dictionary mein store karo

**Question:**  
- `table`: `"a piece of furniture"` aur `"list of facts & figures"`
- `cat`: `"a small animal"`

`table` ki do meanings hain, isliye uski value ek list hogi.

```python
dictionary = {
    "table": ["a piece of furniture", "list of facts & figures"],
    "cat": "a small animal",
}

print(dictionary)
```

Output:
```text
{'table': ['a piece of furniture', 'list of facts & figures'], 'cat': 'a small animal'}
```

### Q2. Unique subjects ke liye classrooms count karo

Subjects:
`"python", "java", "C++", "python", "javascript", "java", "python", "java", "C++", "C"`

Ek classroom per unique subject chahiye. Set duplicates remove kar dega.

```python
subjects = {
    "python", "java", "C++", "python", "javascript",
    "java", "python", "java", "C++", "C",
}

print("Classrooms needed:", len(subjects))
```

Output:
```text
Classrooms needed: 5
```

Unique subjects: Python, Java, C++, JavaScript, C.

### Q3. User se 3 subjects ke marks input lekar dictionary banao

```python
marks = {}

marks["phy"] = int(input("Enter phy marks: "))
marks["chem"] = int(input("Enter chem marks: "))
marks["math"] = int(input("Enter math marks: "))

print(marks)
```

Sample run:
```text
Enter phy marks: 95
Enter chem marks: 88
Enter math marks: 97
{'phy': 95, 'chem': 88, 'math': 97}
```

### Q4. Set mein `9` aur `9.0` ko separate values ke roop mein store karo

Python mein `9 == 9.0` true hota hai, aur dono ka hash bhi equal hota hai. Isliye normal set inhe ek hi element maanta hai.

```python
values = {9, 9.0}
print(values)
```

Output:
```text
{9}
```

Dono ko distinct record ke roop mein preserve karne ke liye type label add kar sakte hain:

```python
values = {("int", 9), ("float", 9.0)}
print(len(values))
```

Output:
```text
2
```

---

## 7. Interview Questions and Answers

### Q1. Python dictionary kya hai?
**Answer:** Dictionary mutable mapping hai jo key-value pairs store karti hai. Example: `student = {"name": "Asha", "marks": 90}`.

### Q2. Dictionary ki keys unique kyun hoti hain?
**Answer:** Ek key ek hi current value map karti hai. Same key dobara assign karne par uski value update ho jaati hai.

### Q3. Dictionary mutable hai?
**Answer:** Haan. Existing values update, new key add aur keys delete kar sakte hain.

### Q4. `d[key]` aur `d.get(key)` mein difference?
**Answer:** Missing key ke case mein `d[key]` `KeyError` raise karta hai. `d.get(key)` by default `None` return karta hai; custom default bhi de sakte hain.

### Q5. `keys()`, `values()` aur `items()` kya return karte hain?
**Answer:** Respectively keys, values, aur `(key, value)` pairs ke dictionary views.

### Q6. Nested dictionary kya hoti hai?
**Answer:** Jab dictionary ke andar kisi key ki value ek aur dictionary ho. Example: `student["score"]["math"]`.

### Q7. Kya dictionary mein list value ho sakti hai?
**Answer:** Haan. Example: `{"marks": [80, 90, 95]}`.

### Q8. Variable ka naam `dict` kyun avoid karna chahiye?
**Answer:** Ye built-in `dict()` function ko shadow kar deta hai.

### Q9. Python set kya hai?
**Answer:** Set unique, hashable elements ka unordered collection hai. Duplicate values store nahi hoti.

### Q10. Kya set indexed hota hai?
**Answer:** Nahi. `s[0]` valid nahi hai kyunki set indexing support nahi karta.

### Q11. Empty set kaise banate hain?
**Answer:** `set()` se. `{}` empty dictionary hoti hai.

### Q12. Set mein list kyun nahi store kar sakte?
**Answer:** List unhashable hai, isliye set element nahi ban sakti. Tuple tabhi set element ban sakti hai jab uske saare elements hashable hon.

### Q13. `remove()` aur `pop()` in sets mein difference?
**Answer:** `remove(value)` specified value delete karta hai aur absent value par `KeyError` deta hai. `pop()` ek arbitrary element remove karke return karta hai; empty set par `KeyError` deta hai.

### Q14. `union()` aur `intersection()` ka difference?
**Answer:** Union dono sets ke saare unique elements deta hai. Intersection sirf common elements deta hai.

### Q15. Kya set mutable hai?
**Answer:** Haan, set mein elements add/remove kar sakte hain. Lekin set ke andar rakhe individual elements hashable hone chahiye.

### Q16. `9` aur `9.0` same set mein ek hi element kyun bante hain?
**Answer:** Python mein `9 == 9.0` true hai aur unka hash equal hota hai, isliye set unhe duplicate-equivalent maanta hai.

### Q17. Duplicate values remove karne ke liye kaunsa structure use karoge?
**Answer:** Set. Agar original order preserve karna ho, toh approach carefully choose karni hogi, kyunki set order-preserving sequence nahi hai.

### Q18. Dictionary aur set mein `{}` ka kya difference hai?
**Answer:** `{}` empty dictionary hai. `{1, 2}` non-empty set hai. Empty set ke liye `set()` likhna zaroori hai.

---

## 8. OA Coding Practice with Solutions

Ye additional OA-style practice hai, original PDF ke content se alag. Har solution ko khud type karke run karo.

### Q1. List ke elements ki frequency dictionary banao

```python
nums = [1, 2, 2, 3, 1, 2]
freq = {}

for num in nums:
    freq[num] = freq.get(num, 0) + 1

print(freq)
```

Output:
```text
{1: 2, 2: 3, 3: 1}
```

**Approach:** `get(num, 0)` existing frequency dega ya first occurrence par `0`; phir count increment hoga.  
**Time:** `O(n)` average.

### Q2. String mein har character ki frequency count karo

```python
text = "banana"
freq = {}

for ch in text:
    freq[ch] = freq.get(ch, 0) + 1

print(freq)
```

Output:
```text
{'b': 1, 'a': 3, 'n': 2}
```

### Q3. Do lists ke unique combined elements find karo

```python
a = [1, 2, 3, 2]
b = [3, 4, 5]

combined = set(a).union(set(b))
print(combined)
```

Output ke elements ka order vary kar sakta hai:
```text
{1, 2, 3, 4, 5}
```

### Q4. Do lists ke common unique elements find karo

```python
a = [1, 2, 2, 3, 4]
b = [2, 3, 3, 5]

common = set(a).intersection(set(b))
print(common)
```

Output:
```text
{2, 3}
```

### Q5. Check karo ki list mein duplicate hai ya nahi

```python
nums = [4, 1, 7, 4]

has_duplicates = len(nums) != len(set(nums))
print(has_duplicates)
```

Output:
```text
True
```

### Q6. Dictionary mein highest marks wala subject find karo

```python
marks = {"phy": 95, "chem": 88, "math": 97}

top_subject = max(marks, key=marks.get)
print(top_subject)
print(marks[top_subject])
```

Output:
```text
math
97
```

### Q7. Do dictionaries merge karo

```python
a = {"x": 1, "y": 2}
b = {"y": 10, "z": 3}

merged = a.copy()
merged.update(b)
print(merged)
```

Output:
```text
{'x': 1, 'y': 10, 'z': 3}
```

Note: Same key hone par second dictionary ki value update karegi.

### Q8. Do strings anagrams hain ya nahi, frequency dictionaries se check karo

Anagrams mein same characters same frequency ke saath hote hain.

```python
def are_anagrams(a, b):
    if len(a) != len(b):
        return False

    freq = {}
    for ch in a:
        freq[ch] = freq.get(ch, 0) + 1

    for ch in b:
        if ch not in freq:
            return False
        freq[ch] -= 1
        if freq[ch] < 0:
            return False

    return all(count == 0 for count in freq.values())

print(are_anagrams("listen", "silent"))
print(are_anagrams("hello", "world"))
```

Output:
```text
True
False
```

### Q9. Unique words count karo

```python
sentence = "python is easy and python is useful"
words = sentence.split()
unique_words = set(words)

print(len(unique_words))
```

Output:
```text
5
```

### Q10. Dictionary ko key ke basis par sort karo

```python
marks = {"zara": 85, "aman": 92, "riya": 88}

sorted_marks = dict(sorted(marks.items()))
print(sorted_marks)
```

Output:
```text
{'aman': 92, 'riya': 88, 'zara': 85}
```

---

## 9. More Practice Questions

Pehle khud solve karo. Agar chaho toh inke solutions baad mein separately add kar sakte ho.

1. List ke numbers ki frequency dictionary banao.
2. String mein first non-repeating character find karo.
3. List mein duplicate values identify karo.
4. Do lists ka union aur intersection find karo.
5. Do dictionaries ke common keys find karo.
6. Do dictionaries ko merge karo, duplicate keys ke rules ke saath.
7. Dictionary ke values ka sum aur average calculate karo.
8. Student marks dictionary se highest aur lowest marks find karo.
9. Words ki frequency count karke most frequent word find karo.
10. Check karo ki do strings anagrams hain ya nahi.
11. Set difference find karo: `A - B`.
12. Symmetric difference find karo, yaani elements jo sirf ek set mein hain.
13. Duplicate subjects ko remove karke unique subjects print karo.
14. Dictionary ko values ke descending order mein sort karo.
15. Two-sum problem solve karo using a set.
16. Check karo ki ek list doosri list ka subset hai ya nahi.
17. Dictionary se specified key safely remove karo.
18. Nested dictionary mein kisi subject ke marks update karo.
19. List of words se unique words ko original order mein preserve karo.
20. Integer list mein `9` aur float `9.0` ke set behavior ko demonstrate karo.

---

## 10. Revision Checklist

- [ ] Dictionary key-value pairs aur curly braces
- [ ] Dictionary add/update karna
- [ ] Duplicate key behavior
- [ ] Nested dictionary access
- [ ] `keys()`, `values()`, `items()`
- [ ] `get()` vs square-bracket access
- [ ] `update()` use karna
- [ ] Set uniqueness aur unordered nature
- [ ] Set ke elements hashable hone chahiye
- [ ] Empty set `set()` vs empty dictionary `{}`
- [ ] `add()`, `remove()`, `clear()`, `pop()`
- [ ] `union()` and `intersection()`
- [ ] Frequency counting with dictionary
- [ ] Duplicate detection with set
- [ ] Anagram problem
- [ ] OA questions timer ke saath solve karna

## Quick Memory Sheet

```python
# Dictionary
student = {"name": "Asha", "marks": 90}
student["marks"] = 95
student["city"] = "Pune"

student.keys()
student.values()
student.items()
student.get("age")             # None if missing
student.update({"age": 21})

# Nested dictionary
record = {"scores": {"math": 95, "phy": 91}}
print(record["scores"]["math"])

# Set
nums = {1, 2, 2, 3}
nums.add(4)
nums.remove(1)
nums.union({3, 5})
nums.intersection({2, 4, 6})

empty_set = set()
empty_dictionary = {}
```

**Study plan:** Original PDF ke examples pehle run karo. Phir dictionary aur set methods ko bina dekhe likho. Last mein frequency counting, duplicate detection aur anagram jaise OA questions timed practice mein solve karo.
