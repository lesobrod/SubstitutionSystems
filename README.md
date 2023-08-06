## Introduction
Substitution System is a map which uses a set of rules to transform elements of a sequence  
into a new sequence using a set of rules which "translate" from the original sequence to its transformation.   
For example, the substitution system `{1->0,0->11}` would take `10->011->1100->001111->11110000->...`  
(From [Mathworld](https://mathworld.wolfram.com/SubstitutionSystem.html))
## General 
This project is based on Wolfram Mathematica functions [SubstitutionSystem](https://reference.wolfram.com/language/ref/SubstitutionSystem.html) and [MultiwaySystem](https://resources.wolframcloud.com/FunctionRepository/resources/MultiwaySystem) which implemented in [Julia](https://julialang.org/)  
for speed and perfomance.  
Rules have to applyed in the given order. So `Vector{Pair{String, String}}` is used for rules.
## Types of objects
Currently functions work for strings and 1D arrays (vectors).
## Types of transformations

