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

https://github.com/thomas0324/Java-Notes/issues/1#issue-665736479
