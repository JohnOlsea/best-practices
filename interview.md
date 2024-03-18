# Interview Problems

## Code, Consult, Communicate

Todo List

Let’s start with the good-old trusty todo list, the “Hello, World” of full programs. You’re going to write a command-line todo list program that meets the following specifications:

1. Prompt the user to enter a chore or task. Store the task in a permanent location so that the task persists when the program is restarted.
2. Allow the user to enter as many tasks as desired but stop entering tasks by entering a blank task. Do not store the blank task.
3. Display all the tasks.
4. Allow the user to remove a task, to signify it’s been
completed.
5. Persist todos to Redis

## Easy
1. Write a program that prints the numbers from 1 to 100. But for multiples of three print “Fizz” instead of the number and for the multiples of five print “Buzz”. For numbers which are multiples of both three and five print “FizzBuzz”.

  **Example Output:**
  ```
  1 2 Fizz 4 Buzz Fizz 7 8 Fizz Buzz 11 Fizz 13 14 FizzBuzz 16 17 Fizz 19 Buzz
  Fizz 22 23 Fizz Buzz 26 Fizz 28 29 FizzBuzz 31 32 Fizz 34 Buzz Fizz 37 38 Fizz Buzz
  41 Fizz 43 44 FizzBuzz 46 47 Fizz 49 Buzz Fizz 52 53 Fizz Buzz 56 Fizz 58 59 FizzBuzz
  61 62 Fizz 64 Buzz Fizz 67 68 Fizz Buzz 71 Fizz 73 74 FizzBuzz 76 77 Fizz 79 Buzz
  Fizz 82 83 Fizz Buzz 86 Fizz 88 89 FizzBuzz 91 92 Fizz 94 Buzz Fizz 97 98 Fizz Buzz
  ```
def fizzbuzz():
    for i in range(1, 101):
        if i % 3 == 0 and i % 5 == 0:
            print("FizzBuzz", end=" ")
        elif i % 3 == 0:
            print("Fizz", end=" ")
        elif i % 5 == 0:
            print("Buzz", end=" ")
        else:
            print(i, end=" ")

fizzbuzz()

2. Write a program that determine whether or not an integer input is a leap year.
  - Definition of leap year:
    - Rule 1: A year is called leap year if it is divisible by 400.

      **Example:** 1600, 2000 etc. are leap year while 1500, 1700 are not leap year.
    - Rule 2: If year is not divisible by 400 as well as 100 but it is divisible by 4 then that year are also leap year.

      **Example:**  2004, 2008, 1012 are leap year.

  **Example Output:**
  ```
  1600 -> true
  2000 -> true
  1500 -> false
  2004 -> true
  2008 -> true
  2010 -> false
  ```
def is_leap_year(year):
    if year % 400 == 0:
        return True
    elif year % 100 != 0 and year % 4 == 0:
        return True
    else:
        return False
years = [1600, 2000, 1500, 2004, 2008, 2010]

for year in years:
    print(f"{year} -> {is_leap_year(year)}")

3. Write a program that produce the following output giving an integer input n.
  * 3.1
```
n=3   n=4    n=6
*     *      *
**    **     **
***   ***    ***
      ****   ****
             *****
             ******
```
def print_pattern(n):
    for i in range(1, n + 1):
        print("*" * i)

inputs = [3, 4, 6]

for n in inputs:
    print(f"n={n}")
    print_pattern(n)
    print()

  * 3.2
```
n=3    n=4      n=6
  *      *        *
 **     **       **
***    ***      ***
      ****     ****
              *****
             ******
```
def print_pattern(n):
    for i in range(1, n + 1):
        spaces = " " * (n - i)
        stars = "*" * i
        print(spaces + stars)

inputs = [3, 4, 6]

for idx, n in enumerate(inputs):
    print(f"n={n}")
    print_pattern(n)
    if idx < len(inputs) - 1:
        print()

  * 3.3
```
n=1    n=2      n=3    	  n=4       n=5
*       *        *         *         *
       * *      * * 	  * *       * *
               *   *	 *   *     *   * 		    
                        *     *   *     *
                                 *       *          
        
```
def print_pattern(n):
    for i in range(1, n + 1):
        print(" " * (n - i), end="")
        print("*", end="")
        if i > 1:
            print(" " * ((i - 1) * 2 - 1) + "*", end="")
        print()
	
inputs = [1, 2, 3, 4, 5]

for n in inputs:
    print(f"n={n}")
    print_pattern(n)
    print("\n")


  * 3.4
```
n=1	n=2	n=3	n=4     n=5
*	**	* *	*  *	*   *
	**	 * 	 **      * *
		* *	 **       *  
			*  *	 * *
				*   *
```
def print_pattern(n):
    for x in range(n):
        for y in range(n):
            if x == y or n - x - 1 == y:
                print("*", end="")
            else:
                print(" ", end="")
        print()

print_pattern(1)
print_pattern(2)
print_pattern(3)
print_pattern(4)
print_pattern(5)

  * 3.5  (NB: Not easy)
```
n=1  n=2  n=3   n=4    n=5        n=9
*    *     *     *      *          *
     *    ***   ***    ***        ***
           *    ***   *****      *****
                 *     ***      *******
                        *      *********
                                *******
                                 *****
                                  ***
                                   *
```
def print_pattern(n):
    for i in range(1, n + 1):
        if i % 2 != 0:
            spaces = " " * ((n - i) // 2)
            stars = "*" * i
            print(spaces + stars)

    for i in range(n - 1, 0, -1):
        if i % 2 != 0:
            spaces = " " * ((n - i) // 2)
            stars = "*" * i
            print(spaces + stars)

inputs = [1, 2, 3, 4, 5, 9]
for case in inputs:
    print("n=" + str(case))
    print_pattern(case)
    print()

  * 3.6
```
n=1     n=2     n=3         n=4
+       A+B     AA+BB       AAA+BBB
        +E+     A+E+B       AA+E+BB
        C+D  	+EEE+       A+EEE+B
                C+E+D       +EEEEE+
                CC+DD       C+EEE+D	
                            CC+E+DD
                            CCC+DDD
```

def sequence(d):
   c, l = 0, 1
   while c < d - 1:
     if l%2:
       yield l
       c += 1
     l += 1

def make_pattern(d):
   t, b, r = f'{"A"*(d-1)}+{"B"*(d-1)}', f'{"C"*(d-1)}+{"D"*(d-1)}', list(sequence(d))
   body = '\n'.join(f'{"A"*((r[-1]-i)//2)}+{"E"*i}+{"B"*((r[-1]-i)//2)}' for i in r[:-1]) + \
     f'\n+{"E"*r[-1]}+\n'+'\n'.join(f'{"C"*((r[-1]-i)//2)}+{"E"*i}+{"D"*((r[-1]-i)//2)}' for i in r[:-1][::-1])
   return f'{t}\n{body}\n{b}'

def diamond(d):
  return {1:lambda _:'+', 2:lambda _:'A+B\n+E+\nC+D'}.get(d, make_pattern)(d)

print(diamond(1))
print('-'*5)
print(diamond(2))
print('-'*5)
print(diamond(3))
print('-'*5)
print(diamond(4))

4. (Python specific) In Python, what is the difference between `else` and `finally` in exception handling?
- `else` block executes when no exception occurs in the try block.
- `finally` block always executes, whether an exception occurs or not.

## Medium
1. Write a program that finds all prime numbers up to n for input n.
**Example Output:**
```
20 -> 2 3 5 7 11 13 17 19
```
def find_primes(n):
    primes = []
    for num in range(2, n + 1):
        if all(num % i != 0 for i in range(2, int(num ** 0.5) + 1)):
            primes.append(num)
    return primes

def main():
    n = int(input("Enter a number: "))
    prime_numbers = find_primes(n)
    print("Prime numbers up to", n, ":", *prime_numbers)

if __name__ == "__main__":
    main()


## Hard
