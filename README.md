# Prime Stuff
Generating prime numbers, factoring, and recording them.

## Motivation
I want to make my own encryption function. Since prime numbers are the basis of most modern encryption first I'll need to generate a few and save them for later usage.

## Usage
Note that there are three primary usages of Factorization.py (which in hindsight is not aptly named). Between lines 144 and 153 different functions can be hashed/unhashed which allow the user to  
1. Find the prime factors of a number (and their associated exponents) or hopefully find that it is prime. Line 138 can be unhashed to auto generate an X digit number to test taking X as input or the user can input the number manually on line 137.  
2. Find all prime factors of a number  
3. Find and record one each of a 16, 17, 18, 19 digit prime number found at random. A starter .txt file is given as well that is meant to be used in conjuction. Have fun finding your own!

## Notes Learned Along the Way
* When factoring primes you need to test i=2 and then from 3 onwards can increment by 2 because testing i=2 already checks all even numbers
* a//b seems to be a bit faster than a/b when doing calculations and in most cases here they can be used interchangeably
* You could generate a number to test to be prime by using a random number generator and set it to find integers between 100 and 999 if you are looking for 3 digit primes. However, I used random number generators to produce digits 0-9, with constraints that the first digit cannot be 0 and the last cannot be even. Not sure if this is faster/more "random" but I prefer it.
* There are many ways to find prime numbers and ultimately in earlier work finding all consectuve lower digit primes (eg. all 9 digit primes in consecutive order) I used a prime seive. Before that I wanted to try a semi-original method I believe I came across in Matt Parker's [book](https://www.amazon.com/Things-Make-Fourth-Dimension-Mathematicians/dp/0374535639/ref=sr_1_1?ie=UTF8&qid=1542311155&sr=8-1&keywords=things+to+make+and+do+in+the+fourth+dimension+matt+parker) (or if not there then on his [YouTube channel](https://www.youtube.com/channel/UCSju5G2aFaWMqn-_0YBtq5A) somewhere). Anyway, all prime numbers x satisfy:  
![eqn](http://latex.codecogs.com/gif.latex?int%28%5Cfrac%7Bx%5E2-1%7D%7B24%7D%29%3D%5Cfrac%7Bx%5E2-1%7D%7B24%7D)  
However this rudimentary check also catches many composite numbers. Assuming we know a couple prime numbers to start (eg. 2, 3, 5) we can then check only previously found numbers thus reducing the number of verification calculations compared to brute force. Additionally a well known trick is to only check numbers up to the square root of the number we are testing for primality. Eg. we want to find that x is prime and if nothing factors out up to sqrt(x) we don't need to check past that. This is because if x did factor to a and b with a<b checking past sqrt(x) means we will only find b, which implies we should have already found a.  
This seems rather elementary, but normally when writing code, out of habit one might write a loop to check from 2 to x, which is much slower than checking 2 to sqrt(x). Overall this method still requires 2 separate checks and while it is 10-100x faster than a traditional brute force method, it is still 10-100x slower than a prime number seive depending on the magnitude of the x value we would like to find prime numbers up to.

## Limitations
The file only holds accuracy up to 19 digit numbers. Higher numbers will result in a RuntimeWarning: overflow encountered in long_scalars.

