#  MCON 264 — Recursion Assignment: Towers of Hanoi × 3


##  Overview

In this lab, you implemented three recursive versions of the Towers of Hanoi problem and (optionally) one iterative version.  
Each part reinforces a key concept of recursion — base case, recursive case, and growth pattern — and illustrates how recursion can be refactored or replaced by iteration.

---

## Part 1 — Classic Towers of Hanoi (`TowersOfHanoi.java`)

### 1. Base Case
_Describe the base condition that stops recursion (for example, what happens when `n == 0`?)._

> The method is returned

### 2. Recursive Case
_Explain the sequence of recursive calls and what each represents._

> ✎ solve(n-1, from, to, aux, moves);
solve(n - 1, aux, from, to, moves); 
> First ll the rings above the largest are moved to the middle ring and then the largest ring is moved to the last ring and then all the remaining rings are moved to the last ring above the largest.

### 3. Sample Trace (for n = 3)

| Move # | From | To |
|:------:|:----:|:--:|
|   1    |  A   | C  |
|   2    |  A   | B  |
|   3    |  C   | B  |
|   4    |  A   | C  |
|   5    |  B   | A  |
|   6    |  B   | C  |
|   7    |  A   | C  |

_Total moves = 2ⁿ − 1 = 7 (for n = 3)_

---

## Part 2 — Counting Moves (`TowersExercise21.java`)

### 1. Approach
_How did you modify the standard recursion to count rather than print moves?_

>  Instead of writing print statement, incremented count.

### 2. Verification of Formula
_Complete the table and verify that count = 2ⁿ − 1._

| n | Expected (2ⁿ − 1) | Program Output | Matches? (Y/N) |
|:--:|:--:|:--------------:|:--------------:|
| 1 | 1 |       1        |       Y        |
| 2 | 3 |       3        |       Y        |
| 3 | 7 |       7        |       Y        |
| 4 | 15 |       15       |       Y        |
| 5 | 31 |       31       |       Y        |

### 3. Reflection
_What changes when you replace printed moves with a counter? What are the pros and cons?_

> Pros: You see how many moves it takes to move all the ring from start to end pegs
> Cons: You cant see what actually happens when the disks are moved.

---

## Part 3 — Hanoi Variation (`TowersVariations.java`)

### 1. New Rule
_Every move must pass through the middle peg. How does this alter the recursion?_

> Now count must be incremented twice and extra recursive statement must be added.

### 2. Observed Move Counts

| n | Expected ≈ 3ⁿ − 1 | Program Output | Matches? (Y/N) |
|:--:|:--:|:--------------:|:--------------:|
| 1 | 2 |       2        |       Y        |
| 2 | 8 |       8        |       Y        |
| 3 | 26 |       26       |       Y        |
| 4 | 80 |       80       |       Y        |

### 3. Analysis
_Why does this variation grow faster than the standard version? How do additional move constraints affect complexity?_

> The variation grows faster because a move that would usually take one step is now taking two steps. This make the complexity greater and more time-consuming.

---

## Comparative Analysis

### 1. Growth Patterns

| Version | Approx. Formula | Growth Type |
|:--|:--|:--|
| Standard | 2ⁿ − 1 | Exponential |
| Variation | 3ⁿ − 1 | Exponential (faster) |
| Iterative (Optional) | 2ⁿ − 1 | Same as recursive but loop based |

### 2. Stack Depth and Memory
_Estimate the maximum recursion depth before StackOverflowError and discuss how stack size (–Xss flag) affects this._

> The maximum recursion depth can reach as far as the size of the stack frame size of the program since every time a recursion method is called again, a new stack is opened up to carry that call and return it when done.

---

## Part 4 — Beyond Recursion (Extra Credit)

### Iterative / Explicit-Stack Version (`TowersIterative.java`)

1. How does your iterative version simulate recursion?
2. How did you track pending calls or frames?
3. Which version (r vs iterative) is clearer? Why?

> Iterative versions simulate recursion by repeating a procedure until certain conditions and returning the method when the best case has been reached.
> Through iterations, you can use for loops to repeat procedures and create a variable called count that tracks the amount of calls.
> Recursion versions can be clearer than iterative versions and at other times it is the opposite. The approach to use either one depends on each situation and problem to be solved. Yet, recursive is generally easier to read and more clear.

---

## Discussion &amp; Reflection

1. What three questions can you use to verify a recursive solution works?
2. How do the base case and recursive case cooperate to guarantee termination?
3. What is the trade-off between elegance and efficiency in recursion?

> What is the best-case, what is the smaller-case, and what's the general-case?
> The recursive case must bring the method bit by bit toward the best case until the method is finally returned.
>Recursion is very beneficial for its sweet and short, clear design. However, recursion can run into issues like stack overflow, call overhead, and extra memory usage.
> 

---

## References (APA or MLA format)

- Dale, N., Joyce, D., &amp; Weems, C. (2016). *Object-Oriented Data Structures Using Java* (Ch. 3 Recursion). Jones &amp; Bartlett.
- Additional videos or websites you consulted (YouTube CS50 Recursion, GeeksForGeeks Hanoi, etc.)

---

 **Submission Checklist**

- [ ] `TowersOfHanoi.java` — implemented and tested
- [ ] `TowersExercise21.java` — counts moves correctly
- [ ] `TowersVariations.java` — middle-peg constraint implemented
- [ ] (Extra Credit) `TowersIterative.java` — loop or explicit stack solution
- [ ] All JUnit tests pass (green on GitHub Actions)
- [ ] This `ANSWERS.md` file completed and committed to repo  
