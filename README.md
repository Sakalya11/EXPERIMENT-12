## Constructors and Destructors 

# Experiment 12: To study and implement Constructors and Destructors

## Aim: -
To run and execute a code in C++ using Constructors and Destructors

## Theory: - 
A constructor in C++ is a special member function of a class that is automatically invoked when an object of that class is created.
The primary purpose of a constructor is to initialize the object's data members and to perform any setup or allocation required for the object to be in a valid state.

### Characteristics of Constructors:
1. Same Name as Class: A constructor has the same name as the class in which it is defined.
2. No Return Type: Constructors do not have a return type, not even void.
3. Automatic Invocation: Constructors are called automatically when an object is created. The programmer does not need to explicitly invoke them.
4. Overloading: Constructors can be overloaded, meaning a class can have multiple constructors with different parameters.


### Types of constructors 

1. A __default constructor__ is a constructor that takes no arguments and initializes objects with default values. If no constructor is provided in a class, C++ automatically generates a default constructor.

2. A __parameterized constructor__ takes one or more arguments, allowing objects to be initialized with specific values. These constructors can be overloaded, providing multiple ways to create an object with different initializations.

3. A __copy constructor__ is a special constructor that creates a new object as a copy of an existing object by taking a reference to another object of the same class. If not explicitly defined, C++ provides a default copy constructor.

4. A __move constructor__ transfers resources from a temporary object (rvalue) to a new object, preventing unnecessary deep copies and enhancing performance, particularly with dynamic memory or large objects.


## Code 
~~~
#include <iostream>
#include <string>
// Sakalya
// 23070123142
// Experiment 12 Constructors 

class Person {
    std::string name;
    int age;

public:
    // Default constructor 
    Person() : name("Unknown"), age(0) {
        std::cout << "Default constructor called.\n";
    }

    // Parameterized constructor 
    Person(std::string n, int a) : name(n), age(a) {
        std::cout << "Parameterized constructor called.\n";
    }

    // Constructor defined outside the class
    Person(std::string n);

    // Copy constructor
    Person(const Person &p) {
        name = p.name;
        age = p.age;
        std::cout << "Copy constructor called.\n";
    }

    void display() {
        std::cout << "Name: " << name << ", Age: " << age << std::endl;
    }
};

// Constructor defined outside the class
Person::Person(std::string n) : name(n), age(0) {
    std::cout << "Constructor defined outside the class called.\n";
}

int main() {
    // Using the default constructor
    Person p1;
    p1.display();

    // Using the parameterized constructor
    Person p2("Alice", 25);
    p2.display();

    // Using the constructor defined outside the class
    Person p3("Bob");
    p3.display();

    // Using the copy constructor
    Person p4 = p2;
    p4.display();

    return 0;
}
~~~
## Code Output 


## Conclusion 
- We learnt how to execute a code using different types of constructors in C++ programming language
- We learnt the different types of constructors , their advantages, the disadvantages and the applications

--------------------------------------------------------------------------------
## Destructors 

### Application of destructors 
1. **Resource Management:** Frees resources like memory or connections when an object is destroyed.

2. **Memory Cleanup:** Prevents memory leaks by deallocating memory used by the object.

3. **Closing Files/Connections:** Ensures files or network connections are properly closed.

4. **Releasing Locks:** Releases synchronization locks to prevent deadlocks.

5. **Logging and Debugging:** Logs object destruction for debugging purposes.

6. **Custom Cleanup:** Handles specific cleanup tasks required by the object.

### Advantages of Destructors:

1. **Automatic Resource Management:** Ensures resources are released automatically when objects are destroyed, reducing the risk of resource leaks.
  
2. **Simplifies Code:** Eliminates the need for manual cleanup, making code cleaner and easier to maintain.

3. **Error Prevention:** Reduces the likelihood of errors like memory leaks and dangling pointers by ensuring proper resource deallocation.

4. **Consistent Cleanup:** Guarantees that cleanup tasks are performed consistently, even in the presence of exceptions or errors.

5. **Encapsulation:** Keeps resource management encapsulated within the object, adhering to the principles of object-oriented programming.

                 |

~~~
#include <iostream>

class Person {
    std::string name;
    int age;

public:
    // Constructor
    Person(std::string n, int a) : name(n), age(a) {
        std::cout << "Constructor called for " << name << ".\n";
    }

    // Destructor
    ~Person() {
        std::cout << "Destructor called for " << name << ".\n";
    }

    void display() {
        std::cout << "Name: " << name << ", Age: " << age << std::endl;
    }
};

int main() {
    Person p1("Alice", 30);
    p1.display();
    Person p2("Bob", 25);
    p2.display();

    // Scope block to demonstrate destructor call at the end of the block
    {
        Person p3("Charlie", 40);
        p3.display();
    } 

    std::cout << "End of main function.\n";

    return 0; // p1 and p2 destructors will be called here
}

~~~
## Code Output

## Conclusion
- We learnt how to use destructors in C++
- we learnt the application, advantages and disadvantages of using a destructor in C++

