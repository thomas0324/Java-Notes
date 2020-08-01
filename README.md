# Java-Notes

## Object-Oriented Programming
OOP is a very fundamental part for Java. 
### Classes
Basically, classes are everywhere in Java. Consider the following classes, 

- Car.java                             

      public class Car {
        private int doors ;
        private int wheels ;
        private String engine ;
        private String model ;
        private String colour ;
        
        // The set method allows to do validation
        public void setModel(String model){
            String validModel = model.toLowerCase() ; 
            if(validModel.equals("carrera") || validModel.equals.("commodore") {
                this.model = model ;    // this keyword refers to the field of this class 
            } else {
                this.model = "unknown" ; 
            }
        }
        
        public String getModel(){
            return this.model ; 
        }
        
      }

- Main.java 
    
      public class Main {

        public static void main(String[] args){
            Car porsche = new Car() ;
            Car holden = new Car() ;
            
            // Changing the variable in the class 
            porsche.model = "Carrera" ; // Error, we can't access the private field 
            porsche.setModel("Carrera") ;  // The correct way 
        }

      }

### Constructors
Constructor is a good way to create an object. Note that constructors can be overloaded like method. It is not rare to see a constructor calling the other constructors. 

- Account.java

      public class Account {
          private String number ; 
          private double Balance ; 
          private String customerName ; 
          private String customerEmailAddress ;
          private String customerPhoneNumber ; 
            
          // Empty Constructor
          public Account() {
              // The empty constructor could call other constructor
              this("123", 0.20, "Default name" , "Default address" , "Default phone") ;
          } 
            
          public Account(String number) {
              // Constructor with one parameter could call other constructor
              this(number , 0.20, "Default name" , "Default address" , "Default phone") ;
          }
            
          // Constructor with parameters
          public Account(String number, double balance, String customerName, String customerEmailAddress, String customerPhoneNumber) {
              this.number = number ; 
              this.balance = balance ; 
              this.customerName = customerName ;
              this.customerEmailAddress = customerEmailAddress ;
              this.customerPhoneNumber = customerPhoneNumber ; 
          }
         
      }

- Main.java
        
      public class Main {
            
          public static void main(String[] args){
 
              // Initialize an object
              Account MyAccount = new Account("12345", 0.00, "Tom", "myemail@gmail.com", "123456789") ;   
                
          }
            
      }

### Inheritance 
Inheritance allows one class to inherit the features (fields and methods) of another class. i.e. The child class can use the methods in the parent class 

Terminology: public class [parent class] extends [child class]  

- Animal.java

      public class Animal {
            // The features that an animal has 
            private String name ;
            private int brain ;
            private int body ;
            private int size ; 
            private int weight ;
            
            public Animal(String name, int brain, int body, int size, int weight) {
                  this.name = name ;
                  this.brain = brain ;
                  this.body = body ;
                  this.size = size ;
                  this.weight = weight ; 
            }
            
            public void eat(){
                  System.out.println("Animal.eat() called") ; 
            }
            
            public void move(int speed){
                  System.out.println("It is moving at " + speed) ; 
            }
      }
      


- Dog.java


      public class Dog extends Animal {
      
            private int eyes ;
            private int legs ;
            private int tail ;
            private int teeth ;
            private String coat ; 
            
            // Base charactistics
            public Dog(String name, int brain, int body, int size, int weight, int eyes, int legs, int tail, int teeth, String coat) {
                  super(name, brain, body, size, weight) ;
                  this.eyes = eyes ;
                  this.legs = legs ;
                  this.tail = tail ;
                  this.teeth = teeth ;
                  this.coat = coat ; 
            }
            
            @override
            public void eat() {
                  System.out.println("Dog.eat() called!!") ;
            }

            public void walk() {
                  System.out.println("Dog.walk() called") ;
                  super.move() ; // super means calling the method from the parent class
            }
            
 
- Main.java 

      public class Main {
            
            public static void main(String[] args) {
                  Animal animal = new Animal("Animal", 1, 1, 5, 5) ;
                  
                  Dog dog = new Dog("York", 1, 1, 1, 1, 1, 1, 1, 1, "silky") ;
                  dog.eat() ; // prints out "Dog.eat() called!!" 
            }
      }

### Reference, Object, Instance and class

- Class

A class is basically a blueprint for a house, using the blueprint(plan) we can build as many houses as we like based on those plans.

- Instance

Each house you build is an object also known as an instance

- Reference 

Each house you build has an address (a physical location). In other words if you want to tell someone where you live, you give them your address. 

You can copy that reference as many times as you like but there is still just one house.

![image](https://user-images.githubusercontent.com/60317305/88474946-e939aa00-cf5d-11ea-97be-80b3e3362db5.png)

### This and Super keywords

- Super

The super keyword is used to access or call the parent class members (variables and methods)

![image](https://user-images.githubusercontent.com/60317305/88475316-4daa3880-cf61-11ea-8f5a-812112948f2d.png)

- This 

The this keyword is used to call the current class members (variables and methods). This is required when we have a parameter with the same name as an instance variable

![image](https://user-images.githubusercontent.com/60317305/88475227-83025680-cf60-11ea-81db-2394c359a1f9.png)

### Method Overloading vs Method Overriding

- Method overloading (Compile time polymorphism)

1. Providing two or more separate methods in a class with the same name but different parameters

2. Method return type may or may not be different and that allows us to reuse the same method name

3. Method will be considered overloaded if both follow the following rules 

       a. Methods must have the same method name
      
       b. Methods must have different parameters

- Method overriding (Runtime polymorphism) 

1. A method in a child class that already exists in the parent class with same signature (same name, same arguments)

2. When overriding a method, it's recommended to put @Override imeediately above the method definition. 

3. Only instance method can be overrided

4. Method will be considered overriden if follow the these rules

       a. must have same name and same arguments
       
       b. Return type can be a subclass of the return type in the parent class 
       
       c. It can't have a lower access modifier
       
       d. For example, it the parent method is protected then using private in the child is not allowed but using public in the child would be allowed.

5. Only inherited methods can be overridden, in other words methods can be overridden only in child classes 

6. Constructors and private methods cannot be overridden 

7. Methods that are final cannot be overridden

8. A subclass can use super.methodName() to call the superclass version of an overridden method

![Annotation 2020-08-01 194606](https://user-images.githubusercontent.com/60317305/89101107-b2690580-d42f-11ea-841f-d0073f6723a0.jpg)

![Annotation 2020-08-01 194825](https://user-images.githubusercontent.com/60317305/89101172-0673ea00-d430-11ea-9dd7-b3b51429163a.jpg)

       
### Static method and variables 

Static methods are declared using a static modifier. 

1. Methods can't access instance methods and instance variables directly

2. Used for operations that don't require any data from an instance of the class ("this") 

![Annotation 2020-08-01 201627](https://user-images.githubusercontent.com/60317305/89101592-ec3c0b00-d433-11ea-8fed-d2cdc757bcab.jpg)

Static variables are declared using the keyword static

1. Static variables are also known as static member variables

2. Every instance of that class shares the same static variable

3. If changes are made to that variable, all other instances will see the effect of the change

![Annotation 2020-08-01 211316](https://user-images.githubusercontent.com/60317305/89102446-dc282980-d43b-11ea-9a00-244baa3b1554.jpg)


### Instance method and variables

Instance methods belong to an instance of a class 

1. To use an instance method, instantiate the class first usually by using the new keyword

2. access instance methods, instance variables, static methods and static variables directly

![Annotation 2020-08-01 202602](https://user-images.githubusercontent.com/60317305/89101739-44bfd800-d435-11ea-9b0f-209062adc89f.jpg)

Instance variable dont use the static keyword

1. Instance variables are also known as fields or member variables

2. Instance variables belong to an instance of a class

3. Every instance has its own copy of an instance variable which can have a different value or state

4. Instance variables represent the state of an instance

![Annotation 2020-08-01 212309](https://user-images.githubusercontent.com/60317305/89102573-4beae400-d43d-11ea-8a27-53e59a9c1b66.jpg)

### Static or Instance method ?

![Annotation 2020-08-01 203416](https://user-images.githubusercontent.com/60317305/89101846-6ff6f700-d436-11ea-8716-2318cdfbeadc.jpg)
