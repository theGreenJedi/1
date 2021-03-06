# 1
Euler #1

---
date: 2015-04-01 19:15:16
title: Project Euler Problem 1 Solution
excerpt: This page presents solutions to Project Euler Problem 1 in C, Clojure, Go, Haskell, Python, Ruby and Scheme.
comments: true
math: true
---


## Question

If we list all the natural numbers below 10 that are multiples of 3 or 5, we 
get 3, 5, 6 and 9. The sum of these multiples is 23.

Find the sum of all the multiples of 3 or 5 below 1000.






## C

```c
#include <stdio.h>

int main(int argc, char **argv)
{
    int sum = 0;
    for (int i = 0; i < 1000; i++) {
        if (i % 3 == 0 || i % 5 == 0) {
            sum += i;
        }
    }
    printf("%d\n", sum);
    return 0;
}

```


```bash
$ gcc -march=native -Ofast -std=c11 -o natural natural.c
$ time ./natural
real   0m0.000s
user   0m0.000s
sys    0m0.000s
```



## Clojure

```clojure
#!/usr/bin/env clojure
(defn multiple? [n]
  (or (= (rem n 3) 0) (= (rem n 5) 0)))

(println (reduce + (filter multiple? (range 1000))))
```


```bash
$ time clojure natural.clj
real   0m1.676s
user   0m1.360s
sys    0m0.080s
```



## Go

```go
package main

import "fmt"

func main() {
    sum := 0
    for i := 0; i < 1000; i++ {
        if i%3 == 0 || i%5 == 0 {
            sum += i
        }
    }
    fmt.Println(sum)
}
```


```bash
$ go build -o natural natural.go
$ time ./natural
real   0m0.001s
user   0m0.000s
sys    0m0.000s
```



## Haskell

```haskell
main ::  IO ()
main = print $ sum [n | n <- [1..999], or [(n `mod` 3 == 0), (n `mod` 5 == 0)]]
```


```bash
$ ghc -O2 -o natural natural.hs
$ time ./natural
real   0m0.001s
user   0m0.000s
sys    0m0.000s
```



## Python

```python
#!/usr/bin/env python
print(sum(i for i in range(1000) if (i % 3 == 0) or (i % 5 == 0)))
```


```bash
$ time python3 natural.py
real   0m0.020s
user   0m0.016s
sys    0m0.000s
```



## Ruby

```ruby
#!/usr/bin/env ruby
sum = 0
1000.times do |i|
  if i % 3 == 0 or i % 5 == 0
    sum += i
  end
end
puts sum
```


```bash
$ time ruby natural.rb
real   0m0.029s
user   0m0.020s
sys    0m0.008s
```



## Scheme

```scheme
(display
  (reduce + 0
          (filter
            (lambda (n)
              (or (= (remainder n 3) 0) (= (remainder n 5) 0)))
            (iota 1000))))
(newline)
```


```bash
$ time mit-scheme-native --quiet < natural.scm
real   0m0.067s
user   0m0.048s
sys    0m0.020s
```


