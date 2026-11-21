# 4. Encapsulation, Data Hiding & Controlled Access

> **Object-Oriented Programming (OOP) Series • Module 04**  
> Complete Step-by-Step Guide with Separate C++ Implementations: Standard Encapsulation vs. Perfect Encapsulation (Getters & Setters)

---

## 1. Core Definition & Real-World Analogy

In Object-Oriented Programming (OOP), **Encapsulation** is the fundamental principle of wrapping or binding **data (attributes/variables)** and the **methods (member functions)** that operate on that data into a single logical unit called a **Class**.

Think of a **medical capsule**: multiple active medicinal ingredients are sealed safely inside a protective outer shell. Similarly, a `class` acts as a protective container that bundles variables and functions together, preventing external code from directly tampering with sensitive internal state.

> **Encapsulation vs. Data Hiding:**  
> Encapsulation is the structural mechanism of bundling data and methods together in a class. Because we restrict direct access to internal members from outer classes or `main()`, Encapsulation achieves **Data Hiding**—exposing only necessary public behaviors while concealing internal data structures and algorithms.

---

## 2. Functions & Access Modifiers in OOP

From an Object-Oriented Design perspective, encapsulation provides four core guarantees:
1. Provides a **secure layer** around class state.
2. **Hides internal implementation** details and underlying algorithms.
3. **Exposes only necessary interfaces** to the external world.
4. Enables **safe inter-class communication** without one class needing to know the internal logic of another.

| Modifier | Same Class | Derived (Child) Class | External Code (`main()` / Other Classes) |
| :--- | :--- | :--- | :--- |
| **`public`** | Accessible | Accessible | Accessible directly via dot operator (e.g., `A.sleep()`). |
| **`protected`** | Accessible | Accessible | Not accessible directly from external code. |
| **`private`** | Accessible | Not Accessible | Not accessible; attempting access causes a compile-time error. |

---

## 3. Code Implementation 1: Standard Encapsulation (Without Getters & Setters)

In our first implementation, we model a `Student` class where general attributes (`id`, `age`, `name`, `nos`) and observable behaviors (`study()`, `sleep()`, `bunk()`) are `public`, while sensitive personal attributes (`*gpa`, `gf`) and private behaviors (`gfchatting()`) are hidden under `private`.

### Step-by-Step Breakdown of Code 1
1. **Step 1 (Public vs. Private Attributes):** General student properties are placed under `public:`, while sensitive fields (`int *gpa` allocated dynamically on the heap, and `string gf`) are placed under `private:`.
2. **Step 2 (Constructors & Destructor):** Even though `*gpa` and `gf` are `private`, the class's own `public` Parameterised Constructor can initialize them (`this->gpa = new int(gpa);`), and the Destructor (`~Student()`) safely frees the heap memory (`delete this->gpa;`).
3. **Step 3 (Private Member Functions):** Helper or strictly personal methods like `gfchatting()` are placed in a `private:` block so external callers in `main()` cannot invoke them, though internal methods of `Student` can.
4. **Step 4 (Access Boundary Verification):** Inside `main()`, calling `A.sleep()` succeeds because it is `public`, whereas trying to access `A.gf` or `A.gfchatting()` triggers a compiler error.

```cpp
#include <iostream>
#include <string>
using namespace std;

class Student {
public:
    // Public Attributes
    int id;
    int age;
    string name;
    int nos; // Number of subjects

private:
    // Private Attributes (Hidden from external world)
    int *gpa;
    string gf;

public:
    // 1. Default Constructor
    Student() {
        cout << "Student Default ctor called" << endl;
    }

    // 2. Parameterised Constructor
    Student(int id, int age, string name, int nos, float gpa, string gf) {
        cout << "Student Parameterised ctor called" << endl;
        this->id = id;
        this->age = age;
        this->name = name;
        this->nos = nos;
        this->gpa = new int(gpa); // Dynamic memory allocation for private pointer
        this->gf = gf;
    }

    // 3. Copy Constructor
    Student(const Student &srcobj) {
        cout << "Student copy ctor called" << endl;
        this->id = srcobj.id;
        this->age = srcobj.age;
        this->name = srcobj.name;
        this->nos = srcobj.nos;
        this->gpa = new int(*(srcobj.gpa));
        this->gf = srcobj.gf;
    }

    // Public Behaviours / Methods / Functions
    void study() {
        cout << this->name << " Studying" << endl;
    }

    void sleep() {
        cout << this->name << " Sleeping" << endl;
    }

    void bunk() {
        cout << this->name << " Bunking" << endl;
    }

    // Destructor to release dynamic memory
    ~Student() {
        cout << "Student Default dtor called" << endl;
        delete this->gpa;
    }

private:
    // Private Method (Strictly internal to Student class)
    void gfchatting() {
        cout << this->name << " chatting with gf" << endl;
    }
};

int main() {
    Student A(1, 12, "Ranu", 5, 7.8, "Menu");

    // Allowed: Accessing public attribute & public method
    cout << A.age << endl;
    A.sleep();

    // Not Allowed (Compile-Time Error if uncommented):
    // cout << A.gf << endl;     // Error: 'gf' is private
    // A.gfchatting();           // Error: 'gfchatting()' is private

    return 0;
}
```

### Execution Output (Code 1)
```text
Student Parameterised ctor called
12
Ranu Sleeping
Student Default dtor called
```

---

## 4. What Happens When ALL Attributes Are Made Private?

Suppose we move `id`, `age`, `name`, and `nos` into the `private:` section alongside `*gpa` and `gf`. Now, executing `cout << A.age << endl;` inside `main()` immediately fails with a compilation error (`'int Student::age' is private within this context`). This transition brings us to **Perfect Encapsulation**.

---

## 5. Perfect Encapsulation & Controlled Access (Getters & Setters)

**Perfect Encapsulation** is achieved when **100% of a class's data members/variables are declared `private`**. Because external code still needs controlled ways to read or update specific attributes during execution, we expose public interface functions known as **Getters** and **Setters**:

* **Getter Methods (e.g., `getGpa()`, `getAge()`):** Public functions that read and return the value of a private variable safely without exposing direct memory access.
* **Setter Methods (e.g., `setGpa(float a)`, `setAge(int a)`):** Public functions that update a private variable while allowing us to enforce validation rules or security checks before modifying internal memory.

---

## 6. Code Implementation 2: Perfect Encapsulation (With Getters & Setters)

In this complete implementation, every single attribute of `Student` is `private`. Notice how `setGpa()` dereferences the private pointer (`*this->gpa = a;`) to update the value stored on the heap, and `getGpa()` returns `*this->gpa`.

### Step-by-Step Walkthrough of Code 2
1. **Step 1 (Full Attribute Privacy):** All six variables (`id`, `age`, `name`, `nos`, `*gpa`, `gf`) are placed inside `private:`. No external function can read or write them directly.
2. **Step 2 (Defining Setter & Getter for Pointer Data):** We define `void setGpa(float a)` to safely write into the heap memory pointed to by `this->gpa`, and `int getGpa() const` to read `*this->gpa`. Notice that since `gpa` is an `int*`, passing `7.8` truncates to integer `7`, and passing `6.7` truncates to `6`.
3. **Step 3 (Defining Getter for Standard Data):** We define `int getAge() const` so `main()` can read `A.age` safely without being able to overwrite it directly.
4. **Step 4 (Controlled Interaction in `main()`):** First, `A.getGpa()` prints `7`. Next, `A.setGpa(6.7)` updates the private value, and `A.getGpa()` prints `6`. Finally, `A.getAge()` prints `12` before the destructor cleans up memory.

```cpp
#include <iostream>
#include <string>
using namespace std;

class Student {
private:
    // ALL Attributes are Private -> Perfect Encapsulation
    int id;
    int age;
    string name;
    int nos;
    int *gpa;
    string gf;

public:
    // Setter & Getter for private pointer attribute 'gpa'
    void setGpa(float a) {
        // Optional validation layer can be added here
        *this->gpa = a;
    }

    int getGpa() const {
        return *this->gpa;
    }

    // Getter for private attribute 'age' (Read-only external access)
    int getAge() const {
        return this->age;
    }

    // Default Constructor
    Student() {
        cout << "Student Default ctor called" << endl;
    }

    // Parameterised Constructor
    Student(int id, int age, string name, int nos, float gpa, string gf) {
        cout << "Student Parameterised ctor called" << endl;
        this->id = id;
        this->age = age;
        this->name = name;
        this->nos = nos;
        this->gpa = new int(gpa);
        this->gf = gf;
    }

    // Copy Constructor
    Student(const Student &srcobj) {
        cout << "Student copy ctor called" << endl;
        this->id = srcobj.id;
        this->age = srcobj.age;
        this->name = srcobj.name;
        this->nos = srcobj.nos;
        this->gpa = new int(*(srcobj.gpa));
        this->gf = srcobj.gf;
    }

    // Public Behaviours
    void study() {
        cout << this->name << " Studying" << endl;
    }

    void sleep() {
        cout << this->name << " Sleeping" << endl;
    }

    void bunk() {
        cout << this->name << " Bunking" << endl;
    }

    // Destructor
    ~Student() {
        cout << "Student Default dtor called" << endl;
        delete this->gpa;
    }

private:
    // Private Method
    void gfchatting() {
        cout << this->name << " chatting with gf" << endl;
    }
};

int main() {
    Student A(1, 12, "Ranu", 5, 7.8, "Menu");

    cout << A.getGpa() << endl;   // Reads initial GPA (7) via Getter
    A.setGpa(6.7);                // Modifies private GPA to 6 via Setter
    cout << A.getGpa() << endl;   // Reads updated GPA (6) via Getter

    cout << A.getAge() << endl;   // Reads private age (12) via Getter

    return 0;
}
```

### Execution Output (Code 2)
```text
Student Parameterised ctor called
7
6
12
Student Default dtor called
```

---

## 7. Comparison: Standard Encapsulation vs. Perfect Encapsulation

| Feature | Code 1: Without Getters/Setters | Code 2: With Getters/Setters |
| :--- | :--- | :--- |
| **Attribute Visibility** | Mixed (`id, age, name, nos` are public; `*gpa, gf` are private). | 100% of data members are strictly `private`. |
| **External Data Access** | Direct dot access allowed for public variables (`A.age`). | Only via controlled methods (`A.getAge()`, `A.getGpa()`). |
| **Data Validation Control** | None on public variables; external code can assign any invalid value. | High; setters (`setGpa()`) can validate inputs before updating state. |
| **Encapsulation Level** | Partial / Standard Encapsulation. | **Perfect Encapsulation** (Strict Data Hiding). |