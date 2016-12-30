# Single responsibility SRP
 - A unit must have one reason to change; or basically has to do one thing, have one job

# Open closed OCP
 - Entities should open for extension but closed for modification
 - Polymorphism
 - When you have a module that need extension without modification, separate the extensibehavior behind an interface and flip the dependencies

# Liskov substitution LSP
 - Derived classes must be substitute for their base classes.

# Interface segregation ISP
 - A client should not be forced to implement an interface (like methods) that it doesn't use.
 - Separate in smaller chunks, segregate, don't use fat interfaces.

# Dependency inversion DIP
 - Code to an interface.
 - High level modules should not depend on low level modules.
 - Depends on abstractions, not on concretions.
 - Low level code is more concerned with details and specifics.