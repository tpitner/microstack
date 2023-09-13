# MicroStack
Stack-based concatenative prefix programming language

## Principles
- highly inspired of Forth, Joy
- based on new word definitions 
- instead of postfix, it uses prefix notation
- uses more stacks
- it makes short programs more readable

## Syntax
- prefix notation
2 3 + dup * -> mult dup plus 2 3 (or * dup + 2 3)
- quoted sequences

## Literals 
- Java style and syntax
- Java types: byte, short, int, long; double, boolean, char, String
- **"Ahoj!"** -> pushes the string onto stack

## Builtins
- **concat** [1 2 3] [4 5 6 7] -> [1 2 3 4 5 6 7] 
- **cons** 3 [4 5] -> [3 4 5]

### General combinators 
- **map** [* dup] [1 2 3 4] -> [1 4 9 16]
- **do** [* dup] -> computes sqr from top of stack

### Conditionals and loops
- **if** [gte0] [+ 1]
- **ifte** [gte0] [+ 1] [- 1]
- **while** [gte0] [- 1]
- **repeat** 5 [* 2]
