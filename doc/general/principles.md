# Principles

This part of the documentation gives an overview of the used software development principles in the trckr project.

## SOLID

The main principle we use in our project is [SOLID](https://en.wikipedia.org/wiki/SOLID_(object-oriented_design)):

* Single responsibility principle
A class should have only a single responsibility (i.e. changes to only one part of the software's specification should be able to affect the specification of the class).

* Open/closed principle
"Software entities … should be open for extension, but closed for modification."

* Liskov substitution principle
"Objects in a program should be replaceable with instances of their subtypes without altering the correctness of that program." See also design by contract.

* Interface segregation principle
"Many client-specific interfaces are better than one general-purpose interface."

* Dependency inversion principle
One should "depend upon abstractions, [not] concretions."

## DRY

Furthermore, it is very important to follow the [DRY (Don't repeat yourself)](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself) principle.

