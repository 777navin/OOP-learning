# Introduction to Object-Oriented Programming (OOP)

> **Source:** Love Babbar / CodeHelp lecture material supplied by Navin,
> titled *OOPS Concepts*.\
> **Scope:** This file focuses on the introductory lecture: why OOP is
> useful, limitations of procedural programming, what OOP means,
> classes, objects, attributes, and behaviour. The supplied screenshot
> also names the four OOP pillars: encapsulation, abstraction,
> polymorphism, and inheritance. Those pillars are introduced here, but
> each will need its own focused lecture note for full depth.\
> **Language:** Easy Hinglish (Roman Hindi + English technical terms).\
> **Practice goal:** OA MCQs, output tracing, C++/Java comparison, and
> interview preparation.\
> **Important:** Sections marked **Additional explanation** deepen the
> lecture using general programming knowledge; they are not claims about
> the exact lecture wording.

------------------------------------------------------------------------

## 1. Learning Objectives

After studying this file, you should be able to:

-   Explain why OOP was developed and what problems it tries to address.
-   Describe the limitations of a procedural or function-oriented
    approach as presented in the lecture.
-   Define OOP as a programming paradigm that models systems using
    objects.
-   Explain how objects combine **data/state** and **behaviour**.
-   Distinguish a **class** from an **object**.
-   Identify attributes and methods in a real-life example.
-   Model multiple students, people, or vehicles using a class and
    multiple objects.
-   Explain how classes help organize code and support modularity,
    reuse, and maintainability.
-   Write and run basic class/object examples in both C++ and Java.
-   Recognize the four commonly taught OOP pillars: encapsulation,
    abstraction, inheritance, and polymorphism.
-   Answer introductory OOP MCQs, output questions, and interview
    questions without confusing class, object, attribute, and method.

## 2. Prerequisites

Only basic programming knowledge is needed:

-   Variables and data types, such as `int`, `double`, and `string`.
-   Functions or methods.
-   Basic input/output.
-   How to compile/run a small C++ or Java program.

You do **not** need DSA or competitive-programming knowledge for this
topic.

## 3. Concept from Love Babbar

This section preserves the main ideas visible in the supplied lecture
PDF and screenshot.

### 3.1 Why OOP?

The lecture explains that OOP developed because limitations were
discovered in earlier programming approaches. To understand the
motivation, it first considers a function-oriented or procedural style
and asks how we would model hundreds of students, each with their own
properties, behaviours, and information that should be controlled.

### 3.2 The multiple-students problem

Imagine a program has hundreds or thousands of students. Each student
may have:

-   Properties such as `id`, `name`, `age`, and `marks`/`nos`.
-   Behaviours such as `study()`, `sleep()`, and `bunk()`.

If the program represents every student through scattered variables and
functions, the code can become difficult to organize. When the program
grows, it becomes harder to understand which data belongs to which
student and which functions should operate on it.

The lecture's central idea is to group related data and behaviour
together.

### 3.3 Drawbacks of functional/procedural programming listed in the lecture

The supplied material lists these drawbacks:

1.  It does not model real-world problems very well.
2.  If new data is added, functions may need to be modified to access
    that data.
3.  Global data can be accessible to many functions.
4.  Code may lack clear boundaries and well-defined structure.
5.  Programs can become monolithic and difficult to maintain as they
    grow in complexity.

**Precision note:** These are drawbacks of poorly structured procedural
designs, not a claim that every procedural program has all these
problems. Procedural programming can be modular and well-designed too.
OOP is one approach to managing complexity, not the only approach.

### 3.4 What is OOP?

The lecture describes OOP as:

-   A programming style for modelling real-world systems.
-   A style that divides a program into objects that can communicate
    with each other.
-   An object-based coding style in which each object has its own
    attributes and behaviour.
-   An approach that combines data and behaviour into a single unit,
    supporting modularity.
-   A way to improve reuse and maintainability by encapsulating data and
    behaviour inside objects.

### 3.5 Classes and objects

The lecture uses real-world entities such as cars, people, students, and
buildings.

-   A **class** is the blueprint that defines what its objects contain
    and what they can do.
-   An **object** is an instance of a class.
-   A student named Rahul can be modelled as one object created from a
    `Student` class.
-   Other students can be represented as separate objects of the same
    class.

### 3.6 Attributes and behaviour

The lecture defines:

-   **Attributes:** State or properties of an object.
-   **Behaviour:** Methods/functions an object can perform.

For a `Person` class, example attributes are `name`, `age`, and
`height`. Example behaviours are `speak()` and `eat()`.

### 3.7 Four pillars named in the screenshot

The screenshot's OOP concept table names:

-   **Encapsulation:** Combining data and methods in a unit, with
    controlled access to data.
-   **Abstraction:** Showing essential information and hiding
    unnecessary implementation details.
-   **Polymorphism:** The same interface or operation can behave
    differently in different contexts.
-   **Inheritance:** A class can derive or reuse characteristics from
    another class.

These are introductory descriptions. The dedicated explanations later in
this file are marked as additional learning where they go beyond the
source.

------------------------------------------------------------------------

## 4. Concepts Explained in Easy Hinglish

### 4.1 Programming paradigm kya hota hai?

Programming paradigm ka matlab hai programming karne ka ek broad style
ya approach. Jaise kisi real-world problem ko functions ke around
organize karna procedural style ho sakta hai, aur objects ke around
organize karna OOP style ho sakta hai.

Ek paradigm sirf syntax nahi hota. Ye decide karne mein help karta hai
ki code ko kaise organize karna hai.

**Interview definition:** A programming paradigm is a general approach
or style for structuring and writing programs.

### 4.2 Procedural approach mein problem kya ho sakti hai?

Maan lo humein college ke 500 students ka record maintain karna hai. Har
student ke paas ID, name, age aur marks hain. Student ke actions bhi ho
sakte hain, jaise study karna ya attendance mark karna.

Agar hum data aur functions ko unrelated jagah par rakhte hain, to: -
Data kis student ka hai, track karna difficult ho sakta hai. - Naya
field add karne par multiple functions update karne pad sakte hain. -
Shared/global data galti se modify ho sakta hai. - Code ke
responsibilities clear nahi reh sakte.

OOP ka idea hai ki related data aur behaviour ko ek logical unit mein
group kiya jaye.

**Important nuance:** Procedural programming mein bhi structures,
modules, and good function boundaries use kiye ja sakte hain. OOP har
problem ka automatic solution nahi hai. Suitable design choose karna
important hai.

### 4.3 Class kya hoti hai?

Class ek blueprint/template hoti hai. Ye define karti hai ki us type ke
objects ke paas kaunsa data hoga aur kaunse operations available honge.

Example: `Student` class define kar sakti hai: - Data: `name`, `age`,
`rollNumber` - Methods: `study()`, `introduce()`

Class khud ek specific student ka record nahi hai. Ye student objects ka
structure define karti hai.

**Interview definition:** A class is a user-defined type or blueprint
that defines the data and operations associated with its objects.

### 4.4 Object kya hota hai?

Object class ka instance hota hai. Object ke paas actual values hoti
hain.

Agar `Student` class blueprint hai, to: - `rahul` ek object ho sakta
hai. - `priya` doosra object ho sakti hai.

Dono same class se bane hain, lekin unki values alag ho sakti hain.

``` text
                 Student (Class)
                 /             \
                /               \
       rahul (Object)       priya (Object)
       name = "Rahul"       name = "Priya"
       age  = 20            age  = 21
```

Is diagram ka matlab: class common structure define karti hai; har
object apni values rakhta hai.

**Interview definition:** An object is an instance of a class with its
own state and access to the behaviour defined by the class.

### 4.5 Attributes / state kya hain?

Attributes object ki properties ya state ko represent karte hain.

Example: - `name = "Rahul"` - `age = 20` - `height = 1.72`

Yahan `name`, `age`, aur `height` attributes hain. Inmein stored values
object ki current state ko describe karti hain.

Ek object ki state time ke saath change ho sakti hai. Jaise `age`
birthday ke baad update ho sakti hai, ya bank account ka `balance`
deposit ke baad badal sakta hai.

### 4.6 Behaviour / methods kya hain?

Behaviour batata hai object kya kar sakta hai. OOP language mein is
behaviour ko methods ke through represent kiya jata hai.

Examples: - `student.study()` - `person.speak()` - `person.eat()` -
`car.start()`

Method aksar object ke data ke saath kaam karta hai. Example:
`introduce()` method object ke `name` aur `age` ko use karke
introduction print kar sakta hai.

### 4.7 Data + behaviour ko saath kyun rakhte hain?

Suppose `BankAccount` object ke paas `balance` hai aur `deposit()`
method hai. Agar balance aur deposit operation logically ek hi entity se
related hain, to unhe ek class mein rakhna natural hai.

``` text
BankAccount
+----------------------+
| Data / State         |
| balance              |
+----------------------+
| Behaviour / Methods  |
| deposit()            |
| withdraw()           |
| getBalance()         |
+----------------------+
```

Isse code ka ownership clear hota hai: account-related data aur
account-related operations ek jagah par milte hain.

**Additional explanation:** Data aur behaviour ko class mein rakhna
encapsulation ki taraf ek step hai. Strong encapsulation ke liye access
rules bhi sahi set karne hote hain. Sirf class bana dena data ko
automatically private nahi banata in every language.

### 4.8 Modularity, reusability, maintainability

-   **Modularity:** Program ko understandable, focused parts mein divide
    karna.
-   **Reusability:** Ek class ko multiple objects ya program ke multiple
    parts mein use kar pana.
-   **Maintainability:** Code ko understand, test, correct, aur extend
    karna comparatively easy hona.

Ek `Student` class likhne ke baad har student ke liye nayi class likhne
ki zaroorat nahi. Same class se multiple objects ban sakte hain.

### 4.9 OOP ke four pillars ka overview

  -----------------------------------------------------------------------
  Pillar                  Easy Hinglish meaning   Simple example
  ----------------------- ----------------------- -----------------------
  Encapsulation           Data aur related        Bank balance ko private
                          methods ko group karna, rakhna
                          aur data access ko      
                          control karna           

  Abstraction             Important operation     ATM par withdraw option
                          dikhana, internal       use karna
                          details hide karna      

  Inheritance             Existing class se       `Car` aur `Bike`, dono
                          related class banana    `Vehicle` se
                          aur selected features   
                          inherit karna           

  Polymorphism            Same                    Different notification
                          operation/interface ka  types ka `send()`
                          different objects ke    
                          liye different          
                          behaviour               
  -----------------------------------------------------------------------

Ye overview hai. Har pillar ke complete rules, language details, aur
traps ke liye dedicated notes banane chahiye.

------------------------------------------------------------------------

## 5. Real-Life Visualizations

### 5.1 Student class

**Real-world situation:** College mein bahut saare students hain. Sabke
paas common fields hain, lekin values alag hain.

**OOP mapping:** - Class: `Student` - Attributes: `name`, `rollNumber`,
`age` - Methods: `study()`, `introduce()` - Objects: Rahul, Priya, Aman

``` text
                  +------------------+
                  | Student (Class)  |
                  +------------------+
                  | name             |
                  | rollNumber       |
                  | age              |
                  +------------------+
                  | study()          |
                  | introduce()      |
                  +------------------+
                      /     |     \
                     /      |      \
                Rahul      Priya    Aman
                Object     Object   Object
```

**Analogy ki limit:** Real students class ki tarah software blueprint se
create nahi hote. Ye programming model hai jo real-world data ko
represent karta hai.

### 5.2 Car class

**Real-world situation:** Cars ke common features ho sakte hain, jaise
brand, color, speed, aur start/stop operations.

**OOP mapping:** - Class: `Car` - Attributes: `brand`, `color`,
`speed` - Methods: `start()`, `accelerate()`, `stop()` - Objects: ek
blue car aur ek red car

Har object ke methods same class se defined ho sakte hain, lekin state
alag hoti hai.

### 5.3 Person class

Lecture ke Person example mein `name`, `age`, `height` jaise attributes
aur `speak()`, `eat()` jaise behaviours dikhaye gaye hain.

``` text
Person (Class)
  Attributes: name, age, height
  Methods:    speak(), eat()

  Rahul: name="Rahul", age=20, height=1.72
  Kunal: name="Kunal", age=22, height=1.80
```

### 5.4 Bank account as an additional example

Bank account example encapsulation ko introduce karne ke liye useful
hai.

-   `balance` state hai.
-   `deposit()` behaviour hai.
-   `withdraw()` behaviour hai.
-   A well-designed class invalid withdrawals ko reject kar sakti hai.

Analogy ki limit: Actual banking systems mein authentication,
transactions, concurrency, audit logs, and database consistency jaise
additional concerns hote hain. Beginner example un sab ko implement nahi
karta.

------------------------------------------------------------------------

## 6. Visual Diagrams

### 6.1 Class versus object

``` text
           Blueprint / Class
             +-----------+
             | Student   |
             | name      |
             | age       |
             | study()   |
             +-----------+
               /       \
              /         \
     +-------------+  +-------------+
     | Object 1    |  | Object 2    |
     | Rahul, 20   |  | Priya, 21   |
     +-------------+  +-------------+
```

**Explanation:** `Student` structure define karta hai. Rahul aur Priya
ke objects us structure ke separate instances hain.

### 6.2 Attributes versus behaviour

``` text
+---------------------------+
| Person                    |
+---------------------------+
| Attributes / State        |
| name, age, height         |
+---------------------------+
| Behaviour / Methods       |
| speak(), eat()            |
+---------------------------+
```

**Explanation:** Upper data section object ko describe karta hai. Lower
methods section object ke actions represent karta hai.

### 6.3 OOP concept map

``` text
OOP
 |
 +-- Class  ------ defines structure and methods
 |
 +-- Object ----- instance with its own state
 |
 +-- Attributes - properties/state
 |
 +-- Methods ---- behaviour/actions
 |
 +-- Four pillars
       +-- Encapsulation
       +-- Abstraction
       +-- Inheritance
       +-- Polymorphism
```

**Explanation:** Class aur object OOP ke core building blocks hain. Four
pillars object-oriented design ke major principles hain.

------------------------------------------------------------------------

## 7. C++ Implementation

### 7.1 Simple example: Student class and objects

``` cpp
#include <iostream>
#include <string>
using namespace std;

class Student {
public:
    string name;
    int age;
    int rollNumber;

    void introduce() const {
        cout << "My name is " << name
             << ", age " << age
             << ", roll number " << rollNumber << ".\n";
    }

    void study() const {
        cout << name << " is studying.\n";
    }
};

int main() {
    Student rahul;
    rahul.name = "Rahul";
    rahul.age = 20;
    rahul.rollNumber = 101;

    Student priya;
    priya.name = "Priya";
    priya.age = 21;
    priya.rollNumber = 102;

    rahul.introduce();
    rahul.study();

    priya.introduce();
    priya.study();

    return 0;
}
```

**Expected output**

``` text
My name is Rahul, age 20, roll number 101.
Rahul is studying.
My name is Priya, age 21, roll number 102.
Priya is studying.
```

**Important lines explained:**

-   `class Student` defines a new class.
-   `public:` means these members can be accessed from outside the
    class.
-   `string name`, `int age`, and `int rollNumber` are data
    members/attributes.
-   `introduce()` and `study()` are member functions/methods.
-   `Student rahul;` creates an object named `rahul`.
-   `rahul.name = "Rahul";` assigns a value to that object's attribute.
-   `rahul.introduce();` calls the method on that object.
-   `const` after a member function indicates that the method does not
    modify the object's non-`mutable` data members.

**Beginner note:** This example uses `public` fields to make the
class/object relationship easy to see. In production designs, fields are
often made `private` and accessed through controlled methods.

### 7.2 Additional example: encapsulated BankAccount

``` cpp
#include <iostream>
#include <string>
using namespace std;

class BankAccount {
private:
    string owner;
    double balance;

public:
    BankAccount(const string& accountOwner, double openingBalance)
        : owner(accountOwner), balance(openingBalance) {}

    bool deposit(double amount) {
        if (amount <= 0) {
            return false;
        }
        balance += amount;
        return true;
    }

    bool withdraw(double amount) {
        if (amount <= 0 || amount > balance) {
            return false;
        }
        balance -= amount;
        return true;
    }

    double getBalance() const {
        return balance;
    }

    string getOwner() const {
        return owner;
    }
};

int main() {
    BankAccount account("Navin", 1000.0);

    account.deposit(500.0);
    bool withdrawn = account.withdraw(200.0);

    cout << "Owner: " << account.getOwner() << '\n';
    cout << "Withdrawal successful: "
         << (withdrawn ? "Yes" : "No") << '\n';
    cout << "Balance: " << account.getBalance() << '\n';

    return 0;
}
```

**Expected output**

``` text
Owner: Navin
Withdrawal successful: Yes
Balance: 1300
```

**Why this is better than public balance:** - `balance` is private, so
outside code cannot directly write `account.balance = -999`. -
`deposit()` and `withdraw()` validate amounts. - The class controls how
its state changes.

**C++ rule:** `private` members are accessible only from the class's
member functions and friends. A constructor is used to initialize the
new object's state.

### 7.3 Common C++ mistakes

**Mistake 1: Using an object before initializing its built-in data
members**

``` cpp
class Student {
public:
    int age;
};

int main() {
    Student s;
    // s.age has an indeterminate value here.
}
```

Prefer initializing members, for example `Student s{}` in this simple
case, or use a constructor that sets valid values.

**Mistake 2: Confusing a class with an object**

``` cpp
class Student {};
Student s; // s is an object; Student is the class.
```

**Mistake 3: Forgetting that access specifiers matter**

``` cpp
class Example {
    int value; // private by default in a class
};
```

In C++, members of a `class` are private by default. Members of a
`struct` are public by default.

------------------------------------------------------------------------

## 8. Java Implementation

### 8.1 Same Student example in Java

Save this as `Main.java`.

``` java
class Student {
    String name;
    int age;
    int rollNumber;

    void introduce() {
        System.out.println(
            "My name is " + name
            + ", age " + age
            + ", roll number " + rollNumber + "."
        );
    }

    void study() {
        System.out.println(name + " is studying.");
    }
}

public class Main {
    public static void main(String[] args) {
        Student rahul = new Student();
        rahul.name = "Rahul";
        rahul.age = 20;
        rahul.rollNumber = 101;

        Student priya = new Student();
        priya.name = "Priya";
        priya.age = 21;
        priya.rollNumber = 102;

        rahul.introduce();
        rahul.study();

        priya.introduce();
        priya.study();
    }
}
```

**Expected output**

``` text
My name is Rahul, age 20, roll number 101.
Rahul is studying.
My name is Priya, age 21, roll number 102.
Priya is studying.
```

**Hinglish explanation:**

-   `class Student` class define karta hai.
-   `new Student()` ek naya object create karta hai.
-   `rahul` aur `priya` reference variables hain jo objects ko refer
    karte hain.
-   Har object ke instance fields ki apni values hoti hain.
-   `introduce()` aur `study()` instance methods hain.

**Java note:** Instance fields ko explicitly set na kiya jaye to unhe
default values milti hain, jaise `int` ke liye `0` aur reference types
ke liye `null`. Lekin meaningful program mein valid initialization karna
better hai.

### 8.2 Encapsulated BankAccount in Java

Save as `Main.java`.

``` java
class BankAccount {
    private final String owner;
    private double balance;

    public BankAccount(String owner, double openingBalance) {
        if (openingBalance < 0) {
            throw new IllegalArgumentException(
                "Opening balance cannot be negative"
            );
        }
        this.owner = owner;
        this.balance = openingBalance;
    }

    public boolean deposit(double amount) {
        if (amount <= 0) {
            return false;
        }
        balance += amount;
        return true;
    }

    public boolean withdraw(double amount) {
        if (amount <= 0 || amount > balance) {
            return false;
        }
        balance -= amount;
        return true;
    }

    public double getBalance() {
        return balance;
    }

    public String getOwner() {
        return owner;
    }
}

public class Main {
    public static void main(String[] args) {
        BankAccount account = new BankAccount("Navin", 1000.0);

        account.deposit(500.0);
        boolean withdrawn = account.withdraw(200.0);

        System.out.println("Owner: " + account.getOwner());
        System.out.println(
            "Withdrawal successful: " + (withdrawn ? "Yes" : "No")
        );
        System.out.println("Balance: " + account.getBalance());
    }
}
```

**Expected output**

``` text
Owner: Navin
Withdrawal successful: Yes
Balance: 1300.0
```

**Java-specific notes:** - `private` fields cannot be accessed directly
from unrelated code. - `this.owner` means the current object's `owner`
field. - `final` on `owner` means the field can be assigned once during
initialization and not reassigned afterward. - Java uses references to
objects. `account` is a reference variable, not the object itself. -
Java automatically manages object memory through garbage collection, but
garbage collection does not remove the need to design object lifetimes
and resource handling carefully.

### 8.3 Common Java mistakes

**Mistake 1: Forgetting `new` for ordinary class instances**

``` java
Student s = new Student();
```

**Mistake 2: Thinking each reference variable creates a separate object
automatically**

``` java
Student first = new Student();
Student second = first;
```

Here `first` and `second` refer to the **same object**. This is
different from creating two separate objects with two `new Student()`
expressions.

**Mistake 3: Assuming fields and local variables have the same
defaults**

Instance fields receive default values. Local variables inside methods
must be definitely assigned before use.

------------------------------------------------------------------------

## 9. C++ vs Java Comparison

  ---------------------------------------------------------------------------------
  Feature                 C++                        Java
  ----------------------- -------------------------- ------------------------------
  Class declaration       `class Student { ... };`   `class Student { ... }`

  Object creation         `Student s;` can create an `Student s = new Student();`
                          automatic object           creates an object and stores a
                                                     reference

  Object access           `s.name` for an object;    `s.name` through a reference
                          `ptr->name` for a pointer  

  Default access in a     `private`                  Package-private when no
  class                                              modifier is written

  Instance fields without Built-in members of an     Fields receive default values
  explicit initialization uninitialized automatic    
                          object can be              
                          indeterminate              

  Methods                 Non-virtual methods use    Instance methods are generally
                          static binding based on    dynamically dispatched unless
                          the expression's type;     restricted by rules such as
                          virtual functions support  `static`, `private`, or
                          dynamic dispatch           `final`

  Memory management       Automatic storage, RAII,   Garbage-collected memory
                          smart pointers, and manual management
                          allocation are available   

  Multiple class          Supported                  A class extends one class, but
  inheritance                                        can implement multiple
                                                     interfaces

  Constructor syntax      Same name as class         Same name as class

  Terminator after class  Class definition ends with No semicolon required after a
                          `;`                        class declaration

  Fields and methods      Access can be              Access can be
                          public/private/protected   public/private/protected, plus
                                                     package-level access when no
                                                     modifier is used
  ---------------------------------------------------------------------------------

**Remember:** Both languages support classes and objects, but their
object creation, memory management, default access, and method dispatch
rules are not identical.

------------------------------------------------------------------------

## 10. Internal Working and Advanced Concepts

This section adds useful interview depth beyond the introductory source.

### 10.1 Class definition versus object storage

A class definition describes the structure and operations. Each ordinary
object has its own non-static instance data.

``` cpp
class Student {
public:
    int age;
};

Student a;
Student b;
a.age = 20;
b.age = 21;
```

`a.age` and `b.age` are separate data members belonging to different
objects.

In Java, two objects created using `new Student()` similarly have
separate instance fields. But if two Java variables refer to the same
object, changes through either variable are visible through the same
object.

### 10.2 Object identity and references

``` java
Student a = new Student();
Student b = a;
```

The assignment copies the reference, not the entire object. Therefore,
`a == b` is `true` because both references point to the same object.

In C++, ordinary object assignment can copy an object's members:

``` cpp
Student a;
Student b = a; // creates b as a copy of a, for this simple class
```

C++ pointers/references can also refer to the same object. Do not assume
Java reference assignment and C++ object copying are the same operation.

### 10.3 Instance members versus static members

An **instance field** belongs to each object. A **static field** belongs
to the class-level shared state.

``` cpp
class Student {
public:
    string name;
    static int totalStudents;
};

int Student::totalStudents = 0;
```

`name` is per object; `totalStudents` is shared at class level. Java
also supports `static` fields and methods.

Use static members only when the information or operation genuinely
belongs to the class as a whole.

### 10.4 Encapsulation is more than grouping

Grouping fields and methods is the basic idea. Strong encapsulation also
controls how internal state can be accessed and changed.

For example, making `balance` private and validating
deposits/withdrawals protects the class invariant that the balance
should not become negative through those public operations.

### 10.5 OOP is a tool, not a universal rule

OOP can improve structure for systems with entities, state, and
behaviour. It can also be overused. A small calculation or a simple
transformation may be clearer as a function without creating a class for
everything.

**Interview-ready insight:** Choose a design that keeps responsibilities
clear and makes changes safe. OOP is one useful design approach, not a
requirement for every piece of code.

------------------------------------------------------------------------

## 11. Common Mistakes and Interview Traps

1.  **Class and object are not synonyms.** A class defines a
    type/blueprint; an object is an instance.
2.  **Attributes and behaviours are different.** `age` is an attribute;
    `study()` is a method.
3.  **A class does not mean one object.** Many objects can be created
    from one class.
4.  **Objects from one class need not have identical state.** Rahul and
    Priya can have different names and ages.
5.  **OOP does not automatically make code secure.** Access control and
    validation must be designed correctly.
6.  **OOP is not the same as only using classes.** Good object-oriented
    design also considers responsibilities and object interactions.
7.  **Procedural code is not automatically bad.** The lecture lists
    common limitations, but procedural code can be modular and
    maintainable.
8.  **Java variables of class type hold references.** Assigning one
    reference variable to another does not create a new object.
9.  **C++ object creation differs from Java.** `Student s;` and
    `Student s = new Student();` do not have identical semantics.
10. **C++ class members are private by default.** Java members without
    an access modifier have package-level access, not `private`.
11. **A method call belongs to an object only when it is an instance
    method.** Static methods belong to the class-level API and do not
    operate on a particular instance in the same way.
12. **A real-life analogy is a model, not reality itself.** A `Car`
    class does not reproduce every physical or legal detail of a real
    car.

------------------------------------------------------------------------

## 12. OA Preparation

**How to use this section:** Attempt all questions first. Write down
your answers before opening the answer key.

### A. Conceptual MCQs

#### Q1. Difficulty: Easy

What does a class primarily define?

A. Only one object's current values\
B. A blueprint/type describing data and operations\
C. A program's output\
D. A single function call

#### Q2. Difficulty: Easy

Which is an example of an attribute of a `Person` object?

A. `speak()`\
B. `eat()`\
C. `age`\
D. `introduce()`

#### Q3. Difficulty: Easy

An object is best described as:

A. A comment in source code\
B. An instance of a class\
C. A compiler error\
D. A data type that cannot store values

#### Q4. Difficulty: Medium

Which option best expresses the central OOP idea described in the
lecture?

A. Put all program data into global variables\
B. Keep every operation in one large function\
C. Combine related data and behaviour into objects\
D. Avoid defining reusable types

#### Q5. Difficulty: Medium

Which statement about procedural programming is most accurate?

A. Procedural programs can never be modular\
B. Every procedural program must use global variables\
C. Poorly structured procedural programs can become difficult to
maintain\
D. Procedural programming cannot use functions

#### Q6. Difficulty: Medium

A `Student` class has `name` and `age`. Two objects are created. Which
is correct?

A. Both objects must have the same name\
B. Each object can have its own `name` and `age` values\
C. The class itself must store every student's individual age in one
field\
D. Objects cannot call methods

#### Q7. Difficulty: Medium

Which list matches the four pillars named in the supplied screenshot?

A. Compilation, linking, execution, debugging\
B. Encapsulation, abstraction, inheritance, polymorphism\
C. Variables, loops, arrays, recursion\
D. Input, output, storage, networking

#### Q8. Difficulty: Hard

Which statement is the strongest explanation of encapsulation?

A. Every field must be public\
B. Data and related operations are grouped, and access to internal state
can be controlled\
C. Every class must inherit from two classes\
D. A method can never return a value

### B. Output-Based Questions

#### Q9. Difficulty: Easy, C++

Predict the output.

``` cpp
#include <iostream>
#include <string>
using namespace std;

class Student {
public:
    string name;

    void introduce() const {
        cout << name << '\n';
    }
};

int main() {
    Student a;
    Student b;
    a.name = "Rahul";
    b.name = "Priya";
    a.introduce();
    b.introduce();
}
```

#### Q10. Difficulty: Medium, Java

Predict the output.

``` java
class Box {
    int value;
}

public class Main {
    public static void main(String[] args) {
        Box a = new Box();
        Box b = a;
        a.value = 7;
        b.value = 12;
        System.out.println(a.value);
    }
}
```

#### Q11. Difficulty: Medium, Java

Predict the output.

``` java
class Student {
    int age;
}

public class Main {
    public static void main(String[] args) {
        Student a = new Student();
        Student b = new Student();
        a.age = 19;
        b.age = 22;
        System.out.println(a.age + " " + b.age);
    }
}
```

#### Q12. Difficulty: Medium, C++

What does this program print?

``` cpp
#include <iostream>
using namespace std;

class Counter {
public:
    int value = 0;
};

int main() {
    Counter first;
    Counter second;
    first.value = 3;
    second.value = 8;
    cout << first.value + second.value << '\n';
}
```

### C. Compilation and Error Questions

#### Q13. Difficulty: Medium, C++

Does this compile? Explain.

``` cpp
class Student {
    int age;
};

int main() {
    Student s;
    s.age = 20;
}
```

#### Q14. Difficulty: Medium, Java

Does this compile?

``` java
class Student {
    private int age;
}

public class Main {
    public static void main(String[] args) {
        Student s = new Student();
        s.age = 20;
    }
}
```

#### Q15. Difficulty: Medium, Java

What is the key issue here?

``` java
class Student {
    int age;
}

public class Main {
    public static void main(String[] args) {
        Student s;
        System.out.println(s.age);
    }
}
```

### D. Conceptual Traps

#### Q16. Difficulty: Medium

True or false: A class and an object are exactly the same thing.

#### Q17. Difficulty: Medium

True or false: If two Java variables refer to the same object, a field
update through one reference can be observed through the other.

#### Q18. Difficulty: Hard

True or false: OOP guarantees that a program will be modular,
maintainable, and secure even if classes are poorly designed.

### E. C++ vs Java Questions

#### Q19. Difficulty: Medium

Which statement is correct?

A. Java class-type variables directly contain the complete object in
every case\
B. Java class-type variables hold references to objects\
C. C++ never allows an object to be created without `new`\
D. C++ and Java use identical memory management

#### Q20. Difficulty: Hard

What happens in the following Java code?

``` java
Student first = new Student();
Student second = first;
```

A. Two separate Student objects are created\
B. No object is created\
C. One object is created, and both variables refer to it\
D. The code is always a compilation error

------------------------------------------------------------------------

## 13. Coding Practice

Attempt the exercises before checking the solutions in Section 14. Keep
each exercise focused on classes, objects, attributes, and methods.

### Exercise 1: Student Introduction

-   **Difficulty:** Easy
-   **Real-life context:** College student records.
-   **Requirements:** Create a `Student` class with `name`, `age`, and
    `rollNumber`.
-   Add an `introduce()` method that prints all three values.
-   Create at least two objects with different values.
-   **Expected behaviour:** Each object prints its own data.
-   **Hints:** Do not create a separate class for every student.
-   **Test cases:** Use two names, different ages, and different roll
    numbers.
-   **C++ starter:**

``` cpp
#include <iostream>
#include <string>
using namespace std;

class Student {
    // Add attributes and introduce()
};

int main() {
    // Create two Student objects and test them
}
```

-   **Java starter:**

``` java
class Student {
    // Add attributes and introduce()
}

public class Main {
    public static void main(String[] args) {
        // Create two Student objects and test them
    }
}
```

### Exercise 2: Person Behaviour

-   **Difficulty:** Easy
-   **Real-life context:** Representing people.
-   **Requirements:** Create `Person` with `name`, `age`, and `height`;
    implement `speak()` and `eat()`.
-   **Expected behaviour:** Each method should identify which person is
    performing the action.
-   **Hints:** Keep attributes and related methods inside the same
    class.
-   **Test cases:** Create two people and call both methods on each
    object.

### Exercise 3: Car Information

-   **Difficulty:** Easy to Medium
-   **Real-life context:** A small vehicle registry.
-   **Requirements:** Create `Car` with `brand`, `color`, and `speed`;
    add `displayInfo()` and `stop()`.
-   **Expected behaviour:** `displayInfo()` prints the car's current
    information; `stop()` sets speed to zero and prints a message.
-   **Hints:** The `speed` value belongs to each car object.
-   **Test cases:** Create two cars with different speeds. Stop only one
    and confirm the other car's speed is unchanged.

### Exercise 4: Bank Account with Controlled Access

-   **Difficulty:** Medium
-   **Real-life context:** A simple account model.
-   **Requirements:** Store `owner` and `balance`; make the balance
    private; provide `deposit()`, `withdraw()`, and `getBalance()`.
-   Reject non-positive deposit/withdrawal amounts and withdrawals
    larger than the balance.
-   **Expected behaviour:** Invalid operations leave the balance
    unchanged.
-   **Hints:** A private field should be modified through public
    methods.
-   **Test cases:** Deposit a positive amount, reject a zero deposit,
    withdraw a valid amount, reject an overdraw, and inspect the final
    balance.

### Exercise 5: Model a Classroom

-   **Difficulty:** Medium
-   **Real-life context:** A classroom containing many students.
-   **Requirements:** Create `Student` and `Classroom` classes. For this
    introductory exercise, `Classroom` may hold a small fixed set of
    students or a simple collection.
-   Add a method that prints each student's introduction.
-   **Expected behaviour:** One classroom can contain multiple distinct
    student objects.
-   **Hints:** Focus on the relationship between objects. Do not add
    unrelated algorithmic tasks.
-   **Test cases:** Add at least three students and check that each
    student's values are printed correctly.

------------------------------------------------------------------------

## 14. Coding Practice Solutions

### Solution 1: Student Introduction in C++

``` cpp
#include <iostream>
#include <string>
using namespace std;

class Student {
public:
    string name;
    int age;
    int rollNumber;

    void introduce() const {
        cout << name << ", age " << age
             << ", roll number " << rollNumber << '\n';
    }
};

int main() {
    Student first;
    first.name = "Rahul";
    first.age = 20;
    first.rollNumber = 101;

    Student second;
    second.name = "Priya";
    second.age = 21;
    second.rollNumber = 102;

    first.introduce();
    second.introduce();
}
```

### Solution 1: Student Introduction in Java

``` java
class Student {
    String name;
    int age;
    int rollNumber;

    void introduce() {
        System.out.println(name + ", age " + age
            + ", roll number " + rollNumber);
    }
}

public class Main {
    public static void main(String[] args) {
        Student first = new Student();
        first.name = "Rahul";
        first.age = 20;
        first.rollNumber = 101;

        Student second = new Student();
        second.name = "Priya";
        second.age = 21;
        second.rollNumber = 102;

        first.introduce();
        second.introduce();
    }
}
```

### Solution 2: Person Behaviour in C++

``` cpp
#include <iostream>
#include <string>
using namespace std;

class Person {
public:
    string name;
    int age;
    double height;

    void speak() const {
        cout << name << " is speaking.\n";
    }

    void eat() const {
        cout << name << " is eating.\n";
    }
};

int main() {
    Person rahul{"Rahul", 20, 1.72};
    Person priya{"Priya", 21, 1.65};

    rahul.speak();
    rahul.eat();
    priya.speak();
    priya.eat();
}
```

### Solution 2: Person Behaviour in Java

``` java
class Person {
    String name;
    int age;
    double height;

    void speak() {
        System.out.println(name + " is speaking.");
    }

    void eat() {
        System.out.println(name + " is eating.");
    }
}

public class Main {
    public static void main(String[] args) {
        Person rahul = new Person();
        rahul.name = "Rahul";
        rahul.age = 20;
        rahul.height = 1.72;

        Person priya = new Person();
        priya.name = "Priya";
        priya.age = 21;
        priya.height = 1.65;

        rahul.speak();
        rahul.eat();
        priya.speak();
        priya.eat();
    }
}
```

### Solution 3: Car Information in C++

``` cpp
#include <iostream>
#include <string>
using namespace std;

class Car {
public:
    string brand;
    string color;
    int speed = 0;

    void displayInfo() const {
        cout << brand << " " << color
             << ", speed " << speed << '\n';
    }

    void stop() {
        speed = 0;
        cout << brand << " has stopped.\n";
    }
};

int main() {
    Car first{"Toyota", "Blue", 50};
    Car second{"Honda", "Red", 30};

    first.stop();
    first.displayInfo();
    second.displayInfo();
}
```

### Solution 3: Car Information in Java

``` java
class Car {
    String brand;
    String color;
    int speed;

    void displayInfo() {
        System.out.println(brand + " " + color
            + ", speed " + speed);
    }

    void stop() {
        speed = 0;
        System.out.println(brand + " has stopped.");
    }
}

public class Main {
    public static void main(String[] args) {
        Car first = new Car();
        first.brand = "Toyota";
        first.color = "Blue";
        first.speed = 50;

        Car second = new Car();
        second.brand = "Honda";
        second.color = "Red";
        second.speed = 30;

        first.stop();
        first.displayInfo();
        second.displayInfo();
    }
}
```

### Solution 4: Bank Account

Use the complete `BankAccount` implementations in Sections 7.2 and 8.2.
They demonstrate private state, public methods, input validation, and
reading state through a getter.

**Expected final balance for the example:** Start at 1000, deposit 500,
withdraw 200, final balance is 1300.

### Solution 5: Classroom model in Java

``` java
import java.util.ArrayList;
import java.util.List;

class Student {
    private final String name;
    private final int age;

    Student(String name, int age) {
        this.name = name;
        this.age = age;
    }

    void introduce() {
        System.out.println(name + ", age " + age);
    }
}

class Classroom {
    private final List<Student> students = new ArrayList<>();

    void addStudent(Student student) {
        students.add(student);
    }

    void introduceStudents() {
        for (Student student : students) {
            student.introduce();
        }
    }
}

public class Main {
    public static void main(String[] args) {
        Classroom classroom = new Classroom();
        classroom.addStudent(new Student("Rahul", 20));
        classroom.addStudent(new Student("Priya", 21));
        classroom.addStudent(new Student("Aman", 19));

        classroom.introduceStudents();
    }
}
```

**Expected output**

``` text
Rahul, age 20
Priya, age 21
Aman, age 19
```

**Hinglish explanation:** `Classroom` ke paas multiple `Student` objects
ki collection hai. Har student apni state rakhta hai. Classroom method
har object ko uska introduction dene ke liye call karta hai.

------------------------------------------------------------------------

## 15. Interview Preparation

### Beginner questions

#### Q1. What is OOP?

**Easy Hinglish answer:** OOP ek programming paradigm hai jisme hum
program ko objects ke around organize karte hain. Har object ke paas
apna data/state aur behaviour/methods ho sakte hain. Isse real-world
entities ko code mein model karna aur related code ko organize karna
easy ho sakta hai.

**Interview English:** Object-Oriented Programming is a programming
paradigm that organizes software around objects, which combine state and
behaviour.

#### Q2. What is a class?

**Easy Hinglish answer:** Class ek blueprint ya user-defined type hoti
hai jo define karti hai ki objects mein kaunse attributes aur methods
honge.

**Interview English:** A class is a blueprint or user-defined type that
defines the data and operations of its instances.

#### Q3. What is an object?

**Easy Hinglish answer:** Object class ka instance hota hai. Uske paas
apni state hoti hai aur class ke methods use kar sakta hai.

**Interview English:** An object is an instance of a class with its own
state and access to the behaviour defined by that class.

#### Q4. What are attributes and methods?

**Easy Hinglish answer:** Attributes object ki properties ya state store
karte hain, jaise `name` aur `age`. Methods object ke operations
represent karte hain, jaise `study()` ya `introduce()`.

**Interview English:** Attributes represent an object's state, while
methods represent operations or behaviour.

### Intermediate questions

#### Q5. Why do we use OOP?

**Easy Hinglish answer:** OOP related data aur behaviour ko objects mein
organize kar sakta hai. Isse responsibilities clear ho sakti hain aur
code ko reuse, test, aur maintain karna easier ho sakta hai. Lekin
benefits design quality par depend karte hain.

**Interview English:** OOP helps organize related state and behaviour
into objects, which can improve modularity, reuse, and maintainability
when designed appropriately.

#### Q6. What is the difference between a class and an object?

**Easy Hinglish answer:** Class structure define karti hai; object us
structure ka actual instance hota hai. Ek class se multiple objects ban
sakte hain, aur unki instance values alag ho sakti hain.

**Interview English:** A class defines a type; an object is a concrete
instance of that type.

#### Q7. What is the difference between state and behaviour?

**Easy Hinglish answer:** State object ki current values ko describe
karti hai. Behaviour batata hai object kya actions perform kar sakta
hai.

**Interview English:** State describes an object's current data, while
behaviour describes the operations it can perform.

#### Q8. Does OOP eliminate all problems of procedural programming?

**Easy Hinglish answer:** Nahi. OOP code organization ke liye useful
approach hai, lekin poorly designed classes bhi tightly coupled,
confusing, ya hard to maintain ho sakti hain. Procedural programming bhi
achhe modular design ke saath maintainable ho sakti hai.

**Interview English:** No. OOP offers useful design tools, but
maintainability depends on the quality of the overall design.

### Advanced questions

#### Q9. Are two variables that have the same class type necessarily referring to different objects?

**Easy Hinglish answer:** Nahi. Java mein `Student b = a;` karne se
reference copy hota hai, naya object nahi banta. C++ mein
`Student b = a;` simple class ke case mein object copy create kar sakta
hai. Language aur operation samajhna zaroori hai.

**Interview English:** No. In Java, reference assignment aliases the
same object. In C++, initializing an object from another object
typically invokes copy construction.

#### Q10. Does putting data and methods inside a class automatically provide encapsulation?

**Easy Hinglish answer:** Sirf class banana enough nahi hai. Access
control aur methods ke through valid state changes enforce karna bhi
important hai. Public fields ko koi bhi directly change kar sakta hai.

**Interview English:** Not by itself. Encapsulation also involves
controlling access to internal state and preserving valid object
invariants.

#### Q11. Why might a class be a poor design choice for a simple operation?

**Easy Hinglish answer:** Agar operation ke paas meaningful state ya
object responsibility nahi hai, to simple function zyada clear ho sakta
hai. Har cheez ko class banana unnecessary complexity add kar sakta hai.

**Interview English:** A class is not always necessary. A simple
function can be clearer when there is no meaningful object state or
responsibility to model.

### Top product-based company level

#### Q12. How would you model hundreds of students without creating a separate class for each student?

**Easy Hinglish answer:** Ek `Student` class define karunga jisme common
attributes aur methods honge. Phir har student ke liye alag object
create hoga. Isse structure reusable rahega aur individual state
separate rahegi.

**Interview English:** I would define one `Student` class for common
structure and behaviour, then create a separate instance for each
student.

#### Q13. How do you decide which data and methods belong in a class?

**Easy Hinglish answer:** Main responsibilities aur ownership dekhta
hoon. Jo data aur operations same concept ki responsibility hain, unhe
ek class mein group karna reasonable hai. Class ko unrelated
responsibilities ka container nahi banana chahiye.

**Interview English:** I group data and operations that belong to the
same responsibility, while avoiding classes that accumulate unrelated
concerns.

#### Q14. What makes a class maintainable?

**Easy Hinglish answer:** Clear responsibility, controlled state
changes, meaningful names, simple public methods, aur low unnecessary
coupling. Class ka internal implementation change ho to baaki code par
minimum impact hona chahiye.

**Interview English:** A maintainable class has a clear responsibility,
a small understandable interface, controlled state changes, and limited
unnecessary coupling.

#### Q15. When is OOP not the best fit?

**Easy Hinglish answer:** Simple data transformations, small scripts, ya
stateless operations mein procedural/function-based approach simpler ho
sakti hai. Design ko problem ke hisaab se choose karna chahiye, trend ke
hisaab se nahi.

**Interview English:** OOP is not always the best fit. Small stateless
operations may be clearer as functions, so the design should match the
problem.

------------------------------------------------------------------------

## 16. Real-World Mini Design Exercise: Student Record

### Requirements

Create a small model for students in a college.

Each student has: - Name - Roll number - Age

Each student can: - Display their details - Introduce themselves

### Responsibilities

-   `Student` owns one student's data.
-   `introduce()` formats the student's introduction.
-   `displayDetails()` prints the student's record.
-   `main()` creates and uses student objects.

### Relationship diagram

``` text
             +------------------+
             | Student          |
             +------------------+
             | name             |
             | rollNumber       |
             | age              |
             +------------------+
             | introduce()      |
             | displayDetails() |
             +------------------+
                    |
           +--------+--------+
           |                 |
      Student object A   Student object B
```

### C++ implementation

``` cpp
#include <iostream>
#include <string>
using namespace std;

class Student {
private:
    string name;
    int rollNumber;
    int age;

public:
    Student(const string& name, int rollNumber, int age)
        : name(name), rollNumber(rollNumber), age(age) {}

    void introduce() const {
        cout << "Hi, I am " << name << ".\n";
    }

    void displayDetails() const {
        cout << "Name: " << name << '\n';
        cout << "Roll number: " << rollNumber << '\n';
        cout << "Age: " << age << '\n';
    }
};

int main() {
    Student first("Rahul", 101, 20);
    Student second("Priya", 102, 21);

    first.introduce();
    first.displayDetails();

    cout << '\n';

    second.introduce();
    second.displayDetails();
}
```

### Java implementation

``` java
class Student {
    private final String name;
    private final int rollNumber;
    private final int age;

    Student(String name, int rollNumber, int age) {
        this.name = name;
        this.rollNumber = rollNumber;
        this.age = age;
    }

    void introduce() {
        System.out.println("Hi, I am " + name + ".");
    }

    void displayDetails() {
        System.out.println("Name: " + name);
        System.out.println("Roll number: " + rollNumber);
        System.out.println("Age: " + age);
    }
}

public class Main {
    public static void main(String[] args) {
        Student first = new Student("Rahul", 101, 20);
        Student second = new Student("Priya", 102, 21);

        first.introduce();
        first.displayDetails();

        System.out.println();

        second.introduce();
        second.displayDetails();
    }
}
```

### Why this design fits the topic

-   One class represents the common structure of all students.
-   Each object stores a distinct student's state.
-   Methods represent behaviour related to the student.
-   Private fields demonstrate controlled access as an additional design
    improvement.
-   Multiple objects can be created without duplicating the class
    definition.

### Limitations and improvements

-   This is an in-memory example, not a database-backed student system.
-   It does not validate age or roll number.
-   It does not model courses, attendance, or permissions.
-   In a larger application, validation and storage responsibilities may
    need separate components.

------------------------------------------------------------------------

## 17. Revision Notes

### Definitions to memorize

-   **OOP:** A programming paradigm that organizes software around
    objects containing state and behaviour.
-   **Class:** A blueprint/type defining the data and operations of its
    instances.
-   **Object:** An instance of a class.
-   **Attribute:** A property or data member representing state.
-   **Method:** A function associated with a class or object that
    represents behaviour.
-   **Modularity:** Dividing software into understandable, focused
    parts.
-   **Encapsulation:** Grouping related data and behaviour while
    controlling access to internal state.
-   **Abstraction:** Exposing essential functionality while hiding
    unnecessary implementation details.
-   **Inheritance:** Defining a class in terms of another class to reuse
    or specialize behaviour/state.
-   **Polymorphism:** Allowing a common interface or operation to work
    with different implementations.

### Fast rules

-   Class = blueprint; object = instance.
-   One class can create many objects.
-   Each ordinary object has its own instance state.
-   Attributes represent state; methods represent behaviour.
-   OOP groups related data and behaviour.
-   OOP can support modularity and maintainability, but does not
    guarantee good design.
-   Java reference assignment does not create a new object.
-   C++ object copy construction and Java reference assignment are
    different.
-   In C++, class members default to private.
-   In Java, a member with no access modifier has package-level access.
-   Private fields should be changed through methods that preserve valid
    state.

### Last-minute OA checklist

-   [ ] Can I define OOP in one or two sentences?
-   [ ] Can I distinguish class and object?
-   [ ] Can I identify attributes and methods in a code snippet?
-   [ ] Can I create two objects with different values?
-   [ ] Can I explain the five procedural-programming limitations listed
    in the lecture?
-   [ ] Can I explain why combining data and behaviour can improve
    organization?
-   [ ] Can I identify the four OOP pillars?
-   [ ] Can I trace Java references correctly?
-   [ ] Can I identify C++ access-control errors?
-   [ ] Can I write a small class in both C++ and Java?

------------------------------------------------------------------------

## 18. Practice Tracker

-   [ ] Concept understood.
-   [ ] Real-life analogy understood.
-   [ ] Class/object diagram understood.
-   [ ] Attributes and behaviour identified correctly.
-   [ ] C++ Student code implemented and run.
-   [ ] Java Student code implemented and run.
-   [ ] C++ vs Java differences revised.
-   [ ] MCQs attempted without answers.
-   [ ] Output questions solved independently.
-   [ ] Compilation/error questions attempted.
-   [ ] Coding exercises completed.
-   [ ] Interview questions answered aloud.
-   [ ] Mini design exercise implemented in both languages.
-   [ ] Revision checklist completed.

------------------------------------------------------------------------

## 19. Source Coverage Audit

The supplied Love Babbar PDF contains 11 pages. The screenshot shows a
longer introductory OOP article and a table naming the four pillars. The
following audit distinguishes lecture material from additional
explanations.

  -----------------------------------------------------------------------
  Source concept          Where covered in this   Status
                          file                    
  ----------------------- ----------------------- -----------------------
  Why OOP was developed   Sections 3.1 and 4.2    Covered

  Functional/procedural   Sections 3.1 to 3.3     Covered in prose;
  approach illustration                           original hand-drawn
                                                  flow is summarized
                                                  rather than copied
                                                  exactly

  Multiple students with  Sections 3.2, 4.4, 5.1, Covered
  their own properties    and 6.1                 
  and behaviours                                  

  Student data such as    Sections 3.2 and 4.4;   Covered conceptually;
  ID/name/age/marks and   Student example code    all listed actions are
  actions such as                                 not individually
  study/sleep/bunk                                implemented

  Drawbacks of procedural Section 3.3             All five listed
  programming                                     drawbacks covered

  Definition of OOP       Sections 3.4 and 4      Covered

  Objects communicate     Section 3.4 and         Mentioned; not expanded
  with each other         interview discussion    into a multi-object
                                                  collaboration example

  Combining data and      Sections 3.4, 4.7, 5,   Covered
  behaviour               and 6.2                 

  Modularity, reuse,      Sections 3.4 and 4.8    Covered
  maintainability                                 

  Class as blueprint      Sections 3.5 and 4.3    Covered

  Object as instance of   Sections 3.5 and 4.4    Covered
  class                                           

  Attributes as           Sections 3.6 and 4.5    Covered
  state/properties                                

  Behaviour as            Sections 3.6 and 4.6    Covered
  methods/functions                               

  Person example: name,   Sections 3.6 and 5.3;   Covered
  age, height, speak(),   code in Section 14      
  eat()                                           

  Car, person, student,   Sections 3.5 and 5      Car, person, and
  building examples                               student expanded;
                                                  building is
                                                  acknowledged as another
                                                  possible entity

  Four pillars table:     Sections 3.7 and 4.9    Introductory overview
  encapsulation,                                  covered
  abstraction,                                    
  polymorphism,                                   
  inheritance                                     

  C++ and Java            Sections 7 and 8        Additional explanation
  implementations                                 

  OA questions and answer Section 12 and below    Additional practice
  key                                             

  Interview answers       Section 15              Additional practice

  Real-world mini design  Section 16              Additional practice
  -----------------------------------------------------------------------

### Readability and limitations

-   The supplied PDF's printed text is readable enough to identify the
    introductory concepts and examples described above.
-   Some hand-drawn annotations and small code snippets in the PDF
    images are not fully legible. This file does not claim to reproduce
    those snippets verbatim.
-   The supplied screenshot contains small text. Its visible concept
    table names the four OOP pillars, which are included here.
-   The source does not provide a full, detailed treatment of each
    pillar in this introductory PDF. The short descriptions in Section
    4.9 are general explanations, not a claim that the source fully
    teaches those topics.
-   The C++/Java code, OA questions, answer explanations, and design
    exercise are additional learning material created to practise the
    source concepts.

------------------------------------------------------------------------

## 20. OA Answer Key with Explanations

```{=html}
<details>
```
```{=html}
<summary>
```
Open the answer key after attempting the questions
```{=html}
</summary>
```
### Q1. Correct answer: B

A class defines a type/blueprint, including the data and operations its
instances can use. A describes object state, while C and D do not define
a class.

**Rule:** Class defines structure; object is an instance.

### Q2. Correct answer: C

`age` is a property/data member. `speak()`, `eat()`, and `introduce()`
are methods.

**Rule:** Attributes describe state; methods describe behaviour.

### Q3. Correct answer: B

An object is an instance of a class.

**Rule:** A class can have many instances.

### Q4. Correct answer: C

The lecture's central idea is to combine related data and behaviour into
an object. Global variables and giant functions do not express that
idea.

**Rule:** Group related state and operations.

### Q5. Correct answer: C

Poorly structured procedural programs can become difficult to maintain.
Procedural programs can still use functions and modules effectively, so
A, B, and D are false.

**Rule:** Describe common risks without claiming every procedural
program has them.

### Q6. Correct answer: B

Different objects of the same class can store different instance values.

**Rule:** Same class structure does not mean same object state.

### Q7. Correct answer: B

The four pillars are encapsulation, abstraction, inheritance, and
polymorphism.

**Rule:** Remember the four names and learn each in detail separately.

### Q8. Correct answer: B

Encapsulation combines related state and behaviour and can control how
the state is accessed or changed. The other options describe no such
principle or are plainly incorrect.

**Rule:** Encapsulation is about grouping plus controlled access, not
making everything public.

### Q9. Output

``` text
Rahul
Priya
```

`a` and `b` are separate C++ objects. Each object's `name` member has
its own value.

### Q10. Output

``` text
12
```

`a` and `b` refer to the same Java object. Setting `b.value = 12`
changes the same object's field that is read through `a`.

### Q11. Output

``` text
19 22
```

Two separate objects are created using two `new Student()` expressions.
Each has its own `age` field.

### Q12. Output

``` text
11
```

`first.value` is 3 and `second.value` is 8. The expression adds them and
prints 11.

### Q13. Correct answer: Does not compile

`age` is private by default in a C++ `class`. The code attempts to
access it from outside the class.

**Fix:** Make it public for a basic demonstration or expose a suitable
public method.

### Q14. Correct answer: Does not compile

`age` is private and cannot be accessed directly from `Main`.

**Fix:** Add a public method or constructor to set the value safely.

### Q15. Correct answer: Does not compile

The local variable `s` has not been initialized before `s.age` is read.
Java requires local variables to be definitely assigned.

**Fix:** Use `Student s = new Student();`.

### Q16. Correct answer: False

A class is the definition/type; an object is an instance.

### Q17. Correct answer: True

If both references point to the same object, changes to the object's
fields can be observed through either reference.

### Q18. Correct answer: False

OOP is a design approach. It cannot guarantee modularity,
maintainability, or security without good design and implementation.

### Q19. Correct answer: B

Java class-type variables hold references to objects. C++ supports
direct object instances without `new`, and the languages do not have
identical memory management.

### Q20. Correct answer: C

One object is created. `second` receives the same reference stored in
`first`.

```{=html}
</details>
```

------------------------------------------------------------------------

## Next lecture note recommendation

For the next OOP file, keep the same repository structure and focus on
**Encapsulation** or **Classes, Objects, and Constructors** depending on
the next Love Babbar lecture. Avoid mixing every OOP pillar into one
oversized topic file; smaller topic notes are easier to revise for OAs
and interviews.
