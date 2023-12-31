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
- simple type literal means the command "push it onto the stack"

Examples:
- **"Ahoj!"** pushes the string onto stack
- **123456789** pushes the int number onto the stack
- **-123.4** pushes the double onto the stack

## Builtins

### List (quoted) commands
- **concat** [1 2 3] [4 5 6 7] -> [1 2 3 4 5 6 7] 
- **cons** 3 [4 5] -> [3 4 5]
- **rest** [1 2 3] -> [2 3]
- **first** [1 2 3] -> 1

### General combinators 
- **map** [* dup] [1 2 3 4] -> [1 4 9 16]
- **fold** TODO
- **do** quotation - the _do_ combinator pops the _quotation_ off the stack and executes it, effectively by dequoting
- example: **do [\* dup]** - computes _sqr_ from top of stack, effectively doing
- \* dup tos nos ... =>  \* tos tos nos ... => sqr(tos) nos ...

### Conditionals and loops
- **if** [positive] [+ 1]
- **ifte** [positive] [+ 1] [- 1]
- **while** [positive] [--]
- **times** n quotation - executes the _quotation_ _n_-times

## Predicates
- leave boolean on the stack based on the condition

### Type predicates
- type checking: boolean    char    int    double    string

### Quotations
- predicates for numbers: odd    even    positive    negative
- predicates for aggregates: in    has empty
- predicates for strings: empty
- **some** quotation - true iff some item(s) in quotation evaluate to true
- **all** quotation - true iff all items in quotation evaluate to true

## Complete list of builtin words
- I/O: PRINT, PRINTLN, INPUT
- general control: CLEAR
- execute quoted: DO
- print and empty stack: DUMP
- swap tos/nos: SWAP, duplicate tos: DUP, duplicate tos+nos: DUP2
- arithmetic: INC, DEC, ADD, SUB, MUL, DIV, MOD, POWER
- quit program: BYE
- loop n-times: TIMES
- string(s) SPLIT, CONCAT
- pick n-th from stack: PICK 
- comparison: GT, LT, GT0,  LT0, EQUAL, NOTEQUAL, LTE, GTE, LTE0, GTE0,
- logical: AND, OR, NOT

# Legacy of other stack languages
## Factor
### Builtins
- `drop ( x -- )`
- `dup ( x -- x x )`
- `over ( x y -- x y x )`
- `swap ( x y -- y x )`

- `2 even? [ "OK" ] [ "Cosmic rays detected" ] if`
- `{ "veni" "vidi" "vici" } [ print ] each`
- `{ 1 2 3 4 } 0 [ + ] reduce`

```
: tail-factorial ( accumulator n -- n! )
dup 0 =
  [ drop ]
  [ [ * ] [ 1 - ] bi tail-factorial ]
  if ;
: factorial ( n -- n! )
  1 swap (factorial) ;
```

## Joy

## Forth


