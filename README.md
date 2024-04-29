# DesignPattern-GOF

Strategy : [ behavioral design pattern ]

Defines a family of algorithms, put each of them in a separate class and makes their objects interchangeable. 

Note :

Applies the Single Responsiblity and the Open-Closed Principles.

1.

Interface - PaymentStrategey
----------------------------

interface PaymentStrategey {

void pay(int amt);

}

2.

Class - PaymentCreditCard  implements PaymentStrategey
------------------------------------------------------

public void pay(int amount){


}

3.

Class - PaymentPayPal implements PaymentStrategeyimplements PaymentStrategey
----------------------------------------------------------------------------

public void pay(int amount){


}

This class has no visibility on how payment is being conducted as it is making use of strategy interface

4.

Service Class - PaymentService
------------------------------

private PaymentStrategey strategy;

public void processOrder(){

}

private int getTotal(){

}

5. 

Client code :

public void main(String args[]){

PaymentService paymentService = new PaymentService();

paymentService.setStrategy(new PaymentByCreditcard());

paymentService.processOrder();

}


<img width="1724" alt="Strategey-Design-Pattern" src="https://github.com/DowlathBashaG/DesignPattern-GOF/assets/9671419/8ef147d3-67f3-4d13-bbf3-03a4d139bf6c">


State Vs Strategy
=================

State can be considered as an extension of Strategy as both patterns are based on composition, they change the behavior of the context by delegating some work to helper objects.




			State 		                             |              Strategy
			
1. State can be dependent as you can                  Strategies are completely independent and unaware of each other
   
   easily jump from one state to another
   
   

2. Doing different things based on the state,          Differnt implementation that accomplish the same thing.
 
   hence the result may vary. 
   
    


   Builder Design Pattern
   
   It is creational design pattern , to create complex objects step by step basis.
   
   Produces different types and representations of an object using the same construction process.
   
   Car -> class
   
   -brand
   
   -model
   
   -color
   
   -nbrdoors
   
   -screenType
   
   -weight
   
   -height
   
   
   Car schema 
   
   -id
   
   -brand
   
   -model
   
   -color
   
   -nbrdoors
   
   -screenType
   
   -weight
   
   -height
   
   While creating constructor , we may not need to fill all the fields of an object.
   
   other options...we need to create several constructors...unncessarry.
   
   Note:
   
   Extract the object constuction or creatiion code out of its own class and move it to separate objects called builders.
   
   Example :
   
   1.
   
   
   public class CarBuilder{
   
   private int id;
   
   private String brand;
   
   private String model;
   
   private String color;
   
   .....
   
   public CarBuilder id(int id){
   
   this.id = id;
   
   }
   
   public CarBuilder brand(String brand){
   
   this.brand = brand;
   
   }
   
   .....
   
   
   
   public Car build(){
    
   return new Car(id, brand, model, color);
   
   }
   
   ==============================================================
   
   2.
   
   public class Car{
   
   private final int id;
   
   private final String brand;
   
   private final String model;
   
   ....
   
   This below constuctor is not public.... Why...because try to make you object constructo non-public when the builder is not an inner-builder 
   
   by doing this you force the users of your app to instantiate your object using the builder.
   
   Car(int id,String brand.....{
   
   this.id = id
   
   ...
   
   ...
   
   }
   
 }
 
 
  3.
  
  CarBuilder builder = new CarBuilder();
  
  builder.id(21).brand("bugatti").model("chiron").color("blue");
  
  
  4. Director class : 
  
  Defines the order in which we should call the construction steps so that we can reuse sepecifi configurations of the products we are building.
  
  public class Director{
  
  public void buildBugatti(CarBuilder builder) {
  
  builder.brand("bugatti").color("white").nbrdoors(2).engine("8L").height(115);

 }

} 

Note :  it is optional , it is hides the details of the product construction from the client code.


Note :

Director director = new Director();

CarBuilder builder = new CarBuilder();

director.buildBugatti(builder);

Car car = builder.build();


<img width="1724" alt="Builder-Design-Pattern" src="https://github.com/DowlathBashaG/DesignPattern-GOF/assets/9671419/f8dab960-ced3-471e-802e-6d3c3cccfeca">
