# Python Notes — Lecture 7: File I/O
## Hinglish Notes | College Lecture + Interview Q&A + OA Practice

> **Source:** Uploaded Python Notes (Lecture 7), 6 pages. Original topics and examples are preserved in this section. Additional interview/OA material is marked separately.

## Contents
1. [File I/O in Python](#1-file-io-in-python)
2. [Open, Read and Close](#2-open-read-and-close-a-file)
3. [Reading a File](#3-reading-a-file)
4. [Writing to a File](#4-writing-to-a-file)
5. [with Syntax](#5-with-syntax)
6. [Deleting a File](#6-deleting-a-file)
7. [Complete Lecture Practice with Answers](#7-complete-lecture-practice-with-answers)
8. [Quick Revision](#8-quick-revision)
9. [Interview Questions and Answers](#9-interview-questions-and-answers)
10. [OA Practice Questions with Solutions](#10-oa-practice-questions-with-solutions)
11. [Extra Practice Questions](#11-extra-practice-questions)
12. [Common Mistakes and Checklist](#12-common-mistakes-and-checklist)

---

## 1. File I/O in Python

**File I/O** ka full form hai File Input/Output. Python files se data **read** aur files mein data **write** kar sakta hai.

Variables mein stored data program end hone par usually memory se chala jata hai, jabki file data ko persistently store kar sakti hai.

### Types of files

- **Text files:** Plain text store karti hain, jaise `.txt`, `.log`, `.csv`, `.py`.
- **Binary files:** Data binary form mein store hota hai, jaise `.mp4`, `.mov`, `.png`, `.jpeg`.
- **Note:** `.docx` Word file bhi internally binary format mein stored hoti hai, chahe usmein text ho.

---

## 2. Open, Read and Close a File

Read/write karne se pehle file open karni chahiye aur kaam complete hone par close karna chahiye.

### Basic syntax

```python
f = open("file_name", "mode")
data = f.read()
f.close()
```

### File modes

| Mode | Meaning |
|---|---|
| `'r'` | Read mode; default |
| `'w'` | Write mode; existing content erase karta hai, file missing ho to create karta hai |
| `'x'` | New file create karta hai; file already ho to error |
| `'a'` | Append mode; file ke end mein add karta hai, missing ho to create karta hai |
| `'b'` | Binary mode |
| `'t'` | Text mode; default |
| `'+'` | Updating mode: reading aur writing |

Modes combine bhi ho sakte hain: `rb` binary file read karta hai; `r+` file ko read aur write karne ke liye kholta hai.

> **Important:** `'w'` mode existing content overwrite karta hai. Zaroori file par ise carefully use karo.

---

## 3. Reading a File

Assume `sample.txt` mein ye content hai:

```text
Hi everyone
we are learning File I/O
using Python.
```

### `read()` and `readline()`

| Function | Kaam |
|---|---|
| `f.read()` | Puri file ko ek string ke roop mein read karta hai |
| `f.readline()` | Ek baar mein ek line read karta hai |

### Example 1: Entire file read karo

```python
f = open("sample.txt", "r")
data = f.read()
print(data)
f.close()
```

Output:
```text
Hi everyone
we are learning File I/O
using Python.
```

### Example 2: First two lines read karo

```python
f = open("sample.txt", "r")
line1 = f.readline()
line2 = f.readline()
print(line1, end="")
print(line2, end="")
f.close()
```

Output:
```text
Hi everyone
we are learning File I/O
```

Har line ke end mein usually `\n` hota hai. `print(..., end="")` extra newline avoid karta hai.

---

## 4. Writing to a File

### `'w'` mode — overwrite

```python
f = open("demo.txt", "w")
f.write("this is a new line")
f.close()
```

Ye file ka purana content erase karke new content likhta hai. File missing ho to create hoti hai.

### `'a'` mode — append

```python
f = open("demo.txt", "a")
f.write("\nthis line is added")
f.close()
```

Ab file read karne par:

```python
f = open("demo.txt", "r")
print(f.read())
f.close()
```

Output:
```text
this is a new line
this line is added
```

---

## 5. `with` Syntax

`with` statement ke saath Python block finish hone par file automatically close kar deta hai. Isliye manually `f.close()` likhne ki zaroorat nahi.

### Read using `with`

```python
with open("demo.txt", "r") as f:
    data = f.read()

print(data)
```

Output (agar file mein pichhle example ka content hai):
```text
this is a new line
this line is added
```

### Write using `with`

```python
with open("demo.txt", "w") as f:
    f.write("new data")
```

Is code ke baad `demo.txt` ka content `new data` hoga; purana content overwrite ho jayega.

**Lecture note:** File ko `r` mode mein open karke read karo. Lecture ke mutabik `w` ya `a` mode mein open ki hui file se read karne par error aata hai. (Technically, read/write modes like `r+` or `a+` alag hote hain; plain `w`/`a` read mode nahi hain.)

---

## 6. Deleting a File

Files delete karne ke liye `os` module use kar sakte hain. Module reusable code/library hoti hai jisme functions hote hain.

```python
import os

os.remove("demo.txt")
```

**Safety tip:** Delete karne se pehle correct path verify karo. File exist na kare to error aa sakta hai.

---

## 7. Complete Lecture Practice with Answers

### Q1. `practice.txt` create karo aur required text write karo

Required content:

```text
Hi everyone
we are learning File I/O
using Java.
I like programming in Java.
```

Solution:

```python
with open("practice.txt", "w") as f:
    f.write("Hi everyone\nwe are learning File I/O\n")
    f.write("using Java.\nI like programming in Java.")
```

### Q2. File mein har `"Java"` ko `"Python"` se replace karo

```python
def replace_java():
    with open("practice.txt", "r") as f:
        data = f.read()

    new_data = data.replace("Java", "Python")

    with open("practice.txt", "w") as f:
        f.write(new_data)

replace_java()

with open("practice.txt", "r") as f:
    print(f.read())
```

Output:
```text
Hi everyone
we are learning File I/O
using Python.
I like programming in Python.
```

**Approach:** Pehle file read karo, string replace karo, phir updated content write karo.

### Q3. Check karo `"learning"` word file mein exist karta hai ya nahi

```python
word = "learning"

with open("practice.txt", "r") as f:
    data = f.read()

if word in data:
    print("Found")
else:
    print("Not found")
```

Output:
```text
Found
```

### Q4. Word pehli baar kis line mein aata hai? Not found ho to `-1`

```python
def check_line(word):
    line_no = 1
    with open("practice.txt", "r") as f:
        for line in f:  # reads one line at a time
            if word in line:
                return line_no
            line_no += 1
    return -1

print(check_line("learning"))
print(check_line("hello"))
```

Output:
```text
2
-1
```

### Q5. Comma-separated file mein even numbers count karo

Assume `numbers.txt` contains:

```text
1,2,3,4,5,6,7,8,9,10,12,15
```

Solution:

```python
count = 0

with open("numbers.txt", "r") as f:
    data = f.read()

nums = data.split(",")  # list of strings
for num in nums:
    if int(num) % 2 == 0:
        count += 1

print("Even numbers:", count)
```

Output:
```text
Even numbers: 6
```

`split(",")` string ko commas par split karke strings ki list banata hai. `int(num)` har string ko integer mein convert karta hai.

---

## 8. Quick Revision

| Concept | Key point |
|---|---|
| File I/O | Files se read aur files mein write |
| Text file | `.txt`, `.csv`, `.log`, `.py` jaise formats |
| Binary file | `.png`, `.jpeg`, `.mp4` jaise formats |
| `open()` | File aur mode specify karke open karta hai |
| `read()` | Puri file ek string mein |
| `readline()` | Ek line |
| `write()` | String content write karta hai |
| `'r'` | Read |
| `'w'` | Overwrite/write |
| `'a'` | Append |
| `'x'` | Create new file, exists ho to error |
| `'b'` / `'t'` | Binary / text mode |
| `with` | Block end par automatic close |
| `os.remove()` | File delete |
| `split(",")` | Comma-separated string ko list mein todta hai |
| `replace(old, new)` | String mein matching text replace karta hai |

---

## 9. Interview Questions and Answers

### Q1. File I/O kya hai?
**Answer:** Program ke through files se data read karna aur files mein data write karna.

### Q2. Text aur binary file mein difference?
**Answer:** Text files character/text encoding ke roop mein read/write hoti hain; binary files raw bytes store karti hain. Images/videos common binary examples hain.

### Q3. `'r'`, `'w'`, `'a'` modes mein difference?
**Answer:** `'r'` read; `'w'` overwrite/create; `'a'` end par append/create.

### Q4. `'w'` mode risky kyun hai?
**Answer:** Existing file ka content truncate/erase kar deta hai. Zaroori data overwrite ho sakta hai.

### Q5. `'x'` mode kya karta hai?
**Answer:** New file create karta hai; same name ki file already ho to fail hota hai.

### Q6. `read()` vs `readline()`?
**Answer:** `read()` entire remaining content ek string mein; `readline()` ek line at a time.

### Q7. `with open(...)` ka benefit?
**Answer:** File block ke end par automatically close hoti hai, even if exception occurs in the block.

### Q8. `write()` ko kya input dena hota hai?
**Answer:** Text mode mein string. Number likhna ho to pehle `str(number)` convert kar sakte ho.

### Q9. `\n` ka meaning?
**Answer:** Newline character, text ko next line par le jata hai.

### Q10. `os` module kyun use hota hai?
**Answer:** Operating-system related operations, jaise file remove karna, ke liye.

### Q11. `os.remove()` mein kya precaution?
**Answer:** Correct file path confirm karo; deletion permanent ho sakta hai aur wrong path par wrong file delete ho sakti hai.

### Q12. `split(",")` kya return karta hai?
**Answer:** Commas ke beech ke parts ki list, normally strings ke roop mein.

### Q13. File mein word search kaise karoge?
**Answer:** `with open(..., "r")` se read karo; `word in data` se presence check karo, ya line-by-line iterate karo.

### Q14. File mein line number kaise find karoge?
**Answer:** Counter ko `1` se start karke har line par increment karo; match par counter return karo.

### Q15. Large file read karne ka better approach?
**Answer:** `for line in f:` jaise line-by-line iteration use karo, taaki poori file ek saath memory mein load na karni pade.

---

## 10. OA Practice Questions with Solutions

Ye additional OA-style questions hain, lecture ke core File I/O concepts par based.

### OA Q1. File mein total lines count karo

```python
def count_lines(filename):
    count = 0
    with open(filename, "r") as f:
        for line in f:
            count += 1
    return count

print(count_lines("practice.txt"))
```

**Approach:** Har line par counter increment.  
**Complexity:** Time `O(n)` in file size; line-by-line processing memory-efficient hai.

### OA Q2. File mein words count karo

```python
def count_words(filename):
    with open(filename, "r") as f:
        data = f.read()
    return len(data.split())

print(count_words("practice.txt"))
```

**Approach:** `split()` whitespace par tokens ki list banata hai.  
**Complexity:** Time `O(n)`; entire text/list memory mein load hoti hai.

### OA Q3. File se blank lines count karo

```python
def count_blank_lines(filename):
    count = 0
    with open(filename, "r") as f:
        for line in f:
            if line.strip() == "":
                count += 1
    return count

print(count_blank_lines("practice.txt"))
```

`strip()` newline aur surrounding whitespace remove karta hai. Time `O(n)`.

### OA Q4. File ka content uppercase karke new file mein save karo

```python
with open("input.txt", "r") as source:
    data = source.read()

with open("uppercase.txt", "w") as target:
    target.write(data.upper())
```

**Approach:** Source read, uppercase conversion, separate destination write. Existing `uppercase.txt` overwrite hoga.

### OA Q5. File mein target word ki occurrences count karo

```python
def count_occurrences(filename, word):
    count = 0
    with open(filename, "r") as f:
        for line in f:
            count += line.count(word)
    return count

print(count_occurrences("practice.txt", "Python"))
```

Ye case-sensitive substring occurrences count karta hai. Time `O(n)` approximately.

### OA Q6. Comma-separated numbers ka sum

```python
with open("numbers.txt", "r") as f:
    data = f.read()

nums = [int(item.strip()) for item in data.split(",") if item.strip()]
print(sum(nums))
```

Assumes file mein valid integer values hain. Invalid tokens hon to input validation/error handling add karo.

### OA Q7. File ki lines reverse order mein new file mein likho

```python
with open("input.txt", "r") as f:
    lines = f.readlines()

with open("reversed_lines.txt", "w") as f:
    f.writelines(reversed(lines))
```

**Note:** Ye poori file memory mein load karta hai; very large files ke liye suitable nahi ho sakta.

### OA Q8. File exist karti hai ya nahi check karo

```python
import os

filename = "practice.txt"

if os.path.exists(filename):
    print("File exists")
else:
    print("File does not exist")
```

Time filesystem operation par depend karta hai.

---

## 11. Extra Practice Questions

Pehle khud attempt karo; phir solutions ke patterns se compare karo.

1. File create karke apna naam aur course likho.
2. Existing file mein new line append karo.
3. File ka entire content print karo.
4. File ki first line print karo.
5. File mein character count karo.
6. File mein `"Python"` kitni baar aata hai, count karo.
7. File mein target word ki first line number return karo.
8. File se even numbers read karke unka sum print karo.
9. File ke text mein all `"old"` ko `"new"` se replace karo.
10. File ke blank lines count karo.
11. File ko line-by-line copy karke new file banao.
12. File mein longest line find karo.
13. File ki lines ko reverse order mein write karo.
14. Missing file ko safely handle karne ke liye exception handling add karo.
15. Explain karo ki large file ke liye `read()` aur line-by-line iteration mein kya trade-off hai.

### Hints

- Append ke liye `'a'`.
- Character count ke liye `len(data)`; newline characters bhi count honge.
- First matching line ke liye counter + early `return`.
- Even numbers: `int(value) % 2 == 0`.
- Replace: `data.replace("old", "new")`, phir write-back.
- Longest line: `max(lines, key=len)`; empty file handle karo.
- Missing file: `try/except FileNotFoundError`.

---

## 12. Common Mistakes and Checklist

### Common mistakes

1. `w` mode mein open karke old content unintentionally erase kar dena.
2. File close karna bhoolna; `with` preferred hai.
3. Read karne ke liye plain `'w'` ya `'a'` mode use karna.
4. `write()` mein integer pass karna instead of string.
5. `\n` bhoolne se text ek hi line par aa jana.
6. `readline()` sirf ek line read karta hai—poori file nahi.
7. `split(",")` se strings milti hain; arithmetic se pehle `int()` karo.
8. Relative path current working directory ke according resolve hota hai.
9. Missing file par `FileNotFoundError` aa sakta hai.
10. `os.remove()` se pehle path verify nahi karna.
11. Whole-file `read()` large files ke liye memory-heavy ho sakta hai.
12. Text replacement case-sensitive hota hai: `"Java"` aur `"java"` different hain.

### Revision checklist

- [ ] Text aur binary files ka difference samjha sakta/sakti hoon.
- [ ] `r`, `w`, `a`, `x`, `b`, `t`, `+` modes explain kar sakta/sakti hoon.
- [ ] `read()` aur `readline()` use kar sakta/sakti hoon.
- [ ] `write()` aur append implement kar sakta/sakti hoon.
- [ ] `with open(...)` ka benefit explain kar sakta/sakti hoon.
- [ ] `os.remove()` aur path safety samajhta/samajhti hoon.
- [ ] File mein word search aur line number find kar sakta/sakti hoon.
- [ ] Comma-separated numbers parse karke count/sum kar sakta/sakti hoon.
- [ ] OA answers mein input assumptions aur complexity state kar sakta/sakti hoon.

---

## Suggested Study Plan

**Session 1 — Basics (30–40 min):** File types, `open()`, modes, `read()`, `readline()`.

**Session 2 — Writing and utilities (30–40 min):** `write()`, append, `with`, `os.remove()`, `split()` and `replace()`.

**Session 3 — Interview/OA (45–60 min):** Word search, line number, even count, line count, word count, uppercase copy. Har code ko test file ke saath run karo.

> **Practice advice:** Test files ko ek dedicated folder mein rakho. `'w'` mode ya `os.remove()` use karne se pehle filename/path check karo.
