Monty
The Monty language :

Monty is a programming and scripting language.
This language was designed by David A. Watt.

Usage :

monty file : where file is the path to the file containing Monty byte code

If the user does not give any file or more than one argument to your program, print the error message USAGE: monty file, followed by a new line, and exit with the status EXIT_FAILURE.

If, for any reason, it’s not possible to open the file, print the error message Error: Can't open file , followed by a new line, and exit with the status EXIT_FAILURE
where is the name of the file

If the file contains an invalid instruction, print the error message L<line_number>: unknown instruction , followed by a new line, and exit with the status EXIT_FAILURE
where is the line number where the instruction appears.
Line numbers always start at 1

The monty program runs the bytecodes line by line and stop if either:
it executed properly every line of the file
it finds an error in the file an error occured

If you can’t malloc anymore, print the error message Error: malloc failed, followed by a new line, and exit with status EXIT_FAILURE.

You have to use malloc and free and are not allowed to use any other function from man malloc (realloc, calloc, …)

Operations : List of monty operations this interpreted understands:

push <integer>: pushes an integer on to the stack
pall: prints the values of every node on the stack
pint: prints the value of the node at the top of the stack
pop: removes the node at the top of the stack
swap: swaps the position of the top two nodes
add: places the sum of the top two nodes into the 2nd node and removes the first
sub: subtracts the top element of the stack from the second top element of the stack
div: divides the second top element of the stack by the top element of the stack
mul: multiples the second top element of the stack with the top element of the stack
mod: computes the rest of the division of the second top element of the stack by the top element of the stack
pchar: prints the char at the top of the stack, followed by a new line
pstr: prints the string starting at the top of the stack, followed by a new line
rotr: rotates the stack to the bottom
rotl: opcode rotate the stack to the top
File Name	Description :
main.c	Main program file
monty.h	Header file
get_op_func.c	function selects the correct func to perform the operation
_pall.c	opcode print all the values on the stack, starting from the top
_pint.c	opcode print the value at the top of the stack
_push.c	opcode pushe an element to the stack
_swap.c	opcode swap the top two elements of the stack
_add.c	opcode add the two tops elements of the stack
_sub.c	opcode subtract the top element of the stack from the second top element of the stack
_div.c	opcode divide the second top element of the stack by the top element of the stack
_mul.c	opcode multiple the second top element of the stack with the top element of the stack
_mod.c	opcode compute the rest of the division of the second top element of the stack by the top element of the stack
_pchar.c	opcode print the char at the top of the stack, followed by a new line
_pstr.c	opcode print the string starting at the top of the stack, followed by a new line
_rotr.c	opcode rotate the stack to the bottom
_rotl.c	opcode rotate the stack to the top
General :
What do LIFO and FIFO mean?

FIFO stand for First In First Out

LIFO stand for Last In First Out
Compilation & Output :

typedef struct stack_s
    {
    int n;
    struct stack_s *prev;
    struct stack_s *next;
    } stack_t;


typedef struct instruction_s
    {
    char *opcode;
    void (*f)(stack_t **stack, unsigned int line_number);
    } instruction_t;
Compilation & Output :

Your code will be compiled this way :
    $ gcc -Wall -Werror -Wextra -pedantic -std=c90 *.c -o monty

