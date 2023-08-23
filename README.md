## Introduction
Substitution System is a map which uses a set of rules to transform elements of a sequence  
into a new sequence using a set of rules which "translate" from the original sequence to its transformation.   
For example, the substitution system `{1 → 0,0 → 11}` would take `10 → 011 → 1100 → 001111 → 11110000 →...`  
(From [Mathworld](https://mathworld.wolfram.com/SubstitutionSystem.html))

## General 
This project is based on Wolfram Mathematica functions [SubstitutionSystem](https://reference.wolfram.com/language/ref/SubstitutionSystem.html), [SequenceReplace](https://reference.wolfram.com/language/ref/SequenceReplace.html) and [MultiwaySystem](https://resources.wolframcloud.com/FunctionRepository/resources/MultiwaySystem) which implemented in [Julia](https://julialang.org/) for speed and perfomance.  
Currently functions work for strings and 1D arrays (vectors).  

## Rules
Отдельное правило выглядит как `lhs => rhs`. 
Если `lhs == rhs` - это тавтология, которая оставляет sequence неизменной.  
Сохранять ее или удалять, зависит от цели.   
Они объединены в вектор, потому что *порядок имеет значение*.  
Все `lhs` должны быть разными! А вот `rhs` могут быть одинаковыми.
Правила генерируются в отдельном модуле [Rules.jl](), их можно использовать для других целей.
На вход принимается алфавит и возможные длины `lhs` и `rhs` в виде `UnitRange`
Есть два метода генерации: 
- создание массива всех комбинаций
- итератор

## Types of transformations
### One-way systems
Основано на поведении [SequenceReplace](https://reference.wolfram.com/language/ref/SequenceReplace.html).  
На вход подается:
- Начальная sequence
- Набор правил `lhs1 => rhs1, ..., lhM => rhsM`
- Число шагов
- Обозначение метода: выдавать весь массив промежуточных результатов или последний из них
Sequence проходится курсором. Правила проходятся по порядку.
Если найдено правило, для которого существует `lhs` начиная с данной позиции, она заменяется на `rhs` 
и курсор ставится в первую позицию, следующую за `rhs`.

### Multiway systems


