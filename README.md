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
