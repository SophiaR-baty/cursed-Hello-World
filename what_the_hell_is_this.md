The single line in this program does a number of things...

1. creates a class called HelloWorld
2. defines `__enter__` for HelloWorld which prints the first half of the class name ("Hello") and ends with a " " instead of a new line
3. defines `__exit__` for HelloWorld which prints the second half of the class name ("World") and ends with a "!" instead of a new line
4. creates an instance of HelloWorld and uses it for a context construct (`with` keyword) -> before it enters the code after the with statement `__enter__` is called printing `"Hello "` and before it leaves the code block of the `with` statement, `__exit__` is called printing `"World!"`
5. The "code" in the with statements is an ellipsis `...` which doesn't do anything...

"Ok, that's great and all but what's all this gibberish with the `~` and `-` operators and how is the class named "HelloWorld" if there is no string in there??" you might ask. 

Well, it's quite simple (conceptionally). Let's first adress the negation `-` and binary complement `~` operators that are all over the single(!) line of code. The `~` operator returns the bitwise complement of a number. The formula for that is `~n=-n-1`. Now if you negate that: `-~n = -(-n-1) = n+1`. Suddenly we have incremented n by 1 😱
Of course using only that to obscure every integer would be boring so it uses two more tricks. Firstly creating integers using its constructor `int()` or by taking the length of an empty tuple `len(())` (I just thought it looked funny) to create an integer with value 0. Secondly dividing by 2 and taking powers of 2 with binary shift operators. 
So at multiple points you will see stuff like `-~len(())<<...` which is basically just `1<<...` which just gets you a power of 2. 

So how did I name the class and how did I define the functions? I first represented the desired string as an integer. `lol` would become `0x6C6F6C` because `l=0x6C` and `o=0x6F`. Obviously for longer strings the integer becomes musch larger like `0x4E6576657220476F6E6E61206769766520796F75207570` but luckily that's no problem for python
You can then just extract a byte at a time from the integer to create a string. 

Uhm... idk if I forgot something interesting but that's it for now ig
