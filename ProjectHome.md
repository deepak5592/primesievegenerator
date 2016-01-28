It uses a very simple algorithm and "C++ Big Integer Library" to generate prime numbers with arbitrary number of decimal places (you are limited only by memory of your computer).


Algorithm:

- Given P (A big enough integer with random digits: digits are provided manually because we don't trust pseudo-random number generators)

- Given "Enough" K random integers (smaller than P)

- We search GCD(P, K(i)) for each i.

- If all GCDs are 1, then test pass and number is returned (probably a prime number), else we repeat for P++.


1000 digits requires approx 10 minutes on my 2Ghz core. This algorithm can be highly parallelized (each GCD can computed in a different thread): current code is single-threaded by the way.

The algorithm try to estimates "K", if P is 10^1000, then K is choosen so that
((6/(PI\*PI))^K)

is smaller than

(1/10^1000).

For 1000 decimal digits (3000+ binary digits) estimated K is 2048, but probably a smaller K is enough (You can use bigger K as well ^^)