# Design Patterns in Race Game

This project demonstrates the implementation of several design patterns in a race game. The patterns used are:

* Template method pattern
* Abstract factory pattern
* Singleton pattern
* Strategy pattern
* Decorator pattern

## Template Method Pattern

The template method pattern is used to define the overall structure of an algorithm, while allowing specific details to be implemented by subclasses. In this project, the `Race` class defines the template method for a race. The `race()` method in the `Race` class outlines the steps of a race, such as setting up the cars, starting the race, and determining the winner. Subclasses of the `Race` class can implement specific details of the race, such as the type of cars used or the length of the race.

**Example:** The `Race` class has a `race()` method that outlines the steps of a race. The `race()` method calls the `setupCars()`, `startRace()`, and `determineWinner()` methods to implement the specific details of the race.

## Abstract Factory Pattern

The abstract factory pattern is used to create a family of related objects without specifying their concrete classes. In this project, the `CarFactory` class defines the abstract factory for creating different types of cars. The `createCar()` method in the `CarFactory` class is responsible for creating a new car object. Subclasses of the `CarFactory` class, such as `CoupeCarFactory` and `RoadsterCarFactory`, implement the `createCar()` method to create specific types of cars, such as `Ferrari812` and `PorscheBoxster`.

**Example:** The `CarFactory` class has a `createCar()` method that takes a car type as input and returns a new car object of that type. The `CoupeCarFactory` class overrides the `createCar()` method to create `SubaruBRZ` and `ToyotaGR86` cars, while the `RoadsterCarFactory` class overrides the `createCar()` method to create `Ferrari812` and `PorscheBoxster` cars.

## Singleton Pattern

The singleton pattern is used to ensure that there is only one instance of a class. In this project, the `Player` class is implemented as a singleton. The `getInstance()` method in the `Player` class returns the single instance of the `Player` class.

**Example:** The `Player` class has a private instance variable that holds the single instance of the class. The `getInstance()` method returns this instance variable.

## Strategy Pattern

The strategy pattern is used to define a family of algorithms, encapsulate each one, and make them interchangeable. In this project, the `EngineBehavior` and `TurboChargerBehavior` interfaces define the strategies for engine and turbocharger behavior, respectively. Subclasses of these interfaces, such as `V6Engine`, `V8Engine`, `V12Engine`, `AlpineTurboCharger`, and `CumminsTurboCharger`, implement the specific algorithms for each strategy. The `Car` class uses the strategy pattern to determine the engine and turbocharger behavior of the car at runtime.

**Example:** The `EngineBehavior` interface has an `engineSound()` method that defines the algorithm for engine sound. The `V6Engine` class implements the `engineSound()` method to produce a V6 engine sound. The `TurboChargerBehavior` interface has a `boostEngine()` method that defines the algorithm for boosting the engine. The `AlpineTurboCharger` class implements the `boostEngine()` method to boost the engine using an alpine turbocharger.

## Decorator Pattern

The decorator pattern is used to attach additional responsibilities to an object dynamically. In this project, the `CarWithNos` class is a decorator that adds NOS to a car. The `setNOS()` method in the `CarWithNos` class allows a `Car` object to be decorated with a `NOS` object. The `activateNOS()` and `deactivateNOS()` methods in the `CarWithNos` class provide the functionality for activating and deactivating the NOS.

**Example:** The `CarWithNos` class has a `setNOS()` method that takes a `NOS` object as input. The `setNOS()` method sets the `nos` instance variable to the input object. The `activateNOS()` and `deactivateNOS()` methods call the corresponding methods of the `nos` instance variable.

## UML Diagram

Here is a UML diagram that shows the relationships between the classes in the project:

```plantuml
@startuml
' Race class with template method as race
class Race {
    race()
}

' CarFactory has two concrete factories CoupeCarFactory and RoadsterCarFactory
class CarFactory {
    createCar()
}

class CoupeCarFactory extends CarFactory
    createCoupeCar()
}

class RoadsterCarFactory extends CarFactory {
    createRoadsterCar()
}

' Player class with singleton pattern
class Player {
    private static Player instance
    getInstance()
    private Player()
}

' Car class with abstract factory pattern
abstract class Car {
    abstract createEngineBehavior()
    abstract createTurboChargerBehavior()
    getEngineBehavior()
    getTurboChargerBehavior()
    race()
}

class Ferrari812 extends Car {
    createEngineBehavior()
    createTurboChargerBehavior()
}

class PorscheBoxster extends Car {
    createEngineBehavior()
    createTurboChargerBehavior()
}

class SubaruBRZ extends Car {
    createEngineBehavior()
    createTurboChargerBehavior()
}

class ToyotaGR86 extends Car {
    createEngineBehavior()
    createTurboChargerBehavior()
}

' EngineBehavior with strategy pattern
abstract class EngineBehavior {
    engineSound()
}

class V6Engine extends EngineBehavior {
    engineSound()
}

class V8Engine extends EngineBehavior {
    engineSound()
}

class V12Engine extends EngineBehavior {
    engineSound()
}

' TurboChargerBehavior with strategy pattern
abstract class TurboChargerBehavior {
    boostEngine()
}

class AlpineTurboCharger extends TurboChargerBehavior {
    boostEngine()
}

class CumminsTurboCharger extends TurboChargerBehavior {
    boostEngine()
}

' NOS has two subclasses Remac and Sema
abstract class NOS {
    activateNOS()
    deactivateNOS()
}

class Remac extends NOS {
    activateNOS()
    deactivateNOS()
}

class Sema extends NOS {
    activateNOS()
    deactivateNOS()
}

' CarWithNos is a decorator that adds NOS to car
class CarWithNos extends Car {
    private NOS nos
    setNOS(NOS nos)
    activateNOS()
    deactivateNOS()
}

' Relationships between classes
Race --|> Car
Car --|> EngineBehavior
Car --|> TurboChargerBehavior
Car --|> NOS

@enduml
