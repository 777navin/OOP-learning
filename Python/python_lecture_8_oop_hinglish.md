# Python Notes — Lecture 8: Object-Oriented Programming (OOP)
## Hinglish Notes | Complete Lecture Code | Interview Q&A | OA Practice

> **Source:** College PDF “Python Notes (Lecture 8)”, 5 pages. Original lecture topics and practice questions are captured first; extra interview/OA practice is clearly marked as additional material.

## Contents
1. [OOP in Python](#1-oop-in-python)
2. [Class and Object](#2-class-and-object)
3. [Class and Instance Attributes](#3-class-and-instance-attributes)
4. [`__init__()` and `self`](#4-__init__-and-self)
5. [Methods](#5-methods)
6. [Static Methods and Decorators](#6-static-methods-and-decorators)
7. [Abstraction and Encapsulation](#7-abstraction-and-encapsulation)
8. [Complete Lecture Practice with Answers](#8-complete-lecture-practice-with-answers)
9. [Quick Revision](#9-quick-revision)
10. [Interview Questions and Answers](#10-interview-questions-and-answers)
11. [OA Practice Questions with Solutions](#11-oa-practice-questions-with-solutions)
12. [Extra Practice Questions](#12-extra-practice-questions)
13. [Common Mistakes and Checklist](#13-common-mistakes-and-checklist)

---

## 1. OOP in Python

**Object-Oriented Programming (OOP)** mein hum code ko real-world objects ke around organize karte hain. Objects data aur us data par kaam karne wale actions ko ek jagah bundle kar sakte hain.

**Lecture example:** Student ke paas `name` aur `marks` hote hain, aur student ka average calculate kiya ja sakta hai. OOP data aur actions ko ek saath organize karta hai.

### OOP kyun use karte hain?
- Related data aur functions ko organize karne ke liye.
- Real-world entities model karne ke liye.
- Code ko reusable aur maintainable banane ke liye.

---

## 2. Class and Object

- **Class:** Objects create karne ka blueprint/template.
- **Object / Instance:** Class se banaya gaya actual entity.

### Lecture example

```python
# Creating a class
class Student:
    name = "karan kumar"

# Creating an object (instance)
s1 = Student()
print(s1.name)
```

Output:
```text
karan kumar
```

`Student` class hai; `s1` us class ka object hai. `s1.name` attribute access karta hai.

---

## 3. Class and Instance Attributes

- **Class attribute (`Class.attr`):** Class ke saare instances ke liye shared hota hai, jab tak instance same name ka apna attribute define na kare.
- **Instance attribute (`obj.attr`):** Particular object se associated hota hai.

### Lecture example

```python
class Student:
    college_name = "ABC College"  # class attribute

    def __init__(self, name):
        self.name = name           # instance attribute

s1 = Student("karan")
s2 = Student("arjun")

print(s1.name, s2.name)
print(Student.college_name)
print(s1.college_name)
```

Output:
```text
karan arjun
ABC College
ABC College
```

Agar instance ke paas class attribute ke same naam ka attribute ho, to us object ke liye instance attribute use hota hai.

### Demonstration: instance attribute class attribute ko shadow karta hai

```python
class Student:
    college_name = "ABC College"

s1 = Student()
s2 = Student()

s1.college_name = "XYZ College"

print(s1.college_name)
print(s2.college_name)
print(Student.college_name)
```

Output:
```text
XYZ College
ABC College
ABC College
```

---

## 4. `__init__()` and `self`

### `__init__()` method

`__init__()` object create hone ke baad initialization ke liye automatically call hota hai. Isse object ke initial attributes set karte hain. Beginner notes mein ise commonly “constructor” kaha jata hai; technically Python object creation mein `__new__()` aur initialization mein `__init__()` ka role hota hai.

### Lecture example

```python
class Student:
    def __init__(self, fullname):
        self.name = fullname

s1 = Student("karan")
print(s1.name)
```

Output:
```text
karan
```

### `self` kya hai?

`self` current instance ka reference hai. Isse us object ke attributes aur methods access karte hain. Instance method call karte waqt Python current object ko automatically pass karta hai, isliye object create karte waqt `self` argument khud nahi dete.

```python
class Student:
    def __init__(self, name):
        self.name = name

    def show_name(self):
        print(self.name)

s1 = Student("Priya")
s1.show_name()
```

Output:
```text
Priya
```

`self.name` object ka attribute hai; `name` constructor ko diya gaya local parameter hai.

---

## 5. Methods

**Method** ek function hai jo class ke andar define hota hai aur object/class ke behavior ko represent karta hai. Instance method ka first parameter conventionally `self` hota hai.

### Lecture example

```python
class Student:
    def __init__(self, fullname):
        self.name = fullname

    def hello(self):
        print("hello", self.name)

s1 = Student("karan")
s1.hello()
```

Output:
```text
hello karan
```

### Lecture Practice Q1: Student average

**Question:** `Student` class banao jo constructor mein name aur 3 subjects ke marks le. Average print karne ka method banao.

```python
class Student:
    def __init__(self, name, marks):
        self.name = name
        self.marks = marks

    def get_avg(self):
        avg = sum(self.marks) / len(self.marks)
        print(self.name, "average:", avg)

s1 = Student("Tony Stark", [99, 98, 97])
s1.get_avg()
```

Output:
```text
Tony Stark average: 98.0
```

**Explanation:** `self.marks` list ke marks hold karta hai. `sum()` marks add karta hai aur `len()` subjects count karta hai. Average = total / count.

**Safer extension:** Empty marks list ho sakti hai, to division by zero avoid karne ke liye validation add karo.

```python
class Student:
    def __init__(self, name, marks):
        self.name = name
        self.marks = marks

    def get_avg(self):
        if not self.marks:
            return None
        return sum(self.marks) / len(self.marks)

s1 = Student("Tony Stark", [99, 98, 97])
print(s1.name, "average:", s1.get_avg())
```

---

## 6. Static Methods and Decorators

### Static method

Static method ko `@staticmethod` decorator se mark kiya jata hai. Ismein `self` automatically pass nahi hota aur method ko object-specific state ki zaroorat nahi hoti.

### Lecture example

```python
class Student:
    @staticmethod
    def college():
        print("ABC College")

Student.college()

s1 = Student()
s1.college()
```

Output:
```text
ABC College
ABC College
```

Static method ko class se ya instance se call kiya ja sakta hai.

### Decorator kya hai?

Decorator ek callable hota hai jo kisi function/method ke behavior ko wrap ya extend kar sakta hai. `@staticmethod` class body mein function ko static method ke roop mein configure karta hai.

### Instance method vs static method

| Feature | Instance method | Static method |
|---|---|---|
| Typical first parameter | `self` | Koi automatic `self` nahi |
| Instance data access | `self` se direct | Object pass/access explicitly karna padega |
| Declaration | `def method(self, ...)` | `@staticmethod` + `def method(...)` |
| Suitable for | Object ke data par operation | Related utility/action jise instance state nahi chahiye |

---

## 7. Abstraction and Encapsulation

### Abstraction

Implementation details hide karke user ko sirf essential features dikhana **abstraction** hai.

**Lecture example:** `car.start()` call karne ke liye user ko engine ke andar ka exact mechanism jaan-na zaroori nahi.

### Encapsulation

Related data aur functions ko ek unit—object—mein bundle karna **encapsulation** hai.

**Lecture example:** `Student` class name aur marks ko `get_avg()` method ke saath organize karti hai.

> **Scope note:** Is lecture mein abstraction aur encapsulation ki introductory definitions di gayi hain. Inheritance aur polymorphism is PDF ke listed topics mein explain nahi kiye gaye.

---

## 8. Complete Lecture Practice with Answers

### Q1. Student class: name, marks, average

```python
class Student:
    def __init__(self, name, marks):
        self.name = name
        self.marks = marks

    def get_avg(self):
        avg = sum(self.marks) / len(self.marks)
        print(self.name, "average:", avg)

s1 = Student("Tony Stark", [99, 98, 97])
s1.get_avg()
```

Output:
```text
Tony Stark average: 98.0
```

### Q2. Account class: debit, credit, balance

**Question:** `Account` class mein `balance` aur `acc_no` attributes hon. Debit, credit aur balance print karne ke methods banao.

```python
class Account:
    def __init__(self, balance, acc_no):
        self.balance = balance
        self.acc_no = acc_no

    def debit(self, amount):
        self.balance -= amount
        print("Rs.", amount, "was debited")
        self.get_balance()

    def credit(self, amount):
        self.balance += amount
        print("Rs.", amount, "was credited")
        self.get_balance()

    def get_balance(self):
        print("Total balance =", self.balance)

acc1 = Account(10000, 12345)
acc1.debit(1000)
acc1.credit(500)
```

Output:
```text
Rs. 1000 was debited
Total balance = 9000
Rs. 500 was credited
Total balance = 9500
```

**Explanation:**
- Starting balance = `10000`.
- Debit `1000` → balance `9000`.
- Credit `500` → balance `9500`.
- Ek method same object ka doosra method `self.get_balance()` se call kar sakta hai.

**Additional safety improvement:** Real account logic mein negative amounts aur insufficient balance validate karna chahiye. Original lecture code mein ye checks nahi hain.

```python
class Account:
    def __init__(self, balance, acc_no):
        if balance < 0:
            raise ValueError("Initial balance cannot be negative")
        self.balance = balance
        self.acc_no = acc_no

    def debit(self, amount):
        if amount <= 0:
            raise ValueError("Amount must be positive")
        if amount > self.balance:
            print("Insufficient balance")
            return
        self.balance -= amount

    def credit(self, amount):
        if amount <= 0:
            raise ValueError("Amount must be positive")
        self.balance += amount

    def get_balance(self):
        return self.balance

acc = Account(10000, 12345)
acc.debit(1000)
acc.credit(500)
print(acc.get_balance())  # 9500
```

---

## 9. Quick Revision

| Concept | Meaning | Example |
|---|---|---|
| OOP | Objects ke around programming organize karna | `Student` |
| Class | Blueprint | `class Student:` |
| Object | Class ka instance | `s1 = Student(...)` |
| Attribute | Object/class ka data | `s1.name` |
| Class attribute | Class ke instances ke liye shared default data | `college_name` |
| Instance attribute | Particular object ka data | `self.name` |
| `__init__()` | Object initialization method | `def __init__(self, name)` |
| `self` | Current instance ka reference | `self.name = name` |
| Instance method | Object behavior; `self` leta hai | `get_avg()` |
| Static method | `self` automatically nahi leta | `@staticmethod` |
| Decorator | Function/method ko wrap/configure karta hai | `@staticmethod` |
| Abstraction | Implementation details hide karna | `car.start()` |
| Encapsulation | Related data + behavior ko ek unit mein bundle karna | `Student` with marks and `get_avg()` |

---

## 10. Interview Questions and Answers

### Q1. OOP kya hai?
**Answer:** Programming approach jisme code ko classes aur objects ke around organize karte hain, taaki data aur behavior related units mein rahein.

### Q2. Class aur object mein difference?
**Answer:** Class blueprint hai; object us blueprint ka actual instance hai.

### Q3. Attribute kya hota hai?
**Answer:** Class/object se associated data, jaise `s1.name` ya `Student.college_name`.

### Q4. Class attribute vs instance attribute?
**Answer:** Class attribute class ke through shared hota hai; instance attribute particular object ka hota hai. Instance attribute same name ke class attribute ko that object ke liye shadow kar sakta hai.

### Q5. `__init__()` ka role?
**Answer:** Object create hone ke baad uski initial state/attributes set karna.

### Q6. `self` kya hai?
**Answer:** Current instance ka reference. Instance method ke through object ke attributes aur methods access karne mein use hota hai.

### Q7. Kya `self` Python keyword hai?
**Answer:** Nahi, ye strong convention hai. Technically another name possible hai, lekin readable Python code mein `self` use karna chahiye.

### Q8. Method aur normal function mein difference?
**Answer:** Method class ke namespace mein define hota hai aur instance/class se associated behavior represent karta hai. Normal function class ke bahar bhi define ho sakta hai.

### Q9. Static method kya hai?
**Answer:** `@staticmethod` se mark kiya function-like method jise automatic `self` ya `cls` nahi milta.

### Q10. `@staticmethod` kya hai?
**Answer:** Decorator jo class body ke function ko static method ke roop mein expose karta hai.

### Q11. Abstraction vs encapsulation?
**Answer:** Abstraction essential interface dikhata aur implementation detail hide karta hai. Encapsulation related data aur behavior ko ek unit mein bundle karta hai.

### Q12. `self.get_balance()` ka meaning?
**Answer:** Current object ka `get_balance()` method call karna.

### Q13. Student average method ka formula?
**Answer:** `sum(marks) / len(marks)`. Empty list ko handle karna zaroori hai.

### Q14. Account class mein debit ke baad balance kaise change hota hai?
**Answer:** Lecture example mein `self.balance -= amount`; credit mein `self.balance += amount`.

### Q15. OOP ka benefit kya hai?
**Answer:** Related code organize karna, object state maintain karna, reuse aur maintainability improve karna.

### Q16. Object ka attribute kaise access karte hain?
**Answer:** Dot notation: `s1.name`.

### Q17. Agar do students ke names different hain to kya woh same class use kar sakte hain?
**Answer:** Haan. Same class se multiple instances ban sakte hain, har instance ke apne `self.name` jaise attributes hote hain.

### Q18. Static method ko object se call kar sakte hain?
**Answer:** Haan. Lecture mein `Student.college()` aur `s1.college()` dono examples hain.

---

## 11. OA Practice Questions with Solutions

Ye **additional** OA-style practice questions hain, original PDF ke extra questions nahi.

### OA Q1. Rectangle class

**Task:** Length aur width store karo; area aur perimeter return karo.

```python
class Rectangle:
    def __init__(self, length, width):
        self.length = length
        self.width = width

    def area(self):
        return self.length * self.width

    def perimeter(self):
        return 2 * (self.length + self.width)

r = Rectangle(5, 3)
print(r.area())
print(r.perimeter())
```

Output:
```text
15
16
```

### OA Q2. Employee annual salary

```python
class Employee:
    def __init__(self, name, monthly_salary):
        self.name = name
        self.monthly_salary = monthly_salary

    def annual_salary(self):
        return self.monthly_salary * 12

e = Employee("Asha", 30000)
print(e.name, e.annual_salary())
```

Output:
```text
Asha 360000
```

### OA Q3. Count passing subjects

**Task:** Marks list ke liye `pass_mark` ya usse zyada score wale subjects count karo.

```python
class Student:
    def __init__(self, marks):
        self.marks = marks

    def count_passed(self, pass_mark=40):
        count = 0
        for mark in self.marks:
            if mark >= pass_mark:
                count += 1
        return count

s = Student([35, 80, 40, 22, 91])
print(s.count_passed())
```

Output: `3`

### OA Q4. Bank account with insufficient-balance check

```python
class Account:
    def __init__(self, balance):
        self.balance = balance

    def debit(self, amount):
        if amount <= 0:
            return "Invalid amount"
        if amount > self.balance:
            return "Insufficient balance"
        self.balance -= amount
        return self.balance

acc = Account(500)
print(acc.debit(200))
print(acc.debit(400))
```

Output:
```text
300
Insufficient balance
```

### OA Q5. Find topper from student objects

```python
class Student:
    def __init__(self, name, marks):
        self.name = name
        self.marks = marks

    def total(self):
        return sum(self.marks)

students = [
    Student("Aman", [70, 80, 90]),
    Student("Riya", [95, 90, 92]),
    Student("Kabir", [80, 85, 88])
]

topper = max(students, key=lambda student: student.total())
print(topper.name, topper.total())
```

Output:
```text
Riya 277
```

### OA Q6. Class attribute counter

**Task:** Count how many objects have been created.

```python
class Item:
    count = 0

    def __init__(self):
        Item.count += 1

a = Item()
b = Item()
c = Item()
print(Item.count)
```

Output: `3`

### OA Q7. Static method to check even number

```python
class NumberTools:
    @staticmethod
    def is_even(n):
        return n % 2 == 0

print(NumberTools.is_even(8))
print(NumberTools.is_even(5))
```

Output:
```text
True
False
```

### OA Q8. Product class with discount

```python
class Product:
    def __init__(self, name, price):
        self.name = name
        self.price = price

    def discounted_price(self, percent):
        if not 0 <= percent <= 100:
            raise ValueError("Discount must be between 0 and 100")
        return self.price * (1 - percent / 100)

p = Product("Keyboard", 2000)
print(p.discounted_price(10))
```

Output: `1800.0`

---

## 12. Extra Practice Questions

Pehle khud code likho, phir solution ke patterns se compare karo.

1. `Car` class banao with brand, model aur year.
2. `Circle` class mein area aur circumference methods likho.
3. `Book` class banao with title, author aur `display_info()`.
4. `Student` class mein average ke saath highest mark bhi return karo.
5. `BankAccount` mein deposit, withdraw aur balance methods likho.
6. `Employee` class mein salary raise method add karo.
7. Class attribute aur instance attribute ka output predict karo.
8. `@staticmethod` se Celsius-to-Fahrenheit conversion likho.
9. `Movie` class mein rating ko 0–10 ke range mein validate karo.
10. `ShoppingCart` class mein item add karke total calculate karo.
11. `LibraryBook` class mein checkout/return methods implement karo.
12. Do objects ke attributes independent hain, verify karne wala code likho.
13. Empty marks list handle karne wala average method likho.
14. Account class mein negative deposit aur insufficient withdrawal reject karo.
15. Class aur instance attributes ke shadowing ka example banao.

### Hints

- Circle area: `3.14159 * r * r`; circumference: `2 * 3.14159 * r`.
- Deposit ke liye positive amount; withdraw ke liye positive amount aur sufficient balance.
- Static conversion: `F = C * 9 / 5 + 32`.
- Shopping cart ke liye items ko list/dictionary mein store kar sakte ho.
- Average ke liye empty list ko handle karo.

---

## 13. Common Mistakes and Checklist

### Common mistakes

1. Class definition aur object creation ko same samajhna.
2. `__init__()` mein `self.name = name` bhool jana.
3. Instance method mein `self` parameter miss karna.
4. `self.name` aur local `name` ka difference confuse karna.
5. Class attribute ko change karte waqt accidentally instance attribute create kar dena.
6. `@staticmethod` ke method mein automatic `self` expect karna.
7. Empty list par average calculate karke division-by-zero error lena.
8. Account debit mein negative amount ya insufficient balance validate na karna.
9. `self.get_balance()` ke bajay method ko wrong tarah call karna.
10. Abstraction aur encapsulation ko exactly same concept samajhna.

### Revision checklist

- [ ] OOP, class aur object explain kar sakta/sakti hoon.
- [ ] Class vs instance attributes ka code likh sakta/sakti hoon.
- [ ] `__init__()` aur `self` samajh aata hai.
- [ ] Instance method aur static method ka difference bata sakta/sakti hoon.
- [ ] `@staticmethod` ka use kar sakta/sakti hoon.
- [ ] Abstraction aur encapsulation examples ke saath explain kar sakta/sakti hoon.
- [ ] Student average class implement kar sakta/sakti hoon.
- [ ] Account debit/credit/balance class implement kar sakta/sakti hoon.
- [ ] Edge cases aur input validation handle kar sakta/sakti hoon.
- [ ] OA problems mein code ke expected output ko dry-run kar sakta/sakti hoon.

---

## Suggested Study Plan

**Session 1 — OOP basics (30–40 min):** OOP, class, object, attributes, `__init__()`, `self`.

**Session 2 — Methods (30–40 min):** Instance methods, static methods, decorators, student average aur account examples.

**Session 3 — Interview/OA (45–60 min):** Rectangle, Employee, passing subjects, bank account, topper, class counter aur product discount. Har question ko pehle khud solve karo.

> **Best rule:** Code ko copy-paste karne se pehle khud type karo, har line ka purpose explain karo, phir output predict karke run karo.
