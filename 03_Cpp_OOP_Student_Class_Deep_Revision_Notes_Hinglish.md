# C++ OOP Notes --- Student Class, Constructors, Copying & Memory Management

> **Revision notes for Love Babbar's C++ OOP lesson**\
> Language: Hinglish (Hindi + English technical terms)\
> Level: Beginner to Intermediate\
> Main example: `Student` class

------------------------------------------------------------------------

## 0. Is lesson mein kya-kya seekha?

Is lesson ka central idea hai: **C++ mein class ka object kaise create
hota hai, initialize hota hai, copy hota hai, memory use karta hai aur
destroy hota hai.**

Love Babbar ke uploaded lesson PDF mein initial topics ka flow hai:
blueprint/class, object as an instance, constructor, parameterized
constructor, destructor aur object life cycle. Pages 1--2 par class ke
andar attributes aur behaviours ka diagram bhi diya gaya hai.

Is discussion mein humne us foundation ko aage badhaya:

1.  Class and Object
2.  Attributes and Methods
3.  Default Constructor
4.  Parameterized Constructor
5.  `this` Pointer
6.  Copy Constructor
7.  Pointer as a class data member
8.  Dynamic Memory Allocation using `new`
9.  Shallow Copy vs Deep Copy
10. Destructor and `delete`
11. Copy Assignment Operator
12. Object Life Cycle
13. Rule of Three
14. C++ OOP concepts ka PHP/Laravel se connection

------------------------------------------------------------------------

# 1. Class and Object

## 1.1 Class kya hoti hai?

**Definition:** A class is a user-defined data type that acts as a
blueprint/template for creating objects.

Hinglish explanation: Class ek blueprint ya design hoti hai. Isme define
karte hain ki object ke paas kaunsa data hoga aur woh kaunse kaam kar
sakta hai.

Example: Student class decide karti hai ki har student object ke paas
`id`, `age`, `name`, `nos`, `gpa` ho sakta hai aur woh `study()`,
`sleep()`, `bunk()` jaise actions perform kar sakta hai.

``` cpp
class Student {
public:
    int id;
    int age;
    string name;

    void study() {
        cout << name << " is studying" << endl;
    }
};
```

## 1.2 Object kya hota hai?

**Definition:** An object is an instance of a class.

Hinglish: Class blueprint hai aur object us blueprint se bana actual
instance hai. Har object ke non-static data members ki apni values hoti
hain.

``` cpp
Student A;
Student B;
```

Yahan: - `Student` = class / type - `A` = first object - `B` = second
object

A aur B dono Student type ke objects hain, lekin unka `name`, `age` aur
doosra data alag ho sakta hai.

## 1.3 Class vs Object

  -----------------------------------------------------------------------
  Class                               Object
  ----------------------------------- -----------------------------------
  Blueprint/template                  Class ka instance

  Structure define karti hai          Actual values rakhta hai

  `class Student { ... };`            `Student A;`

  Ek class se multiple objects ban    Har object ki apni non-static state
  sakte hain                          hoti hai
  -----------------------------------------------------------------------

------------------------------------------------------------------------

# 2. Attributes and Methods

## 2.1 Attributes / Data Members

**Definition:** Attributes are variables declared inside a class that
represent the data/state of an object.

``` cpp
int id;
int age;
string name;
int nos;
float *gpa;
```

Hinglish: Attributes object ki information store karte hain. Student ke
case mein ID, age, name, number of subjects aur GPA.

## 2.2 Methods / Member Functions

**Definition:** Methods are functions declared inside a class that
represent the behaviour/actions of an object.

``` cpp
void study() {
    cout << name << " studying" << endl;
}

void sleep() {
    cout << name << " sleeping" << endl;
}

void bunk() {
    cout << name << " bunking" << endl;
}
```

-   `study()` = behaviour
-   `sleep()` = behaviour
-   `bunk()` = behaviour

## 2.3 `public` keyword

`public` access specifier ka matlab hai ki class ke ye members class ke
bahar se bhi accessible hain, subject to normal object access.

``` cpp
class Student {
public:
    int age;
};
```

``` cpp
Student A;
A.age = 20;
```

C++ class mein members by default `private` hote hain. `public:` likhne
par uske baad ke members public hote hain, jab tak next access specifier
na aaye.

------------------------------------------------------------------------

# 3. Constructors

## 3.1 Constructor kya hota hai?

**Definition:** A constructor is a special member function that is
automatically called when an object is created.

Hinglish: Jab object create hota hai, constructor automatically execute
hota hai. Iska common purpose object ko initial state dena hota hai.

Constructor ke rules: 1. Constructor ka naam class ke naam jaisa hota
hai. 2. Iska koi return type nahi hota --- `void` bhi nahi. 3. Object
create hone par suitable constructor call hota hai. 4. Constructor
overloaded ho sakta hai, yaani same class mein different parameter lists
ke saath multiple constructors ho sakte hain.

## 3.2 Default Constructor

**Definition:** A default constructor is a constructor that can be
called with no arguments.

``` cpp
Student() {
    cout << "Default constructor called" << endl;
}
```

Use:

``` cpp
Student A;
```

Is example mein `A` create hote hi default constructor call hoga.

Important: Agar class mein hum apna parameterized constructor declare
kar dete hain, toh compiler automatically no-argument default
constructor provide nahi karta. Agar `Student A;` bhi chahiye, toh
default constructor khud define karein.

## 3.3 Parameterized Constructor

**Definition:** A parameterized constructor accepts arguments to
initialize an object's data members.

``` cpp
Student(int id, int age, string name, int nos, float gpa) {
    this->id = id;
    this->age = age;
    this->name = name;
    this->nos = nos;
    this->gpa = new float(gpa);
}
```

Use:

``` cpp
Student A(1, 15, "Navin", 6, 9.9);
```

Values ka mapping:

  Parameter         Value Object member
  ----------- ----------- ---------------
  `id`                  1 `A.id`
  `age`                15 `A.age`
  `name`        `"Navin"` `A.name`
  `nos`                 6 `A.nos`
  `gpa`               9.9 `*A.gpa`

## 3.4 Constructor Overloading

Jab ek class mein multiple constructors hon, lekin unke parameter lists
different hon, use constructor overloading kehte hain.

``` cpp
Student() {
    // no arguments
}

Student(int id, string name) {
    // two arguments
}
```

Compiler arguments ke basis par suitable constructor select karta hai.

------------------------------------------------------------------------

# 4. `this` Pointer

## 4.1 Definition

`this` is an implicit pointer available inside a non-static member
function. It points to the current object on which the member function
is operating.

Hinglish: `this` current object ka address represent karta hai. Isse
current object ke members access kar sakte hain.

Example:

``` cpp
Student(int id, int age) {
    this->id = id;
    this->age = age;
}
```

Yahan: - `this->id` = current object ka data member - `id` = constructor
ka parameter - `this->age` = current object ka age member - `age` =
parameter

`this->id = id;` ka simple meaning: parameter `id` ki value current
object ke `id` member mein store karo.

Note: `this` non-static member functions mein available hota hai. Static
member function ke paas current object ka `this` pointer nahi hota.

------------------------------------------------------------------------

# 5. Pointer Basics

## 5.1 Pointer kya hota hai?

**Definition:** A pointer is a variable that stores the memory address
of another object or variable.

``` cpp
int number = 10;
int *ptr = &number;
```

-   `number` = normal integer variable
-   `&number` = number ka address
-   `ptr` = address store karne wala pointer
-   `*ptr` = us address par stored value

## 5.2 `&` and `*` ka meaning

  Symbol / expression   Meaning
  --------------------- ---------------------------------------------------------
  `&number`             `number` ka address
  `int *ptr`            Integer pointer declaration
  `*ptr`                Pointer ko dereference karke value access karna
  `nullptr`             Pointer currently kisi valid object ko point nahi karta

Example:

``` cpp
int number = 10;
int *ptr = &number;

cout << number << endl; // 10
cout << *ptr << endl;   // 10
cout << ptr << endl;    // address (value run ke hisaab se different)
```

## 5.3 `nullptr`

`nullptr` C++ ka null pointer literal hai. Iska use batata hai ki
pointer abhi kisi valid object ko point nahi kar raha.

``` cpp
float *gpa = nullptr;
```

Uninitialized pointer ke bajaye pointer ko `nullptr` se initialize karna
safer hai.

------------------------------------------------------------------------

# 6. Stack and Heap Memory

## 6.1 Automatic / Stack Storage

Example:

``` cpp
int main() {
    Student A(1, 15, "Navin", 6, 9.9);
    Student B(2, 13, "Kajal", 4, 9.5);
}
```

A aur B local automatic objects hain. Inka lifetime scope ke saath tied
hota hai. Jab scope end hota hai, inke destructors automatically call
hote hain.

Beginner mental model: Local objects ko commonly stack par samjhaya jata
hai.

## 6.2 Dynamic / Heap Allocation

Example:

``` cpp
Student *ptr = new Student(3, 14, "Babban", 7, 9.9);
```

-   `new` dynamically memory allocate karta hai.
-   `Student(...)` object ko construct karta hai.
-   `ptr` allocated object ka address store karta hai.
-   Object ka lifetime manually `delete` tak ya kisi owning smart
    pointer ke cleanup tak rehta hai.

Beginner mental model: Dynamically allocated object heap/free store par
hota hai. Pointer variable `ptr`, agar local variable hai, toh automatic
storage duration mein hota hai.

## 6.3 Stack vs Heap --- revision table

  -----------------------------------------------------------------------
  Automatic local object              Dynamically allocated object
  ----------------------------------- -----------------------------------
  Example: `Student A;`               Example: `new Student(...)`

  Scope end par automatically destroy `delete` ya owner cleanup required

  Local object ko directly access:    Pointer se access: `ptr->name`
  `A.name`                            

  Constructor automatically call      Constructor automatically call by
                                      `new` expression
  -----------------------------------------------------------------------

Technical note: C++ standard storage duration define karta hai; "stack"
and "heap" common implementation/teaching terms hain. Har local variable
ke liye compiler ka physical stack placement guarantee nahi hota.

------------------------------------------------------------------------

# 7. Object Access: `.` vs `->`

Normal object ke members access karne ke liye dot operator use hota hai:

``` cpp
Student A;
A.study();
cout << A.name;
```

Pointer ke through object members access karne ke liye arrow operator
use hota hai:

``` cpp
Student *ptr = new Student();

ptr->study();
cout << ptr->name;
```

  Normal object   Pointer to object
  --------------- -------------------
  `A.name`        `ptr->name`
  `A.age`         `ptr->age`
  `A.study()`     `ptr->study()`

Arrow operator ka equivalent form:

``` cpp
ptr->name
```

is:

``` cpp
(*ptr).name
```

Parentheses important hain because `.` operator ki precedence `*` se
higher hoti hai.

------------------------------------------------------------------------

# 8. Dynamic Memory Allocation: `new` and `delete`

## 8.1 `new` operator

**Definition:** `new` dynamically allocates storage and
initializes/constructs an object in that storage. It returns a pointer
to the created object.

``` cpp
float *gpa = new float(9.9);
```

Yahan: 1. Ek float ke liye dynamic storage allocate hoti hai. 2. Float
ko `9.9` se initialize kiya jata hai. 3. Returned address `gpa` mein
store hota hai.

Class object example:

``` cpp
Student *ptr = new Student(3, 14, "Babban", 7, 9.9);
```

## 8.2 `delete` operator

**Definition:** `delete` destroys an object created by a matching
single-object `new` expression and releases its storage.

``` cpp
delete gpa;
gpa = nullptr;
```

Class object:

``` cpp
delete ptr;
ptr = nullptr;
```

`delete ptr` karne par: 1. Student object ka destructor call hota hai.
2. Object ki storage release hoti hai. 3. `ptr` variable khud
automatically null nahi hota. Isliye `ptr = nullptr;` useful practice
hai.

Important matching: - `new` ke saath `delete` - `new[]` ke saath
`delete[]`

Same allocation ko do baar delete nahi karna chahiye. Invalid pointer ko
delete karna undefined behaviour hai.

------------------------------------------------------------------------

# 9. Pointer as a Class Data Member

Ab hamare Student class mein:

``` cpp
float *gpa = nullptr;
```

Ye normal float variable nahi hai. Ye float value ka address store karta
hai.

Parameterized constructor:

``` cpp
Student(int id, int age, string name, int nos, float gpa) {
    this->id = id;
    this->age = age;
    this->name = name;
    this->nos = nos;
    this->gpa = new float(gpa);
}
```

Use:

``` cpp
Student A(1, 15, "Navin", 6, 9.9);
```

GPA read karne ke liye:

``` cpp
cout << *A.gpa << endl;
```

-   `A.gpa` = pointer/address
-   `*A.gpa` = actual float value

Agar `gpa` null ho sakta hai, dereference se pehle check karna chahiye:

``` cpp
if (A.gpa != nullptr) {
    cout << *A.gpa << endl;
}
```

------------------------------------------------------------------------

# 10. Copy Constructor

## 10.1 Definition

A copy constructor is a special constructor that initializes a new
object using an existing object of the same class.

Common signature:

``` cpp
Student(const Student &source);
```

Breakdown: - `Student` = class name / constructor name -
`const Student&` = existing Student object ka const reference - `source`
= source object ka parameter name

## 10.2 Copy constructor kab call hota hai?

Example:

``` cpp
Student A(1, 15, "Navin", 6, 9.9);
Student C = A;
```

C ek new object hai jo A se initialize ho raha hai. Is situation mein
copy constructor use hota hai.

Another common form:

``` cpp
Student C(A);
```

Ye bhi copy initialization hai.

Note: Modern C++ mein kuch situations mein compiler copy elision kar
sakta hai. Lekin `Student C = A;` jaise existing lvalue se copy
initialization mein copy constructor required hota hai.

## 10.3 Reference kyun use karte hain?

Copy constructor ka parameter reference hona chahiye:

``` cpp
Student(const Student &source)
```

Agar parameter by value hota:

``` cpp
Student(Student source) // incorrect copy-constructor design
```

toh parameter banane ke liye phir copy constructor chahiye hota, jisse
recursive copying ki problem hoti.

`const` ka matlab source object ko is reference ke through modify nahi
karna.

------------------------------------------------------------------------

# 11. Shallow Copy vs Deep Copy

Ye lesson ka sabse important memory-management concept hai.

## 11.1 Shallow Copy

**Definition:** Shallow copy copies member values as-is. For a raw
pointer member, this means copying the address, not allocating separate
pointed-to memory.

Example:

``` cpp
this->gpa = source.gpa;
```

Suppose A ka `gpa` address 1000 hai. Shallow copy ke baad C ka `gpa` bhi
1000 hoga.

Concept:

``` text
Object A                 Object C
gpa = address 1000       gpa = address 1000
        \                  /
         \                /
          Heap memory at 1000
                 |
                9.9
```

Problem: 1. A aur C same memory ko point karte hain. 2. A ka destructor
memory delete karta hai. 3. C ka pointer ab freed memory ko point karta
hai. 4. C ka destructor same memory dobara delete karne ki koshish kar
sakta hai. 5. Double delete / undefined behaviour ho sakta hai.

## 11.2 Deep Copy

**Definition:** Deep copy creates a separate allocation for owned
dynamic data and copies the actual value into that new allocation.

Correct line:

``` cpp
this->gpa = new float(*source.gpa);
```

Breakdown: - `source.gpa` = source pointer ka address - `*source.gpa` =
source memory ke andar stored float value - `new float(...)` = ek nayi
memory allocation mein us value ko store karna

Concept:

``` text
Object A                 Object C
gpa = address 1000       gpa = address 2000
        |                       |
        v                       v
 Heap memory 1000          Heap memory 2000
      9.9                       9.9
```

A aur C ki values same hain, lekin allocations separate hain.

Agar C ka GPA change karein:

``` cpp
*C.gpa = 8.5;
```

Toh A ka GPA 9.9 hi rahega, C ka GPA 8.5 ho jayega.

## 11.3 Deep copy constructor

``` cpp
Student(const Student &source) {
    this->id = source.id;
    this->age = source.age;
    this->name = source.name;
    this->nos = source.nos;

    if (source.gpa != nullptr) {
        this->gpa = new float(*source.gpa);
    } else {
        this->gpa = nullptr;
    }
}
```

Null check isliye hai taaki source ka pointer null hone par usko
dereference na karein.

------------------------------------------------------------------------

# 12. Destructor

## 12.1 Definition

A destructor is a special member function that is automatically called
when an object is destroyed.

Syntax:

``` cpp
~Student() {
    delete gpa;
    gpa = nullptr;
}
```

Rules: 1. Destructor ka naam class name ke aage `~` lagakar banta hai.
2. Destructor ka return type nahi hota. 3. Destructor parameters accept
nahi karta. 4. Class ka ek destructor hota hai. 5. Object destroy hone
par destructor automatically execute hota hai.

## 12.2 Destructor kyun important hai?

Humne GPA ke liye dynamic memory allocate ki:

``` cpp
this->gpa = new float(gpa);
```

Toh us memory ko release bhi karna hoga:

``` cpp
delete gpa;
```

Destructor resource cleanup ke liye use hota hai.

## 12.3 Destructor kab call hota hai?

-   Automatic local object: jab uska scope end hota hai.
-   Dynamic object: matching `delete` execute hone par.
-   Objects same scope mein create hue hon: normal destruction reverse
    order of completed construction mein hoti hai.

Example:

``` cpp
Student A(...);
Student B(...);
Student C(...);
```

Scope end par destruction order:

``` text
C destroyed first
B destroyed second
A destroyed last
```

Ye LIFO (Last In, First Out) order hai.

------------------------------------------------------------------------

# 13. Copy Assignment Operator

Copy constructor aur copy assignment operator same nahi hain.

## 13.1 Definition

The copy assignment operator assigns the state of an existing object to
another object that has already been created.

Example:

``` cpp
Student A(1, 15, "Navin", 6, 9.9);

Student B;  // B already exists
B = A;      // copy assignment
```

Custom operator signature:

``` cpp
Student& operator=(const Student &source);
```

## 13.2 Copy constructor vs copy assignment

  -----------------------------------------------------------------------
  Copy Constructor                    Copy Assignment
  ----------------------------------- -----------------------------------
  New object initialize karta hai     Existing object ko assign karta hai

  `Student B = A;`                    `B = A;`

  Object creation ke time             Object creation ke baad
  -----------------------------------------------------------------------

## 13.3 Self-assignment check

``` cpp
if (this == &source) {
    return *this;
}
```

Agar:

``` cpp
A = A;
```

toh current object aur source same object hain. Is check se unnecessary
work aur memory handling problems avoid hoti hain.

## 13.4 Deep-copy assignment operator

``` cpp
Student& operator=(const Student &source) {
    if (this == &source) {
        return *this;
    }

    float *newGpa = nullptr;

    if (source.gpa != nullptr) {
        newGpa = new float(*source.gpa);
    }

    delete this->gpa;

    this->id = source.id;
    this->age = source.age;
    this->name = source.name;
    this->nos = source.nos;
    this->gpa = newGpa;

    return *this;
}
```

Important: - Pehle source ka GPA safely copy karne ke liye new
allocation banate hain. - Phir destination ka old GPA delete karte
hain. - Baaki data members copy karte hain. - New pointer destination ko
assign karte hain. - `*this` current object ko refer karta hai, aur
reference return karne se assignment chaining possible hoti hai.

------------------------------------------------------------------------

# 14. Rule of Three

**Definition:** If a class manually manages a resource and needs to
define any one of the destructor, copy constructor, or copy assignment
operator, it will generally need to define all three correctly.

Three functions:

1.  Destructor --- resource release karta hai.
2.  Copy Constructor --- new object ke liye resource ki independent copy
    banata hai.
3.  Copy Assignment Operator --- existing object ko safely independent
    copy assign karta hai.

Why connected?

Our class owns dynamic memory through `float *gpa`. Agar sirf destructor
likha aur compiler-generated copy operations use kiye, toh pointers
shallow copy ho sakte hain. Isse double deletion ya invalid memory
access ka risk hai.

## Rule of Five --- next related topic

Modern C++ mein Rule of Three ko extend karke Rule of Five bhi padhte
hain.

It includes: 1. Destructor 2. Copy constructor 3. Copy assignment
operator 4. Move constructor 5. Move assignment operator

Move semantics resources ko copy karne ke bajaye transfer karne mein
help karti hain. Isko next lesson ke roop mein padhein.

------------------------------------------------------------------------

# 15. Complete Corrected Student Program

Neeche complete revision program hai. Isme: - Default constructor -
Parameterized constructor - Deep copy constructor - Copy assignment
operator - Methods - Destructor - Stack/automatic objects - Dynamic
allocation - `new` and `delete`

``` cpp
#include <bits/stdc++.h>
using namespace std;

class Student {
public:
    // Attributes
    int id;
    int age;
    string name;
    int nos;
    float *gpa = nullptr;

    // 1. Default Constructor
    Student() {
        id = 0;
        age = 0;
        name = "";
        nos = 0;
        gpa = nullptr;

        cout << "Default Constructor called" << endl;
    }

    // 2. Parameterized Constructor
    Student(int id, int age, string name, int nos, float gpa) {
        this->id = id;
        this->age = age;
        this->name = name;
        this->nos = nos;

        this->gpa = new float(gpa);

        cout << "Parameterized Constructor called" << endl;
    }

    // 3. Deep Copy Constructor
    Student(const Student &source) {
        this->id = source.id;
        this->age = source.age;
        this->name = source.name;
        this->nos = source.nos;

        if (source.gpa != nullptr) {
            this->gpa = new float(*source.gpa);
        } else {
            this->gpa = nullptr;
        }

        cout << "Copy Constructor called" << endl;
    }

    // 4. Copy Assignment Operator
    Student& operator=(const Student &source) {
        cout << "Copy Assignment called" << endl;

        if (this == &source) {
            return *this;
        }

        float *newGpa = nullptr;

        if (source.gpa != nullptr) {
            newGpa = new float(*source.gpa);
        }

        delete this->gpa;

        this->id = source.id;
        this->age = source.age;
        this->name = source.name;
        this->nos = source.nos;
        this->gpa = newGpa;

        return *this;
    }

    // 5. Methods / Behaviours
    void study() {
        cout << name << " studying" << endl;
    }

    void sleep() {
        cout << name << " sleeping" << endl;
    }

    void bunk() {
        cout << name << " bunking" << endl;
    }

    // 6. Destructor
    ~Student() {
        cout << "Destructor called: " << name << endl;

        delete gpa;
        gpa = nullptr;
    }
};

int main() {

    // Automatic local objects
    Student A(1, 15, "Navin", 6, 9.9);
    Student B(2, 13, "Kajal", 4, 9.5);

    A.bunk();
    B.sleep();

    // Copy Constructor
    Student C = A;

    cout << "A GPA: " << *A.gpa << endl;
    cout << "C GPA: " << *C.gpa << endl;

    // Prove deep copy
    *C.gpa = 8.5;

    cout << "After changing C GPA:" << endl;
    cout << "A GPA: " << *A.gpa << endl;
    cout << "C GPA: " << *C.gpa << endl;

    // Copy Assignment
    Student D;
    D = A;

    cout << "D GPA: " << *D.gpa << endl;

    // Dynamic object
    Student *ptr = new Student(3, 14, "Babban", 7, 9.9);

    cout << ptr->name << endl;
    cout << ptr->age << endl;
    cout << *ptr->gpa << endl;

    ptr->study();

    // Destroy dynamic object
    delete ptr;
    ptr = nullptr;

    return 0;
}
```

## Program output --- important observations

Output order:

1.  A and B parameterized constructors
2.  A and B methods
3.  C copy constructor
4.  GPA values
5.  D default constructor
6.  D copy assignment
7.  Dynamic object's parameterized constructor
8.  Dynamic object's details and method
9.  Dynamic object's destructor on `delete ptr`
10. D, C, B, A destructors when `main()` ends

Exact destructor messages include the object names. D's name becomes
Navin after `D = A`, so D's destructor prints Navin.

------------------------------------------------------------------------

# 16. Common Mistakes and Their Fixes

  -----------------------------------------------------------------------
  Mistake                             Correct approach
  ----------------------------------- -----------------------------------
  Uninitialized pointer               Initialize with `nullptr`

  Forgetting to copy `gpa`            Implement deep copy

  `gpa = source.gpa` for owning raw   Allocate a separate copy
  pointer                             

  `delete` same address twice         Ensure each allocation has one
                                      owner/release

  Forgetting destructor cleanup       Release owned memory

  Using `.` with pointer              Use `->`

  Using `->` with normal object       Use `.`

  Forgetting `delete ptr`             Release manually allocated object

  Dereferencing null pointer          Check `ptr != nullptr` first

  Only writing destructor for owning  Also consider copy constructor and
  raw pointer                         copy assignment
  -----------------------------------------------------------------------

------------------------------------------------------------------------

# 17. C++ OOP and PHP / Laravel Connection

C++ and PHP have similar OOP fundamentals, although memory management
and language behaviour differ.

  -----------------------------------------------------------------------
  C++                                 PHP
  ----------------------------------- -----------------------------------
  `class Student {}`                  `class Student {}`

  `Student A;`                        `$student = new Student();`

  Constructor `Student()`             `__construct()`

  Destructor `~Student()`             `__destruct()`

  `this->name`                        `$this->name`

  `public`                            `public`

  `private`                           `private`

  `protected`                         `protected`

  `extends`                           `extends`

  `virtual` functions / overriding    Method overriding and dynamic
                                      dispatch
  -----------------------------------------------------------------------

PHP example:

``` php
<?php

class Student
{
    public int $id;
    public int $age;
    public string $name;
    public float $gpa;

    public function __construct(
        int $id,
        int $age,
        string $name,
        float $gpa
    ) {
        $this->id = $id;
        $this->age = $age;
        $this->name = $name;
        $this->gpa = $gpa;
    }

    public function study(): void
    {
        echo $this->name . " studying";
    }
}

$student = new Student(1, 15, "Navin", 9.9);

$student->study();
```

Laravel mein ye OOP knowledge kaam aayegi: - Models --- data aur
database interaction - Controllers --- HTTP requests handle karna -
Services --- business logic organize karna - Middleware --- request
filtering - Interfaces --- contracts define karna - Dependency Injection
--- dependencies provide karna - Inheritance and polymorphism ---
reusable and flexible design

Note: PHP generally automatic memory management karta hai. C++ ke raw
pointer wale `new float` / `delete` pattern ko Laravel/PHP mein directly
copy nahi karte.

------------------------------------------------------------------------

# 18. Interview Questions and Answers

### Q1. What is a class?

A class is a user-defined blueprint that defines data members and member
functions for its objects.

### Q2. What is an object?

An object is an instance of a class.

### Q3. What is a constructor?

A constructor is a special member function automatically called when an
object is created.

### Q4. What is a default constructor?

A constructor that can be called without arguments.

### Q5. What is a parameterized constructor?

A constructor that accepts parameters to initialize an object.

### Q6. What is a copy constructor?

A constructor that initializes a new object using an existing object of
the same class.

### Q7. Why does a copy constructor usually accept a reference?

To avoid copying the source object just to pass it as an argument, which
would cause recursive copy-constructor calls.

### Q8. What is the `this` pointer?

It is an implicit pointer to the current object in a non-static member
function.

### Q9. What is a pointer?

A variable that stores a memory address.

### Q10. What is dynamic memory allocation?

Allocating storage during program execution, commonly using `new` in
C++.

### Q11. What is shallow copy?

Copying pointer values/addresses as-is, which can cause multiple objects
to refer to the same resource.

### Q12. What is deep copy?

Creating a separate resource allocation and copying the actual data into
it.

### Q13. What is a destructor?

A special member function automatically called when an object is
destroyed.

### Q14. What is the difference between `.` and `->`?

`.` accesses members through an object; `->` accesses members through a
pointer to an object.

### Q15. What is the difference between `new` and `delete`?

`new` allocates and constructs; `delete` destroys and releases a
matching dynamically allocated object.

### Q16. What is the difference between copy constructor and copy assignment?

Copy constructor initializes a new object; copy assignment updates an
already-existing object.

### Q17. What is Rule of Three?

A resource-owning class that needs a custom destructor generally needs a
correct copy constructor and copy assignment operator too.

------------------------------------------------------------------------

# 19. Practice Tasks

Try solving these without looking at the solution.

## Beginner

-   [ ] Create a `Student` class with `id`, `age`, `name`.
-   [ ] Add `study()` and `sleep()` methods.
-   [ ] Create two objects.
-   [ ] Write a default constructor.
-   [ ] Write a parameterized constructor.

## Intermediate

-   [ ] Add a `float *gpa` member.
-   [ ] Allocate GPA dynamically in the parameterized constructor.
-   [ ] Write a destructor.
-   [ ] Create a copy constructor.
-   [ ] Test whether a shallow copy creates a shared pointer.
-   [ ] Implement deep copy.
-   [ ] Change copied object's GPA and verify original is unchanged.

## Advanced for this lesson

-   [ ] Implement copy assignment operator.
-   [ ] Handle self-assignment.
-   [ ] Test `A = A`.
-   [ ] Create a dynamic Student object using `new`.
-   [ ] Access it with `->`.
-   [ ] Destroy it with `delete`.
-   [ ] Explain Rule of Three in your own words.

------------------------------------------------------------------------

# 20. Quick Revision Cheat Sheet

  Topic                       One-line revision
  --------------------------- ----------------------------------------------------
  Class                       Blueprint for objects
  Object                      Instance of a class
  Attribute                   Data/state of an object
  Method                      Behaviour of an object
  Constructor                 Automatically initializes an object
  Default constructor         Can be called without arguments
  Parameterized constructor   Accepts arguments
  Copy constructor            Initializes new object from existing object
  `this`                      Pointer to current object
  Pointer                     Stores an address
  `nullptr`                   Null pointer value
  Stack / automatic storage   Local object's lifetime is scope-based
  Heap / dynamic storage      Dynamically allocated storage
  `new`                       Allocates and constructs
  `delete`                    Destroys and releases
  Shallow copy                Copies pointer address
  Deep copy                   Creates independent resource copy
  Destructor                  Cleans up object-owned resources
  Copy assignment             Copies into existing object
  Rule of Three               Destructor + copy constructor + copy assignment
  Rule of Five                Rule of Three + move constructor + move assignment

------------------------------------------------------------------------

# 21. What to Learn Next?

Recommended order after this lesson:

1.  Static data members and static member functions
2.  Encapsulation
3.  Abstraction
4.  Inheritance
5.  Types of inheritance
6.  Polymorphism
7.  Compile-time polymorphism
8.  Function overloading
9.  Operator overloading
10. Runtime polymorphism
11. Function overriding
12. Virtual functions
13. Virtual destructors
14. Rule of Five and move semantics
15. Smart pointers (`unique_ptr`, `shared_ptr`)

------------------------------------------------------------------------

## Final Revision Advice

Is lesson ko master karne ke liye sirf definitions yaad mat karo. Har
concept ka code khud type karke run karo.

Sabse important three lines:

``` cpp
this->gpa = new float(gpa);          // Allocate GPA memory

this->gpa = new float(*source.gpa);  // Deep copy

delete gpa;                          // Release GPA memory
```

Agar tum in lines ka difference, memory diagram aur object lifecycle
explain kar sakte ho, toh tumne is lesson ka core concept samajh liya
hai.

**Goal:** Class se object creation, constructor se initialization, copy
constructor se independent copy, aur destructor se cleanup --- ye
complete workflow confidently explain kar pana.
