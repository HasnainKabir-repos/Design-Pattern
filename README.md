## Singleton Pattern

--- Player class

## Strategy Pattern

--- EngineBehavior superclass
--- V6Engine, V8Engine, V12Engine subclasses
--- Car is abstract class that acts as a context class to wrap those subclasses


--- TurbochargerBehavior superclass
--- AlpineTurboCharger, CumminsTurbocharger subclasses
--- Car is abstract class that acts as a context to wrap these

## Template Pattern

--- Race class where template method is the race method

## Factory pattern

--- Track superclass
--- BBRaceWayTrack, BlueMoonBaySpeedWayTrack, CircuitDeSpaFrancorchampsTrack subclasses

----- Factory method exists on the Rii class in the Main directory

### Abstract Factory

--- CarFactory is the abstract factory
--- CoupeCarFatory and RoadsterCarFactory are concrete factories

### Decorator Pattern

--- CarWithNos is the decorator class that adds NOS to car
--- Can be chosen by user if the car has NOS or not

--- NOS has two subclasses ResonacNos and SemaNos
