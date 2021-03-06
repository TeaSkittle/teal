# teal

An esoteric programming language based on a simple transpiler written in Bash. Essentially this language compiles to C using gcc, but forces certain concepts and styling to itself. The transpiler uses regex with sed, grep, and awk in a rather hacky way and translates itself to C and then compiles. It is meant to be used as a hobby language for fun, hence why I am referening to it as an esotreric language. This is very much a work in progress, so use with a grain of salt.

## Design Features

Overall *teal* is designed to be a safe functional-styled language with C-like syntax.

- Aimed at x86 (32-bit)
- No NULL
- No void
- No undefined variables
- No for or while loops (only recursion is allowed)
- Immutable varables by default
- Various unsafe C functions are not allowed: strcpy, strcat, and more...

## FizzBuzz

Here is a FizzBuzz program as a proof of concept:
```C
// teal FizzBuzz example
import stdio

int fizzBuzz( int i, int j ){
	if( i <= j ){
		if( i % 15 == 0 ){
			printf( "%s\n", "FizzBuzz" );
			i++;
			fizzBuzz( i, j );
		} else if( i % 3 == 0 ){
			printf( "%s\n", "Fizz" );
			i++;
			fizzBuzz( i, j );
		} else if( i % 5 == 0 ){
			printf( "%s\n", "Buzz" );
			i++;
			fizzBuzz( i, j );
		} else {
			printf( "%d\n", i );
			i++;
			fizzBuzz( i, j );
		}
	} return 0;
}

int main(){
	fizzBuzz( 0, 100 );
	return 0;
}
```

## Compiling

To compile and run *teal* code, first ensure *teal* is executable and run the transpiler:
```Bash
chmod +x teal
teal FizzBuzz.t
./a.out
```
