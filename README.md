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
- **"Ahoj!"** pushes the string onto stack
- **123456789** pushes the int number onto the stack

## Builtins
- **concat** [1 2 3] [4 5 6 7] -> [1 2 3 4 5 6 7] 
- **cons** 3 [4 5] -> [3 4 5]

### General combinators 
- **map** [* dup] [1 2 3 4] -> [1 4 9 16]
- **do** quotation - the _do_ combinator pops the _quotation_ off the stack and executes it, effectively by dequoting
- example: **do [* dup]** - computes sqr from top of stack, effectively doing
- * dup tos nos ... =>  * tos tos nos ... => sqr(tos) nos ...

### Conditionals and loops
- **if** [gte0] [+ 1]
- **ifte** [gte0] [+ 1] [- 1]
- **while** [gte0] [- 1]
- **repeat** 5 [* 2]
